---
title: Varnish Cache dla miękkich form inteligencji
---

# Wdrożenie z miękkiej perspektywy

Nigdy nie miałem okazji wdrażać Varnisha (ani innego web acceleratora czy reverse proxy) siedząc bezpośrednio przy kodzie. Jednak w ostatnim czasie przeszedłem przez cały proces implementacji rozwiązania z punktu widzenia project managera. Słownictwo wykorzystywane przez programistów podczas prac nad Varnishem zazwyczaj jest bardzo wysokopoziomowe, ponieważ zakłada, że menadżer i tak nie zrozumie szczegółów rozwiązania lub wręcz przeciwnie - jest bardzo techniczne i wtedy rzeczywiście PM nic z tego nie rozumie.

Poniższy artykuł ma na celu wyjaśnienie podstawowych pojęć związanych z Varnishem, aby osoby niebędące specialistami w tym zakresie były w stanie zrozumieć, o czym mówią programiści.

# Web accelerator czy Reverse proxy?

Varnish jest zazwyczaj nazywany web acceleratorem lub reverse proxy. Skąd pochodzą te nazwy? Akceleracja sugeruje, że głównym zadaniem narzędzia jest przyśpieszanie działania strony. W najprostszym rozumieniu działania Varnisha można tak go określić. Varnish tworzy warstwę stojącą między użytkownikiem i serwerem aplikacyjnym (dla uproszczenia załóżmy, że mamy do czynienia z aplikacją monolityczną uruchomioną na jednym serwerze aplikacyjnym), i jego głównym zadaniem jest redukowanie obciążenia aplikacji przez cacheowanie powtarzalnych żądań, które następnie będzie można serwować użytkownikom bez odwoływania się do serwera aplikacyjnego.

Poza mechanizmem cacheowania dostarcza on szersze rozwiązania jak np. load balancing. Na potrzeby tego artykułu skupimy się jednak głównie na cache.

Aby zrozumieć pojęcie reverse proxy wyjaśnijmy w uproszczeniu, czym jest serwer proxy. Wyobraźmy sobie, że jesteśmy użytkownikiem Internetu, który chce włamać się na stronę banku internetowego. W celu ukrycia swojej tożsamości korzystamy z serwera proxy, który będzie pośredniczył w ruchu między nami i bankiem. Dzięki wykorzystaniu takiego pośrednika można powiedzieć, że “chowamy się” za nim i z punktu widzenia ofiary (banku) to serwer proxy włamuje się do banku, a nie my. Wysyłane przez nas żądanie trafia do serwera proxy, następnie do banku, odpowiedź zwracana jest do serwera proxy i na końcu do nas.

Reverse proxy to podobny mechanizm, ale stojący po drugiej stronie płotu. W tym wypadku to serwer (a nie użytkownik) “chowa się” za serwerem reverse proxy, który symuluje jego zachowanie. Z perspektywy użytkownika wysyłamy żądanie do naszej aplikacji, które tak naprawdę trafia do serwera reverse proxy. Ten serwer decyduje czy odpowie nam samodzielnie, czy przekaże nasze zapytanie do prawdziwego serwera aplikacyjnego.

# Podstawowa zasada działania cache w Varnishu

Proces wygląda następująco:

*   Użytkownik wchodzi na stronę internetową.
*   Żądanie HTTP trafia do Varnisha:
    *   Jeżeli Varnish posiada aktualny cache elementu, o który jest proszony to odsyła response użytkownikowi.
    *   Jeżeli Varnish nie posiada aktualnego cache elementu to przekazuje request do serwera aplikacyjnego i w dalszej kolejności zwraca odpowiedź użytkownikowi na podstawie danych otrzymanych od serwera aplikacyjnego.

# VCL, Varnish Configuration Language

Językiem, w którym tworzymy konfigurację Varnisha jest VCL. W rozmowach z programistami określenie VCL często jest skrótem myślowym do określenia pliku konfiguracyjnego Varnisha. VCL pozwala nam na dostosowanie narzędzia do naszych potrzeb.

# Czas ważności (TTL) i typ cache

Podstawowym podziałem cacheowanych w Varnishu elementów jest rozdzielenie contentu statycznego od dynamicznego. Przykładem contentu statycznego może być logo firmy, które zazwyczaj jest niezmienne. Przykładem contentu dynamicznego może być wielkie zdjęcie obrazujące stan magazynowy towaru w sklepie internetowym, które jest aktualizowane co 30 minut.

Dla dwóch powyższych typów zawartości strony możemy zdefiniować czasy TTL (time-to-live), które określą czas ważności cache liczony od momentu jego utworzenia. Przykładowo, określamy TTL na 60 minut. Jeżeli wejdziemy na stronę internetową to bazując na naszej wizycie jej cache zostanie stworzony w Varnishu i wszyscy kolejni użytkownicy wchodzący na tą samą stronę w ciągu najbliższych 60 minut otrzymają zawartość strony bardzo szybko, ponieważ odpowiedź zostanie przygotowana w warstwie reverse proxy, bez wykorzystania serwera aplikacyjnego. Umożliwia nam to bardzo szybkie pokazanie strony internetowej użytkownikowi, ale generuje ryzyko, że w ciągu tych 60 minut strona w serwerze aplikacyjnym zostanie zaktualizowana - wtedy użytkownicy będą otrzymywać nieaktualną wersję strony, aż do zakończenia czasu TTL.

Parametrem mówiącym o wieku danego elementu cache jest Age, który przedstawia nam wartość w postaci ilości sekund - od chwili utworzenia cache, do teraz. Gdy Age zrówna się z TTL - cache uznawany jest za nieaktualny.

# Grace Time

Czas “ważności” cache można w awaryjnych sytuacjach wydłużyć. Varnish od wersji 4 pozwala na zdefiniowanie tak zwanego czasu Grace Time. Określa on czas ponad TTL w ciągu którego możemy pogodzić się z odpowiedzią użytkownikowi nieaktualną zcacheowaną wersją strony, gdy napotkamy problem z uzyskaniem odpowiedzi od serwera aplikacyjnego.

Przykładem zastosowania grace time może być sytuacja, w której czas ważności cache konkretnej strony minął, użytkownik przesyła request o daną stronę, z poziomu Varnisha okazuje się że serwer aplikacyjny jest niedostępny lub bardzo obciążony, Varnish sprawdza grace time danego elementu i jeżeli konfiguracja pozwala nam na pogodzenie się z faktem nieaktualnej odpowiedzi to Varnish odpowiada użytkownikowi.

Równolegle do przeprowadzania tej operacji, Varnish jest w stanie zainicjować proces odświeżający pamięć podręczną danego elementu, aby została ona zaktualizowana w osobnym wątku na potrzeby przyszłych użytkowników.

# Health check

W celu określenia wydajności działania backendu oraz podjęcia decyzji o wykorzystaniu grace time Varnish pozwala na wykonywanie health checków. Sposób ich działania jest samoopisujący się przez poniższy kod pochodzący z dokumentacji Varnisha.

```
backend server1 {
  .host = "server1.example.com";
  .probe = {
         .url = "/";
         .interval = 5s;
         .timeout = 1 s;
         .window = 5;
         .threshold = 3;
    }
  }

```

# Automat skończony (finite state machine)

W celu rozwiązania wcześniej przedstawionego problemu możliwej nieaktualności pamięci podręcznej musimy zrozumieć stany, jakie występują w Varnishu, który bywa nazywany skończoną maszyną stanów / automatem skończonym / finite state machine.

Stany można rozumieć jako sposób obsłużenia danego żądania HTTP, które trafia do Varnisha. Podstawowe z nich to:

*   `miss` - Żądanie od użytkownika przechodząc przez Varnish szukało i nie znalazło zcacheowanej wersji elementu, którego potrzebowało. W takiej sytuacji konieczne jest odwołanie się do z aplikacji.
*   `pass` - Żądanie nie szukało wersji zcacheowanej, a jedynie “przeszło” przez Varnisha prosto do aplikacji. W momencie zwracania odpowiedzi również nie jest ono cacheowane.
*   `hit` - Żądanie znalazło aktualny cache w Varnishu. Pobiera element z cache i zwraca odpowiedź użytkownikowi. Nie obciąża aplikacji.
*   `hit_for_pass` - Typ akcji, który mówi o tym, że Varnish to nie tylko warstwa cache, a także mądre oprogramowanie stanowiące firewall stojący przed aplikacją. `hit_for_pass` to działanie, przy którym w cache nie znajduje się zcacheowany obiekt i inicjuje ono pobranie go z aplikacji. Oznacza jednak dane żądanie jako “w trakcie pobierania” i dzięki temu inni użytkownicy aplikacji, którzy zapytają o to samo nie generują kolejnych żądań odwołania do backendu, a czekają w warstwie reverse proxy, aż to jedno dojdzie z aplikacji do Varnisha. Dzięki temu, w przypadku 1000 użytkowników pytających o to samo przekazujemy 1 żądanie do aplikacji, 999 żądań czeka w Varnishu. Gdy odpowiedź wróci do Varnisha z backendu - otrzyma ją 1000 użytkowników.
*   `waiting` - Akcja określająca, że żądanie użytkownika czeka na aktualizację wynikającą z innego żądania `hit_for_pass`.

Kompletną listę stanów i wyjaśnienie ich działania warto przestudiować w rozdziałach [VCL Basics](https://book.varnish-software.com/4.0/chapters/VCL_Basics.html) oraz [Build in subroutines](https://varnish-cache.org/docs/trunk/users-guide/vcl-built-in-subs.html.) zawartych w oficjalnej dokumentacji.

# Inwalidacja cache

> There are 2 hard problems in computer science: cache invalidation, naming things, and off-by-1 errors.
> 
> – Phil Karlton (edited by: Leon Bambrick)

Większość systemów nie opiera się jedynie na samym odczytywaniu danych, a pozwala dodatkowo na ich modyfikację. Programista implementujący rozwiązanie jest w stanie wyznaczyć operacje, które powinny natychmiastowo wymuszać wyczyszczenie cache. Przykładem może być aktualizacja nazwy produktu w sklepie internetowym. Załóżmy, że nasza strona produktowa jest na tyle niezmienna, że cacheujemy ją w pełni. Pewnego dnia, administrator sklepu aktualizuje nazwę produktu. W związku z tym, użytkownicy wchodzący na omawianą stronę powinni zobaczyć jego nową nazwę. W tym celu programista po zapisaniu produktu w panelu administracyjnym może wyczyścić dane elementy cache omawianej strony produktowej i tym samym wymusić załadowanie nowej zawartości strony wprost z serwera aplikacyjnego.

Do przeprowadzania powyższych operacji korzystamy z dwóch typów żądań. Pierwsze z nich to `purge`, który pozwala nam na wyczyszczenie pamięci podręcznej konkretnego adresu URL / elementu. Wywoływany jest on podobnie do typowych requestów HTTP GET. Drugim typem żądania jest `ban`, który na podstawie wskazanego wyrażenia regularnego może nam pomóc z wyczyszczeniem cache wielu stron / elementów. Ban może również zostać wywołany podobnie do requestu HTTP, ale domyślnym momentem jego uruchamiania jest moment trafienia w cache (`hit`).

# Edge Side Includes

W celu zoptymalizowania procesu inwalidacji cache możemy wykorzystać mechanizm ESI. Pozwala on na wyznaczenie w obrębie strony konkretnych elementów, które nie powinny być cacheowane. Przykładowo, decydujemy się trzymać w cache całą stronę karty produktu, ale zauważamy na niej dwa elementy, które często się zmieniają - cena oraz stan magazynowy. Te dwa elementy możemy otoczyć blokami ESI. Doprowadzi to do sytuacji, w której będziemy mieli zachowaną w pamięci podręcznej całą stronę, a o te dwa wskazane elementy każdorazowo będziemy odpytywać serwer aplikacyjny - dzięki temu one zawsze będa aktualne, a pozostała zawartość strony będzie ładować się bardzo szybko. W efekcie nie musimy inwalidować cache tej strony.

# Monitorowanie efektów

Po wdrożeniu Varnisha z pewnością chcielibyśmy zmierzyć efekty płynące z faktu jego zaimplementowania. Należy pamiętać, że popularne oprogramowania monitorujące lub profilujące (jak np. New Relic) są spięte zazwyczaj z serwerem aplikacyjnym. Przykładowo, w przypadku pracy z językiem PHP nasze oprogramowanie może analizować pracę PHP-FPM. Varnish znajduje na warstwie bliższej użytkownikowi, w związku z czym nie zaobserwujemy efektów jego pracy w New Relicu, a dostrzeżemy jedynie zmniejszony ruch na serwerze aplikacyjnym.

Efekty pracy Varnisha możemy zaobserwować np. przez cykliczne uruchamianie testów symulujących klikanie użytkownika internetowej według wskazanych scenariuszy. Przez wyciągnięcie czasów średnich ładowania poszczególnych stron w okresie przed i po wdrożeniu Varnisha powinniśmy móc zauważyć różnicę.

# Podsumowanie

Reverse proxy nie takie straszne jak je malują. Dzięki tego typu narzędziom możemy przyśpieszyć działanie strony internetowej i poprawić doświadczenia użytkowników. To wszystko przy dość niewielkim koszcie wdrożenia. W skrajnych przypadkach możemy wykorzystać tego typu rozwiązanie do zamaskowania niewydolności backendu spowodowanej naszymi własnymi błedami… wróć… błędami tych legendarnych, innych programistów (sic!).

Oryginalna dokumentacja Varnisha została napisana w bardzo przyjazny sposób i w pełni zachęcam do jej lektury.

* * *

#### Źródła i pojęcia

*   \[1\] [Varnish Documentation, https:/varnish-cache.com](https://varnish-cache.org/docs/trunk/index.html)
*   \[2\] [VCL Basics, https://book.varnish-software.com](https://book.varnish-software.com/4.0/chapters/VCL_Basics.html)
*   \[3\] [Built in subroutines, https:/varnish-cache.com](https://varnish-cache.org/docs/trunk/users-guide/vcl-built-in-subs.html)
*   \[4\] [Grace, https:/varnish-cache.com](http://varnish-cache.org/trac/wiki/VCLExampleGrace)
*   \[5\] [Purging & banning, https:/varnish-cache.com](https://varnish-cache.org/docs/3.0/tutorial/purging.html)

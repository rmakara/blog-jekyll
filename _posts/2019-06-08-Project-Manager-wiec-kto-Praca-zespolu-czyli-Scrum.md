---
layout: post
title: Project Manager, więc kto? Praca zespołu, czyli &#34;Scrum&#34;
image: /assets/20190608_header.jpg
description: Zadania wykonywane przez managerów w firmach IT nie są w pełni transparentne dla zespołów developerskich. Co robią project managerowie? Wyjaśnijmy! W dzisiejszym artykule opisujemy zaangażowanie project managera w codzienną pracę zespołu.	
---

> Jest to czwarty artykuł z cyklu _Project Manager, więc kto._, jeżeli nie czytałeś/aś od początku to zachęcam do przejścia na stronę [Project Manager, więc kto? Wstęp](https://rmakara.github.io/Project-Manager-wiec-kto-Wstep).

> Rola project managera może być skrajnie różna w zależności od firmy. Często stanowiska nazywane zwrotem "project manager" - nie są dla project managerów. Seria artykułów będzie zawierać pewne uproszczenia i ograniczony kontekst.	

> Ten artykuł nie jest o Scrumie. 

# Pseudo-Agile

Podchodząc do omówienia tematu udziału project managera w świecie przeplatającym się z Agile ([ScrumAnd](https://www.scrum.org/resources/blog/scrumand-stance-requires-thought-and-discipline-0)) lub Pseudo-Agile ([ScrumBut](https://www.scrum.org/resources/what-scrumbut)), dość trudno jest trafić we wszelkie gusta oraz dotychczasowe doświadczenia osób, które taki materiał będą czytać. Do tego dochodzi fakt, że w ramach tej serii postów chcemy skupić sie na rzeczywistości do jakiej może trafiać osoba zatrudniająca się jako project manager w software house. Nie chcemy opisywać z sukcesem wdrożonego podejścia zwinnego, bo wtedy, post ten mógłby być przepisanym na krótszą formę Scrum Guide, opisującą tylko zakres obowiązków ról miękkich, albo właściwie postu w ogóle by nie było, bo przecież w Scrum Guide nie ma project managera. 

Artykuł będzie rozbity na dwie części. Pierwsza opisze rolę PMa w świecie w którym firma realizuje Scruma w składzie Project Manager + Zespół Developerski i prawdopodobnie nie jest jeszcze przesiąknięta wartościami scrumowymi. W drugiej części, przedstawimy inne środowisko, w którym mamy kompletny według Scrum Guide zespół: Development Team, Product Owner, Scrum Master. Poszukamy w nim również miejsca dla managera, a w późniejszych częściach tego cyklu artykułów, gdy będziemy opisywać możliwości wspierania organizacji przez managerów - delikatnie omówimy sposoby skalowania metodyk zwinnych.

# Ale... w Scrum Guide nie ma project managera

Nie ma. I bardzo dobrze, bo Scrum Guide jest o Scrumie, a nie o zarządzaniu.

Na chwilę odchodząc od Scruma wspomnijmy o sytuacji, którą w ramach tej serii postów świadomie ominiemy. Istnieją firmy, które nie mają żadnych project managerów, a stawiają developerów na pierwszej linii przed klientem. Składają się ze specjalistów technicznych, którzy dodatkowo wyposażeni są w umiejętności miękkie. Odnoszą duże sukcesy i zazwyczaj prowadzone są pasją swoich pracowników, którzy zrozumieli ideę Software Craftsmanship, są bardzo dobrymi developerami, a także mają bardzo otwarte głowy na rozumienie biznesu klienta. Przykładami takich firm moga być [SoftwareMill](https://softwaremill.com/) lub [Mirumee](https://mirumee.com/), które tworzą bardzo dobre miejsca do pracy i rozwoju. Dzisiaj jednak nie o tym modelu firm będzie mowa.

# Czymże jest Scrum?

W dzisiejszym świecie istnieje wiele przesłanek mówiących o tym, że Scrum jest metodyką zarządzania projektami. Gdy bywałem na konferencjach dotyczących prowadzenia projektów często pojawiały się prelekcje "Prince2 vs Scrum" wygłaszane przez doświadczonych managerów. Jest to kontynuowane wraz ze wzrostem liczby certyfikatów dla kadry zarządzającej w świecie IT, gdzie Scrum rzeczywiście urósł do rangi metodyki zarządzania projektami i jest głównym (często jedynym) narzędziem, którym wbijamy każdy gwóźdź. Scrum zaczął stawać się zestawem praktyk dla "scrum masterów" oraz project managerów. W ramach scrumowej pracy świat zaczął zapominać trochę o początkach...

No właśnie, po co i dla kogo został stworzony Scrum? Został stworzony przez programistów chcących wyznawać idee prowadzące do wytwarzania oprogramowania bardzo wysokiej jakości, które odpowiadałoby na bieżące, przyszłe i realne potrzeby biznesowe, zamiast waterfollowego realizowania planów, które były aktualne miesiące temu. Efektem miało być zbliżenie do siebie developerów, managerów i biznesu, a nie wytworzenie nowej, modnej metody zarządzania projektami. Oczywiście nie jest tak, że jeżeli coś zostało stworzone kilkanaście lub kilkadziesiąt lat temu to nie powinno ulegać procesowi ewolucji i rozwoju. Warto jednak pamiętać o celu jakim jest nasza praca. Najczęściej jest nim dostarczanie rozwiązań, które będą wykorzystywane przez innych. Celem naszej pracy w branży IT raczej nie jest rysowanie obrazków publikowanych na Behance, pisanie testów jednostkowych, przesuwanie diagramów Gantta czy zdobywanie certyfikatów. Warto o tym pamiętać przy ocenie słuszności drogi w którą zmierzamy my lub cała branża.

W sierpniu 2018 roku Robert C. Martin napisał post opisujący ten problem. Możecie go znaleźć pod linkiem [The Tragedy of Craftsmanship, The Clean Code Blog](https://blog.cleancoder.com/uncle-bob/2018/08/28/CraftsmanshipMovement.html). Dla mnie osobą, która w okolicy 2014 roku właśnie w taki sposób przedstawiała mi tego typu zagadnienia był mój były szef programistów (pozdrawiam Chips). :)

Dlatego też w ramach tego postu chciałbym żebyśmy nie patrzyli na Scrum jak na metodykę zarządzania projektami, a... jak na metodę efektywnej pracy zespołowej opartej o zasady, wartości oraz kulturę ciągłego doskonalenia.

# Kontekst naszej historii

Jesteś project managerem, który/a zostaje zatrudniony/a w software house. Zostajesz zesłany/a do pracy w czterech "projektach", które są realizowane przez zespoły składające się z programistów/ki, testerów/ki, desginerów/ki, analityków/czki. Jeden z projektów jest typowym utrzymaniem stabilnie działającego softu legacy. Drugi to 2-osobowy zespół consultingowy dla klienta zewnętrznego. Trzeci to napisanie modułu, którego realizacja potrwa 2 miesiące, po czym zostanie opublikowany w marketplace. Czwarty to green-fieldowy projekt dotyczący zaawansowanego systemu wspierający handel B2B, tworzony dla firmy produkującej i sprzedającej półprodukty przeznaczone do produkcji elektroniki przemysłowej. W każdym będziesz musiał w mniejszym lub większym stopniu wspierać pracę zespołu.

Skupmy się na czwartym. Do projektu przydzielone zostają osoby, które nie trafiają do niego na podstawie Twojej analizy zapotrzebowania na konkretne kompetencji, ani Twoich decyzji. Zostajesz postawiony/a przed faktem dokonanym, który wynikł z wypadkowej potrzeb na realizację celu projektu zdefiniowanych przez inne osoby oraz aktualnie wolnych specjalistów w Twojej firmie, którzy akurat pokończyli inne projekty. Ta grupa osób w najbliższym czasie będzie musiała stać się zespołem, który przez kolejne 12 miesięcy będzie miał wytworzyć wspomniany system oraz uruchomić go produkcyjnie. W skład zespołu wchodzą: 
* lead developer, 
* 3 backend developerów,
* 2 frontend developerów,
* 1 UX designer,
* 1 tester,
* 1 project manager, czyli Ty.

Jest wtorek, otrzymujesz informacje że powyższy zespół może rozpocząć pracę w poniedziałek. Od czego zaczynasz?

# Planowanie

Prawdopodobnie na tym etapie będzie do wykonania trochę pracy managerskiej. Dalej pamiętasz, że Scrum nie jest metodyką zarządzania projektami? Dlatego też, ten etap poruszymy w części o "Prince2". 

W ramach "pracy scrumowej" przygotowujesz się do rozpoczęcia współpracy z zespołem.

# Kick off meeting

Jako pierwsze wydarzenie Scrumowe (którego nie ma w Scrum Guide) chcesz zoorganizować kickoff meeting, aby w jak najszybszy sposób zmaksymalizować wiedzę zespołu o tym co będziecie robić. Umawiasz wszystkich na pierwsze wewnętrzne spotkanie podczas którego opiekun biznesowy, który sprzedał dany projekt opisuje Wam jego cel, rzeczywistość biznesową oraz klienta z którym przyjdzie Wam współpracować. Masz również okazję do zapoznania wszystkich ze sobą oraz przedstawienia swoich oczekiwań (przecież jesteś managerem). 

Podczas posiedzenia dodajecie cykliczne [ceremonie scrumowe](https://www.atlassian.com/agile/scrum/ceremonies) do kalendarza. Wyjaśniasz, w jaki sposób będzie wyglądało raportowanie czasu w projekcie, ponieważ pracujecie na zasadach [time&materials](https://en.wikipedia.org/wiki/Time_and_materials), więc na podstawie takich raportów fakturowany będzie klient. Niestety, jesteśmy w układzie gdzie większa część zespołu nie jest przydzielona jedynie do tego projektu, a na boku ma jeszcze 20% swojego etatu przeznaczonego na wsparcie utrzymania projektów, które współtworzyli poprzednio. 

Podczas spotkania otrzymujecie artefakt przygotowany przez analityka biznesowego, który przez ostatnie 2 miesiące na podstawie warsztatów z klientem stworzył dokumentację zbierającą wymagania biznesowe. Nie braliście udziału w jej przygotowywaniu. Po spotkaniu macie kilka dodatkowych dni na (re)analizę 100 stron dokumentacji. Robicie to, bo za chwilę będzie trzeba siadać, projektować i kodować.

Informujesz zespół, że zoorganizujecie podobny kickoff z klientem, aby przełamać lody i zapoznać się również z nim.

# Początek developmentu

Po wspomnianym kickoffie z klientem rozpoczynacie pracę nad realizacją projektu. Rozpisujecie wymagania w formie user stories, granulujecie te które chcecie zrealizować w najbliższym czasie, estymujecie, planujecie sprint backlog i startujecie pierwszy sprint. 

Designer zaczyna projektować, programiści przygotowują środowiska developerskie, testowe, stagingowe, produkcyjne i realizują pierwsze zadania, które przynajmniej w teorii powinny zacząć dostarczać wartość biznesową. 

Zaczęło się. Co od tego momentu będziesz robić jako project manager?

# Model siedmiu poziomów delegacji

Niestety najlepszą odpowiedzią jest ulubiony zwrot konsultantów: "to zależy". Spróbujmy jednak odegrać rolę kompetentnego konsultanta, więc "to zależy, od...". 

Pracując nad skomplikowanymi lub złożonymi rzeczami bardzo ciężko jest opisać każdy czynnik wpływający na to jak będzie wygądała taka praca. Kiedyś, jedna osoba zapisała się na kartach historii przez powiedzenie bardzo ważnego zwrotu:

> "All models are wrong, but some are useful."


Każdy model jest próbą przeniesienia całej rzeczywistości i miliardów neuronów tworzących ludzkie mózgi na jeden slajd, czyli jest bardzo mocnym uproszczeniem. Jest to jednak przydatne, aby ułatwić rozważanie nad złożoną rzeczywistością. Do naszych dalszych przemyśleń i umożliwienia znalezienia odpowiedzi na pytanie "to zależy, od..." skorzystamy z modelu przytoczonego przez Jurgena Apello w książce Management 3.0. Pojawia się tam model 7 poziomów delegacji / dojrzałości zespołu, są to:

* __Mów__, w którym możesz wspomnieć o swojej motywacji do realizowania czegoś, ale przede wszystkim mówisz innym co mają robić i podejmujesz za nich decyzje.
* __Sprzedawaj__, podejmujesz decyzje za innych, ale dodatkowo starasz się ich przekonać do ich słuszności, aby zwiększyć poziom zaangażowania i bycia częścią procesu.
* __Konsultuj__, prosisz o przedstawienie punktu widzenia innych osób z zespołui bierzesz go pod uwagę, ale finalnie decyzja należy do Ciebie.
* __Szukaj konsensusu__, w procesie rozwiązywania problemów występujesz jako członek zespołu i wspólnie poszukujecie złotego środka oraz podejmujecie decyzje.
* __Doradzaj__, oferujesz zespołowi swoją wiedzę i przedstawienie punktu widzenia, ale wszelkie prawa do decyzji oddajesz w ich ręce. Na tym poziomie tracisz większość swojej mocy decyzyjnej.
*  __Dowiaduj się__, pozwalasz zespołowi na omówienie tematu i wymyślenie rozwiązań bez Twojego udziału. Po tym prosisz ich o przedstawienie efektów oraz przekonania Ciebie do ich decyzji. 
* __Deleguj__, oddajesz odpowiedzialność za podejmowanie decyzji zespołowi. Nie bierzesz udziału w omawianiu problemu, wymyśleniu rozwiązania, podejmowaniu decyzji. Nie chcesz wiedzieć o szczegółach decyzji, a ufasz zespołowi na tyle, że traktujesz ich decyzję jako najlepszą możliwą i ją akceptujesz.

Jeżeli chcesz więcej dowiedzieć się o powyższym modelu, zachęcam do przeczytania artykułu [The 7 Levels of Delegation, Jurgen Appelo](https://medium.com/@jurgenappelo/the-7-levels-of-delegation-672ec2a48103).

Twoje obowiązki będą mocno zależne od tego na jakim poziomie delegacji współpracujesz z konkretnym zespołem. Jeżeli zespół nie jest zbyt doświadczony prawdopodobnie będzie potrzebował współpracy na jednym z pierwszych poziomów delegacji. Jeżeli jednak ma bardzo duże doświadczenie to prawdopodobnie ich decyzje będą lepsze od Twoich, a najlepsze co możesz zrobić to wspierać wyznaczanie celów, kierunku oraz określać granice możliwego postępowania. 

Na wyższych poziomach delegacji objawia się coraz bardziej sens "Take it to the Team", czyli sposobu rozwiązywania problemów szeroko opisywanego np. w książce [Coaching Agile Teams, Lyssa Adkins](https://www.lyssaadkins.com/coaching-agile-teams-book). Jeżeli bardzo dojrzałemu zespołowi o wysokim poziomie umiejętności (eksperci wg [modelu Dreyfus](https://blog.krolartur.com/jak-dobry-jestes-w-tym-co-robisz-czyli-model-dreyfus-i-co-z-niego-wynika/), który został dobrze opisany przez Artura Króla) będziemy pokazywać palcem co mają robić to prawdopodobnie szybko będą mieli nas dość ze względu na tzw. [micromanagement](https://en.wikipedia.org/wiki/Micromanagement).

No więc, to zależy. Z pewnością jednak jako członek zespołu scrumowego przyjdzie Ci wspierać niektóre z poniższych obszarów. Postaraj się opisywane poniżej elementy ocenić względem powyższego modelu i zastanów się co musiał(a)byś w ich zakresie robić na niższych, a co na wyższych poziomach delegacji.

# Project manager, jako single point of contact

Jednym z częstych pomysłów na usprawnienie komunikacji i pozwolenie zespołowi na skupienie się na wytwarzaniu jest bycie głównym punktem przepływu informacji między zespołem oraz interesariuszami projektu. W tej sytuacji jesteś jedyną osobą, która rozmawia z jedną i drugą stroną. Masz jednak możliwość tworzenia obszarów w obrębie, których jedni z drugimi mogą kontaktować się bezpośrednio, aby doprecyzować jakiś konkretny temat.

Dzięki temu zespół nie ma na głowie 10 interesariuszy z których każdy mówi im coś innego, klient ma jedną wyznaczoną osobę do której może się odezwać w każdym temacie, zarząd Twojej firmy również ma jedną osobę od której w każdej chwili może poznać status projektu.

Przykład interpretacji przez pryzmat modelu 7 poziomów delegacji:
* __Niski poziom delegacji:__ jesteś pośrednikiem 100% komunikacji, bo ta bardzo stresuje zespół i tworzy ryzyko godzenia się na rzeczy na które nie powinniśmy się godzić (np. zmiana architektury technicznej systemu bez zmiany wcześniej zadeklarowanego czasu realizacji konkretnego etapu projektu).
* __Wysoki poziom delegacji:__ oddajesz komunikację z interesariuszami w zakresie omawiania potrzeb biznesowych w ręce zespołu, ponieważ specjaliści techniczni są zdecydowanie lepszymi osobami do rozmawiania o przenoszeniu potrzeb biznesowych na kod, i to oni muszą je zrozumieć. Ty i Zespół wiecie, że zmniejszy to liczbę zniekształceń przekazywanej informacji, doprowadzi do lepszych rozwiązań, bardziej zaangażuje zespół i klienta.

# Project manager, jako sekretarz/ka

W ramach swojej pracy prawdopodobnie będziesz musiał robić to co byłoby w roli scrum mastera, którego zadaniem w zespołach scrumowych jest rozwiązywanie tzw. impedimentów, czyli przeszkód utrudniających zespołowi efektywną pracę. Także będziesz wykonywać typową pracę biurową. 

W skład tego może wchodzić pomoc i przypominanie o uzupełnianiu raportów czasu, dbanie o punktualność odbywanych spotkań, przypominanie o przygotowaniu się do np. sprint review mającego miejsce dzień później, a nawet dbanie o dostępność flipchartów i mazaków w salach konferencyjnych. Nie wykluczone, że na Twoją głowę spadnie również załatwianie tematów związanych ze zwolnieniami lekarskimi lub urlopami członków zespołu oraz rozwiązywanie konfliktów powstających podczas podejmowania decyzji o tym, kto powinien pójść na urlop podczas długiego weekendu majowego, a kto nie.

# Project manager, jako scrum master

Ten element jest rozwinięciem poprzedniego. Poza wykonywaniem czynności kalendarzowych i biurowych na rzecz zespołu pomagasz im ściśle optymalizować proces developmentu oraz współpracy z klientem. Usprawniasz komunikację, podczas ceremonii scrumowych możesz odgrywać rolę facylitatora. Zbierasz metryki pozwalające na wyciągnięcie wniosków i usprawnienie procesu wytwarzania, mogą to być ilość błędów, czas poświęcany na wykonywanie niektórych czynności przez brak automatyzacji, velocity, lead time, cycle team, częstotliwość releasów. Wizualizujesz te dane. 

W ramach tego elementu jesteś już nie tylko managerem, ale osobą mającą pomóc zespołowi w efektywniejszej pracy. Ważne jest, że w roli scrum mastera to nie Ty wykonujesz najcieższą robotę, a jesteś coachem pomagającym rozwijać się zespołowi lub mentorem pokazującym konkretny sposób na rozpoczęcie przygody z niektórymi technikami. Dbasz o te rzeczy w skali zespołu lub spotkań one-on-one z każdym z jego członków.

# Project manager, jako proxy product owner

Biorąc pod uwagę, że w swoim zespole nie macie rozdzielonych ról scrum mastera oraz product ownera - po części stajesz się również product ownerem. Często jest tak, że product owner występuje po stronie klienta lub w buty PO wchodzi lead developer pracujący w Waszym zespole. Nie zawsze jednak tak jest. 

Wtedy Twoim zadaniem jest (w podejściu bardziej zwinnym) wyznaczanie długoterminowych oraz krótkoterminowych celów do osiągnięcia przez zespół oraz maksymalizacja wartości dostarczanej klientowi w ramach kolejnych iteracji lub (w podejściu bardziej waterfallowym) zadbanie o wytworzenie ustalonego zakresu projektu, a nie czegoś innego. 

Bierzesz udział w precyzowaniu zadań dla zespołu, odpowiadasz na pytania specjalistów w kwestii wymagań klienta, priorytetyzujesz zadania w backlogu, kontaktujesz się z interesariuszami, aby zrozumieć ich potrzeby. 

# Project manager, jako element ścieżki eskalacyjnej

W sytuacji gdy coś będzie szło źle, zespół popełni błąd mający skutki finansowe dla firmy klienta lub klient po prostu będzie niezadowolony z jakości Waszej pracy to prawdopodobnie staniesz się również osobą, która w pierwszej linii będzie odbierać jego "ataki". Przekłada się to na wykazywanie zrozumienia sytuacji z perspektywy klienta jako partnera biznesowego, a także zrozumienie zespołu, który wypadałoby bronić. 

W rzeczywistości, będąc rozdartym pomiędzy tymi dwoma stronami prawdopodobnie nie będziesz po stronie klienta, ani po stronie zespołu... a po stronie projektu. Co czasami będzie oznaczało pójście bardziej w jedną lub drugą stronę.

# Żart o żabie

Powyższe pokazuje, że w kontekście pracy zespołowej pełnisz kilka ról w jednej osobie. To często może rodzić wewnętrzne konflikty interesów, ponieważ odgrywając rolę PO będziesz musiał głęboko wchodzić w rozumienie i omawianie zadań, a wchodząc w buty SM powinieneś stać w lekkim dystansie od tego, aby móc jak najbardziej obiektywnie oceniać sytuację w zespole i ją usprawniać. Z trzeciej strony, wracając do roli PM powinieneć dbać o budżet i harmonogram.

> Lew zebrał na polanie zwierzęta i mówi: 
> - Musimy się podzielić. Mądre zwierzaki przejdą na prawo a ładne na lewo. 
> Część zwierząt pobiegła na prawo a część na lewo. 
> Tylko żaba pozostała na środku. 
> - Żabo, a ty co? Dlaczego nigdzie nie poszłaś? - pyta zdziwiony lew. 
> - Przecież się nie rozdwoję!

# Project manager w Scrumie

Wiele osób bardzo trzymających się Scrum Guide prawdopodobnie powiedziałoby, że taki układ z PMem i Development Teamem jest antywzorcem, który nie powinien być stosowany. Jeżeli jesteś w firmie w której pracujecie w taki sposób to być może narzekasz na to, że jeżeli mielibyście SM oraz PO to pracowalibyście dużo lepiej. W rzeczywistości byłoby tak, że wtedy pewnie znalazłyby się inne powody do narzekania, bo narzekania ciężko się oduczyć. :)

Mimo, iż sam preferuję prace w pełnym zespole scrumowym to nie odrzucam scenariusza z udziałem PMa, bez ról PO oraz SM. Scrum raczej nie zadziała idealnie jeżeli nasz zespół będzie składał się z osób, które są aktualnie na pierwszych poziomach modelu Dreyfus w zakresie wytwarzania oprogramowania, czyli potrzebują gotowych rozwiązań, procedur, przepisów na sukces. 

Zespół nie stanie się samoorganizujący tylko dlatego, że powie się o tym jego członkom. Istnieje szansa, że ten zespół nawet nie będzie zespołem. Czy zespół scrumowy odnajdzie się w Scrumie zanim się uformuje? Czy w ogóle będzie potrafił? Być może przez cały czas trwania projektu "Scrum" zatrzyma jego rozwój na pierwszym kroku procesu budowania zespołów jakim jest znane [storming-norming-forming-performing](https://www.mindtools.com/pages/article/newLDR_86.htm)? 

Scrum niekoniecznie będzie idealny, jeżeli z dwoma developerami będziemy mieli do stworzenia konkretny, dobrze opisany, o działaniu już zweryfikowanym przez rynek moduł przeznaczony na marketplace, we współpracy z płacącym nam dużo pieniędzy, ale maksymalnie niemiłym i niechętnym do kooperacji klientem. Zakres modułu będzie znany, więc nie będziemy mogli powiedzieć, że pracujemy w startupowych warunkach skrajnej niepewności, gdzie potrzebujemy wielu iteracji do minimalizacji ryzyka developowania rzeczy nieważnych. Nie będziemy też potrzebować ścisłej współpracy z interesariuszami, ponieważ Ci chcą jedynie zobaczyć gotowy produkt za 60 dni.

Co jeżeli pracujemy w na tyle zaawansowanym [SDLC](https://en.wikipedia.org/wiki/Systems_development_life_cycle), że deployujemy naszą aplikację kilkaset razy dziennie, a o releasach decydujemy jedynie pojedynczymi [feature togglami](https://martinfowler.com/articles/feature-toggles.html)? Czy tygodniowe sprinty nie będą nas ograniczać?

W takich sytuacjach, w kontekście pracy zespołowej project manager we współpracy z liderem technicznym zespołu ponownie powinien ponownie przypomnieć sobie o pełnym zakresie obowiązków przypisanym do jego stanowiska jakim jest - "getting things done". Jego zadaniem jest wspieranie pracy zespołu, aby pomagać innym rosnąć oraz aby projekt odniósł sukces. Może to mieć miejsce w "Scrumie", zaangażowaniu w planingi, daily, groomingi, review, optymalizacje procesu, facylitacje, przekazywanie wizji produktu, maksymalizacje wartości biznesowej lub nie wchodzenie innym w drogę. Scrum jest jedynie narzędziem wspierającym, podobnie jak Lean, Extreme Programming, Crystal, SAFe, Kanban czy Nexus. Na pewnym poziomie eksperckości ślepa wiara w 16 stronicowy podręcznik po prostu nie zadziała w trudnych sytuacjach jakie przynosi nam codzienna praca. Warto jednak korzystać z gotowych przepisów, gdy takimi ekspertami jeszcze nie jesteśmy. 

# Podsumowanie

Project managerze pracujący w Scrumie, bez Agile Coacha, bez Scrum Mastera i bez Product Ownera. Jeżeli po dołączeniu do firmy, konieczność pracy w takim środowisku Cię zaskoczyła, bo jest sprzeczna z książkami opisującymi Agile i Scrum, którymi chwali się każda firma IT w 2019 roku, pamiętaj, że - to jeszcze nie kamieniołom. Ta sytuacja nie jest najgorszym możliwym scenariuszem jaki może pojawić się w życiu. Jeżeli masz poczucie bycia rozdartym i żyjesz w ciągłym konflikcie interesów to nie jesteś jedyny/a. Pamiętaj jednak, że taki układ czasami rzeczywiście ma sens. 

Postaraj się odnaleźć pozytywne aspekty takiego otoczenia zanim ślepo uwierzysz, że książkowe wdrożenie Scruma byłoby lepsze. Jeżeli jednak istnieją elementy tej metodyki (pracy zespołowej), które wg Ciebie warto wdrożyć do codziennej pracy Waszego zespołu - pamiętaj o continuous improvement i zapytaj zespołu czy checie wspólnie spróbować je zastosować. Być może odkryjecie, że to nie dla Was? A może będzie to początek transformacji w kierunku prawdziwej zwinności bazującej na odpowiednich wartościach, fundamentach i kulturze?

* * *

#### Źródła i pojęcia

*   \[1\] [The “ScrumAnd” Stance (requires thought and discipline), Gunter Verheyen](https://www.scrum.org/resources/blog/scrumand-stance-requires-thought-and-discipline-0)
*   \[2\] [What is ScrumBut?, Scrum.org](https://www.scrum.org/resources/what-scrumbut)
*   \[3\] [The Tragedy of Craftsmanship, The Clean Code Blog, Robert C. Martin](https://blog.cleancoder.com/uncle-bob/2018/08/28/CraftsmanshipMovement.html)
*   \[4\] [Have we met?, Dan Radigan, Atlassian](https://www.atlassian.com/agile/scrum/ceremonies)
*   \[5\] [Time&materials, Wikipedia](https://en.wikipedia.org/wiki/Time_and_materials)
*   \[6\] [The 7 Levels of Delegation, Jurgen Appelo](https://medium.com/@jurgenappelo/the-7-levels-of-delegation-672ec2a48103)
*   \[7\] [Coaching Agile Teams, Lyssa Adkins](https://www.lyssaadkins.com/coaching-agile-teams-book)
*   \[8\] [Jak dobry jesteś w tym co robisz, czyli Model Dreyfus i co z niego wynika?, Artur Król](https://blog.krolartur.com/jak-dobry-jestes-w-tym-co-robisz-czyli-model-dreyfus-i-co-z-niego-wynika/)
*   \[9\] [Micromanagement, Wikipedia](https://en.wikipedia.org/wiki/Micromanagement)
*   \[10\] [Forming, Storming, Norming, and Performing, Mind Tools](https://www.mindtools.com/pages/article/newLDR_86.htm)
*   \[11\] [Systems development life cycle](https://en.wikipedia.org/wiki/Systems_development_life_cycle)
*   \[12\] [Feature Toggles (aka Feature Flags), Martin Fowler](https://martinfowler.com/articles/feature-toggles.html)
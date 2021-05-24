---
layout: post
title: Event Storming&#58; Warsztaty Agile Wrocław
image: /assets/20180410_header.jpg
description: Relacja z warsztatów Product Craftsmanship - Agile Wrocław poświęconych metodzie Event Storming. Prowadzenie&58; Mariusz Gil i Krzysztof Menżyk.
article_language: pl
---

# Powrót do warsztatów

Od czasu mojej przeprowadzki do Wrocławia przestałem brać udział w otwartych wydarzeniach organizowanych w formie warsztatowej. Alternatywą było regularne słuchanie wykładów na wszelkiego rodzaju meetup’ach. Pod koniec marca grupa [Product Craftsmanship - Agile Wrocław](https://web.facebook.com/Product-Craftsmanship-Agile-Wroc%C5%82aw-1791532430917050/) zorganizowała [warsztaty](https://www.meetup.com/pl-PL/Product-Craftsmanship-Agile-Wroc%C5%82aw/events/248656214/?eventId=248656214) poświęcone metodzie [Event Storming](https://en.wikipedia.org/wiki/Event_storming) prowadzone przez [Mariusza Gila](https://twitter.com/mariuszgil) i [Krzysztofa Menżyka](https://twitter.com/kmenzyk) w których wziąłem udział.

# Event Storming w mojej dotychczasowej karierze

O Event Stormingu pierwszy raz przeczytałem na początku 2017 roku, gdy pełnymi siłami starałem się przebrnąć przez książkę Erica Evensa. Pewnego dnia, w jednym z prowadzonych przeze mnie projektów lider zespołu zdecydował się na zmianę firmy, zmuszeni byliśmy do szybkiego przetransferowania wiedzy na inną osobę. Problemem projektowym stał się dla nas [współczynnik autobusu](https://en.wikipedia.org/wiki/Bus_factor) równy 1 oraz czas w postaci dwóch tygodni na przekazanie skomplikowanego projektu nowej osobie. Dysponowaliśmy ponad setką stron dokumentacji oraz mocno rozbudowanym systemem. Nowy lider nie byłby w stanie przyjąć tak dużej ilości złożonych informacji w tak krótkim czasie. Zainspirowani Event Stormingiem postanowiliśmy spróbować wykorzystać tę metodę.

Nie mieliśmy żadnego doświadczenia z tą metodą i nie skorzystaliśmy z niej stricte jako sposobu do zapisu ścieżki wydarzeń domenowych, a raczej jako narzędzia do przekazania wiedzy o działaniu istniejącego systemu. Pracowaliśmy w zespole zdalnym. Przy użyciu narzędzia [Realtime Board](https://realtimeboard.com/) wspólnie “wykarteczkowaliśmy” działanie całej logiki, przyporządkowując konkretne znaczenia do każdego z kolorów karteczek oraz dzieląc system na [bounded contexty](https://martinfowler.com/bliki/BoundedContext.html). Karteczki oznaczały: zdarzenia inicjowane przez użytkownika, modele, triggery (automatyczne wyzwalacze kolejnych zdarzeń), zdarzenia niewyzwalane triggerami, webservice (wywołania przychodzące i wychodzące), pliki csv (źródła cyklicznych importów danych). Zdecydowanie nie było to książkowe wykorzystanie Event Stormingu, ale w ten sposób przekazaliśmy nowej osobie wiedzę o całym systemie w błyskawicznym tempie. Zaangażowanie nowego lidera w tworzenie boardu sprawiło, że brał on czynny udział w jego projektowaniu, mimo że system już istniał.

Stworzony model posłużył nam również do wyjaśnienia działania całego systemu wszystkim programistom, którzy dotychczas rozumieli go jedynie “wycinkowo”. Do dnia dzisiejszego nowi członkowie zespołu wprowadzani są do pracy nad tym projektem przez wysłuchanie opowieści opisującej “wykarteczkowany” model działania systemu.

Brak doświadczenia nie przeszkodził w żaden sposób, w wykorzystaniu tak lekkiego sposobu dokumentowania, rozmawiania, projektowania jakim jest wykorzystywanie sticky notesów.

> Software Development is a learning process, Working code is a side effect.
> 
> – Alberto Brandolini

# Warsztaty - problem nad którym pracowaliśmy

Podczas warsztatów naszym zadaniem było zrozumienie problemu sprzedaży biletów do kina oraz stworzenie big picture procesu doprowadzającego widza do wejścia na salę. Podzieleni byliśmy na 5-osobowe grupy w których jedna z osób wcielała się w rolę eksperta domenowego, a pozostała czwórka w członków zespołu projektowego mających zamodelować we współpracy z ekspertem dany system/proces. Ekspert dysponował znacznie większą wiedzą o sprzedaży biletów od pozostałych osób.

Dysponowaliśmy długim kawałkiem papieru, kolorowymi karteczkami, markerami, umiejętnością mówienia i pokazywania palacami.

# Krok 1 - Wild exploration

Początkiem modelowania procesu było zdefiniowanie zdarzeń domenowych (faktów) mających znaczenie dla eksperta domenowego. Były one zapisywane na pomarańczowych karteczkach z wykorzystaniem czasowników dokonanych w stronie biernej. Przykładami takich eventów są: “bilet zakupiony”, “widz wpuszczony na salę”. Na podstawie naszej bardzo podstawowej wiedzy wygenerowaliśmy sporą liczbę faktów, które na osobnych karteczkach przykleiliśmy na długiej [rolce papieru](https://www.ikea.com/pl/pl/catalog/products/80324072/). Na tym etapie nie były one w żaden sposób uporządkowane.

# Krok 2 - Enforce the timeline

Etap ten polega na uporządkowaniu spisanych sticky notesów ze zdarzeniami domenowymi na linii czasu, gdzie lewa strona oznacza “pierwsze wydarzenia”, a prawa strona “końcowe wydarzenia”. Podczas tworzenia takiej chronologii byliśmy w stanie dostrzec miejsca w których zdecydowanie czegoś brakowało i tym samym do głowy przychodziły nam kolejne zdarzenia, które zapisywaliśmy na kolejnych pomarańczowych karteczkach i umieszczaliśmy w odpowiednim miejscu na papierze obrazującym cały proces. Krok ten pozwala również na ułożenie niektórych zdarzeń w bardzo powiązane ze sobą sekwencje. Umożliwia również dostrzeżenie zdarzeń, które mogą dziać się w tym samym czasie. W takiej sytuacji, rownież łatwo dostrzec alternatywne scenariusze rozwiązania niektórych problemów pojawiających się w obrębie procesu, ponieważ karteczki naklejone na tej samej współrzędnej osi X (innej współrzędnej na osi Y) - zwracają na siebie uwagę.

W tym momencie został wprowadzony kolejny kolor karteczki - czerwony. Miał on na celu oznaczenie hot spotów, czyli fragmentów procesu generujących długie i problematyczne dyskusje. Napotykając takie miejsca oznaczyliśmy je czerwoną karteczką i prowadziliśmy dalsze prace nad uporządkowaniem zdarzeń na osi czasu. Jednym z benefitów event stormingu jest postawienie obok siebie kilku osób, które dotychczas ze sobą nie rozmawiały. Takie sytuacje rodzą konflikty, które często zmuszają przedstawicieli firmy klienta do przemyślenia ich procesu biznesowego. Podczas tworzenia modelu big picture nie warto wstrzymywać się na dziesiątki minut na omawianiu takich punktów, a warto je oznaczyć i wrócić do nich później. Czerwony kolor kartki rzuca się w oczy i natychmiastowo pokazuje potencjalnie problematyczne elementy systemu.

# Krok 3 - Reverse narrative

Prowadzący warsztaty przytoczyli [metodę amerykańskich śledczych](http://www.dailymail.co.uk/sciencetech/article-460505/How-spot-liar-tell-story-backwards.html), która polega na zmuszeniu podejrzanego do opowiedzenia jego wersji wydarzeń od tyłu. Takie zadanie jak odwrócenie chronologii wpływa na tzw. [cognitive load](http://psychology.iresearchnet.com/forensic-psychology/police-psychology/detection-of-deception-cognitive-load/), czyli zwięszkenie wysiłku intelektualnego jaki musimy wytworzyć do przeprocesowania naszych myśli i zamiany ich w historię. Mówiąć w skrócie, trudniej kłamać mówiąc co się wydarzyło od tyłu, ponieważ nie jest to naturalny sposób myślenia człowieka o sytuacjach.

Odwrócenie sekwencji zdarzeń wpływa też na zmianę sposobu myślenia z przyczyna-skutek na skutek-przyczyna. Jeżeli w kroku drugim ułożyliśmy zdarzenia jako “zakupiono bilet -> odebrano bilet” to myślimy o nich w sposób “Co się stało po zakupieniu biletu? Bilet został odebrany.”. Jeżeli natomiast spróbujemy w drugą stronę to myślimy “Co musiało się stać, aby bilet został odebrany?”. Otwiera nam to zupełnie inną perspektywę i ułatwia dostrzeżenie innych warunków i scenariuszy doprowadzenia do tego samego zdarzenia. Krok ten pozwolnił nam na zapisanie kolejnych zdarzeń domenowych.

# Krok 4 - Add users and systems

Po uporządkowaniu procesu mogliśmy oznaczyć aktorów pojawiających się w systemie będących albo “ludźmi”, albo “systemami zewnętrznymi”. Pozwalało to na niewgłębianie się w logikę zewnętrznych systemów (jak np. bramka płatności), a jedynie oznaczenia ich udziału kolejnym kolorem karteczki. Ciekawym elementem tego kroku było ukazanie tego samego aktora pod kilkoma nazwami. Człowiek idący do kina na film był na różnych etapach procesu nazywany: leadem, klientem lub widzem.

Nie było to elementem naszych warsztatów, ale zgodnie z definicją słowa kontekst (setup w którym słowa nabierają szczególnego znaczenia) Event Storming umożliwia nakreślenie granic [bounded contextów](https://martinfowler.com/bliki/BoundedContext.html), będących jednym ze wzroców [Domain-Driven Design](https://www.amazon.com/gp/product/0321125215?ie=UTF8&tag=martinfowlerc-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0321125215).

# Krok 5 - Choose the right problem

W taki sposób stworzony wysokopoziomowy model ułatwia przemyślenie tego na rozwiązaniu których problemów w całym procesie powinniśmy się skupić. Zgodnie z tym o czym pisałem już kiedyś - oprogramowanie zazwyczaj tworzymy po to, aby: zarobić więcej, obniżyć koszty, obniżyć poziom ryzyka, rozwiązać problem. Poszukując odpowiedzi na to gdzie powinniśmy pokierować swoją uwagę, warto spojrzeć na model właśnie w sposób oznaczenia (kolejny kolor karteczki) miejsc przynoszących nam pieniądze lub generujących stratę. Te punkty często będą najbardziej wartościowe dla klienta.

# Czy to tylko tyle?

Zdecydowanie nie! Jest to jedynie wstęp do metody pozwalający na stworzenie big picture procesu. Olbrzymią zaletą Event Stormingu jest wypracowanie wspólnego języka programistów z przedstawicielami biznesowymi, czyli [Ubiquitous Language](https://martinfowler.com/bliki/UbiquitousLanguage.html). Innymi poziomami Event Stormingu są process modeling oraz software design, które pozwalają na przełożenie wysokopoziomowego biznesowego modelu (poziom big picture) na niskopoziomowy projekt aplikacji. Etapy te pozwalają np. na zejście do poziomu commandów oraz read modeli znanych ze wzorca [CQRS](https://martinfowler.com/bliki/CQRS.html), co jest bardzo przydatne dla programistów podczas tworzenia kodu aplikacji. Idąc dalej, zdarzenia domenowe mogą być sugestią działania aplikacji opartych o [event sourcing](https://martinfowler.com/eaaDev/EventSourcing.html).

Jeżeli ten artykuł zainspirował Ciebie do spróbowania event stormingu, zachęcam do obejrzenia prezentacji twórcy tej metody - [Alberto Brandolini - 50,000 Orange Stickers Later](https://www.youtube.com/watch?v=1i6QYvYhlYQ).

Istnieje jedna rada, której użyję jako podsumowanie: **nie czytaj zbyt długo o Event Stormingu, spróbuj w praktyce, w gronie swojego zespołu, bez udziału klienta**.

# Wnioski po warsztacie Agile Wrocław

Wracam do udziału w warsztatach. To zdecydowanie efektywniejszy sposób zdobywania umiejętności, niż forma wykładowa.

Spotkanie przeprowadzone przez Mariusza Gila i Krzysztofa Menżyka, zorganizowane przez Agile Wrocław było na tak wysokim poziomie, że bez zastanowienia zostaję patronem Agile Wrocław. Również możecie to zrobić dzięki profilowi [Agile Wrocław na Patronite](https://patronite.pl/agilewroclaw).

Jest to jedna z metod, których trzeba uczyć się w praktyce, a nie jedynie o nich czytać. Dlatego też wspólnie z kolegą, z którym uczestniczyłem w zajęciach przeprowadzimy dla części osób z naszej firmy warsztat pokazujący tę metodę w praktyce. Wierzymy, że nasunie nam to kolejne wnioski, zwiększy poziom doświadczenia oraz zachęci inne osoby do zainteresowania się lekkimi sposobami dokumentowania i projektowania. Warsztat wewnętrzny w naszej firmi ebędzie miał miejsce 2018-04-13 (publiczna deklaracja musi zadziałać :)).

* * *

#### Źródła i pojęcia

*   \[1\] [Product Craftsmanship - Agile Wrocław, Facebook](https://web.facebook.com/Product-Craftsmanship-Agile-Wroc%C5%82aw-1791532430917050/)
*   \[2\] [Event storming, Wikipedia](https://en.wikipedia.org/wiki/Event_storming)
*   \[3\] [Event storming, książka Alberto Brandoliniego](http://eventstorming.com/)
*   \[4\] [Bus factor, Wikipedia](https://en.wikipedia.org/wiki/Bus_factor)
*   \[5\] [Bounded context, Domain-Driven Design, Martin Fowler](https://martinfowler.com/bliki/BoundedContext.html)
*   \[6\] [Realtime Board](https://realtimeboard.com/)
*   \[7\] [How to spot a liar: get them to tell their story backwards, dailymail.co.uk](http://www.dailymail.co.uk/sciencetech/article-460505/How-spot-liar-tell-story-backwards.html)
*   \[8\] [Cognitive load, psychology.iresearchnet.com](http://psychology.iresearchnet.com/forensic-psychology/police-psychology/detection-of-deception-cognitive-load/)
*   \[9\] [Domain-Driven Design, Eric Evans](https://www.amazon.com/gp/product/0321125215?ie=UTF8&tag=martinfowlerc-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0321125215)
*   \[10\] [Ubiquitous Language, Martin Fowler](https://martinfowler.com/bliki/UbiquitousLanguage.html)
*   \[11\] [Command Query Responsibility Segregation, Martin Fowler](https://martinfowler.com/bliki/CQRS.html)
*   \[12\] [Alberto Brandolini - 50,000 Orange Stickers Later](https://www.youtube.com/watch?v=1i6QYvYhlYQ)
*   \[13\] [Agile Wrocław, Patronite](https://patronite.pl/agilewroclaw)
*   \[14\] [Ten, w którym odkrywamy domenę. Product Craftsmanship - Agile Wrocław.](https://www.meetup.com/pl-PL/Product-Craftsmanship-Agile-Wroc%C5%82aw/events/248656214/?eventId=248656214)
*   \[15\] [Discovering unknown with Event Storming, Mariusz Gil](https://www.youtube.com/watch?v=Pl5HD8Ae3PU)
*   \[16\] [Rolka papieru, Ikea](https://www.ikea.com/pl/pl/catalog/products/80324072/)
*   \[17\] [Event Sourcing, Martin Fowler](https://martinfowler.com/eaaDev/EventSourcing.html)

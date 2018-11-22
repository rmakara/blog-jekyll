---
layout: post
title: OnEstimates. Część III&#58; Zagrożenia płynące z estymacji
image: /assets/20171119_header.jpg
---

# Każdy kij ma dwa końce

Powiedzieliśmy już, że z estymacji płynie bardzo wiele korzyści i główną z nich jest edukacja. Z drugiej jednak strony, wdrażanie nowego elementu niesie za sobą konsekwencje tworzenia nowych ryzyk w innych obszarach systemu złożonego, a taki tworzony jest przez wszystko co ma związek z wytwarzaniem oprogramowania.

Patrząc na potencjalne problemy z różnych perspektyw (dev, QA, PM, SM, PO) można dostrzec zupełnie coś innego. Korzystając z tego, że miałem okazję pracować zarówno jako developer, jak i project manager przytoczę elementy, które były dla mnie niezrozumiałe gdy siedziałem tylko po jednej ze stron.

# Plany biznesowe i akcje marketingowe

Tworzenie softu jest częścią biznesu. Osoby biznesowe traktują proces tworzenia oprogramowania jako element czegoś większego. To sprawia, że estymacje mogą prowadzić do określenia orientacyjnych (lub precyzyjnych) terminów wdrożenia nowych funkcjonalności z którymi mogą wiązać się plany biznesowe firmy. Wyobraźmy sobie np. wdrożenie nowej funkcjonalności obsługi e-faktur i proces zachęcania użytkowników do przejścia z wykorzystywania faktur papierowych na wersje elektroniczne. W celu przeprowadzenia takiego działania milion klientów otrzymujących faktury papierowe ma dostać wraz z kolejną fakturą ulotkę informującą o korzyściach płynących z przejścia na wersje elektroniczną. Takie działanie musi być poprawnie osadzone w czasie i nastąpić po wdrożeniu obsługi e-faktur do oprogramowania. W jaki sposób zsynchronizować jedno z drugim? Estymować, mierzyć i weryfikować. Jeżeli nasze estymacje będą niepoprawne, a wszelkie działania marketingowe oraz proces wytwarzania danego modułu trwa np. 3-4 miesiące to w sytuacji, gdy ulotki zostaną rozesłane do miliona klientów, a system nie będzie gotowy - mamy problem. Informacja o tego typu problemach w większości firm nawet nie trafia do programistów. Warto ich informować, aby generować poczucie odpowiedzialności i zobowiązania.

# Harmonogram

Współpracując z innymi musimy być przewidywalni, ponieważ muszą oni dostosować wykonywaną przez siebie pracę do nas, a my naszą do nich. Jeżeli niepoprawnie wyestymujemy czasy zamykania kolejnych etapów wytwarzania systemu, czyli innymi słowy stworzymy nierealny harmonogram doprowadzamy do sytuacji w której zaburzamy nie tylko cykl swojej pracy, ale również wszystkie harmonogramy zależne. Książkowym przykładem jest wytwarzanie aplikacji z dużą ilością integracji, które dopiero będą przygotowywane w innym systemie przez firmę trzecią. Każde przesunięcie terminu w wytwarzaniu powoduje nie tylko zmianę harmonogramu prac firmy trzeciej, ale również naszej… a być możę również działów w naszej firmie, których praca ponownie jest zależna od obiecanych przez nas elementów.

# Planowanie budżetu

Ze względu na złożoność wytwarzanych aplikacji bardzo ciężko jest wyszacować koszt stworzenia dużego systemu już na początku jego realizacji. Między innymi przez to popularna jest forma rozliczania [time & materials](https://en.wikipedia.org/wiki/Time_and_materials), która opiera się na pobieraniu opłat w oparciu o stawki godzinowe. Zmiana formy rozliczania na taką nie oznacza, że nasz klient nagle przeobraża się w studnię bez dna i możemy od niego pobierać pieniądze w nieskończoność. Budżet jest ograniczony, zawsze. Estymowanie, mierzenie i weryfikowanie pozwala na kontrolę aktualnego stanu budżetu oraz planowanie jego wykorzystnaia w przyszłości. Co można zrobić źle? Estymować i mierzyć, ale nie weryfikować. Jeżeli taki scenariusz połączymy z wytwarzaniem dużego systemu w modelu “wdróżmy wszystko naraz, a nie iteracyjnie” to kończymy bez budżetu, ale z systemem wytworzonym w 80%, który nie jest gotowy do wykorzystania przez klientów.

# Motywacja zespołu

W poprzedniej części serii o estymacjach przytaczaliśmy następujące prawo:

> Praca rozszerza się tak, aby wypełnić czas dostępny na jej ukończenie.
> 
> – Prawo Parkinsona, Cyril Northcote Parkinson

Brak definiowania deadlineów wpływa negatywnie na wydajność, kreatywność i poczucie odpowiedzialności zespołów. Wiąże się to między innymi z teorią mówiącą, że w ramach wspierania pracy zespołów samoorganizujących się powinniśmy umożliwić im samoorganizację, ale jednoczęśnie nadając pewne ograniczenia w obrębie których taki zespół samodzielnie powinien stworzyć rozwiązania. Jednym z takich ograniczeń jest właśnie termin - należy pamiętać, aby był wywarzony - motywujący i osiągalny - ponieważ może wpłynąć na zespół zarówno pozytywnie, jak i negatywnie.

Szacowanie jest motywujące również przez publiczne (i grupowe) mówienie o tym. Stałe podawanie niepoprawnych estymacji pozbawione wyciągania wniosków na przyszłość jest pewną plamą na honorze, którą widzą koledzy i koleżanki z zespołu.

# Wysoka niedokładność

Nabywając każdą nową umiejętność na początku jesteśmy skazani na niepowodzenia. Estymowanie w początkowych fazach pracy z systemem którego nie znamy generuje stres wśród członków zepsołu i łatwo jest doprowadzić do sytuacji w której ludzie nie chcą kontynuować szacowania, ponieważ w pierwszych sprintach wiele estymacji jest przekroczonych. Rolą osób spokojniejszych (lub [Scrum Mastera](https://en.wikipedia.org/wiki/Scrum_(software_development)#Scrum_master)) jest wyjaśnienie po co to robimy i dlaczego warto, oraz doprowadzenie do sytuacji w której każdy członek zespołu rozumie powody stojące za estymowaniem, zamiast traktować spotkania groomingowe jako najbardziej stresujący moment tygodnia.

# Mowa nienawiści

Podobnie jak w przypadku komunikacji przy code review, można stworzyć atmosferę w której przeglądanie kodu innych osób czy analizowanie estymacji i ich słuszności stanie się okazją do wyładowania emocjonalnego, i powiedzenia innym jacy są źli. Ponownie, rolą Scrum Mastera lub współpracującego ze sobą zespołu jest doprowadzenia do sytuacji w której nikt nie traktuje tego procesu jako potencjalnego powodu do zaczepki, a jako element wspierający w stawaniu się lepszą grupą zmierzającą w tym samym kierunku.

# Błędy i zmiany

Szacując objętność dowolnego zadania bardzo często skupiamy się na obsłudze [szczęśliwej ścieżki](https://en.wikipedia.org/wiki/Happy_path) jego wykonania. Zapominamy o ewentualnych błędach, które może generować stworzone rozwiązanie oraz konieczności wdrożenia modyfikacji na które wpadamy podczas jego realizacji. W takich sytuacjach z pomoca przychodzi nam rozmowa z zespołem podczas [daily](https://en.wikipedia.org/wiki/Scrum_(software_development)#Daily_scrum), wykorzystwanie funkcjonalności Remaining Estimate w systemach ticketowych, [test driven development](https://martinfowler.com/bliki/TestDrivenDevelopment.html) oraz [behaviour driven development](https://dannorth.net/introducing-bdd/).

Specjaliści najczęściej są optymistami. Warto zestawiać własne myślenie z głębokim drążeniem tematu w zakresie tego czego mogliśmy nie przemyśleć, co mogliśmy przeoczyć, co może pójść nie tak, czy da się to zrobić prościej.

# Samodzielne estymacje

Zupełnie jak w stadzie wilków - nikt nie jest Alfą i Omegą. Bardzo trudne jest osiągnięcie wysokiego prawdopodobieństwa szacunków w systemie złożonym, gdy wykonuje to jedna osoba. Taki element procesu można uznać za antywzorzec i należy omówić z zespołem jego modyfikację na korzyść estymacji grupowych i wspólnego analizowania problemu. Każdy z nas ma inne doświadczenie i każdy popełnił inne błędy w życiu. Dzięki temu nieocenione jest wykorzystywanie punktu widzenia innych osób mogących powiedzieć _“been there, done that… zróbmy to inaczej…“_. Życie przyzwyczaja nas do uczenia się na błędach własnych, a nie na błędach innych osób - nie jest to jednak najefektywniejsza ścieżka.

# Estymowanie cudzej pracy

To chyba najpopularniejszy antywzorzec z którym się spotykałem. Lider zespołu lub manager estymujący czas realizacji zadania bez udziału specjalistów, którzy będą dane zadanie realizować. Doprowadza to do stresowania zespołu, ale przede wszystkim do pozbawiania nas szansy na omówienie rozwiązywanego problemu w kilka osób. Gdy to tylko możliwe - estymujmy w grupach, koniecznie przy udziale tych osób, które będą brać udział w doprowadzaniu zadania do końca.

# Agresywny klient

Współpracownicy oraz klienci są różni. Zdarzają się sytuacje w których rozmawiamy z osobami kontaktowymi po stronie klienta, które mogą być dość konkretne, ostre lub niemiłe. W takich sytuacjach osoby o słabszych charakterach mają tendencję do zaniżania swoich estymacji, celem uniknięcia kontaktu z nieprzychylną klienta. Problemy wychodzą później, gdy konieczne jest przedstawienie wyników swojej pracy. W takich momentach warto chronić osoby, które na trudną komunikację z klientem reagują wysokim stresem i warto umożliwić im skupienie się na samej efektywnej realizacji zadania.

# Zbyt wczesne szacowanie i brak odpowiedniej granulacji

Warunkiem poprawnego okreslenia objętości zadania jest posiadanie wystarczającej ilości danych o nim. Estymując zadanie o olbrzymim zakresie, bez przeprowadzenia wstępnej analizy dość trudno jest precyzyjnie je oszacować. Warto zebrać podstawowe informacje, a przede wszystkim podzielić task na mniejsze, których szacowanie będzie zdecydowanie łatwiejsze.

# Podsumowanie

Każdy kij ma dwa końce. W przypadku estymacji zdecydowanie korzystniejszym z końców jest ten pozytywny, ale warto pamiętać również o negatywnych aspektach płynących z procesu estymowania i przygotować się na spotkanie z nimi, ponieważ z pewnością się pojawią.

Powyższe przykłady stanowią jedynie niewielki wycinek problemów jakie mogą powstać podczas podejmowania wysiłku szacowania pracy. Należy jednak pamiętać, że najczęstszym rozwiązaniem jest - praca zespołowa.

> Talent wins games, but teamwork and intelligence win championships.
> 
> – Michael Jordan

* * *

#### Źródła i pojęcia

*   \[1\] [Time & materials, Wikipedia](https://en.wikipedia.org/wiki/Time_and_materials)
*   \[2\] [Scrum Master, Wikipedia](https://en.wikipedia.org/wiki/Scrum_(software_development)#Scrum_master)
*   \[3\] [Daily Scrum, Wikipedia](https://en.wikipedia.org/wiki/Scrum_(software_development)#Daily_scrum)
*   \[4\] [Test Driven Development, Martin Fowler](https://martinfowler.com/bliki/TestDrivenDevelopment.html)
*   \[5\] [Behaviour Driven Development, Dan North](https://dannorth.net/introducing-bdd/)

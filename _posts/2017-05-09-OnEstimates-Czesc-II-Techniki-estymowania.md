---
layout: post
title: OnEstimates. Część II&#58; Techniki estymowania
image: /assets/20170509_header.jpg
article_language: pl
---

Norma, czyli wszystko “na już”
==============================

W momencie zapytania specjalisty o czas realizacji danego zadania - niezaleznie od jego objętości - dość szybko można uzyskać liczbę godzin w jakim szacunkowo będzie mogło ono zostać zrealizowane. Czasami taki proces estymowania trwa od kilku do kilkunastu sekund. Takie sytuacje obarczone są jednak dużym ryzykiem błędu. Na podstawie doświadczeń zebranych z punktu widzenia programisty oraz punktu widzenia project managera stwierdzam, że pytanie:

> Ile czasu zajmie Ci realizacja zadania X?

gwarantuje uzyskanie bezwartościowej odpowiedzi. Bardziej wartościowym sformułowaniem okazuje się być:

> Kiedy będziesz wiedział(a) ile czasu zajmie Ci realizacja zadania X?

Postawienie specjalisty przed takim wyzwaniem umożliwia przygotowanie się do udzielenia odpowiedzi, granulacji zadania i zrobienia wstępnego rozeznania. W efekcie, taka lingwistyczna modyfikacja w przypadku estymacji potrzebnych “na już” umożliwia uzyskanie kompetentnej odpowiedzi, nawet po 10-15 minutach.

Granulacja
==========

Niezależnie od przyjętej techniki estymowania nieodłącznym krokiem wyceny danego zakresu pracy jest jego rozbicie na mniejsze elementy. Ocena epicu, który będzie realizowany przez najbliższe 3 miesiące lub nawet historyjki pozornie wymagającego dwóch dni pracy w postaci jednej liczby jest dość naiwnym posunięciem. Podział na podpunkty z których każdy zajmie od 0 do 4 godzin daje zdecydowanie lepsze efekty. Wyobraźmy sobie, że musimy przygotować mechanizm weryfikacji dwuetapowej (2FA), który będzie wykorzystywany w systemie umożliwiającym wykonywanie transferów pieniężnych pomiędzy kontami. Analizując jego estymację w głowię można rzucić losową liczbę godzin już po 10 sekundach. W takiej sytuacji, w przypadku chęci weryfikacji tej liczby można byłoby zastosować na niej technikę 5 Why. Możemy jednak spróbować rozbić zadanie na podzadania:

*   Stworzenie paczki 2FA.
*   Przemyślenie zależności i ich wstrzykiwania.
*   Stworzenie kontrolera obsługującego request.
*   Stworzenie handlera / serwisu zawierającego logikę działania.
*   Stworzenie mechanizmu generowania kodów jednorazowych.
*   Stworzenie interfejsu odpowiadającego za wysyłkę kodów.
*   Stworzenie klasy implementującej powyższy interfejs dla wysyłki w formie maila.
*   Stworzenie klasy implementującej powyższy interfejs dla wysyłki w formie sms.
*   Stworzenie konfiguracji umożliwiającej zdefiniowanie długości kodów jednorazowych, sposobu wysyłki kodu (mail, sms), którą później wykorzystamy w naszym serwisie 2FA.
*   Spięcie wszystkiego razem.
*   Testy jednostkowe.
*   Testy manualne.
*   apiDoc.
*   Komunikacja w zakresie doprecyzowania wymagań co do których wątpliwości pojawiły nam się podczas tworzenia podzadań (czy sms, czy email, czy kody numeryczne, czy alfanumeryczne, czas ważności kodu, czy function as a service).

Powyższa lista być może pomija kilka istotnych punktów. Daje jednak pewne wyobrażenie na to jak rozwiązanie będzie zaimplementowane i pokazuje, że zostało to wstępnie przemyślane i tym samym udostępnia tą wiedzę innym członkom zespołu. Estymacja każdego z powyższych podzadań pomaga w celnym oszacowaniu całości. Taka forma wzbudza zaufanie specjalisty, managera i klienta.

Jednostka pierwsza - Godziny idealne
====================================

Najbardziej oczywistą jednostką wyrażającą szacunkową wartość, która poinformuje nas o koszcie realizacji danych czynności wydają się być godziny. Ze względu na fakt powszechności jej stosowania w naszym życiu codziennym wiele osób rozumie czas poświęcany na pracę w ciągu jednego dnia jako 8 godzin. W przypadku wyceny zadania na 24 godziny wydaje się być oczywistym, że czas jego realizacji to 3 dni robocze, czyli zadanie rozpoczęte w poniedziałek będzie gotowe na czwartek rano. Należy jednak pamiętać, że ludzie nie są w stanie wydajnie pracować przez 100% swojego czasu. Dodatkowo, należy od tej wartości odjąć czas na rzeczy towarzyszące naszej codzienności tj. lunch, kawę, spotkania, plotki oraz Wykop. Po urealnieniu wspomnianych 8 godzin okazuje się, że wydajnie pracujemy od 3 do 6 godzin dziennie.

Innym problemem płynącym z estymacji w postaci godzin idealnych (ang. ideal hours) jest różnica w poziomie umiejętności ludzi oraz presja pojawiająca się przy estymowaniu grupowym. Jeżeli proces wygląda tak, że zespół w pierwszej kolejności szacuje zadania do realizacji, a dopiero potem rozdziela je na konkretne osoby to wspólnie uzyskana estymata może być realna do osiągnięcia przez osobę mającą 5-letnie doświadczenie, a w przypadku przyporządkowania tego samego zadania do osoby dopiero rozpoczynającej swoją karierę - czas potrzebny na realizację będzie 12-krotnie wyższy. Taki problem można ominąć przez odwrócenie procesu i estymowanie czasu realizacji dopiero po wyznaczeniu konkretnych osób, które będą nad danymi zadaniami pracować. Wtedy jednak pojawia się stres i presja, a przez to tracimy największą wartość płynącą z estymacji grupowych - prawdziwą pracę zespołową, różne i obiektywne punkty widzenia.

Jednostka druga - Punkty, rozmiary koszulek
===========================================

Kolejną z jednostek są punkty (ang. story points). W wersjach alternatywnych możemy wykorzystywać również rozmiary koszulek (XS, S, M, L, XL, XXL) lub inne mniej, lub bardziej abstrakcyjne metafory. Punkty, których pula definiowana jest najczęściej przez liczby Fibonacciego (0, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144 \[…\]) dają nam jednak wystarczająco wiele możliwości i nie zmuszają do wymyślania przenośni.

Podstawową różnicą między godzinami idealnymi i punktami jest fakt, że punkty służą do określenia rozmiaru danego zadania, a nie czasu jego realizacji. Pokażą czy zadanie X jest mniejsze lub większe od innych. W związku z tym, że estymacje punktowe bazują w sporej mierze na porównaniach, prawdziwa ich wartość ukazuje się dopiero po pewnym czasie, gdy zespół posiada doświadczenie w estymowaniu zadań wewnątrz danego projektu i tym samym dysponuje większą liczbą punktów odniesienia do których może porównywać kolejne zadania.

Taki sposób określenia zakresu zadania również rozwiązuje problem doświadczenia osoby, które będzie je realizowała. Niezależnie od tego czy będzie to osoba o mniejszym, czy większym doświadczeniu to na podstawie wspólnych ustaleń zespołu zadanie X stale jest mniejsze od zadania Y, a większe od zadania Z.

Wraz ze wzrostem doświadczenia możliwe jest stawianie celów dotyczących granulacji na zasadzie “Chcemy, aby maksymalną możliwą estymatą było 13 punktów.”. Wartość ta, wraz ze wzrostwem umiejętności szacowania i wiedzy o projekcie może być zmniejszana o kolejne skoki, czyli w tym przypadku do 8 (-> 5 -> 3…) punktów.

Zdecydowaną trudnością we wdrożeniu estymacji niegodzinowych jest konieczność przekonania klienta do wykorzystania wartości, których w pierwszym odczuciu nie można wykorzystać do wyliczenia szacunkowego kosztu danego zlecenia.

Jednostka trzecia - NoEstimates
===============================

Kilka lat temu w świecie wytwarzania oprogramowania popularny zrobił się ruch popularyzowany przez hashtag #NoEstimates. Wbrew swojej nazwie, sposób ten nie polega na pełnej rezygnacji z szacowania pracy potrzebnej do wykonania, a na maksymalnym jej uproszczeniu. Wymaga jednak pewnej dojrzałości od zespołu i zakłada, że wszystkie historyjki będą zdefiniowane w taki sposób, aby ich objętość była podobna. Przy założeniu, że nauczymy się definiować wszystkie PBI (Product Backlog Item) tak, aby ich pracochłonność była podobna i była relatywnie mała to możemy badać progres w realizacji, prędkość zespołu (ang. velocity) przez zliczanie liczby historyjek obecnych w backlogu / rozpoczynanych / zamykanych w danym okresie czasu. W tej technice za jednostkę uznajemy pojedynczy PBI.

Przedsmakiem do osiągnięcia takich umiejętności może być rozpoczęcie od estymacji punktowych i zmierzanie z nimi do szacowania wszystkich historyjek tylko przy użyciu liczb 0, 1, 2.

> #NoEstimates nie jest porzuceniem estymowania, mierzenia, budżetowania.

Scrum
=====

Wykorzystywanie najpopularniejszego frameworku w świecie IT do organizacji pracy zespołowej uczy nas spotkań refinementowych / groomingowych oraz planingowych. Te pierwsze poświęcone są rozbijaniu zadań na mniejsze, doprecyzowywaniu, niwelowaniu zależności między nimi oraz estymowaniu (!#NoEstimates). Drugie natomiast, poświęcane są na dobór odpowiedniej liczby priorytetowych zadań do rozpoczynanego Sprintu, które uprzednio zostały wyznaczone przez Product Ownera oraz do wspólnego omówienia sposobu ich realizacji. Narzucenie takich ram pracy współgra z zespołowym podejściem do pracy, estymacji oraz wytwarzania oprogramowania.

Wartości dla zespołu i klienta
==============================

Rzetelne podejście do procesu granulacji oraz estymowania zadań niesie za sobą wiele benefitów zarówno dla firmy wytwarzającej oprogramowanie, jak i dla klienta, doprowadzając do sytuacji w której jest to proces opłacalny dla każdego. Dzięki zespołowym przeprowadzeniu tego procesu:

*   Szerzymy wiedzę zespołu o projekcie.
*   Gromadzimy mierzalne dane umożliwiające planowanie w perspektywie długoterminowej.
*   Dajemy sobie szansę na wyciąganie wniosków opartych o dane oraz dostosowywanie procesu dla podnoszenia efektywności.
*   Zwiększamy przewidywalność efektów możliwych do osięgnięcia w trakcie kolejnych iteracji.
*   Umożliwiamy Product Ownerowi realny dobór i priorytetyzację wartościowego dla Biznesu zakresu prac.
*   Grupowo zastanawiamy się nad złożonością zadań, efektywnie omawiamy sposób ich realizacji oraz minimalizujemy liczbę zaskoczeń mogących pojawiać się podczas realizacji zadania, dzięki jego wstępnej ocenie przez osoby o różnych punktach widzenia.
*   Obniżamy koszt wytworzenia oprogramowania.

* * *

#### Źródła i pojęcia

*   \[1\] [Uwierzytelnianie wielopoziomowe, Wikipedia](https://pl.wikipedia.org/wiki/Uwierzytelnianie_wielopoziomowe)
*   \[2\] [Wstrzykiwanie zależności, Wikipedia](https://pl.wikipedia.org/wiki/Wstrzykiwanie_zale%C5%BCno%C5%9Bci)
*   \[3\] [Services in Domain Driven Design](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)
*   \[4\] [What is a handler](http://stackoverflow.com/questions/195357/what-is-a-handler)
*   \[5\] [apiDoc](http://apidocjs.com/)

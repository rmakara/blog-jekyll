---
layout: post
title: Czym jest SPIKE? Wyjaśnienie dla Project Managera
image: /assets/20200116_header.jpg
description: Jakie benefity może osiągnąć zespół developerski oraz project manager przez korzystanie ze spajków? 
article_language: pl
---

# Wina analityków

W firmach często pracujemy w systemie projektowym. W związku z tym zdarza się nam realizować spore analizy upfront. Jest to jak najbardziej ok i zwiększa naszą wiedzę w sposób pozwalający na wycenę projektu oraz późniejszą jego realizację. Często jednak programiści narzekają, że _"analiza była słaba"_. Nie jest to oczywiście wina analityków. Jest to kwestia tego, że zawsze narzeka się na osoby "przed nami" w nieperfekcyjnym procesie w którym brakuje poprawnych przepływów feedbacku, więc... być może to wina programistów, że nie rozmawiają z analitykami? Who knows. :) A być może późniejsza analiza to coś normalnego?

# Co na to Pan(i) Agile?

W podejściu zwinnym, effort "uczenia się" lub effort analityczny jest częścią Sprintu. Oznacza to, że każdy członek Development Teamu za taką analizę odpowiada. Jeżeli braki w wiedzy do zrealizowania danej historyjki są dość małe to można taką analizę wykonać w obrębie tego samego issue co samą implementację.

Co jednak, gdy mamy duże braki w wiedzy i nie pozwalają nam one na oszacowanie czasu potrzebnego do realizacji zadania, rozpisanie sub-tasków, ani nawet podjęcie decyzji czy jego implementacja powinna się w ogóle odbyć? Innymi słowy, nie mamy wiedzy, aby rozpocząć realizację zadania. PM pyta _"ile godzin?"_, a odpowiedzi nie da się udzielić.

Na pomoc przychodzi typ zadania znany w środowisku programowania ekstremalnego jako - SPIKE.

# Czym jest spike?

SPIKE to wysiłek / effort, który może być wydzielony z historyjek implementacji konkretnych funkcjonalności na rzecz zdobycia wiedzy, która pozwoli nam rozpocząć faktyczną pracę nad zadaniem (lub podjąć decyzję o jego odrzuceniu). Spajki mogą być funkcjonalne, techniczne, architektoniczne [...]. 

Ich wynikiem jest zwiększenie wiedzy o danym problemie co pozwolą na podjęcie lepszej decyzji.

# Przykład 

Mamy user story: _"Jako Content Manager chcę w Prismicu zbudować stronę statyczną z odnośnikami do polecanych artykułów, aby następnie została ona wyświetlona na stronie statycznej w naszym storefroncie"_.

Załóżmy, że nasz zespół nigdy nie integrował się z [Prismiciem](https://prismic.io/) i trochę nie wie od czego zacząć. Oszacowanie punktowe / czasowe realizacji tej historyjki będzie strzałem bazującym na domysłach. Nie są znane też ryzyka, które mogą zaistnieć podczas implementacji. No i teraz możemy wydzielić przykładowe spike. Opiszmy je w formie storiesów (kilka różnych wersji):

* [SPIKE] Jako Dev Team chcemy zdobyć wiedzę o tym jak pobierać dane z Prismica oraz w jakiej formie przekazywane są strony z Prismica na storefront, aby precyzyjnie zdefiniować zadania z zakresu integracji z Prismic i je wyestymować
* [SPIKE] Jako Dev Team chcemy zweryfikować czy pokazywanie linków na stronach statycznych z Prismica niesie za sobą jakieś potencjalne problemy, aby precyzyjnie podczas refinementu uwzględnić ryzyka do przemyślenia podczas implementacji historyjki
* [SPIKE] Jako Dev Team chcemy zebrać wnioski z integracji z systemami CMS w innych naszych projektach, aby przyjąć jak najlepszą koncepcję architektoniczną dla integracji z Prismiciem

# Przykłady spike'ów z innej beczki

* [SPIKE] Chcemy wykonać analizę SWOT, aby ustalić czy powinniśmy zaimplementować system rekomendacji produktowych w naszym eCommerce wykorzystując PHP, Pythona, czy może powinniśmy kupić gotowe rozwiązanie?
* [https://github.com/DivanteLtd/shopware-pwa/issues/98](https://github.com/DivanteLtd/shopware-pwa/issues/98)
* [https://github.com/DivanteLtd/shopware-pwa/issues/100](https://github.com/DivanteLtd/shopware-pwa/issues/100)
* [https://github.com/SAP/cloud-commerce-spartacus-storefront/issues/1218](https://github.com/SAP/cloud-commerce-spartacus-storefront/issues/1218)

# Dobre praktyki spajkowania

* Dla każdego spike warto ustalić __konkretny timebox__. Np. na realizację naszego spike o Prismica chcemy poświęcić __maksymalnie 3 godziny__. W tym czasie zdobywamy jak najwięcej wiedzy + spisujemy wnioski. To musi nam wystarczyć do podjęcia kolejnych decyzji.
* Warto zaznaczyć w kryteriach akceptacyjnych danego spike co powinno być wynikiem jego realizacji. Analiza SWOT, rekomendacja, lista ryzyk, lista sub-tasków, pseudo-kod?

# Jak Ci to pomoże jako PMowi?

* Estymaty historyjek do implementacji będą bardziej precyzyjne.
* Ludzie mają tendencję do implementacji pierwszego rozwiązania jakie wpadnie im do głowy. Spajkowanie pomaga na weryfikację czy pierwszy pomysł na pewno jest najlepszy. 
* Spajki skrócą czas implementacji oraz późniejszego ping-pongu na etapie testowania.
* Założenia techniczne prawdopodobnie będą lepsze i czas potrzebny na późniejszy refactoring będzie mniejszy.
* Zwiększenie wiedzy pozwoli na stworzenie sub-tasków, które uczynią proces implementacji bardziej transparentnym. Unikniemy sytuacji "koduję, będzie gotowe jak skończę".
* Odseparowanie "uczenia się" od implementacji zwiększy transparentność tego co aktualnie się dzieje z danym zadaniem. Unikniemy tego, że przez 2 tygodnie będziemy czekać na realizację czegoś, co w praktyce nawet się nie zaczęło, bo ktoś samodzielnie wchodzi w bardzo głębokie rozkminy na poziomie _"czy można płakać pod wodą?"_.
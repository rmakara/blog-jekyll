---
layout: post
title: Przez brak continuous deployment tracisz do 20% budżetu. Wyjaśnienie dla Project Managera
image: /assets/20200121_header.jpg
description: Jak techniki programistyczne przekładają się na benefity, które mogą być zauważone z perspektywy project managerów? Dzisiaj o continuous delivery i deployment.
article_language: pl
---

# Jak być najszybszym?

Jest taka książka jak [Accelerate: The Science of Lean Software and DevOps](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339), która omawia kilkuletnie badanie nad kulturą DevOps w którym przeanalizowano 23 000 ankiet z ponad 2000 organizacji. Klastruje ono organizacje jako tzw. low perfermerów, mid performerów oraz high performerów.

Jeżeli jesteś dużą firmą, która jest wspierana przez technologię to jeżeli nie stosujesz technik wyłonionych przez te badanie to - __poniesiesz porażkę__. 

> In 2017, the DORA research team found that high performers executed 46 times more code deployments, and had a lead time, from commit to deploy, that was 440 times faster; a mean time to recover from downtime that was 170 times faster; and a change failure rate that was 5 times lower.

__Continuous deployment__ to scenariusz w którym wszystko co pojawi się branchu master od razu jest deployowane na produkcję. Na potrzeby tego artykułu możemy przyjąć, że wszystko z brancha master/develop idzie na środowisko testowe. Technika ta ma olbrzymie znaczenie dla tematów nietechnicznych, w tym prowadzenia projektu.

Badanie mówi m.in. o tym, że:

* Software delivery ma kluczowy wpływ na kulturę organizacyjną firm nie-IT (naszych klientów!).
* Bez Lean, Agile, DevOps - jesteśmy w polu.
* CD zwiększa motywację zespołów developerskich (np. częstsza gratyfikacja z sukcesów).
* Zwiększa współpracę członków zespołu (np. konieczność utrzymywania brancha master/develop w "deployowalnej" jakości).
* Obniża ryzyko przyszłych deploymentów, czyli tzw. _"deployment pain"_ ([prezentacja o DevOps w 2009 roku mówiła "róbmy 10 deploymentów dziennie"](https://www.youtube.com/watch?v=LdOe18KhtT4)).

# Z czym musisz się pogodzić bez CD na środowisko testowe?

* Motywacja zespołu oraz poczucie odpowiedzialności specjalistów za projekt będą zdecydowanie niższe.
* Stworzycie ryzyko tego, że przez pół roku będziecie developować roczny projekt bez działającego czegokolwiek.
* Negatywnie zwiększycie potrzebny budżet projektu do dowiezienia tego samego zakresu. Moja estymacja to +20% przy długich projektach.
* Będziesz zmuszony ufać na słowo developerom mówiącym, że "kodzik jest ok". 
* Co najgorsze, developerzy będą ufać swojemu liderowi, że "kodzik jest ok".
* Go Live będzie wyzwaniem.

# Insights z książki Accelerate w wersji dla PMa

* Jeżeli czas Twojego zespołu poświęcany na deploymenty jest większy niż 1h tygodniowo to jest to zły wynik.
* Jeżeli robisz deploymenty rzadziej, niż raz na tydzień to jest to bardzo zły wynik.
* Jeżeli nie znasz technik poruszanych w Accelerate - to nie umiesz robić oprogramowania w 2020 roku. Wylistuję je w kolejnym artykule - [LINK](https://rmakara.github.io/24-praktyki-high-performerw-z-ksiazki-accelerate).

# Co Tobie continuous deployment na test env da jako PMowi?

* __W każdej chwili będziesz mógł wejść na test env i zobaczyć w jakim stanie jest Wasz projekt.__
* Zmniejszysz potrzebny budżet na development, testowanie, deployment.
* Zwiększysz motywację i odpowiedzialność Development Teamu.

# Skąd te +20% budżetu?

Lean wykazuje [8 marnotrawstw](https://en.wikipedia.org/wiki/Lean_manufacturing#Types_of_waste). W świecie software developmentu marnotrawstwem może być np. ręczne przenoszenie nowych wersji aplikacji na produkcję lub środowisko testowe. Jeżeli nie będziemy mieli continuous delivery/deployment to specjaliści będą zmuszeni do robienia tego za każdym razem ręcznie. Doprowadzi to do tego, że:

* Testerzy będą czekać dłużej na udostepnienie wersji do testowania.
* Programiści będą zmuszeni porozumiewać się w zakresie czasu / dnia / godziny / osób potrzebnych do deploymentu. Pojawią się pytania "czy / kiedy ta zmiana będzie wypuszczona?".
* Niezautomatyzowany proces deploymentu aplikacji, czyli prace wykonywane ręcznie będą generować błędy.
* Prawdopodobnie rzadziej będziemy decydować się na deployment aplikacji, więc cycle time będzie dłuższy, a feedback od klientów będzie otrzymywany wolniej. Później dowiemy się o problemach i błędach.
* Zaistnieje większe prawdopodobieństwo, że nasza gałąź główna w repozytorium kodu nie będzie utrzymywana w stanie "deployowalnym" i konieczne będzie cykliczne usuwanie nagromadzonych naleciałości.
* Osoby odpowiedzialne za deployment prawdopodobnie staną się silosami wiedzy w zakresie tego jak taki deployment wykonać (bus factor=1?).
* Kolumna WAITING FOR DELOYMENT_ obecna na tablicy kanbanowej stanie się wąskim gardłem w którym prawdopodobnie nie zdecydujemy się wprowadzić limitu work-in-progress.
* Ilość zadań _IN PROGRESS_ wzrośnie ze względu na oczekiwanie na deploymentu, co będzie powodwać konieczność do powracania do nich w celu wykonania deploymentu, więc wzrośnie koszt przełączania się między kontekstami różnych zadań.

I tak w każdym tygodniu pracy... być może koszt będzie większy niż +20%. :)

# Podsumowując

W wersji minimalnej postaraj się o:

* Continuous deployment na środowisko testowe.
* Continuous delivery na środowisko stagingowe.
* Continuous delivery na środowisko produkcyjne.

# Więcej informacji

* [2018 State of DevOps Report](https://inthecloud.withgoogle.com/state-of-devops-18/dl-cd-typ.html)
* [2019 State of DevOps Report](https://puppet.com/resources/report/state-of-devops-report/)
* [Accelerate: The Science of Lean Software and DevOps](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339)
* [Velocity 09: John Allspaw and Paul Hammond, "10+ Deploys Per Day"](https://www.youtube.com/watch?v=LdOe18KhtT4)

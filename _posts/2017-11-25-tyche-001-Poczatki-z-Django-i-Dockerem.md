---
title: tyche 001&#58; Początki z Django i Dockerem
image: /assets/2017_11_25_header.jpg
---

# Programista stażysta

Na początku pisania tego blogu wraz z udziałem w konkursie [Daj się poznać](https://devstyle.pl/daj-sie-poznac/) miałem na celu napisanie aplikacji automatyzującej pracę Project Managera. Aplikacji nie rozwijałem. Ograniczyłem się do napisania dwóch skryptów, które rozwiązały moje największe problemy pracy codziennej. Nie jestem z tego powodu dumny, ale podsumowanie całości było takie, że nie wróciłem do kodowania.

Robię podejście numer dwa. W trzyosobowym zespole rozpoczęliśmy prace nad aplikacją, którą roboczo nazwaliśmy [tyche](https://pl.wikipedia.org/wiki/Tyche). Nazwa pochodzi od greckiej bogini przypadku i ślepego losu. Na bieżącym etapie nie będę opisywał przeznaczenia wytwarzanej aplikacji, ponieważ na to jeszcze przyjdzie czas. W każdym razie, celem jest przypomnienie sobie umiejętności pisania kodu.

# Pierwsze kroki

Rozpoczeliśmy od stworzenia zespołowego kanału [Slacka](http://slack.com), repozytorium kodu na [GitHubie](github.com) wraz z podpiętym narzędziem [ZenHub](https://www.zenhub.com/). Poza samym stworzeniem aplikacji każdy z nas chce poznać nowe narzędzia i technologie z którymi wcześniej nie mieliśmy do czynienia. Jako bazę użyjemy Pythona 3 (polecam artykuł [Python2orPython3](https://wiki.python.org/moin/Python2orPython3)) i frameworku Django. Żaden z nas nie ma doświadczenia w kodowaniu w Django, więc zapowiada się dość zabawna przygoda. W celu usprawnienia stawiania pierwszych kroków w pierwszym commicie do repozytorium znalazł się Dockerfile.

# Docker - podstawowe polecenia

W ramach tego artykułu nie będę opisywał procesu stawiania środowiska przy wykorzystaniu gotowego obrazu [Dockerowego](https://www.docker.com/what-docker) pobranego z [Docker Huba](https://hub.docker.com/), ponieważ takich opisów są już tysiące. Skorzystałem z oficjalnego tutoriala [Quickstart: Comopse and Django](https://docs.docker.com/compose/django/). Jako mały cheat sheet dla siebie z przyszłości wylistuję elementy, które w procesie stawiania środowiska okazały się przydatne.

Pracując na Ubuntu 16.04 LTS, wykonanie tutoriala znajdującego się na oficjalnej stronie Dockera przechodzi całkiem bezproblemowo. Podczas jego realizacji przydatnych było kilka poleceń:

*   `docker ps` - Listuje kontenery.
*   `docker exec -it <container_id> <command>` - Wykonuje polecenie CLI wewnątrz wskazanego kontenera.
*   `docker logs <container_id>` - Wyświetla logi ze wskazanego kontenera.
*   `docker rmi [rf] <image_id>` - Usuwa wskazany obraz.
*   `docker build . --no-cache` - Flaga `--no-cache` wymusza zbudowanie kontenera od zera.
*   `docker-compose up` - Buduje, tworzy, uruchamia kontener, obrazy, wolumeny.
*   `docker-compose down` - Zatrzymuje i usuwa kontenery, obrazy, wolumeny stworzone podczas `up`.
*   `docker-compose build` - Buduje kontener(y).
*   `docker-compose exec web bash` - Uruchamia interaktywny prompt wewnątrz kontenera.

Przy wykorzystywaniu powyższych poleceń pojawiło się kilka ciekawostek.

# docker vs docker-compose

Czym jest `docker`, a czym `docker-compose`? `docker` jest interfejsem CLI służącym do zarządzania poszczególnymi kontenerami. `docker-compose` jest pewnym API/fasadą stojącą warstwę przed interfejsem Dockera. `docker-compose` pozwala wykonywać operacje na wielu kontenerach i dzięki temu skraca listę komend potrzebnych do osiągnięcia określonego celu, po to wykorzystuje plik `docker-compose.yml`.

# docker exec -it

Interesujący jest parametr `-it` występujący obok `docker exec`. Tutaj szczerze mówiąc nie wiem czy jestem w stanie to dobrze wyjaśnić, ponieważ źródła które czytałem nie były dla mnie w pełni zrozumiałe, a wyjaśnienie znajdujące się w oficjalnej dokumentacji również jest niejasne. Całość ma związek z `stdin`, `stdout` oraz `tty`. Parametr `-t` dotyczy `tty`, które jest pojęciem mającym swoje korzenie w historii używania terminali w starych komputerach i jest rozwinięciem skrótu jest `TeleTYpewriter`. W dzisiejszych czasach oznacza wirtualną tekstową konsolę do których (jest ich 6) w Ubuntu możemy wejść przez użycie jednego ze skrótów:

*   `tty1` - `Ctrl + Alt + F1`,
*   `tty2` - `Ctrl + Alt + F2`,
*   `tty3` - `Ctrl + Alt + F3`,
*   `tty4` - `Ctrl + Alt + F4`,
*   `tty5` - `Ctrl + Alt + F5`,
*   `tty6` - `Ctrl + Alt + F6`,
*   Powrót do GUI - `Ctrl + Alt + F7`,

Parametr `-i` oznacza dodanie strumieniu wejściowego. W połączeniu `-it` mówi Dockerowi, że w ramach polecenia `exec` chcemy dodać silnik terminalu wraz z możliwością przekazania czegoś do wejścia, po czym wynik wykonania operacji otrzymujemy w strumieniu wyjściowym, w warstwie, w której wykonujemy polecenie `docker exec -it <command>`.

# Volumes

W pliku konfiguracyjnym definiujemy `volumes`. Wykorzystywane są one w celu skopiowania naszego kodu źródłowego z lokalnego hosta (do którego mamy podpięte repozytorium) w głąb kontenera. Innymi słowy, przekazujemy aktualny kod źródłowy nad którym pracujemy do kontenera, aby mógł on zostać uruchomiony wewnątrz kontenera. Nie musimy go kopiować ręcznie.

# Podsumowanie

Wykorzystywanie Dockera jest przydatne nie tylko w środowisku produkcyjnym do łatwego skalowania aplikacji, ale też jest wygodnym rozwiązaniem umożliwiającym prace w środowisku developerskim. Po przygotowaniu kilku plików możemy umieścić je w repozytorium, aby ułatwić życie naszym kolegom, których zadanie ograniczy się do pobrania kodu z repozytorium i uruchomienia kontenerów przez `docker-compose`.

* * *

#### Źródła i pojęcia

*   \[1\] [Daj się poznać](https://devstyle.pl/daj-sie-poznac/)
*   \[2\] [tyche, Wikipedia](https://pl.wikipedia.org/wiki/Tyche)
*   \[3\] [Slack](http://slack.com)
*   \[4\] [GitHub](github.com)
*   \[5\] [ZenHub](https://www.zenhub.com/)
*   \[6\] [Python2orPython3, WikiPython](https://wiki.python.org/moin/Python2orPython3)
*   \[7\] [What is Docker?, Docker.com](https://www.docker.com/what-docker)
*   \[8\] [Docker Hub](https://hub.docker.com/)
*   \[9\] [Docker Quickstart: Comopse and Django](https://docs.docker.com/compose/django/)

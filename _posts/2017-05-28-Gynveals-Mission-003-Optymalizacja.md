---
layout: post
title: Gynveal's Mission 003&#58; Optymalizacja
image: /assets/20170528_header.jpg
---

# Wystarczy poczekać

Powodem pominięcia Misji 002 jest fakt, że trudno było mi wpaść na pomysł jej rozwiązania. Uznałem, że na dzień dzisiejszy potrzebuję czegoś bardziej trywialnego, a taka wydała się być Misja 003. Z czasem jednak wrócę do wykonania również zadania drugiego.

Misja 003 zawiera gotowy do wykonania kod, który pokaże nam poszukiwane hasło.

> **Misja 003**  
> **DIFFICULTY: \[2/10\]**
> 
> Tym razem nie trzeba nic robić. Wystarczy uruchomić poniższy skrypt, chwilkę poczekać, a hasło zostanie wypisane. No, taką dłuższą chwilkę…
> 
> ```
> #!/usr/bin/python
> def magic1(a, b):
>   o = 0
>   i = 0
>   while i < a:
>     o += 1
>     i += 1
>   i = 0
> 
>   while i < b:
>     o += 1
>     i += 1
>   return o
> 
> def magic2(a, b):
>   o = 0
>   i = 0
>   while i < b:
>     o = magic1(o, a)
>     i += 1
>   return o
> 
> n1 = int("2867279575674690971609643216365"
>          "4161626212087501848651843132337"
>          "3373323997065608342")
> 
> n2 = int("1240905467219837578349182398365"
>          "3459812983123659128386518235966"
>          "4109783723654812937")
> 
> n = magic2(magic1(n1, n2), 1337)
> print hex(n)[2:-1].decode("hex").splitlines()[0]
> 
> ```

Na pierwszy rzut oka program wygląda bardzo prosto. Poziom zadania określony jako 2/10 popiera tezę mówiącą o tym, że wystarczy uruchomić skrypt. W celu rozwiązania zadania ściągamy kod, zapisujemy w pliku `Gynveal_003.py` i wykonujemy. Po dopiciu kawy tracimy nadzieję na otrzymanie wyniku jego działania i podejmujemy decyzję o przejściu do optymalizacji.

# Analiza

W kodzie aplikacji mamy dwie zmienne `n1` oraz `n2` przechowujące bardzo duże wartości całkowite, które następnie wykorzystywane są jako parametry metody `magic1(n1, n2)`. Ta następnie jest wykorzystywana jako parametr metody `magic2(magic1(n1, n2), 1337)`. Żartobliwie, ostatnim parametrem jest [leet](https://pl.wikipedia.org/wiki/Leet_speak) popularyzowany w społeczności IRCowej już kilkanaście lat temu.

Przeanalizujmy metodę `magic1(a, b)`:

```python
def magic1(a, b):
  o = 0
  i = 0
  while i < a:
    o += 1
    i += 1
  i = 0

  while i < b:
    o += 1
    i += 1
  return o

```

Zauważamy, że zawiera ona dwie pętle w których liczba przebiegów jest uwarunkowana od `a` oraz `b`, czyli parametrów przekazywanych do metody. Pamiętając o naszych dwóch dużych zmiennych spostrzegamy, że daje nam to 4.108185e+80 iteracji. W ramach każdego z kolejnych przebiegów wartości zmiennych `o` oraz `i` są sobie równe. Po zakończeniu pętli `i` wartość zmiennej jest zerowana w ramach przygotowania do wykonania kolejnej. Zmienna `o` natomiast zerowana nie jest, a jest inkrementowana dalej w drugiej pętli, której liczba przebiegów jest zdefiniowana przez wartość parametru `b`.

W efekcie, pierwsza pętla ustawia wartość zmiennej `o` na równą parametrowi `a`, a druga pętla zwiększa wartość zmiennej `o` o wartość parametru `b`. Innymi słowy, metoda `magic1(a, b)` realizuje operację dodawania. Możemy ją przekształcić do postaci:

```
def magic1(a, b)
  return a + b

```

Druga z magicznych metod `magic2(a, b)` na pierwszy rzut oka wygląda dość podobnie:

```python
def magic2(a, b):
  o = 0
  i = 0
  while i < b:
    o = magic1(o, a)
    i += 1
  return o

```

Wewnętrz pętli zawarte jest jednak wywołanie metody `magic1(o, a)`. Podobnie jak w poprzednim przypadku `i` jest inkrementowane, aż do uzyskania wartości równej parametrowi `b`. Zaczynamy z wartością `o` ustawioną na 0. Wewnątrz pętli, do wartości `o` jest przypisywany wynik dodawania otrzymany z metody `magic1(o, a)`, czyli suma aktualnej wartości parametru `o` i naszej dużej zmiennej `a`, dzieje się to tyle razy ile wynosi wartość zmiennej `b`. Oznacza to, że metoda realizuję operację mnożenia. Optymalizujemy przekształcając do postaci:

```python
def magic2(a, b):
  return a * b

```

Finalna wersja naszego zoptymalizowanego programu wygląda następująco:

```python
def magic1(a, b):
  return a + b

def magic2(a, b):
  return a * b

n1 = int("2867279575674690971609643216365"
         "4161626212087501848651843132337"
         "3373323997065608342")

n2 = int("1240905467219837578349182398365"
         "3459812983123659128386518235966"
         "4109783723654812937")

n = magic2(magic1(n1, n2), 1337)
print n
print hex(n)[2:-1].decode("hex").splitlines()[0]

```

Jego wykonanie zwraca wynik:

```python
n = 549264340234998467129494984689502898642039973222263002891494221114915022603203250023

```

Ostatnia linia konwertuje wartość zapisaną w systemie dziesiętnym na system szesnastkowy. Wycina początkowe `0x` z notacji i dekoduje wszystkie kolejne bajty, aż do ostatniego znaku, tym samym zwracając:

```python
Haslo: "WolneOprogramowanie!"

```

# Podsumowanie

Mi osobiście po realizacji tego zadania do głowy dwa wnioski. Pierwszy z nich to cytat:

> Premature optimization is the root of all evil.
> 
> – Donald Knuth

Zakładając, że kod z zadania byłby kodem produkcyjnym można byłoby wyobrazić sobie, że przyjęte rozwiązanie było wydajne, dobre i szybkie do zaimplementowania w początkowym okresie istnienia systemu. Bardzo dobrze, że na tym etapie nie było optymalizowane. Dopiero gdy nasze wielkie liczby niepozwoliły na jego wykonanie mogliśmy upewnić się, że cały system działa poprawnie dla mniejszych danych, mogliśmy zmierzyć wydajność jego działania przy użyciu [profilera](https://en.wikipedia.org/wiki/Profiling_(computer_programming)) i wykazać wąskie gardła, a dopiero w kolejnych kroku zabrać się za optymalizację optymalizację. Problem ten został szczegółowo omówiony w artykule [Premature Optimization](http://wiki.c2.com/?PrematureOptimization).

Drugim z wniosków jest ponownie popularny cytat:

> Done is better than perfect.

Branża IT cechuje się tym, że przy realizacji projektów istniejących wystarczająco długo perfekcjonizm można włożyć między bajki. W pełni czyste podejście do wytwarzania oprogramowania często okaże się być jednym z większym wrogów. Należy pamiętać, że pracą programistów nie jest pisanie wspaniałych klas, zyskiwania milisekund na rzadko wykonywanych operacjach, sprowadzanie wysokopoziomowych operacji do żonglowania wartościami między rejestrami przy użyciu assembly. Naszym zadaniem jest dostarczanie wartościowych dla klienta rozwiązań problemów, które będą dla niego jak najlepsze w danym czasie lub w spojrzeniu perspektywicznym. To jednak nie oznacza perfekcjonizmu. Jako uzupełnienie tego wniosku warto przytoczyć [The Cult of Done Manifesto](http://www.manifestoproject.it/bre-pettis-and-kio-stark/) z którego moimi ulubionymi elementami są:

> 2.Accept that everything is a draft. It helps to get done.
> 
> 5.Banish procrastination. If you wait more than a week to get an idea done, abandon it.
> 
> 10.Failure counts as done. So do mistakes.

#### Źródła i pojęcia

*   \[1\] [Gynvael’s Livestream #39: RPC, czyli zdalne API](https://www.youtube.com/watch?v=xR0hAJPp1vs)
*   \[2\] [Leet speak, Wikipedia](https://pl.wikipedia.org/wiki/Leet_speak)
*   \[3\] [Profiling, Wikipedia](https://en.wikipedia.org/wiki/Profiling_(computer_programming))
*   \[4\] [Premature Optimization, Donald Knuth](http://wiki.c2.com/?PrematureOptimization)
*   \[5\] [The Cult of Done Manifesto](http://www.manifestoproject.it/bre-pettis-and-kio-stark/)

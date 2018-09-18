---
title: Gynveal's Mission 001&#58; Szyfrowanie XORem
---

# Misje Gynvaela Coldwinda

Gynveal pracuje jako Security Engineer w Google oraz jest kapitanem jednej z topowych drużyn CTF Security na świecie. Napisał takie książki jak [Zrozumieć programowanie](https://zrozumiecprogramowanie.pl/#/mainPage) i [Praktyczna Inżynieria Wsteczna](http://gynvael.coldwind.pl/?id=630). Prowadzi [blog](http://gynvael.coldwind.pl/0), [anglojęzyczny kanał YouTube](https://www.youtube.com/user/GynvaelEN) oraz [polskojęzyczny kanał YouTube](https://www.youtube.com/user/GynvaelColdwind). W ramach tego ostatniego, realizuje cotygodniowe live streamy dotyczące programowania oraz bezpieczeństwa oprogramowania. Ostatnimi czasy, chcąc bardziej zaangażować swoich widzów zaczął udostępniać zadania do wykonania nawiązujące do tematyki odcinka. Okazują się one być bardzo ciekawe. Seria Gynveal's Mission omawiać będzie moje realizacje zadań, pochodzących ze streamów Gynveala.

# Jak nie szyfrować - XOR

W ramach odcinku [Gynvael’s Livestream #37: Jak nie szyfrować - XOR](https://www.youtube.com/watch?v=fBEe8DGZL5o) omówiony został problem dotyczący pokładania wiary w bezpieczeństwo ciągów danych zaszyfrowanych przez XOR’owanie każdego bitu z nieznanym kluczem. Live stream prezentuje wykorzystanie [ataku statystycznego](https://pl.wikipedia.org/wiki/Atak_statystyczny) celem odszyfrowanie tekstu. Z całego live streamu najbardziej spodobało mi się wykorzystanie hex editora z funkcjonalnością wizualizacji zapalonych i zgaszynych bitów do ustalenia długości wykorzystanego klucza. Polecam.

W każdym razie, odcinek kończy się następującym zadaniem:

> **Misja 001**  
> **DIFFICULTY: \[4/10\]**
> 
> Nasi przyjaciele z sekcji dziewiątej założyli podsłuch w biurze podejrzanego. Należy dodać, że to podsłuch najnowszej generacji. Posiada on m.in. wbudowaną sieć neuronową, która od razu zapisuje wszystkie rozpoznane słowa w formie tekstu. Co więcej, każde słowo jest oddzielnie szyfrowane XOR’em przy użyciu tego samego 160-bitowego klucza.
> 
> Ii… no… zgubiliśmy klucz. Trochę wstyd prosić sekcję dziewiątą znowu o pomoc, więc zadanie odzyskania danych i klucza powierzamy Tobie. Oto dane, które otrzymaliśmy:
> 
> 1f9111 1799 0790001226d8 0a9e1e5c3ada 1f 099e195e 0a97075a21dac1 0a9710 199e075131d3 1199 12961350
> 
> Wiemy, że podejrzany posługuje się wyłącznie językiem angielskim.
> 
> Rozszyfruj słowa i podaj odzyskany fragment klucza.

# Czytanie ze zrozumieniem

Na początek, wylistujmy istotne elementy z powyższej treści:

*   Zaszyfrowane dane są tekstem.
*   Tekst jest zapisany w języku angielskim, więc wszystkie słowa pochodzą z języka angielskiego.
*   Do zaszyfrowania tekstu XOR’em został użyty 160-bitowy klucz.
*   Wszystkie słowa zostały zaszyfrowane osobno, przy użyciu dokładnie tego samego klucza.

Wiemy o języku angielskim, który występuje w wersji oryginalnej tekstu. Daje nam to możliwość przeprowadzenia ataku statystycznego, który został omówiony w firmie Gynveala. Tutaj jednak mamy dodatkową informację mówiącą o tym, że słowa zostały zaszyfrowane osobno. W związku z tym, że długość klucza (160 bitów) jest dłuższa od najdłuższego z zaszyfrowanych słów (56 bitów) można byłoby założyć, że mamy do czynienia z [one-time pad](https://en.wikipedia.org/wiki/One-time_pad). Jednak zaszyfrowanie każdego ze słów osobno sprawia, że tak nie jest i jednocześnie daje nam możliwość wykorzystania metody [educated guessing](https://en.wiktionary.org/wiki/educated_guess).

# Rozwiązanie

Przygotujmy sobie tablicę zawierającą zaszyfrowany tekst. Dla ułatwienia odczytywania poszczególnych liter zapiszę każdy z bajtów osobno:

```python
data = [
 [0x1f, 0x91, 0x11],
 [0x17, 0x99],
 [0x07, 0x90, 0x00, 0x12, 0x26, 0xd8],
 [0x0a, 0x9e, 0x1e, 0x5c, 0x3a, 0xda],
 [0x1f],
 [0x09, 0x9e, 0x19, 0x5e],
 [0x0a, 0x97, 0x07, 0x5a, 0x21, 0xda, 0xc1],
 [0x0a, 0x97, 0x10],
 [0x19, 0x9e, 0x07, 0x51, 0x31, 0xd3],
 [0x11, 0x99],
 [0x12, 0x96, 0x13, 0x50],
]

```

W powyższym tekście widać, że:

*   1 słowo składa się z jednego bajtu,
*   2 słowa składają się z 2 bajtów,
*   2 słowa składają się z 3 bajtów,
*   2 słowa składają się z 4 bajtów,
*   3 słowa składają się z 6 bajtów,
*   1 słowo składa się z 7 bajtów.

Pamiętając o tym, że jest to tekst anglojęzyczny możemy wywnioskować, że jedyne jednoliterowe słowa występujące w języku angielskim to `a` oraz `I`.

Tablica prawdy XOR’a wygląda następująco:

| p | q | p ^ q |
|---|---|-----|
| 0 | 0 | 0   |
| 0 | 1 | 1   |
| 1 | 0 | 1   |
| 1 | 1 | 0   |

Na jej podstawie można wywnioskować, że:

> a^k ^ b^k

jest równoznaczne z:

> a^b

Taką zależność można zobrazować poniższym kodem:

```python
a = 0b111111
b = 0b101001
k = 0b010101

print bin(a)		# 0b111111
print bin(b)		# 0b101001
print bin(k)		# 0b10101
print '-'
print bin(a^k)		# 0b101010
print bin(b^k)		# 0b111100
print '-'
print bin(a^k ^ b^k)	# 0b10110
print bin(a^b)		# 0b10110

```

Dzięki powyższym faktom, możemy spróbować wyciągnąć wykorzystać słowo `0x1f` przy założeniu, że jest to `a` lub `I`. Tworzymy funkcję:

```python
def Xor(hex_letter, key_index):
  return chr(hex_letter ^ keys[key_index])

```

oraz tablicę, która posłuży nam do przechowywania klucza i umieszczamy w niej pierwszy bajt powstały przez XOR `0x1f` ze słowem `a`:

```python
keys = [
  data[4][0] ^ ord('a')
]

```

Teraz tworzymy pętlę, która wyświetli nam na ekranie wszystkie z zaszyfrowanych słów odszyfrowanych przy użyciu klucza przechowywanego w tablicy `keys`:

```python
for i in data:
  for k in i:
    sys.stdout.write(hex(k) + ' ')

  print ""
  for j in range(0, len(keys)):  
    if len(i) > j:
      sys.stdout.write(Xor(i[j], j))

  print ""

```

Wynik:

```
0x1f 0x91 0x11 
a
0x17 0x99 
i
0x7 0x90 0x0 0x12 0x26 0xd8 
y
0xa 0x9e 0x1e 0x5c 0x3a 0xda 
t
0x1f 
a
0x9 0x9e 0x19 0x5e 
w
0xa 0x97 0x7 0x5a 0x21 0xda 0xc1 
t
0xa 0x97 0x10 
t
0x19 0x9e 0x7 0x51 0x31 0xd3 
g
0x11 0x99 
o
0x12 0x96 0x13 0x50 
l

```

Jeżeli pierwszy znak naszego klucza jest poprawny to możemy założyć, że pierwsze trzyliterowe słowo to `and`. Podstawiamy te znaki do tablicy z kluczem i testujemy:

```python
keys = [
  data[4][0] ^ ord('a'),
  data[0][1] ^ ord('n'),
  data[0][2] ^ ord('d')
]

```

Wynik:

```
0x1f 0x91 0x11 
and
0x17 0x99 
if
0x7 0x90 0x0 0x12 0x26 0xd8 
you
0xa 0x9e 0x1e 0x5c 0x3a 0xda 
tak
0x1f 
a
0x9 0x9e 0x19 0x5e 
wal
0xa 0x97 0x7 0x5a 0x21 0xda 0xc1 
thr
0xa 0x97 0x10 
the
0x19 0x9e 0x7 0x51 0x31 0xd3 
gar
0x11 0x99 
of
0x12 0x96 0x13 0x50 
lif

```

Odszyfrowany fragment wygląda dobrze, ponieważ zawiera w pełni poprawne słówko `the`. Wyszukujemy słowo w którym brakuje nam tylko jednej literki (ostatnie) i domyślamy się, że `lif?` może oznaczać `life`. Podstawiamy do tablicy z kluczem:

```python
keys = [
  data[4][0] ^ ord('a'),
  data[0][1] ^ ord('n'),
  data[0][2] ^ ord('d'),
  data[10][3] ^ ord('e')
]

```

Tym razem, wynik zawiera poprawnie odszyfrowane słówko `walk`:

```
0x1f 0x91 0x11 
and
0x17 0x99 
if
0x7 0x90 0x0 0x12 0x26 0xd8 
you`
0xa 0x9e 0x1e 0x5c 0x3a 0xda 
taki
0x1f 
a
0x9 0x9e 0x19 0x5e 
walk
0xa 0x97 0x7 0x5a 0x21 0xda 0xc1 
thro
0xa 0x97 0x10 
the
0x19 0x9e 0x7 0x51 0x31 0xd3 
gard
0x11 0x99 
of
0x12 0x96 0x13 0x50 
life

```

Skupiamy się na słowach sześcioznakowych i początku `you'`. Można zaryzykować, że chodzi o `you're`:

```python
keys = [
  data[4][0] ^ ord('a'),
  data[0][1] ^ ord('n'),
  data[0][2] ^ ord('d'),
  data[10][3] ^ ord('e'),
  data[2][4] ^ ord('r'),
  data[2][5] ^ ord('e')
]

```

Wynik:

```
0x1f 0x91 0x11 
and
0x17 0x99 
if
0x7 0x90 0x0 0x12 0x26 0xd8 
you`re
0xa 0x9e 0x1e 0x5c 0x3a 0xda 
taking
0x1f 
a
0x9 0x9e 0x19 0x5e 
walk
0xa 0x97 0x7 0x5a 0x21 0xda 0xc1 
throug
0xa 0x97 0x10 
the
0x19 0x9e 0x7 0x51 0x31 0xd3 
garden
0x11 0x99 
of
0x12 0x96 0x13 0x50 
life

```

Do końcu słówka `throug` dodajemy literkę `t`:

```python
keys = [
  data[4][0] ^ ord('a'),
  data[0][1] ^ ord('n'),
  data[0][2] ^ ord('d'),
  data[10][3] ^ ord('e'),
  data[2][4] ^ ord('r'),
  data[2][5] ^ ord('e'),
  data[6][6] ^ ord('t'),
]

```

dzięki czemu otrzymujemy w pełni odszyfrowany tekst:

```
0x1f 0x91 0x11 
and
0x17 0x99 
if
0x7 0x90 0x0 0x12 0x26 0xd8 
you`re
0xa 0x9e 0x1e 0x5c 0x3a 0xda 
taking
0x1f 
a
0x9 0x9e 0x19 0x5e 
walk
0xa 0x97 0x7 0x5a 0x21 0xda 0xc1 
througt
0xa 0x97 0x10 
the
0x19 0x9e 0x7 0x51 0x31 0xd3 
garden
0x11 0x99 
of
0x12 0x96 0x13 0x50 
life

```

Możemy teraz odczytać pierwsze 7 bajtów klucza:

```python
print 'Key: '
for i in keys:
  sys.stdout.write(hex(i) + ' ')

```

# Wynik rozwiązania

```
Encrypted text:
1f9111 1799 0790001226d8 0a9e1e5c3ada 1f 099e195e 0a97075a21dac1 0a9710 199e075131d3 1199 12961350

Key: 
0x7e 0xff 0x75 0x35 0x54 0xbd 0xb5 

Decrypted text: 
and if you`re taking a walk throught the garden of life

```

# Podsumowanie

Głównym wnioskiem, który moglibyśmy pozostawić w tym miejscu jest to, że dane niemożliwe do odczytania przez człowieka w żadnym stopniu nie mówią o stopniu ich bezpieczeństwa. Wytwarzając oprogramowanie należy inwestować w często pomijane bezpieczeństwo. Podobnie jak umowy zawierane między firmami, czas poświęcony na security okazuje się być bezcenny, a jego prawdziwą wartość można docenić dopiero w czasie ‘wojny’.

Powyższy artykuł został napisany podczas jednego z najwięszych ataków Ransomware na swiecie - WannaCry.

#### Źródła i pojęcia

*   \[1\] [Gynveal Coldwind, Zrozumieć programowanie](https://zrozumiecprogramowanie.pl/#/mainPage)
*   \[2\] [Gynveal Coldwind, Praktyczna Inżynieria Wsteczna](http://gynvael.coldwind.pl/?id=630)
*   \[3\] [Gynveal Coldwind, Blog](http://gynvael.coldwind.pl/0)
*   \[4\] [Gynveal Coldwind, YouTube ENG](https://www.youtube.com/user/GynvaelEN)
*   \[5\] [Gynveal Coldwind, YouTube PL](https://www.youtube.com/user/GynvaelColdwind)
*   \[6\] [Gynvael’s Livestream #37: Jak nie szyfrować - XOR](https://www.youtube.com/watch?v=fBEe8DGZL5o)
*   \[7\] [Atak statystyczny](https://pl.wikipedia.org/wiki/Atak_statystyczny)
*   \[8\] [One-time pad](https://en.wikipedia.org/wiki/One-time_pad)
*   \[9\] [Educated guessing](https://en.wiktionary.org/wiki/educated_guess)

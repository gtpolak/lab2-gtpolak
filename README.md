# Język skryptowy lab2
#### Funkcje

Pewne funkcje użyte zostały już we wcześniejszej lekcji była nią np. funkcja `print()`. Były to gotowe funkcje dostarczone wraz z bibliotekami Pythona.
```Python
print("Hello world!")
a = []
a.extend(range(2, 20))
print(a)
print(str(12))
print(list(range(10, 20, 3)))
```

Poniżej przedstawiono przykład prostej funkcji jaką można napisac samemu. Każda nowo tworzona funkcja posiada nagłówek zbudowany ze słowa `def` nazwy funkcji oraz przyjmowanych przez nią argumentów umieszczonych w nawiasach. Potem jest oczywiście ciało funkcji wykonujące określone czynności. Funkcję wywołać można przez podanie jej nazwy oraz odpowiednich parametrów jakie przyjmuje. Prosta przykładowa funkcja oraz jej wywołanie zaprezentowano poniżej.
> Należy pamiętać, że blok kodu w każdej funkcji rozpoczyna się dwukropkiem i jest on wcięty:bangbang:
```Python
def my_func():
    print("spam")
    print("spam")
    print("spam")

my_func()
```
Żeby poprawnie wywołac funkcję należy ją napisać przed jej wywołaniem. Rezultatem poniższego wywołania kodu bedzie błąd `NameError: name 'hello' is not definied`
```Python
hello()

def hello():
    print("hello")
```

#### Komentarze
By ułatwić szytelność kodu stosuje się komentarze. W Pythonie komentarz jednolinowy zapisuje się przez znak # na początku komentowanej linii. Natomiast aby utworzyć komentarz wieloliniowy należy użyć potrónych cudzysłowiów.
```Python
def shout(word):
    """
    komentarz wieloliniowy
    """
    # komentarz jednoliniowy
    print(word + "!")

shout("spam")
```

#### Argumenty funkcji
Argumenty funkcji używane sa jak zmienne w ciele funkcji i nie mogą być użyte poza nią to samo dotyczy amiennych utworzonych wewnątrz funkcji.
```Python
def print_with_exclamation(word):
    print(word + "!")
    
print_with_exclamation("spam")
print_with_exclamation("eggs")
print_with_exclamation("python")
```

```Python
def print_sum_twice(x, y):
    print(x + y)
    print(x + y)

print_sum_twice(2, 5)
```
Poniższa funkcja w swoim ciele uzywa parametru `var` który poza ciałem funkcji nie jest dostępny oznacza to, że te zmienne są lokalne
```Python
def function(var):
    var += 1
    print(var)

function(7)
print(var)
```
#### zwracanie wartości z funkcji
Pewne funkcje takie jak `int` lub `str` zwracają wartość która może być użyta później. Aby funkcja mogła zwracać wartość musi zawierać słowo kluczowe `return`.
```Python
def max(x, y):
    if x >= y:
        return x
    else:
        return y

print(max(4, 6))
z = max(9, 3)
print(z)
```
Gdy na pewnym poziomie zagnierzdzenia kodu znajduje się słowo kluczowe `return` żadna z instrukcji ktora zostanie napisana potem nie zostanie wykonana.
```Python
def add_numbers(x, y):
    sum = x + y
    return sum
    print("Ten napis nie wyświetli się")

print(add_numbers(4, 5))
```
#### Funkcje jako obiekty
Chociaż są one tworzone inaczej niż normalne zmienne, funkcje są jak każda inna wartość. Można je przypisywać i nadpisywać do zmiennych, a następnie wywoływać ich nazwy.
```Python
def multiply(x, y):
    return x * y

a = 4
b = 6
operation = multiply
print(operation(a, b))
```

#### Funkcja jako argument innnej funkcji
Poniżej przedstawiony został przykład jak do jednej z funkcji jako parametr podac inną funkcję
```Python
def add(x, y):
    return x + y

def do_twice(func, x, y):
    return func(func(x, y), func(x, y))

a = 5
b = 10
print(do_twice(add, a, b))
```

#### Moduły
```Python
import random

for i in range(5):
    val = random.randint(1, 6)
    print(val)
```
# rama aby zaimportowac wszystkie objetky z modułu należy wykożystać  * np from math import *
```Python
from math import pi

print(pi)
```

# import dowolny_modul
# generowany jest wyjątek ImportError ponieważ tai moduł nie jest dostępny
```Python
from math import sqrt as square_root

print(square_root(100))
```

# występuje 3 główne rodzajemodułów w pythonie, npaisane przez programistę, instalowane z dodatkowych źródeł oraz instalowane łącznie z pythonem
# wywoływany wcześniej moduł znajduje się w standardowych bibliotekach Pythona który posiada wiele użytecznych modulów.
# niektóre z nich umożliwiaja oreacje na stringach, obiektach dat operacje matematyczne, obsługi plików json, działania na wielu watkach
#  i wiele innych
# wiele z dodatkowych modułów do Pythona znajduje się w PyPI (Python Package Index) aby w prosty sposób móc doinstalowac jakiś moduł
# który jest potrzebny nalezy wykożystać program zwany pip. Aby zainstalowac interesy=ujący moduł wystarczy przejść do
# wiersza poleceń i wpisac komędę pip install nazwa_biblioteki.
# po jej zainstalowaniu mozna już swobodnie wykożystać jej możliwosci we własnym kodzie


# błędy
# Błędy informują użytkownika o tym że coś poszło nie tak. gdy wykrywany jest jkiś błąd program natychmiast się zatrzymuje
# jednym z cześtrzych błędów jest błąd dotyczący dzieelnia przez 0 i jest nim ZeroDevisionError
# innymi często występującymi błędami są
# ImportError
# IndexError
# NameError
# SyntaxError
# TypeError
# ValueError

# aby przechwycić występujący wyjątek wykorzystuje się instrukcje try/except
# blok try może mieć wiele różnych bloków except aby wyłapywac różne rodzaje błędów/

# różne rodzaje błędów mogą być także umieszczone w jednym bloku except aby wyłapywać wszystkie z nich
```Python
try:
    var = 100
    print(var + "witaj")
    print(var / 2)
except ZeroDivisionError:
    print("Dzielenie przez 0")
except (ValueError, TypeError):
    print("jakiś błąd")
```
# możliwy jest też zapis bloku exception bez informacji o jkaimkolwiek konkretnym błędzie
# można w ten sposób przechwycić wszystkie błędy jakie mogą wystąpić i wykonać dla nich tę samą akcję
```Python
try:
    word = "spam"
    print(word / 0)
except:
    print("wykryto błąd")
```

# blok finally
# blok finally umieszcza się z ablokami try i except. Używany jest do wykonania jaiegoś fragmentu kodu bez względu na to
# czy wystąpi bądź nie wystąpi błąd w fragmęcie kodu w bloku try
```Python
try:
    print("hello")
    # print(1/0)
except ZeroDivisionError:
    print("Dzielenie przez 0")
finally:
    print("Ta linia kodu wykona się zawsze o bloku try")
```

#
#
#
# instrukcja reise
# instrukacja reise  służy do poprawianai błędów
# trzeba podać typ zgłąszanego wyjątku
#
# print(1)
# # raise ValueError
# print(2)
#
# name = "123"
# raise NameError("błędna nazwa")
# print(name)

#
#
#
# asercje
# asercje są kontrolą stanu jaki powinno się uzyskać po wykonaniu określonego fragmentu kodu
# testuje ona i jeśli wynik jest fałszywy to jest rzucany wyjątek
print(1)
assert 2 + 2 == 4
print(2)
# assert 1 + 1 == 3
# asercje mogą równiez przyjmowac drugi argument  kóry jest przekazywany jeśli assercja zawiedzie

temp = -10
assert temp >= 0, "niej niż 0"

# ramka
# gdy asercj się nie wykona poprawnie można wyłapać jej błąd używając bloku try
# except jeśli to nie będzie zrobione program sie zatrzyma

# otwieranie plików
# operaje na plikach w pythonie
# przed edycją pliku potrzeba go otworzyć przy pomocy poniższego polecenia
myfile = open("spam.txt")
# rama
# argumentem funkcji open jest ścieżka do pliku. Jeśli plik znajduje sie w katalogu projektu wystarczy wpisac jego nazwę

# pliki można otwierać i przetwarzać w róznych trybach. Tryb ustawia się przez podanie go jako drugi argument funkcji open
# podanie r umozliwiać będzie otwarce pliku w trybie tylko do odczytu co zresztą jest trybem domyślnym
# w zapewnia tryb zapisu zawartości pliku (nadpisuje wcześniejszą zawartość)
# a zapewnia możliwość dopisywania do pliku bez utraty wcześniejszej jego zawartości
# b otwira plik w trybie binarnym używane do plików innych niz tekstowe np obrazy, dźwięk itp !!!!!!!!!!
myfile = open("spam.txt", "w")
myfile = open("spam.txt", "r")
myfile = open("spam.txt", "wb")

# tablice






*This text will be italic*
_This will also be italic_

**This text will be bold**
__This will also be bold__

_You **can** combine them_

![GitHub Logo](https://qph.fs.quoracdn.net/main-qimg-a1b88cb3f8232c96214d7d5b9d479ab8-)

> We're living the future so the present is our past.

    def foo():
        if not bar:
        return True
        
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

:small_blue_diamond:
:bangbang:



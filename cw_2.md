# Zadanie 1 
Wykorzystując dekoratory, napisz cache dla funkcji tetranacci z poprzedniego zadania.
Ten dekorator powinien zapobiegać przed ponownym obliczaniem tych samych wartości.

```Python
def tetranacci_cache(func):
    x = {}
    def wrapper(n):
        if n not in x:
            x[n] = func(n)
        return x[n]
    return wrapper
    

@tetranacci_cache
def tetranacci(n):
    if n == 1 or n == 2 or n == 3:
        return 0
    elif n == 4:
        return 1
    else:
        return tetranacci(n-1) + tetranacci(n-2) + tetranacci(n-3) + tetranacci(n-4)

print(tetranacci(5))
  
```

# Zadanie 2
Zaimplementuj własny generator o nazwie repeat, zwracający obiekt podany przez użytkownika dokładnie N razy.
Jeśli wartość parametru N nie została określona, generator powinien zwracać wartości w nieskończoność.

PRZYKŁAD
repeat(10, 3) → 10 10 10
repeat(10, 5) → 10 10 10 10 10
repeat(5) → 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5…
repeat(5, None) → 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5…

```Python
def repeat(x,n=None):
    if n is None:
        while True:
            yield x
    else:
        for i in range(n):
            yield x
        
for b in repeat(2):
    print(b)
```

# Zadanie 3 
W kodzie z zajęć w klasie Pojazd utwórz atrybut, który niezależnie od utworzonego obiektu będzie miał taką samą wartość.
każdy obiekt ma mieć kolor biały

```Python
class Pojazd:
    kolor = 'biały'
    def __init__(self, predkosc_max, przebieg):
        self.predkosc_max = predkosc_max
        self.przebieg = przebieg

pojazd1 = Pojazd(240, 50)
print(pojazd1.predkosc_max)
print(pojazd1.przebieg)
print(pojazd1.kolor)
```

# Zadanie 4 
Wykorzystaj klasy Autobus i Pojazd.
Zdefiniuj metodę opłata, k†óra będzie miała wartość domyślną liczba_miejsc * 100
Jeżeli Pojazd jest instancją Autobusu, opłata ma zostać powiększona o 10% wartości opłaty początkowej.
Np. jeżeli autobus domyślnie ma 50 miejsc to opłata całkowita wyniesie 5500

```Python
class Pojazd:
    def __init__(self, predkosc_max, przebieg, nazwa_modelu):
        self.predkosc_max = predkosc_max
        self.przebieg = przebieg
        self.nazwa_modelu = nazwa_modelu
    
    def liczba_miejsc(self, miejsca):
        return f"{self.nazwa_modelu} pomieści {miejsca} osób."
    
    def oplata(self, miejsca):
        return f"opłata za {miejsca} miejsca wysienie {miejsca * 100}"
         
       
    
class Autobus(Pojazd):
    def liczba_miejsc(self, miejsca=50):
        return super().liczba_miejsc(miejsca)
    
    def oplata(self,miejsca):
        return f"Gdy Pojazd jest istancją Autobusu {super().oplata(miejsca *1.1)}"

autobus1 = Autobus(300, 20, "Autobus XYZ")
pojazd1 = Pojazd(300, 20, "Pojazd XYZ")
print(autobus1.liczba_miejsc(20))
print(pojazd1.liczba_miejsc(20))
print(pojazd1.oplata(20))
print(autobus1.oplata(20))
```

# Zadanie 5
Napisz klasę FunkcjaKwadratowa, która przechowuje funkcje typu $ax^2$+bx+c.
Klasa powinna zawierać trzy pola: a, b, c, które są przypisywane w konstruktorze.
Główną metodą powinna być rozwiaz(), która zwraca miejsca zerowe podanej funkcji.
Należy zwrócić uwagę na przypadki gdy a=0, b=0 lub c=0,
a także obmyślić sposób informowania o nieskończonej liczbie, jednym lub zerze rozwiązań.

```Python
import math

class FunkcjaKwadratowa:
    def __init__(self, a, b, c):
        self.a = a
        self.b = b 
        self.c = c

    def wypisz(self):
        return self.a,self.b,self.c

    def oblicz_wartosc(self, x):
        wynik = self.a*x**2 +self.b * x + self.c
        return wynik

        
    def rozwiaz(self):
        delta = self.b**2 - 4*self.a * self.c    
            
        if self.a == 0:
            if self.b == 0:
                if self.c == 0:
                    return "Nieskończenie wiele rozwiązań"
                else:
                    return "Brak rozwiązań"
            else:
                x1 = (-self.c)/self.b
                x2 = x1
                return f"Jedno rozwiązanie: x = {x1}"
        else:
            if delta < 0:
                return "Brak rozwiązań"
            elif delta == 0:
                x1 = (-self.b)/(2* self.a)
                x2 = x1
            else:
                x1 = (-self.b - delta**(0.5))/2*self.a
                x2 = (-self.b + delta**(0.5))/2*self.a
        return f"Dwa miejsca zerowe: x1 = {x1}, x2 = {x2}"

        
def main():
    f1 = FunkcjaKwadratowa(2, 3, 1)
    f1.wypisz()
    print(f1.oblicz_wartosc(0))
    print(f1.oblicz_wartosc(1))

    print(FunkcjaKwadratowa(0, 0, 0).rozwiaz())
    print(FunkcjaKwadratowa(0, 0, 1).rozwiaz())
    print(FunkcjaKwadratowa(0, 2, 3).rozwiaz())
    print(FunkcjaKwadratowa(1, 2, 3).rozwiaz())
    print(FunkcjaKwadratowa(1, -5, 6).rozwiaz())
    print(FunkcjaKwadratowa(1, 4, 4).rozwiaz())

if __name__ == "__main__":
    main()
```



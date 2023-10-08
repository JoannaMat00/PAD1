# Ćwiczenie 1
Napisz funkcję o nazwie check_range, która sprawdza, czy liczba znajduje się w podanym zakresie (zawiera zarówno niski i wysoki).
Jeśli tak, zwróć „x jest między y a z”.
Jeśli tak nie jest, zwróć „x NIE jest między y a z”.
Gdzie: x to liczba, y jest dolną granicą, z to górna granica

```Python
def check_range(x,y,z):
  if y <= x <= z:
    print("x jest między y a z")
  else:
    print("x NIE jest między y a z ")

check_range(34, 9, 228)
```
```Python
check_range(7, 2, 5)
```

Napisz funkcję o nazwie bool_range, która robi to samo, ale zwraca tylko wartość logiczną.

```Python
def bool_range(x,y,z):
  return y <= x <= z
```
```Python
bool_range(7, 5, 20)
```
```Python
bool_range(67, 22, 25)
```

# Ćwiczenie 2
Napisz funkcję o nazwie unique_list, która pobiera listę i zwraca listę zawierającą tylko unikalne elementy danych wejściowych.

```Python
my_list = [1,3,5,6,4,3,2,3,3,4,3,4,5,6,6,4,3,2,12,3,5,63,4,5,3,3,2]

def unique_list(x):
  print(list(set(my_list)))
```

```Python
unique_list(my_list)
```
Znajdź inny sposób wykonania tej samej operacji bez definiowania funkcji.

```Python
my_list = [1,3,5,6,4,3,2,3,3,4,3,4,5,6,6,4,3,2,12,3,5,63,4,5,3,3,2]
print(list(set(my_list)))
```
# Ćwiczenie 3
Napisz funkcję o nazwie objętość_kuli, która przyjmuje promień kuli i zwraca jej objętość zaokrągloną do 2 dp. (Google wzór na objętość kuli, użyj pi = 3,14)

```Python
def volume_of_sphere(r):
  pi = 3.14
  return round((4/3) * pi * r**3,2)
```
```Python
volume_of_sphere(2)
```

# Ćwiczenie 4
Zdefiniuj funkcję rekurencyjną o nazwie num_fact, która zwraca silnię podanej liczby.

```Python
def num_fact(number):
  if number == 1:
    return 1

  else:
    return number * num_fact(number - 1)
```
```Python
num_fact(10)
```














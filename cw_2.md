# Zadanie 1 (4 pkt)
Wykorzystując dekoratory, napisz cache dla funkcji tetranacci z poprzedniego zadania.
Ten dekorator powinien zapobiegać przed ponownym obliczaniem tych samych wartości.


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
  

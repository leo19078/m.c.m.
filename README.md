# m.c.m.
Programa para obtener el minimo comun multipro 
import math
from collections import Counter

def mcm(a, b):
    return abs(a * b) // math.gcd(a, b)

def find_mcm_ways(n):
    ways = []
    for i in range(1, n + 1):
        ways.append((i, n))
    return ways

# Diccionario para almacenar el número de veces que aparece cada m.c.m. y sus representaciones
mcm_info = {}

for num in range(1, 101):
    mcm_ways = find_mcm_ways(num)
    for pair in mcm_ways:
        mcm_value = mcm(pair[0], pair[1])
        if mcm_value not in mcm_info:
            mcm_info[mcm_value] = []
        mcm_info[mcm_value].append(pair)

# Encontrar el m.c.m. que aparece 7 veces
target_count = 7
smallest_mcm_with_target_count = None

for mcm_value, pairs in mcm_info.items():
    if len(pairs) == target_count:
        smallest_mcm_with_target_count = mcm_value
        break

if smallest_mcm_with_target_count is not None:
    print(f"El número más chico que se puede representar exactamente {target_count} veces como m.c.m. de dos números es {smallest_mcm_with_target_count}.")
    print("Sus representaciones son:")
    for pair in mcm_info[smallest_mcm_with_target_count]:
        print(f"{pair[0]} x {pair[1]}")
else:
    print(f"No se encontró ningún número que se pueda representar exactamente {target_count} veces como m.c.m. de dos números.")

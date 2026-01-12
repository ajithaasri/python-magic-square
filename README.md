# python-magic-square

import numpy as np

order = int(input("Enter order of magic square (order must be odd): "))

# If even number is given then increment it by one
if order % 2 == 0:
    order += 1
    print("Given order is even so it is incremented by 1.")

mid = order // 2

magic = np.zeros((order, order), dtype=int)

k = mid
j = 0

for i in range(1, order * order + 1):
    magic[j][k] = i
    p = j
    j = j - 1
    q = k
    k = k + 1

    if j < 0:
        j = order - 1

    if k > order - 1:
        k = 0

    if magic[j][k] != 0:
        k = q
        j = p + 1

print("\nGenerated Magic Square is: \n")

for j in range(order):
    print("|", end="")
    for k in range(order):
        print(f" {magic[j][k]:2d} |", end="")
    print()
    print("-" * (order * 5 + 1))


OUTPUT:

Enter order of magic square (order must be odd): 5

Generated Magic Square is: 

| 17 | 24 |  1 |  8 | 15 |
---------------------------
| 23 |  5 |  7 | 14 | 16 |
---------------------------
|  4 |  6 | 13 | 20 | 22 |
---------------------------
| 10 | 12 | 19 | 21 |  3 |
---------------------------
| 11 | 18 | 25 |  2 |  9 |
---------------------------

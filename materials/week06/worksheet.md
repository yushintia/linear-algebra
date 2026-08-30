# Week 6 Worksheet: Check Before You Solve

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café is testing three new drink pairs. For each pair, the
recipe amounts are known, but the ingredient prices are not. Before
solving for the prices, compute each determinant first.

### Combo 1: Cold Brew and Iced Tea

Both drinks use the same two ingredients: cold-brew concentrate and
water.

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Cold Brew | 3 units concentrate + 1 unit water | 1200 원 |
| Iced Tea | 1 unit concentrate + 2 units water | 500 원 |

Matrix:

```
[ 3  1 ]
[ 1  2 ]
```

**Determinant:** ______________________

**Does exactly one price exist?** ______________________

**If yes, solve for the price of concentrate (`c`) and water (`w`).**
Show your work below.

_________________________________________________________________

_________________________________________________________________

**Answer:** `c` = ______ 원, `w` = ______ 원

### Combo 2: Small and Large Smoothie

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Small Smoothie | 2 units fruit + 1 unit yogurt | 1000 원 |
| Large Smoothie | 4 units fruit + 2 units yogurt | 2200 원 |

Matrix:

```
[ 2  1 ]
[ 4  2 ]
```

**Determinant:** ______________________

**Does exactly one price exist?** ______________________

**Do not fully solve this one.** Instead, compare `2200` to `2 x 1000`.
What do you notice?

_________________________________________________________________

### Combo 3: Bubble Tea, Regular and Party Size

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Bubble Tea | 1 unit tapioca + 2 units milk tea | 900 원 |
| Party-Size (5x) | 5 units tapioca + 10 units milk tea | 4500 원 |

Matrix:

```
[ 1   2 ]
[ 5  10 ]
```

**Determinant:** ______________________

**Do not fully solve this one either.** Instead, compare `4500` to
`5 x 900`. What do you notice?

_________________________________________________________________

**Question:** Combo 2 and Combo 3 both have a determinant of zero, but
they are not the same kind of "not unique." What is different between
them?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: A 3x3 determinant by cofactor expansion

The café is testing an Iced Mocha, using espresso, milk, and
chocolate syrup. Its recipe matrix is:

```
[ 1  0   1 ]
[ 2  1  -1 ]
[ 0  3   1 ]
```

Expand along the top row. Find each of the three minors, apply the
sign pattern, and compute the determinant. Show your work.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Determinant:** ______________________

**Does this recipe have exactly one exact answer?** ______________________

### Task 2: Classify by determinant only

For each matrix below, compute only the determinant. Do not solve the
full system. Classify each as **invertible** (exactly one solution)
or **singular** (not exactly one solution).

**System 1**
```
[ 1  2 ]
[ 3  4 ]
```
Determinant: ______ Classification: ___________________

**System 2**
```
[ 2  4 ]
[ 1  2 ]
```
Determinant: ______ Classification: ___________________

**System 3**
```
[ 5  0 ]
[ 0  5 ]
```
Determinant: ______ Classification: ___________________

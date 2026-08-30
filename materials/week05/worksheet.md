# Week 5 Worksheet: Factoring the Café's Recipe

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café sells two drinks, Latte and Mocha, from the same two
ingredients: milk and syrup. The recipe amounts never change. Let
`m` = price of 1 unit of milk (원), `s` = price of 1 unit of syrup
(원).

```
Latte: 2m + s = (Latte total)
Mocha: m + 3s = (Mocha total)
```

### Step 1: Write the recipe grid

Fill in the left-side grid of numbers, `A`, from the two recipes
above.

```
A = [       ]
    [       ]
```

### Step 2: Find the multiplier

To zero out the bottom-left entry of `A`, what number do you scale
row 1 by, before subtracting it from row 2?

Multiplier = ______

Compute the new row 2: ______________________________

### Step 3: Write `L` and `U`

```
L = [       ]        U = [       ]
    [       ]            [       ]
```

**Check:** multiply `L` by `U`. Do you get `A` back?

_________________________________________________________________

### Step 4: Solve Monday's receipts

Monday: Latte totaled 800 원, Mocha totaled 900 원.

Forward substitution, solve `Ly = b`:

```
y1 = ______
_____ (y1) + y2 = 900   →   y2 = ______
```

Back substitution, solve `Ux = y`:

```
_____ (x2) = ______   →   x2 = ______ (s)
_____ (x1) + _____ = ______   →   x1 = ______ (m)
```

**Answer:** `m` = ______ 원, `s` = ______ 원

---

## Part B (about 15 minutes)

### Task 1: Reuse for Tuesday

Tuesday's receipts changed: Latte totaled 700 원, Mocha totaled
1100 원. Reuse the **same** `L` and `U` from Part A. Do not redo
elimination.

```
y1 = ______
_____ (y1) + y2 = 1100   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (s)
_____ (x1) + _____ = ______   →   x1 = ______ (m)
```

**Answer:** `m` = ______ 원, `s` = ______ 원

### Task 2: Reuse for a new day

A new day's receipts arrive: Latte totaled 1100 원, Mocha totaled
1400 원. Reuse `L` and `U` again.

```
y1 = ______
_____ (y1) + y2 = 1400   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (s)
_____ (x1) + _____ = ______   →   x1 = ______ (m)
```

**Answer:** `m` = ______ 원, `s` = ______ 원

**Question:** Why didn't you redo elimination for Task 1 or Task 2?

_________________________________________________________________

### Task 3: Does it need pivoting?

For each grid below, decide if a row swap is needed before
elimination can start.

**Grid P**
```
[ 0  3 ]
[ 2  1 ]
```
Needs pivoting? ___________________ Why? __________________________

**Grid Q**
```
[ 5  2 ]
[ 1  4 ]
```
Needs pivoting? ___________________ Why? __________________________

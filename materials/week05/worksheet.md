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

---

<!-- page break for print -->

## Instructor Answer Key — do not hand out this section

### Part A

**Step 1:**

```
A = [ 2  1 ]
    [ 1  3 ]
```

**Step 2:** Multiplier `= 1/2 = 0.5`. New row 2: `[1, 3] − 0.5×[2, 1] = [0, 2.5]`.

**Step 3:**

```
L = [ 1    0 ]        U = [ 2   1  ]
    [ 0.5  1 ]            [ 0  2.5 ]
```

Check: `L × U` reproduces `A`. Any equivalent correct verification
(e.g. multiplying row by row) is acceptable.

**Step 4 (Monday, b = 800, 900):**

```
y1 = 800
0.5(800) + y2 = 900   →   y2 = 500
2.5(x2) = 500          →   x2 = 200 (s)
2(x1) + 200 = 800       →   x1 = 300 (m)
```

**Answer: `m = 300` 원, `s = 200` 원.** (Matches the Week 1 answer
key — same recipe, same prices.)

### Part B

**Task 1 (Tuesday, b = 700, 1100):**

```
y1 = 700
0.5(700) + y2 = 1100   →   y2 = 750
2.5(x2) = 750            →   x2 = 300 (s)
2(x1) + 300 = 700         →   x1 = 200 (m)
```

**Answer: `m = 200` 원, `s = 300` 원.**

**Task 2 (new day, b = 1100, 1400):**

```
y1 = 1100
0.5(1100) + y2 = 1400   →   y2 = 850
2.5(x2) = 850             →   x2 = 340 (s)
2(x1) + 340 = 1100         →   x1 = 380 (m)
```

**Answer: `m = 380` 원, `s = 340` 원.**

**Discussion question answer:** The left side of the system, the
recipe grid `A`, never changed — only the right-hand side (the
day's receipts) changed. `L` and `U` depend only on `A`, so they
stay valid for any new right-hand side.

**Task 3:**

- **Grid P: needs pivoting.** The top-left entry is `0`. Elimination
  would try to divide by `0`, so rows 1 and 2 must swap first.
- **Grid Q: does not need pivoting.** The top-left entry is `5`, a
  nonzero number, so elimination can proceed directly.

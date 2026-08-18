# Week 1 Worksheet: The Café's Two Drinks

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café sells two drinks. Both are made from the same two
ingredients: **milk** and **syrup**. Nobody wrote down the price of
one unit of milk or one unit of syrup. But the recipe amounts are
known, and yesterday's receipts show the total ingredient cost for
each drink.

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Latte | 2 units milk + 1 unit syrup | 800 원 |
| Mocha | 1 unit milk + 3 units syrup | 900 원 |

Let `m` = price of 1 unit of milk (원), `s` = price of 1 unit of
syrup (원).

### Step 1: Guess and check

Before using this week's method, try guessing. Fill in the table.
For each guess, compute the Latte cost (`2m + s`) and the Mocha cost
(`m + 3s`), and check if both match the receipts.

| Guess: m = | Guess: s = | Latte cost (2m + s) | Mocha cost (m + 3s) | Both correct? |
|---|---|---|---|---|
| 200 | 400 | | | |
| 300 | 100 | | | |
| your guess | your guess | | | |

**Question:** Was guessing fast? Would it stay fast with 5 drinks and
5 ingredients instead of 2?

_________________________________________________________________

### Step 2: Write the system

Turn the table into two linear equations in `m` and `s`.

Latte: ______________________ = 800

Mocha: ______________________ = 900

### Step 3: Solve using this week's method

Use row operations (swap, scale, add) or substitution — your choice —
to eliminate one unknown. Show your work below.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Answer:** `m` = ______ 원, `s` = ______ 원

### Step 4: Check

Put your `m` and `s` back into both original equations. Do they both
come out true?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Verify with the augmented matrix

Write your Part A system as an augmented matrix, then perform **one**
row operation on it (your choice: swap, scale, or add) and write the
result.

Augmented matrix:

```
[            ]
[            ]
```

After one row operation:

```
[            ]
[            ]
```

### Task 2: Classify each system

For each system below, decide: **unique solution**, **infinitely many
solutions**, or **no solution**. You do not need to fully solve them —
look for what happens when you try to eliminate.

**System 1**
```
x + y = 5
x - y = 1
```
Classification: ___________________

**System 2**
```
2x + 2y = 8
x + y = 4
```
Classification: ___________________

**System 3**
```
x + y = 3
x + y = 7
```
Classification: ___________________

**Question:** What is different about the *left side* of System 2's
two equations compared to System 3's two equations?

_________________________________________________________________

---

<!-- page break for print -->

## Instructor Answer Key — do not hand out this section

### Part A

**Step 1 (guess and check):**

| m | s | 2m + s | m + 3s | Match? |
|---|---|---|---|---|
| 200 | 400 | 800 | 1400 | No (Mocha too high) |
| 300 | 100 | 700 | 600 | No (both too low) |

The point of Step 1 is that guessing rarely lands on the exact
answer, and each guess only rules out one possibility.

**Step 2:**

- Latte: `2m + s = 800`
- Mocha: `m + 3s = 900`

**Step 3 (solution):**

From the Latte equation: `s = 800 - 2m`. Substitute into the Mocha
equation: `m + 3(800 - 2m) = 900` → `m + 2400 - 6m = 900` →
`-5m = -1500` → `m = 300`. Then `s = 800 - 2(300) = 200`.

**Answer: `m = 300` 원, `s = 200` 원.**

**Step 4 (check):** `2(300) + 200 = 800` ✓. `300 + 3(200) = 900` ✓.

### Part B

**Task 1:** Augmented matrix for `2m + s = 800`, `m + 3s = 900`:

```
[ 2  1 | 800 ]
[ 1  3 | 900 ]
```

Any single legal row operation is an acceptable answer, for example
swapping the two rows, or scaling row 2 by 2 to get
`[ 2  6 | 1800 ]`. Accept any correct application of swap/scale/add.

**Task 2 classification:**

- **System 1: unique solution.** (`x = 3`, `y = 2`; the two equations describe two different lines that cross once.)
- **System 2: infinitely many solutions.** Row 1 is exactly row 2 scaled by 2 — the same line written twice.
- **System 3: no solution.** The left sides are identical (`x + y`) but the right sides differ (3 vs 7) — a contradiction.

**Discussion question answer:** System 2's two equations are scaled
copies of each other (multiply the second by 2 to get the first).
System 3's two equations have the same left side but different right
sides, so they contradict rather than agree.

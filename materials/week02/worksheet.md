# Week 2 Worksheet: The Café, Written as Ax = b

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

Recall Week 1's two drinks. Both are made from **milk** and **syrup**.
You already found the price of each unit by hand:

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Latte | 2 units milk + 1 unit syrup | 800 원 |
| Mocha | 1 unit milk + 3 units syrup | 900 원 |

Let `m` = price of 1 unit of milk (원), `s` = price of 1 unit of
syrup (원). Week 1 found `m = 300`, `s = 200`.

### Step 1: Write the system as Ax = b

Fill in the coefficient matrix `A`, the unknown vector `x`, and the
known vector `b`:

```
A = [        ]      x = [   ]      b = [    ]
    [        ]          [   ]          [    ]
```

### Step 2: Verify by matrix-vector multiplication

Using `m = 300` and `s = 200`, compute `Ax` row by row (multiply
each row's entries by `x`'s entries, in order, then add):

Row 1 (Latte): ______________________ = ______

Row 2 (Mocha): ______________________ = ______

### Step 3: Compare

Does `Ax` equal `b`? _____________________________________________

### Step 4: Reflect

Week 1 found `m` and `s` by row reduction. This week, you checked the
same answer by multiplying instead. Which felt faster to write down?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Are the sizes compatible?

For each pair below, decide whether `Ax` is defined. If it is, give
the size of the answer (how many entries).

| `A`'s size | `x`'s entries | Defined? | Answer's size (if defined) |
|---|---|---|---|
| 3 × 2 | 2 | | |
| 2 × 4 | 3 | | |
| 1 × 5 | 5 | | |
| 4 × 4 | 4 | | |

### Task 2: A third drink joins the menu

The café adds a third drink, **Iced Milk Tea**: 3 units milk + 1 unit
syrup, priced at 1,100 원, using the same per-unit ingredient costs
as the Latte and Mocha.

Write the **combined** system (all three drinks) as `Ax = b`. `x`
still has only 2 entries (`m` and `s`); there are now 3 rules.

```
A = [        ]      x = [   ]      b = [    ]
    [        ]          [   ]          [    ]
    [        ]                         [    ]
```

**Question:** What are the dimensions of this new `A`? Is it still a
square matrix?

_________________________________________________________________

**Question:** Using `m = 300`, `s = 200`, does the Iced Milk Tea row
also check out? (You do not need to decide whether every possible
system like this has a solution. That question is next week's job.)

_________________________________________________________________

---

<!-- page break for print -->

## Instructor Answer Key — do not hand out this section

### Part A

**Step 1:**

```
A = [ 2   1 ]      x = [ m ]      b = [ 800 ]
    [ 1   3 ]          [ s ]          [ 900 ]
```

**Step 2:**

- Row 1 (Latte): `2(300) + 1(200) = 800`
- Row 2 (Mocha): `1(300) + 3(200) = 900`

**Step 3:** Yes, `Ax = [800, 900]`, which equals `b` exactly.

**Step 4:** Open discussion. Expected direction: multiplying is
faster to check once you already have candidate numbers; row
reduction is still needed to find the numbers in the first place.

### Part B

**Task 1:**

| `A`'s size | `x`'s entries | Defined? | Answer's size |
|---|---|---|---|
| 3 × 2 | 2 | Yes | 3 |
| 2 × 4 | 3 | No | — |
| 1 × 5 | 5 | Yes | 1 |
| 4 × 4 | 4 | Yes | 4 |

**Task 2:**

```
A = [ 2   1 ]      x = [ m ]      b = [  800 ]
    [ 1   3 ]          [ s ]          [  900 ]
    [ 3   1 ]                         [ 1100 ]
```

**Dimensions:** `A` is now 3 × 2, three rows and two columns. It is
**not** a square matrix (rows ≠ columns), unlike the café's original
3 × 3 recipe matrix from the slides.

**Iced Milk Tea check:** `3(300) + 1(200) = 900 + 200 = 1100`. Yes,
it checks out — this particular extra rule happens to agree with the
same `m` and `s`. Accept answers that correctly compute this and
note the coincidence; do not expect students to generalize about
when a non-square system has a solution, that is Week 3's question.

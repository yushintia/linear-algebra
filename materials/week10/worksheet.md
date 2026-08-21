# Week 10 Worksheet: The Café's Second Blend Machine

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café buys a second blending machine. It blends mango syrup
(`m`) and lime syrup (`l`), then feeds the result back through itself.
The blending rule is:

```
new m = 4m + 2l
new l =  m + 3l
```

### Step 1: Guess and check

Before using this week's method, try guessing a starting mix. Run it
through the rule once, and check if the result points the same
direction as your guess (a scalar multiple of it).

| Guess: m = | Guess: l = | New m (4m + 2l) | New l (m + 3l) | Same direction? |
|---|---|---|---|---|
| 1 | 1 | | | |
| 2 | 1 | | | |
| your guess | your guess | | | |

**Question:** Was guessing fast? Would it stay fast if the machine
blended 5 syrups instead of 2?

_________________________________________________________________

### Step 2: Write the matrix

Write the blending rule as one matrix `B`.

```
B = [       ]
    [       ]
```

### Step 3: Build and solve the characteristic equation

Write `det(B - λI) = 0`, expand it, and solve for `λ`. Show your
work below.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Answer:** `λ` = ______ and `λ` = ______

---

## Part B (about 15 minutes)

### Task 1: Find and check one eigenvector

Using the **larger** `λ` from Part A, solve `(B - λI)v = 0` to find
its eigenvector. Then check your answer with `Bv = λv`.

Eigenvector for the larger `λ`:

```
(       ,       )
```

Check (show the multiplication):

_________________________________________________________________

### Task 2: Is `λ = 1` an eigenvalue? Check three matrices

You do not need to fully solve for eigenvectors here. For each
matrix, compute `det(A - 1·I)`. If it equals 0, `λ = 1` is an
eigenvalue; if not, it is not.

**Matrix 1**
```
[ 1  0 ]
[ 0  5 ]
```
`det(A - I)` = ______  Is `λ = 1` an eigenvalue? ___________________

**Matrix 2**
```
[ 2  0 ]
[ 0  3 ]
```
`det(A - I)` = ______  Is `λ = 1` an eigenvalue? ___________________

**Matrix 3**
```
[ 1  1 ]
[ 0  1 ]
```
`det(A - I)` = ______  Is `λ = 1` an eigenvalue? ___________________

**Question:** What do Matrix 1 and Matrix 3 have in common that
Matrix 2 does not?

_________________________________________________________________

---

<!-- page break for print -->

## Instructor Answer Key — do not hand out this section

### Part A

**Step 1 (guess and check):**

| m | l | 4m + 2l | m + 3l | Same direction? |
|---|---|---|---|---|
| 1 | 1 | 6 | 4 | No (6:4 ≠ 1:1) |
| 2 | 1 | 10 | 5 | Yes! (10:5 = 2:1) |

The point of Step 1 is that most guesses rotate off their starting
direction; only special ones do not. `(2, 1)` happens to land on one
of the real eigenvectors, which Step 3 will confirm.

**Step 2:**

```
B = [ 4  2 ]
    [ 1  3 ]
```

**Step 3 (characteristic equation):**

```
det(B - λI) = (4-λ)(3-λ) - (2)(1) = 0
λ² - 7λ + 12 - 2 = 0
λ² - 7λ + 10 = 0
(λ - 5)(λ - 2) = 0
```

**Answer: `λ = 5` and `λ = 2`.**

### Part B

**Task 1 (eigenvector for `λ = 5`):**

```
(B - 5I)v = 0
[ -1   2 ] [m]   [0]
[  1  -2 ] [l] = [0]
```

Both rows say `m = 2l`. Pick `l = 1`, so `m = 2`. Eigenvector:
`(2, 1)` — the same direction Step 1's lucky second guess found.

**Check:** `B(2,1) = (4·2+2·1, 1·2+3·1) = (10, 5) = 5(2, 1)`. ✓

**Task 2 (is `λ = 1` an eigenvalue?):**

- **Matrix 1:** `det([[0,0],[0,4]]) = (0)(4) - (0)(0) = 0`. **Yes**, `λ = 1` is an eigenvalue.
- **Matrix 2:** `det([[1,0],[0,2]]) = (1)(2) - (0)(0) = 2`. **No**, `λ = 1` is not an eigenvalue.
- **Matrix 3:** `det([[0,1],[0,0]]) = (0)(0) - (1)(0) = 0`. **Yes**, `λ = 1` is an eigenvalue.

**Discussion question answer:** Matrix 1 and Matrix 3 both have a `1`
somewhere on the diagonal (or, more precisely, subtracting `1` from
the diagonal makes the matrix singular, determinant zero). Matrix 2's
diagonal entries are `2` and `3`, so subtracting `1` never makes it
singular; `λ = 1` is not one of its eigenvalues.

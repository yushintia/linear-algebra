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

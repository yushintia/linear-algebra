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

## Part C: More Practice (about 25 minutes)

These problems use this week's characteristic equation and eigenvector
method in different real-world settings.

### Task 1: Vibration Analysis — Natural Frequencies

A two-mass spring system's coupled stiffness matrix is:

```
K = [ 5  -2 ]
    [-2   2 ]
```

Each eigenvalue of `K` corresponds to one vibration mode. Build and
solve `det(K - λI) = 0`. Show your work.

_________________________________________________________________

_________________________________________________________________

`λ` = ______ and `λ` = ______

Find the eigenvector for the **larger** `λ`, and check it with
`Kv = λv`.

Eigenvector: `( ______ , ______ )`

Check: _________________________________________________________________

### Task 2: Population Growth — Which Group Dominates?

A population-growth model for two linked species uses matrix:

```
G = [ 3  1 ]
    [ 0  2 ]
```

Build and solve `det(G - λI) = 0` for `λ`.

`λ` = ______ and `λ` = ______

Find the eigenvector for the larger (dominant) `λ`.

Eigenvector: `( ______ , ______ )`

**Question:** Based on this eigenvector, which species' population
comes to dominate the total, the longer this growth rule runs?

_________________________________________________________________

### Task 3: A Tiny Link Network — Steady Importance

Two web pages link only to each other. The "importance transfer"
matrix is:

```
N = [ 0  1 ]
    [ 1  0 ]
```

Build and solve `det(N - λI) = 0`.

`λ` = ______ and `λ` = ______

Find the eigenvector for `λ = 1`, and check it with `Nv = λv`.

Eigenvector: `( ______ , ______ )`

**Question:** If both pages start with equal importance, what happens
to that equal split as this "follow the link" rule repeats? (Use
`Nv = λv` for `λ = 1`.)

_________________________________________________________________

### Task 4: Mechanical Stability — Does It Settle Down?

A control system's error-dynamics matrix is:

```
S = [ -1   2 ]
    [  0  -3 ]
```

Build and solve `det(S - λI) = 0`.

`λ` = ______ and `λ` = ______

**Question:** A system is stable (small errors shrink toward zero
over time) if every eigenvalue is negative. Is this system stable?
___________________

### Task 5: A Weather Model — Long-Run Ratio

A simple sunny/rainy weather model uses a day-to-day transition
matrix:

```
W = [ 0.8  0.5 ]
    [ 0.2  0.5 ]
```

Build and solve `det(W - λI) = 0`.

`λ` = ______ and `λ` = ______

Find the eigenvector for `λ = 1`, and check it with `Wv = λv`.

Eigenvector: `( ______ , ______ )`

**Question:** This eigenvector gives the long-run ratio of sunny to
rainy days. What is that ratio, written in lowest terms?

_________________________________________________________________

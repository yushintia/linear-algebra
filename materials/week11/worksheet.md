# Week 11 Worksheet: Diagonalizing the Café's Growth Matrix

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café's loyalty numbers grow week after week under the
matrix:

```
A = [ 2  1 ]
    [ 1  2 ]
```

You already know (from Week 10's method) that `A` has eigenvalues
`λ₁ = 3` and `λ₂ = 1`, with eigenvectors `(1, 1)` and `(1, -1)`.

### Step 1: Build P and D

Place the eigenvectors as columns of `P`, in the same order as their
matching eigenvalues on the diagonal of `D`.

```
P = [        ]     D = [        ]
    [        ]         [        ]
```

### Step 2: Find P⁻¹

Compute the inverse of the `P` you just built. Show your work.

_________________________________________________________________

_________________________________________________________________

`P⁻¹ = `

```
[        ]
[        ]
```

### Step 3: Check that A = PDP⁻¹

Multiply `P`, `D`, and `P⁻¹` back together (or check `AP = PD`
column by column) and confirm you land back on the original `A`.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Question:** Which column of `P` did the eigenvalue `3` end up
matched with? What would go wrong if you swapped the column order of
`P` but not `D`?

_________________________________________________________________

### Step 4 (if you finish early)

Compute `A²` two different ways: (1) by multiplying `A` by itself
directly, and (2) using `PD²P⁻¹`. Confirm both give the same answer.

_________________________________________________________________

_________________________________________________________________

---

## Part B (about 15 minutes)

The café adds a second word-of-mouth channel. Its new growth matrix
is:

```
B = [ 4  1 ]
    [ 2  3 ]
```

### Task 1: Find the eigenvalues

Solve `det(B - λI) = 0` for `λ`. Show your work.

_________________________________________________________________

_________________________________________________________________

`λ₁ = ______`, `λ₂ = ______`

### Task 2: Find one eigenvector for each eigenvalue

Solve `(B - λI)v = 0` for each eigenvalue you found.

_________________________________________________________________

_________________________________________________________________

Eigenvector for `λ₁`: `(______, ______)`

Eigenvector for `λ₂`: `(______, ______)`

### Task 3: Build P, D, and P⁻¹

```
P = [        ]     D = [        ]     P⁻¹ = [        ]
    [        ]         [        ]           [        ]
```

### Task 4: Predict 4 weeks ahead, the fast way

Suppose the café starts this new channel at `x₀ = (10, 10)`. Using
`xₙ = P Dⁿ P⁻¹ x₀`, predict `x₄`.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

`x₄ = (______, ______)`

**Question:** Which eigenvalue of `B` is dominant? After many weeks,
which direction will the café's numbers mostly follow?

_________________________________________________________________

---

## Part C: More Practice (about 25 minutes)

These problems use this week's `A = PDP⁻¹` shortcut in different
real-world settings. Each matrix's eigenvalues and eigenvectors are
given, so you can go straight to building `P`, `D`, and `P⁻¹`.

### Task 1: Projecting Years Ahead

A wildlife biologist tracks young (`Y`) and adult (`A`) rabbits using
a year-to-year growth matrix:

```
G = [ 3  1 ]
    [ 1  3 ]
```

`G` has eigenvalues `λ₁ = 4` and `λ₂ = 2`, with eigenvectors `(1, 1)`
and `(1, -1)`.

Build `P`, `D`, and find `P⁻¹`:

```
P = [        ]     D = [        ]     P⁻¹ = [        ]
    [        ]         [        ]           [        ]
```

Starting counts are `x₀ = (30, 10)` (young, adult). Using
`xₙ = P Dⁿ P⁻¹ x₀`, predict `x₃` (three years ahead).

_________________________________________________________________

_________________________________________________________________

`x₃ = (______, ______)`

**Question:** Which eigenvalue is dominant here? After many more
years, what young:adult ratio will the population approach?

_________________________________________________________________

### Task 2: Repeating a Frame Transform

An animation repeats the same transform on a shape's corner point
every frame:

```
T = [ 4  0 ]
    [ 1  2 ]
```

`T` has eigenvalues `λ₁ = 4` and `λ₂ = 2`, with eigenvectors `(2, 1)`
and `(0, 1)`.

Build `P`, `D`, and find `P⁻¹`:

```
P = [        ]     D = [        ]     P⁻¹ = [        ]
    [        ]         [        ]           [        ]
```

A corner point starts at `x₀ = (2, 3)`. Using `xₙ = P Dⁿ P⁻¹ x₀`,
predict where the point is after 3 frames, `x₃`.

_________________________________________________________________

_________________________________________________________________

`x₃ = (______, ______)`

### Task 3: Two Linked Funds

Two investment funds grow together, year to year, under matrix:

```
C = [ 5  2 ]
    [ 2  5 ]
```

`C` has eigenvalues `λ₁ = 7` and `λ₂ = 3`, with eigenvectors `(1, 1)`
and `(1, -1)`.

Build `P`, `D`, and find `P⁻¹`:

```
P = [        ]     D = [        ]     P⁻¹ = [        ]
    [        ]         [        ]           [        ]
```

Starting balances are `x₀ = (600, 200)`. Using `xₙ = P Dⁿ P⁻¹ x₀`,
predict the balances after 2 years, `x₂`.

_________________________________________________________________

_________________________________________________________________

`x₂ = (______, ______)`

### Task 4: A Simplified Two-Group Spread Model

A simplified (linear, not the full nonlinear disease model) two-group
spread model tracks susceptible (`S`) and infected (`I`) counts, week
to week, under matrix:

```
E = [ 0.9  0.1 ]
    [ 0.1  0.9 ]
```

`E` has eigenvalues `λ₁ = 1` and `λ₂ = 0.8`, with eigenvectors
`(1, 1)` and `(1, -1)`.

Build `P`, `D`, and find `P⁻¹`:

```
P = [        ]     D = [        ]     P⁻¹ = [        ]
    [        ]         [        ]           [        ]
```

Starting counts are `x₀ = (900, 100)`. Using `xₙ = P Dⁿ P⁻¹ x₀`,
predict `x₂` (two weeks ahead).

_________________________________________________________________

_________________________________________________________________

`x₂ = (______, ______)`

**Question:** Add the two numbers in your `x₂` together. What do you
notice, and which eigenvalue explains it?

_________________________________________________________________

### Task 5: Two Months Ahead

A subscription service tracks users switching between Free (`F`) and
Premium (`P`) tiers, month to month, under a transition matrix:

```
M = [ 0.6  0.2 ]
    [ 0.4  0.8 ]
```

`M` has eigenvalues `λ₁ = 1` and `λ₂ = 0.4`, with eigenvectors
`(1, 2)` and `(1, -1)`.

Build `P`, `D`, and find `P⁻¹`:

```
P = [        ]     D = [        ]     P⁻¹ = [        ]
    [        ]         [        ]           [        ]
```

Starting counts are `x₀ = (900, 300)` (Free, Premium). Using
`xₙ = P Dⁿ P⁻¹ x₀`, predict `x₂` (two months ahead).

_________________________________________________________________

_________________________________________________________________

`x₂ = (______, ______)`

**Question:** Which tier does the `λ = 1` eigenvector, `(1, 2)`, say
will eventually hold more users?

_________________________________________________________________

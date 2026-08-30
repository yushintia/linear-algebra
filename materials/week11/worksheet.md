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

# Week 9 Worksheet: The Café's Flavor Mixes

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

Recall the café's three tested flavor mixes, written as
ingredient-change vectors `(e, m, s)`:

```
v1 = (-2, 1, 0)
v2 = (1, 0, 1)
v3 = (-1, 1, 1)
```

### Step 1: Test a smaller set first

Before testing all three, test just `{v1, v2}`.

Set up `c1*v1 + c2*v2 = (0, 0, 0)` and write it as three separate
equations, one per coordinate:

`e`-coordinate: ______________________ = 0

`m`-coordinate: ______________________ = 0

`s`-coordinate: ______________________ = 0

Solve this small system for `c1` and `c2`. Is `{v1, v2}` independent?

`c1 = ______`  `c2 = ______`  Independent? ___________

### Step 2: Test the full set of three

You already know, from the handout, that
`v1 + v2 - v3 = (0, 0, 0)`. Using this fact, state the values of
`c1, c2, c3` (not all zero) that make `c1*v1 + c2*v2 + c3*v3 = 0`.

`c1 = ______`  `c2 = ______`  `c3 = ______`

Is `{v1, v2, v3}` independent or dependent? ___________________

### Step 3: Find a basis

Using Steps 1 and 2, circle the vectors that belong in a basis for
`span{v1, v2, v3}`:

`v1`      `v2`      `v3`

State the dimension of `span{v1, v2, v3}`: ______

**Question:** Could `{v1, v3}` also work as a basis for this same
space? Why or why not?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Dimension of a new subspace

The café is testing a second taste rule for a new drink:

```
e - 2m + 3s = 0
```

Solve for `e` in terms of `m` and `s`:

`e = ___________________________`

Write the general solution as a linear combination of two vectors:

`(e, m, s) = m( _____ , _____ , _____ ) + s( _____ , _____ , _____ )`

State a basis for this solution space, and its dimension:

Basis: ________________________  Dimension: ______

### Task 2: Rank and nullity

The new taste rule is a 1×3 matrix, `A = [1  -2  3]`.

`rank(A)` = ______   (how many independent rows does `A` have?)

Using your answer to Task 1, `nullity(A)` = ______

Check the rank-nullity theorem: `rank(A) + nullity(A) = n`, where `n`
is the number of unknowns. Does it hold?

_________________________________________________________________

### Task 3: A quick independence check

For each set, decide **independent** or **dependent**. If dependent,
write the redundant vector as a combination of the others.

**Set 1:** `{(1, 0), (0, 1)}`

Independent or dependent? ___________ Why: ___________________

**Set 2:** `{(2, 1), (4, 2)}`

Independent or dependent? ___________ Why: ___________________

**Set 3:** `{(1, 1, 0), (0, 1, 1), (1, 2, 1)}`

Independent or dependent? ___________ Why: ___________________

---

<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1:**

- `e`: `-2c1 + c2 = 0`
- `m`: `c1 = 0`
- `s`: `c2 = 0`

From the `m` and `s` equations directly, `c1 = 0` and `c2 = 0`. Only
the trivial combination works, so `{v1, v2}` is **independent**.

**Step 2:** From `v1 + v2 - v3 = 0`: `c1 = 1`, `c2 = 1`, `c3 = -1`.
Since not all are zero, `{v1, v2, v3}` is **dependent**.

**Step 3:** A basis is `{v1, v2}` (circle these two; `v3` is
redundant). Dimension = **2**. Yes, `{v1, v3}` also works as a basis:
it is independent (neither is a multiple of the other) and it spans
the same plane, since `v2 = v3 - v1` is reachable from it. Any two of
the three independent-of-each-other vectors form a valid basis; the
dimension, 2, never changes.

### Part B

**Task 1:** Solve for `e`: `e = 2m - 3s`.

`(e, m, s) = (2m - 3s, m, s) = m(2, 1, 0) + s(-3, 0, 1)`

Basis: `{(2, 1, 0), (-3, 0, 1)}`. Dimension: **2**.

**Task 2:** `rank(A) = 1` (one nonzero row, so its column space is a
single line). `nullity(A) = 2` (matches Task 1). Check:
`rank + nullity = 1 + 2 = 3 = n` (3 unknowns: `e`, `m`, `s`). ✓

**Task 3:**

- **Set 1: independent.** Neither vector is a scalar multiple of the other; only the trivial combination reaches `(0,0)`.
- **Set 2: dependent.** `(4, 2) = 2 · (2, 1)`, so `(4,2)` is redundant.
- **Set 3: dependent.** `(1, 1, 0) + (0, 1, 1) = (1, 2, 1)`, so the third vector is a combination of the first two.

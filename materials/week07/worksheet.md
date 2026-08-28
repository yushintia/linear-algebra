# Week 7 Worksheet: The Café's Blend Rules

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The café tracks each candidate blend as a pair `(m, s)`: units of milk
and units of syrup used per cup. For this exercise, allow `m` and `s`
to be any real number, even negative — we are only testing the
**rules**, not whether a blend is practical to actually pour.

### Step 0: Guess first

Before checking any rule, look at Set B below. Does it look like a
vector space to you? Test your guess by trying two specific points:
does `(1, 0)` belong to Set B? Does `-1 · (1, 0)` also belong to it?

_________________________________________________________________

### Step 1: Check each set

For each set, decide **yes** or **no**: is it a vector space? If your
answer is no, say which rule fails: no zero element, or not closed
under addition, or not closed under scalar multiplication.

**Set A:** all pairs `(m, s)` with `m + s = 0`

Vector space? ___________ Why: _________________________________

**Set B:** all pairs `(m, s)` with `m ≥ 0`

Vector space? ___________ Why: _________________________________

**Set C:** all pairs `(m, s)` with `m + s = 10`

Vector space? ___________ Why: _________________________________

### Step 2: Find two spans

Find the span of each set of vectors. Describe it in words (a point,
a line, or the whole plane).

`span{(1, 1), (2, 2)}` = ______________________________________

`span{(1, 0), (0, 2)}` = ______________________________________

**Question:** Why does adding `(2, 2)` to the first span not make it
any bigger?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Describe a whole solution space

The café's diet drink has one rule left, linking espresso `e`, milk
`m`, and syrup `s`:

```
3e - m - s = 0
```

Solve for `m` in terms of `e` and `s`:

`m = ___________________________`

Write the general solution as a linear combination of two vectors:

`(e, m, s) = e( _____ , _____ , _____ ) + s( _____ , _____ , _____ )`

**Check:** pick `e = 1`, `s = 1`. Compute `(e, m, s)` from your
formula, then substitute all three values back into the original
rule. Does it hold?

_________________________________________________________________

### Task 2: Classify each set

For each set of points `(x, y, z)`, decide: **subspace** or **not a
subspace**. If not, say why.

**Set 1**
```
x + y + z = 0
```
Classification: ___________________ Why: ___________________

**Set 2**
```
x + y + z = 1
```
Classification: ___________________ Why: ___________________

**Set 3**
```
x = 0
```
Classification: ___________________ Why: ___________________

**Question:** What is different between Set 1 and Set 2, even though
their left sides look almost the same?

_________________________________________________________________

---

<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 0:** `(1, 0)` belongs to Set B (`m = 1 ≥ 0`). But
`-1 · (1, 0) = (-1, 0)` does not (`m = -1 < 0`). This shows Set B is
not closed under scalar multiplication before students check it
formally.

**Step 1:**

- **Set A: yes, a vector space.** It is a line through the origin (`(0,0)` satisfies `m+s=0`); adding or scaling any point on it stays on it.
- **Set B: no.** Not closed under scalar multiplication — scaling `(1, 0)` by `-1` leaves the set, as shown in Step 0.
- **Set C: no.** No zero element — `(0, 0)` does not satisfy `m + s = 10`.

**Step 2:**

- `span{(1, 1), (2, 2)} = {(a, a) : a any real number}` — still just one line.
- `span{(1, 0), (0, 2)} = {(a, b) : a, b any real numbers}` — the whole plane.

**Discussion question answer:** `(2, 2)` points in the exact same
direction as `(1, 1)` (it is `2 · (1, 1)`), so it adds no new
direction to the span. The span only grows when a new vector points
somewhere the existing set cannot already reach.

### Part B

**Task 1:**

Solve for `m`: `m = 3e - s`.

`(e, m, s) = (e, 3e - s, s) = e(1, 3, 0) + s(0, -1, 1)`

**Check:** `e = 1`, `s = 1` gives `(e, m, s) = (1, 3, 0) + (0, -1, 1)
= (1, 2, 1)`. Substitute: `3(1) - 2 - 1 = 0`. ✓

**Task 2 classification:**

- **Set 1: subspace.** Contains `(0,0,0)`; closed under addition and scaling (a homogeneous linear equation). It is a plane through the origin.
- **Set 2: not a subspace.** Does not contain `(0,0,0)`, since `0+0+0 ≠ 1`. A plane that misses the origin.
- **Set 3: subspace.** Contains `(0,0,0)`; it is the entire y-z plane, closed under addition and scaling.

**Discussion question answer:** Set 1's equation equals zero
(homogeneous), so it passes through the origin and is a subspace.
Set 2's equation equals a nonzero number, so it is a parallel plane
that misses the origin and fails the zero-element test.

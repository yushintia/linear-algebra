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

## Part C: More Practice (about 25 minutes)

Each task below is a different real-world system. None of them are
the café.

### Task 1: Signal Processing — Basis Waveforms

An audio engineer represents a two-sample snippet of sound as a
vector `(a1, a2)`, the amplitude at two time points. Any snippet is
built by combining two basic waveform vectors: `w1 = (1, 1)` (a
"sum" wave) and `w2 = (1, -1)` (a "difference" wave).

**Find the span:**

`span{(1, 1), (1, -1)}` = ______________________________________

**Question:** Could a single waveform vector, like just `(1, 1)`,
span every possible two-sample snippet? Why or why not?

_________________________________________________________________

### Task 2: Color Space (RGB) — Grayscale Subspace and Channel Span

Colors in a simple 3-channel model are vectors `(R, G, B)`. For this
exercise, allow each channel to be any real number, even negative or
over the usual limit — we are only testing the rules.

**Set G: all grayscale colors, where `R = G = B`**

Vector space? ___________ Why: _________________________________

**Set S: all colors with `R + G + B = 1`** (a fixed total brightness)

Vector space? ___________ Why: _________________________________

**Find the span:**

`span{(1, 0, 0), (0, 1, 0)}` = ______________________________
(describe it: a point, a line, a plane, or all of R³)

**Question:** Does adding the vector `(2, 0, 0)` to the set above
make the span any bigger? Why or why not?

_________________________________________________________________

### Task 3: Robotics — Joint-Angle Calibration Constraint

A robotics engineer models a two-joint arm's calibration constraint
as pairs `(θ1, θ2)` (joint angles, in degrees, allowed to be any real
number for this test).

**Set K: all pairs with `θ1 - 2θ2 = 0`**

Vector space? ___________ Why: _________________________________

**Set L: all pairs with `θ1 - 2θ2 = 5`**

Vector space? ___________ Why: _________________________________

**Question:** Both sets are described by very similar-looking
equations. What is the one difference between them that decides
whether each is a vector space?

_________________________________________________________________

### Task 4: Polynomial Space — Root Condition and Span

A simple polynomial space consists of degree-≤1 polynomials
`p(x) = a + bx`, written as the vector `(a, b)`.

**Set R: all polynomials with `p(1) = 0`** (that is, `a + b = 0`,
so `x = 1` is always a root)

Vector space? ___________ Why: _________________________________

**Find the span:**

`span{(1, 1), (2, 3)}` = ______________________________________
(these represent the polynomials `1 + x` and `2 + 3x`)

**Question:** Is `3 + 2x` (the vector `(3, 2)`) inside this span?
Explain how you would check.

_________________________________________________________________

### Task 5: Physics — Cable Tension Equilibrium

Three cables pull on a single support ring. For the ring to stay in
static equilibrium along one measured direction, the tensions must
satisfy:

```
2T1 - T2 + T3 = 0
```

(`T1`, `T2`, `T3` in newtons; allow negative values here, since we
are only testing the algebra, not whether a cable can physically
push.)

Solve for `T2` in terms of `T1` and `T3`:

`T2 = ___________________`

Write the general solution as a linear combination of two vectors:

`(T1, T2, T3) = T1( _____ , _____ , _____ ) + T3( _____ , _____ , _____ )`

**Check:** pick `T1 = 1`, `T3 = 1`. Compute `(T1, T2, T3)` from your
formula, then substitute all three values back into the original
equation. Does it hold?

_________________________________________________________________

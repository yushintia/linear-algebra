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

## Part C: More Practice (about 25 minutes)

These problems use the same independence, span, basis, and dimension
ideas as Parts A and B, applied to different real-world settings.

### Task 1: Robotics — Degrees of Freedom

A robot arm's end effector is tested along three motion directions
(in cm per step, `x, y, z` coordinates):

```
d1 = (1, 0, 1)
d2 = (0, 1, 1)
d3 = (1, 1, 2)
```

Set up `c1*d1 + c2*d2 + c3*d3 = (0, 0, 0)` and find a nonzero
solution.

`c1 = ______`  `c2 = ______`  `c3 = ______`

Is `{d1, d2, d3}` independent or dependent? ___________________

State a basis for `span{d1, d2, d3}`, and its dimension. This
dimension is the arm's true degrees of freedom at this instant, even
though three directions were tested.

Basis: ________________________  Dimension: ______

### Task 2: Color Mixing — an RGB Basis

A stage-light rig mixes light from three spotlights, each an
`(R, G, B)` vector:

```
p1 = (1, 0, 0)   pure red
p2 = (0, 1, 0)   pure green
p3 = (2, 1, 0)   an "amber" spot, secretly wired from red and green
```

Show that `p3` is a linear combination of `p1` and `p2`:

`p3 = ______ * p1 + ______ * p2`

State a basis for `span{p1, p2, p3}`, and its dimension:

Basis: ________________________  Dimension: ______

**Question:** Can this rig ever project a blue-tinted light, like
`(0, 0, 1)`? Why or why not, in terms of span?

_________________________________________________________________

### Task 3: Audio — Does a Third Waveform Add Anything?

A synthesizer builds a 3-sample waveform snapshot `(s1, s2, s3)` by
combining two basic waveforms:

```
w1 = (1, 0, -1)
w2 = (0, 1, 0)
```

An engineer proposes adding a third waveform, `w3 = (2, 3, -2)`, to
reach new sounds. Write `w3` as a combination of `w1` and `w2`, if
possible:

`w3 = ______ * w1 + ______ * w2`

Does adding `w3` let the synthesizer reach any sound it could not
already reach with just `{w1, w2}`? ___________________

State the dimension of `span{w1, w2, w3}`: ______

### Task 4: Physics — a Basis for Forces in a Plane

Three forces act on a bracket, each an `(x, y)` vector in newtons:

```
f1 = (3, 4)
f2 = (6, 8)
f3 = (1, 0)
```

**Part (a):** Is `f2` a redundant vector? Why? ___________________

**Part (b):** Is `{f1, f3}` independent? (Neither should be a scalar
multiple of the other.) ___________________

**Part (c):** Since `{f1, f3}` is independent and lives in the
2-dimensional plane `R²`, state a basis for `span{f1, f2, f3}` and its
dimension:

Basis: ________________________  Dimension: ______

### Task 5: Economics — a Resource Rule's Solution Space

A factory's sustainability rule requires labor `L`, material `M`, and
energy `E` per unit produced to satisfy:

```
L - 2M + E = 0
```

Solve for `L` in terms of `M` and `E`:

`L = ___________________________`

Write the general solution as a linear combination of two vectors:

`(L, M, E) = M( _____ , _____ , _____ ) + E( _____ , _____ , _____ )`

State a basis and dimension for this solution space:

Basis: ________________________  Dimension: ______

The rule is a 1×3 matrix, `A = [1  -2  1]`. State `rank(A)` and
`nullity(A)`, and check the rank-nullity theorem:

`rank(A) = ______`  `nullity(A) = ______`
Check: `______ + ______ = ______ = n` (______ unknowns)

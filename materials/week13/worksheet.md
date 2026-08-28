# Week 13 Worksheet: The Café's Next Order

Linear Algebra (501976-001) · Work with a partner. Bring a pencil. No
calculator needed.

---

## Part A (about 15 minutes)

The Campus Café's blending machine can only mix drinks along one
fixed line for now: equal parts espresso and milk, no syrup. In
(espresso, milk) order, that line is spanned by:

```
u = (1, 1)
```

A customer orders a drink that is not on that line:

```
y = (4, 2)
```

### Step 1: Guess and check

Before using this week's formula, try guessing a point on the line
(any point of the form `(t, t)`) that looks close to `y = (4, 2)`.

| Guess: t = | Point (t, t) | Distance to y = (4,2) |
|---|---|---|
| 1 | (1, 1) | |
| 3 | (3, 3) | |
| your guess | | |

**Question:** How would you know, just from guessing, that you had
found the *closest* point rather than just a *close* point?

_________________________________________________________________

### Step 2: Compute the projection

Use the projection formula:

```
proj_u(y) = ((y · u) / (u · u)) u
```

`y · u` = ______________________ = ______

`u · u` = ______________________ = ______

`proj_u(y)` = ______________________ = ( ______ , ______ )

### Step 3: Find the leftover part

```
z = y - proj_u(y) = ______________________ = ( ______ , ______ )
```

### Step 4: Check with the right-angle rule

Compute `z · u`. It must equal 0 for `proj_u(y)` to really be the
closest point.

`z · u` = ______________________ = ______

**Question:** Was your best guess from Step 1 exactly at
`proj_u(y)`, closer, or farther? What does that tell you about
guessing versus computing?

_________________________________________________________________

---

## Part B (about 15 minutes)

The café adds a second starter mix. The machine can now blend two
orthogonal mixes, in (espresso, milk, syrup) order:

```
P = (1, 1, 0)     equal espresso and milk, no syrup
Q = (0, 0, 2)     pure syrup, double strength
```

### Step 1: Confirm orthogonality

The two-direction projection formula only works when `P · Q = 0`.
Check this first.

`P · Q` = ______________________ = ______

### Step 2: Project the café's next order

A different regular orders:

```
y = (5, 1, 6)
```

Compute each piece of the projection.

`(y · P) / (P · P)` = ______________________ = ______

`(y · Q) / (Q · Q)` = ______________________ = ______

`proj_W(y)` = ______ P + ______ Q = ( ______ , ______ , ______ )

### Step 3: Find the leftover part

```
z = y - proj_W(y) = ( ______ , ______ , ______ )
```

### Step 4: Check that the leftover is orthogonal to both mixes

`z · P` = ______

`z · Q` = ______

**Question:** What does the leftover part `z` tell the barista about
this customer's usual order, in plain words (espresso, milk, syrup)?

_________________________________________________________________

**Question:** Rebuild the original order by adding `proj_W(y) + z`.
Does it equal `y = (5, 1, 6)`? Why must it, no matter which vector
you started with?

_________________________________________________________________

---

<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1 (guess and check):**

| t | Point | Distance to (4,2) |
|---|---|---|
| 1 | (1,1) | `sqrt((4-1)²+(2-1)²) = sqrt(9+1) = sqrt(10) ≈ 3.16` |
| 3 | (3,3) | `sqrt((4-3)²+(2-3)²) = sqrt(1+1) = sqrt(2) ≈ 1.41` |

The point of Step 1 is that no guess can be *proven* closest by
distance-checking alone against every other point on the line —
only the projection formula, backed by the right-angle rule,
guarantees the closest point.

**Step 2:**

```
y·u = 4(1) + 2(1) = 6
u·u = 1(1) + 1(1) = 2
proj_u(y) = (6/2)(1,1) = 3(1,1) = (3, 3)
```

**Step 3:**

```
z = (4,2) - (3,3) = (1, -1)
```

**Step 4:**

```
z·u = 1(1) + (-1)(1) = 0   ✓
```

**Discussion:** `t = 3` from Step 1 happens to land exactly on
`proj_u(y) = (3,3)`, if students tried it — a coincidence worth
pointing out. In general, guessing cannot confirm closeness the way
the right-angle check does: distance comparison only ranks the
guesses you happened to try, while `z · u = 0` proves no other point
on the line is closer, full stop.

### Part B

**Step 1:**

```
P·Q = 1(0) + 1(0) + 0(2) = 0   ✓ orthogonal, formula applies
```

**Step 2:**

```
y·P = 5(1) + 1(1) + 6(0) = 6
P·P = 1(1) + 1(1) + 0(0) = 2
(y·P)/(P·P) = 6/2 = 3

y·Q = 5(0) + 1(0) + 6(2) = 12
Q·Q = 0(0) + 0(0) + 2(2) = 4
(y·Q)/(Q·Q) = 12/4 = 3

proj_W(y) = 3P + 3Q = (3,3,0) + (0,0,6) = (3, 3, 6)
```

**Step 3:**

```
z = (5,1,6) - (3,3,6) = (2, -2, 0)
```

**Step 4:**

```
z·P = 2(1) + (-2)(1) + 0(0) = 0   ✓
z·Q = 2(0) + (-2)(0) + 0(2) = 0   ✓
```

**Discussion question 1 answer:** The closest drink the machine can
make is `(3, 3, 6)`: equal espresso and milk, double-strength syrup
scaled to 6. The leftover `(2, -2, 0)` tells the barista the customer
usually wants 2 more units of espresso and 2 fewer units of milk than
that closest match — syrup is already exactly right (the leftover's
third coordinate is 0).

**Discussion question 2 answer:**
`(3,3,6) + (2,-2,0) = (5,1,6) = y` ✓. This must always hold because
`z` is *defined* as `y - proj_W(y)`, so adding `proj_W(y)` back in
always reconstructs `y` exactly — this is the orthogonal
decomposition `y = ŷ + z` from the slides, and it holds for any
vector `y` and any subspace `W`, not just this example.

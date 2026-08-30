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

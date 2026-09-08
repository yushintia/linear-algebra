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

## Part C: More Practice (about 25 minutes)

Projection is not just for the café's blending machine. The five
problems below use the same projection formula in five different
real-world settings.

### Problem 1: Computer Graphics — Casting a Shadow

In a 2D side-view game, sunlight casts every object's shadow
straight down onto flat ground. The ground is the line spanned by
`u = (1, 0)`. A floating object sits at position `y = (6, 4)`.

```
y · u = ______________________ = ______

u · u = ______________________ = ______

proj_u(y) = ______________________ = ( ______ , ______ )

z = y - proj_u(y) = ( ______ , ______ )

z · u = ______
```

**Question:** What do the two coordinates of `proj_u(y)` represent
for the object's shadow — and what does `z` represent about the
object's height above the ground?

_________________________________________________________________

### Problem 2: Data Science — The Simplest Possible Model

Before fitting a full line next week, consider the simplest model of
all: predicting every reading with the same constant number. Three
sensor readings are `y = (2, 4, 6)`. The space of "same constant for
every reading" is the line spanned by `u = (1, 1, 1)`.

```
y · u = ______________________ = ______

u · u = ______________________ = ______

proj_u(y) = ______________________ = ( ______ , ______ , ______ )

z = y - proj_u(y) = ( ______ , ______ , ______ )
```

**Question:** Compute the plain average of the three readings in
`y`. How does it compare to the constant you found inside
`proj_u(y)`? (This is why "the mean" is itself a projection.)

_________________________________________________________________

### Problem 3: Physics — Force Along a Ramp

A crate sits on a frictionless ramp. The direction down the ramp's
surface is `u = (4, 3)`. Gravity pulls straight down on the crate
with force `F = (0, -50)` (newtons). Projecting `F` onto `u` gives
the part of gravity that pulls the crate down the ramp; the leftover
is the part pressing the crate into the ramp.

```
F · u = ______________________ = ______

u · u = ______________________ = ______

proj_u(F) = ______________________ = ( ______ , ______ )

z = F - proj_u(F) = ( ______ , ______ )

z · u = ______
```

**Question:** Find `||proj_u(F)||` (the along-ramp pull) and `||z||`
(the into-ramp push). Do these two, combined with `||F|| = 50`,
satisfy the Pythagorean theorem?

_________________________________________________________________

### Problem 4: Navigation — Closest Point on a Flight Corridor

A delivery drone's flight corridor is a straight line through the
origin in direction `u = (3, 4)` (east, north, in km). A warehouse
sits at `y = (10, 5)`. Air-traffic control wants the point on the
corridor closest to the warehouse.

```
y · u = ______________________ = ______

u · u = ______________________ = ______

proj_u(y) = ______________________ = ( ______ , ______ )

z = y - proj_u(y) = ( ______ , ______ )

z · u = ______
```

**Question:** What are the (east, north) coordinates of the closest
point on the corridor to the warehouse? How far off the corridor is
the warehouse itself (compute `||z||`)?

_________________________________________________________________

### Problem 5: Signal Processing — Approximating with Two Waveforms

A recording engineer wants to approximate a 3-sample captured signal
`y = (4, 2, 5)` using only two reference waveforms, `r1 = (1, 1, 0)`
and `r2 = (1, -1, 0)`.

```
r1 · r2 = ______   (confirm they are orthogonal before using the
                     two-direction formula)

(y · r1) / (r1 · r1) = ______

(y · r2) / (r2 · r2) = ______

proj_W(y) = ______ r1 + ______ r2 = ( ______ , ______ , ______ )

z = y - proj_W(y) = ( ______ , ______ , ______ )

z · r1 = ______        z · r2 = ______
```

**Question:** Which sample of the original signal do the two
reference waveforms completely fail to capture? How do you know,
just from looking at `z`?

_________________________________________________________________

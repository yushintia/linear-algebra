# Week 3 Worksheet: Building and Testing Transformations

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

A new banner design needs the café logo changed by this rule:

> **Rule:** Scale the x-coordinate by 3. Flip the sign of the
> y-coordinate.

### Step 1: Find where the standard basis vectors land

Apply the rule to `(1, 0)` and to `(0, 1)` by hand.

`T(1, 0)` = ( _____ , _____ )

`T(0, 1)` = ( _____ , _____ )

### Step 2: Build the matrix

Each answer above becomes one column. Fill in the matrix:

```
    [ _____  _____ ]
A = [ _____  _____ ]
```

### Step 3: Apply your matrix to two points

Use your matrix from Step 2. Show your work.

Point `(2, 5)`:

_________________________________________________________________

`A(2, 5)` = ( _____ , _____ )

Point `(-1, 4)`:

_________________________________________________________________

`A(-1, 4)` = ( _____ , _____ )

### Step 4: Check

Apply your matrix to `(0, 0)`. What do you get?

_________________________________________________________________

**Question:** Why must this answer always be `(0, 0)`, for any linear
transformation?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Transform the unit square

The unit square has four corners: `(0,0)`, `(1,0)`, `(0,1)`, `(1,1)`.

Apply this rotation matrix to all four corners:

```
    [ 0  -1 ]
A = [ 1   0 ]
```

| Corner | New position |
|---|---|
| (0, 0) | ( ___ , ___ ) |
| (1, 0) | ( ___ , ___ ) |
| (0, 1) | ( ___ , ___ ) |
| (1, 1) | ( ___ , ___ ) |

Sketch the original square and the new shape on the same grid below
(draw two boxes, one for "before," one for "after"):

```
 before                after



```

### Task 2: Is it a linear transformation?

For each rule, decide **yes** or **no**, and give one reason.

**Rule A:** "Add 2 to every x-coordinate, keep y the same."

Linear transformation? ___________ Reason: ___________________________

**Rule B:** "Multiply every coordinate by -1."

Linear transformation? ___________ Reason: ___________________________

**Rule C:** "Square the x-coordinate, keep y the same."

Linear transformation? ___________ Reason: ___________________________

---

## Part C: More Practice (about 25 minutes)

Five more transformations, none of them the café's logo. Same two
skills: build a matrix from where it sends the standard basis
vectors, and check whether a rule is linear at all.

### Task 1: Resizing a toolbar icon

A photo-editing app's arrow icon has two key points, measured from
the icon's center (its origin): `(3, 6)` and `(-2, 9)`. To fit a new
wide toolbar, the icon must be stretched 3 times wider (x-direction)
and squeezed to one-third its height (y-direction).

Find where the standard basis vectors land:

`T(1, 0)` = ( _____ , _____ )

`T(0, 1)` = ( _____ , _____ )

Build the matrix:

```
    [ _____  _____ ]
A = [ _____  _____ ]
```

Apply your matrix to both points.

`A(3, 6)` = ( _____ , _____ )

`A(-2, 9)` = ( _____ , _____ )

### Task 2: A currency-exchange counter

A campus exchange counter converts a wallet holding `u` US dollars
and `w` euros into Korean won, at fixed rates: 1 USD -> 1,300 won,
1 EUR -> 1,450 won.

Find where the standard basis vectors land (this transformation's
output is a single number, won, not a pair):

`T(1, 0)` (1 USD, 0 EUR) = _____ won

`T(0, 1)` (0 USD, 1 EUR) = _____ won

Build the matrix (one row, two columns):

```
A = [ _____   _____ ]
```

A customer's wallet holds `u = 50`, `w = 20`. Apply the matrix.

`A(50, 20)` = _____ won

### Task 3: A robot's rotated sensor

A warehouse robot's camera is mounted rotated 90 degrees clockwise
relative to the robot's own body frame. The 90-degree clockwise
rotation matrix is:

```
    [ 0   1 ]
A = [ -1  0 ]
```

The camera detects a box at local sensor coordinates `(4, 1)`. Apply
the matrix to convert this into the robot's body-frame coordinates.

`A(4, 1)` = ( _____ , _____ )

**Question:** If the box were sitting exactly on the camera's own
lens, at local coordinates `(0, 0)`, where would the matrix place it
in body-frame coordinates? Why must this always be true for a linear
transformation?

_________________________________________________________________

### Task 4: Which conversion is linear?

A thermostat's firmware compares two candidate conversion rules.

**Rule D (distance):** convert `(miles, feet)` to `(kilometers,
meters)` by scaling each coordinate: multiply miles by 1.609,
multiply feet by 0.3048.

**Rule T (temperature):** convert Celsius to Fahrenheit using
`F = (9/5)C + 32`.

For each rule, decide **yes** or **no**, and give one reason.

Rule D linear transformation? ___________ Reason: ___________________________

Rule T linear transformation? ___________ Reason: ___________________________

### Task 5: A game's wall-bounce physics

A 2D platformer's physics engine needs a "wall bounce" rule: when a
ball hits a vertical wall, its velocity's x-component flips sign;
the y-component is unchanged.

Find where the standard basis vectors land under this rule:

`T(1, 0)` = ( _____ , _____ )

`T(0, 1)` = ( _____ , _____ )

Build the matrix:

```
    [ _____  _____ ]
A = [ _____  _____ ]
```

The ball's velocity the instant before impact is `(6, -3)` (moving
right and down). Apply your matrix to find its velocity right after
the bounce.

`A(6, -3)` = ( _____ , _____ )

**Question:** A ball that is perfectly still at the moment of impact
has velocity `(0, 0)`. What must the bounce transformation do to that
velocity, and why?

_________________________________________________________________

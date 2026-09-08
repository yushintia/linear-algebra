# Week 6 Worksheet: Check Before You Solve

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café is testing three new drink pairs. For each pair, the
recipe amounts are known, but the ingredient prices are not. Before
solving for the prices, compute each determinant first.

### Combo 1: Cold Brew and Iced Tea

Both drinks use the same two ingredients: cold-brew concentrate and
water.

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Cold Brew | 3 units concentrate + 1 unit water | 1200 won |
| Iced Tea | 1 unit concentrate + 2 units water | 500 won |

Matrix:

```
[ 3  1 ]
[ 1  2 ]
```

**Determinant:** ______________________

**Does exactly one price exist?** ______________________

**If yes, solve for the price of concentrate (`c`) and water (`w`).**
Show your work below.

_________________________________________________________________

_________________________________________________________________

**Answer:** `c` = ______ won, `w` = ______ won

### Combo 2: Small and Large Smoothie

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Small Smoothie | 2 units fruit + 1 unit yogurt | 1000 won |
| Large Smoothie | 4 units fruit + 2 units yogurt | 2200 won |

Matrix:

```
[ 2  1 ]
[ 4  2 ]
```

**Determinant:** ______________________

**Does exactly one price exist?** ______________________

**Do not fully solve this one.** Instead, compare `2200` to `2 x 1000`.
What do you notice?

_________________________________________________________________

### Combo 3: Bubble Tea, Regular and Party Size

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Bubble Tea | 1 unit tapioca + 2 units milk tea | 900 won |
| Party-Size (5x) | 5 units tapioca + 10 units milk tea | 4500 won |

Matrix:

```
[ 1   2 ]
[ 5  10 ]
```

**Determinant:** ______________________

**Do not fully solve this one either.** Instead, compare `4500` to
`5 x 900`. What do you notice?

_________________________________________________________________

**Question:** Combo 2 and Combo 3 both have a determinant of zero, but
they are not the same kind of "not unique." What is different between
them?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: A 3x3 determinant by cofactor expansion

The café is testing an Iced Mocha, using espresso, milk, and
chocolate syrup. Its recipe matrix is:

```
[ 1  0   1 ]
[ 2  1  -1 ]
[ 0  3   1 ]
```

Expand along the top row. Find each of the three minors, apply the
sign pattern, and compute the determinant. Show your work.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Determinant:** ______________________

**Does this recipe have exactly one exact answer?** ______________________

### Task 2: Classify by determinant only

For each matrix below, compute only the determinant. Do not solve the
full system. Classify each as **invertible** (exactly one solution)
or **singular** (not exactly one solution).

**System 1**
```
[ 1  2 ]
[ 3  4 ]
```
Determinant: ______ Classification: ___________________

**System 2**
```
[ 2  4 ]
[ 1  2 ]
```
Determinant: ______ Classification: ___________________

**System 3**
```
[ 5  0 ]
[ 0  5 ]
```
Determinant: ______ Classification: ___________________

---

## Part C: More Practice (about 25 minutes)

Each task below is a different real-world system. None of them are
the café.

### Task 1: Geometry — Garden Plot Area via Determinant

A landscaper marks out a parallelogram-shaped flower bed using two
edge vectors from the same corner: `u = (6, 2)` and `v = (1, 4)`
(meters). The area of the parallelogram equals the absolute value of
the determinant of the matrix with `u` and `v` as columns.

```
[ 6  1 ]
[ 2  4 ]
```

**Determinant:** ______________________

**Area of the parallelogram bed:** ______________________ m²

A walking path cuts the bed exactly in half along the diagonal,
making a triangular planting area on one side.

**Area of the triangular planting area:** ______________________ m²

### Task 2: Robotics — Camera-to-Arm Transformation Check

A robot's vision system converts camera pixel coordinates to arm
coordinates using a 2x2 transform matrix. The system was just
recalibrated for two different camera mounts. Before trusting either
mount, the software checks whether its transform matrix is
invertible (a singular matrix means the mount collapsed 2D space
onto a line, and pixel positions can no longer be recovered).

**Mount 1**
```
[ 2  3 ]
[ 4  6 ]
```
Determinant: ______ Invertible or singular? ___________________

**Mount 2**
```
[ 3  1 ]
[ 2  4 ]
```
Determinant: ______ Invertible or singular? ___________________

**Question:** Which mount needs to be recalibrated before the robot
can safely use it?

_________________________________________________________________

### Task 3: Circuit Analysis — Three-Loop Mesh Determinant

A circuit with three current loops has this resistor coefficient
matrix (from Kirchhoff's Voltage Law):

```
[  6  -2   0 ]
[ -2   5  -1 ]
[  0  -1   4 ]
```

Expand along the top row. Find each of the three minors, apply the
sign pattern, and compute the determinant. Show your work.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Determinant:** ______________________

**Does this circuit have exactly one set of loop currents, for any
choice of voltage sources?** ______________________

### Task 4: Cryptography — Encoding Key Invertibility

A simple message-encoding scheme multiplies pairs of letter values by
a fixed 2x2 key matrix. Decoding only works if the key matrix is
invertible — otherwise, two different messages could encode to the
same result, and decoding would be impossible. Check both candidate
keys.

**Key A**
```
[ 3  5 ]
[ 2  4 ]
```
Determinant: ______ Usable as an encoding key? ___________________

**Key B**
```
[ 4  6 ]
[ 2  3 ]
```
Determinant: ______ Usable as an encoding key? ___________________

### Task 5: Economics — Input-Output Model Check

A simplified two-sector economy (agriculture, manufacturing) relates
total output to demand through a coefficient matrix. Two candidate
models are proposed; check whether each one guarantees a unique
output solution for any demand.

**Model 1**
```
[  0.9  -0.2 ]
[ -0.3   0.8 ]
```
Determinant: ______ Classification: ___________________

**Model 2**
```
[  0.6  -0.4 ]
[ -0.3   0.2 ]
```
Determinant: ______ Classification: ___________________

**Question:** What does it mean, in practical terms, for an
economist to rely on Model 2 to plan production?

_________________________________________________________________

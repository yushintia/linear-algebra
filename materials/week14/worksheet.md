# Week 14 Worksheet: The Café's Brew-Time Test

Linear Algebra (501976-001) · Work with a partner. Bring a pencil. No
calculator needed.

---

## Part A (about 15 minutes)

The Campus Café ran a second taste test, this time on brew time.
Five customers each tried a cup brewed for a different number of
extra minutes beyond the standard steep time, then rated the taste
from 1 to 10.

| Cup | Extra brew minutes (`x`) | Rating (`y`) |
|---|---|---|
| 1 | 1 | 4 |
| 2 | 2 | 4 |
| 3 | 3 | 6 |
| 4 | 4 | 7 |
| 5 | 5 | 9 |

Just like the syrup data from class, no straight line passes through
all five points.

### Step 1: Does an exact line exist?

Look at the table. If you tried to draw one straight line through
all five points, would it work exactly? Why or why not, in terms of
equations and unknowns?

_________________________________________________________________

_________________________________________________________________

### Step 2: Build the design matrix

We want a line `rating = b + m · minutes`, with two unknowns:
intercept `b` and slope `m`. Fill in the design matrix `A` and
target vector `b` (one row per cup):

```
A = [ 1   __ ]        b = [ __ ]
    [ 1   __ ]            [ __ ]
    [ 1   __ ]            [ __ ]
    [ 1   __ ]            [ __ ]
    [ 1   __ ]            [ __ ]
```

### Step 3: Compute the sums

With `n = 5` data points, compute:

`Σx = _____`

`Σy = _____`

`Σx² = _____`

`Σxy = _____`

### Step 4: Write the normal equations

Using your sums from Step 3, fill in the 2x2 normal-equations system
`AᵀAx̂ = Aᵀb`:

```
n·b   + (Σx)·m  = Σy    ->   ___ b + ___ m = ___
(Σx)·b + (Σx²)·m = Σxy  ->   ___ b + ___ m = ___
```

Do not solve yet — Part B picks up here.

---

## Part B (about 15 minutes)

### Task 1: Solve the normal equations

Solve your Part A system for `b` and `m`. Use substitution or row
operations — your choice. Show your work.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Answer:** `b = ______`, `m = ______`

**Best-fit line:** `rating = _____ + _____ · minutes`

### Task 2: Check the residuals

For each cup, compute the predicted rating and the residual
(`actual - predicted`).

| Cup | `x` | Actual `y` | Predicted | Residual |
|---|---|---|---|---|
| 1 | 1 | 4 | | |
| 2 | 2 | 4 | | |
| 3 | 3 | 6 | | |
| 4 | 4 | 7 | | |
| 5 | 5 | 9 | | |

Sum of squared residuals: `_____`

### Task 3: Interpolation vs. extrapolation

Using your best-fit line from Task 1, predict the rating at each
`x` below. Then classify each prediction as **interpolation** or
**extrapolation**.

**Prediction at `x = 2.5`:** rating = ______  Classification: ___________________

**Prediction at `x = 8`:** rating = ______  Classification: ___________________

**Question:** One of these predictions gives a rating outside the
1-10 scale customers were asked to use. Which one, and what does
that tell you about trusting it?

_________________________________________________________________

_________________________________________________________________

---

## Part C: More Practice (about 25 minutes)

Least-squares fitting works the same way no matter what the data
represents. Each problem below gives you a small, clean dataset:
build the normal equations, solve, and interpret the fit.

### Problem 1: Plant Growth

A biology student measures a seedling's height (cm) once a day for
five days.

| Day (`x`) | Height in cm (`y`) |
|---|---|
| 1 | 4 |
| 2 | 4 |
| 3 | 7 |
| 4 | 8 |
| 5 | 12 |

```
Σx = _____     Σy = _____     Σx² = _____     Σxy = _____

Normal equations:  ___ b + ___ m = ___
                    ___ b + ___ m = ___

b = ______        m = ______

Best-fit line: height = _____ + _____ · day
```

**Question:** Using your best-fit line, predict the seedling's
height on day 6. Is this interpolation or extrapolation?

_________________________________________________________________

### Problem 2: Points Scored per Game

A basketball player's points scored over five games:

| Game (`x`) | Points (`y`) |
|---|---|
| 1 | 11 |
| 2 | 11 |
| 3 | 14 |
| 4 | 15 |
| 5 | 19 |

```
Σx = _____     Σy = _____     Σx² = _____     Σxy = _____

Normal equations:  ___ b + ___ m = ___
                    ___ b + ___ m = ___

b = ______        m = ______

Best-fit line: points = _____ + _____ · game
```

**Question:** Compute the residual for Game 3. What does a residual
of (close to) zero tell you about that particular game?

_________________________________________________________________

### Problem 3: Quarterly Price Index

A commodity's price index over five quarters:

| Quarter (`x`) | Price index (`y`) |
|---|---|
| 1 | 106 |
| 2 | 110 |
| 3 | 113 |
| 4 | 120 |
| 5 | 126 |

```
Σx = _____     Σy = _____     Σx² = _____     Σxy = _____

Normal equations:  ___ b + ___ m = ___
                    ___ b + ___ m = ___

b = ______        m = ______

Best-fit line: price index = _____ + _____ · quarter
```

**Question:** What does the slope `m` represent in plain economic
terms (units: price-index points per quarter)?

_________________________________________________________________

### Problem 4: Velocity of a Rolling Cart

A cart rolls down a ramp. Its velocity (m/s) is measured once per
second:

| Time in s (`x`) | Velocity in m/s (`y`) |
|---|---|
| 1 | 4 |
| 2 | 9 |
| 3 | 11 |
| 4 | 15 |
| 5 | 16 |

```
Σx = _____     Σy = _____     Σx² = _____     Σxy = _____

Normal equations:  ___ b + ___ m = ___
                    ___ b + ___ m = ___

b = ______        m = ______

Best-fit line: velocity = _____ + _____ · time
```

**Question:** In physics, the slope of a velocity-vs-time line is
acceleration. What acceleration (in m/s²) does this fit suggest?

_________________________________________________________________

### Problem 5: Force Sensor Calibration

An engineer calibrates a force sensor by applying known reference
forces and recording the sensor's output voltage:

| Reference force in N (`x`) | Output in mV (`y`) |
|---|---|
| 1 | 6 |
| 2 | 7 |
| 3 | 15 |
| 4 | 15 |
| 5 | 22 |

```
Σx = _____     Σy = _____     Σx² = _____     Σxy = _____

Normal equations:  ___ b + ___ m = ___
                    ___ b + ___ m = ___

b = ______        m = ______

Best-fit calibration line: voltage = _____ + _____ · force
```

**Question:** Using your calibration line, if a future reading comes
back as `voltage = 13 mV`, roughly what force does that correspond
to? (Solve `13 = b + m · force` for `force`.)

_________________________________________________________________

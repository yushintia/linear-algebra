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

<!-- page break for print -->

## Instructor Answer Key — do not hand out this section

### Part A

**Step 1:** Five data points give five equations, but the line has
only two unknowns (`b` and `m`) — an overdetermined system. `b` (the
target vector of ratings) almost never lands exactly in the column
space of `A`, so no exact line passes through all five points.

**Step 2:**

```
A = [ 1  1 ]        b = [ 4 ]
    [ 1  2 ]            [ 4 ]
    [ 1  3 ]            [ 6 ]
    [ 1  4 ]            [ 7 ]
    [ 1  5 ]            [ 9 ]
```

**Step 3:**

```
Σx = 1+2+3+4+5 = 15
Σy = 4+4+6+7+9 = 30
Σx² = 1+4+9+16+25 = 55
Σxy = 1(4)+2(4)+3(6)+4(7)+5(9) = 4+8+18+28+45 = 103
```

**Step 4:**

```
5b + 15m = 30
15b + 55m = 103
```

### Part B

**Task 1 (solution):**

From the first equation: `b = (30 - 15m) / 5 = 6 - 3m`. Substitute
into the second:

```
15(6 - 3m) + 55m = 103
90 - 45m + 55m = 103
90 + 10m = 103
10m = 13
m = 1.3
```

Back-substitute: `b = 6 - 3(1.3) = 6 - 3.9 = 2.1`.

**Answer: `b = 2.1`, `m = 1.3`.**

**Best-fit line: `rating = 2.1 + 1.3 · minutes`.**

**Task 2 (residuals):**

| Cup | `x` | Actual `y` | Predicted | Residual |
|---|---|---|---|---|
| 1 | 1 | 4 | 3.4 | 0.6 |
| 2 | 2 | 4 | 4.7 | -0.7 |
| 3 | 3 | 6 | 6.0 | 0.0 |
| 4 | 4 | 7 | 7.3 | -0.3 |
| 5 | 5 | 9 | 8.6 | 0.4 |

Sum of squared residuals: `0.6² + 0.7² + 0.0² + 0.3² + 0.4² = 0.36 +
0.49 + 0.00 + 0.09 + 0.16 = 1.10`.

**Task 3:**

- **Prediction at `x = 2.5`:** `2.1 + 1.3(2.5) = 2.1 + 3.25 = 5.35`. This is **interpolation** — `2.5` sits inside the observed range of `1` to `5`.
- **Prediction at `x = 8`:** `2.1 + 1.3(8) = 2.1 + 10.4 = 12.5`. This is **extrapolation** — `8` sits outside the observed range.

**Discussion question answer:** The `x = 8` extrapolation gives a
predicted rating of `12.5`, which is impossible on a 1-10 scale. This
is a concrete sign the fitted line should not be trusted far outside
the data it was built from — the model has no information about
how ratings behave past `x = 5`, and nothing stops the straight line
from producing a nonsense value once you push it far enough.

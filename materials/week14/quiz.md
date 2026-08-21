# Week 14 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes. Separate from today's Quiz 2.

---

**1.** The café's taste-test data has 5 points but only 2 unknowns
(slope and intercept). What kind of system is this?

A. Underdetermined
B. Overdetermined
C. Homogeneous
D. Diagonal

**2.** What does the least-squares solution `x̂` minimize?

A. The number of data points
B. The largest single residual
C. The sum of squared residuals
D. The slope of the fitted line

**3.** In the design matrix `A = [1  x]` for fitting a line, what
does the column of 1s represent?

A. The slope
B. The intercept
C. The residual
D. The number of data points

**4.** Which system is the normal equations, used to find the
least-squares solution?

A. `Ax = b`
B. `AᵀAx̂ = Aᵀb`
C. `Ax̂ = 0`
D. `AᵀA = I`

**5.** A residual is best described as:

A. The predicted value minus the actual value's coefficient
B. The gap between one actual data point and the line's prediction for it
C. The slope of the best-fit line
D. The number of unknowns in the system

**6.** The café's line was fit using syrup amounts from 1 to 5
units. Predicting the rating at 20 units of syrup is an example of:

A. Interpolation
B. An overdetermined system
C. Extrapolation
D. A normal equation

**7. (Short answer)** A different café dataset produces the normal
equations `3b + 6m = 12` and `6b + 14m = 26`. Solve for `b` and `m`,
and show your steps.

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** More equations (5 data points) than unknowns (2) makes this an overdetermined system.
2. **C.** `x̂` is chosen to make `Ax̂` as close to `b` as possible, in the sum-of-squared-residuals sense.
3. **B.** The column of 1s lets the fitted line sit above or below the origin — without it, the line is forced through `(0, 0)`.
4. **B.** `AᵀAx̂ = Aᵀb` is the normal equations, derived from requiring `b - Ax̂` to be orthogonal to every column of `A`.
5. **B.** A residual is the gap between one actual point and what the line predicts for it: `actual - predicted`.
6. **C.** `20` is far outside the observed range of `1` to `5`, so this is extrapolation — much less trustworthy than a prediction inside the data's range.
7. From the first equation: `b = (12 - 6m) / 3 = 4 - 2m`. Substitute into the second: `6(4 - 2m) + 14m = 26` → `24 - 12m + 14m = 26` → `24 + 2m = 26` → `2m = 2` → `m = 1`. Then `b = 4 - 2(1) = 2`. **`b = 2`, `m = 1`.**

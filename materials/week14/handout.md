# Week 14 Handout: Least Squares

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 14 slides. Keep it. It is the final
worked example of the semester's running case study.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Noisy data** | Real measurements that do not exactly follow any clean pattern. |
| **Best fit** | The line that comes closest to every data point overall. |
| **Residual** | The gap between one actual point and the line's prediction for it. |
| **Error** | Another word for residual: the amount a prediction misses by. |
| **Least squares** | Picking the line that makes the sum of squared residuals as small as possible. |
| **Overdetermined system** | A system with more equations (data points) than unknowns, usually with no exact solution. |
| **Design matrix** | The matrix `A` built from the input data, one row per data point. |
| **Normal equations** | The system `AᵀAx̂ = Aᵀb`, solved to find the least-squares solution. |
| **Least-squares solution** | The vector `x̂` that makes `Ax̂` as close as possible to `b`. |
| **Sum of squared residuals** | The total error a least-squares line minimizes. |
| **Interpolation** | Predicting inside the range of data you already have. |
| **Extrapolation** | Predicting outside that range, always riskier than interpolation. |
| **Outlier** | One data point far from the rest, which can pull a fitted line off course. |

---

## 2. The Café's Taste-Test Data, Solved Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café ran a real taste test. Five customers
each tried a cup with a different amount of syrup, then rated the
taste from 1 to 10:

| Cup | Syrup units (`x`) | Rating (`y`) |
|---|---|---|
| 1 | 1 | 3 |
| 2 | 2 | 4 |
| 3 | 3 | 6 |
| 4 | 4 | 5 |
| 5 | 5 | 8 |

No straight line passes through all five points. The owner wants the
single line that best matches what customers said.

**Where does the café come from?** The Campus Café is not a real
place — it is a running example invented for this course, and its
numbers are chosen to work out evenly. What is real is the method:
every step below is the general procedure you will use whenever real
data does not fit a model exactly, following Lay, Lay & McDonald,
Ch. 6.

**Step 1 — Set up the model.** We want a line `rating = b + m ·
syrup`, with two unknowns: intercept `b` and slope `m`.

**Step 2 — Build the design matrix.** Each cup gives one row: a 1
(for the intercept) and its syrup amount (for the slope). The
ratings form `b`, the target vector:

```
A = [ 1  1 ]        b = [ 3 ]
    [ 1  2 ]            [ 4 ]
    [ 1  3 ]            [ 6 ]
    [ 1  4 ]            [ 5 ]
    [ 1  5 ]            [ 8 ]
```

(Here `b` on the right is the target vector, not the intercept
unknown — the slides reuse the letter `b` for both, which is
standard notation; keep the model equation and this vector separate
in your head.)

**Step 3 — Compute the sums.** With `n = 5` data points:

```
Σx = 1+2+3+4+5 = 15
Σy = 3+4+6+5+8 = 26
Σx² = 1+4+9+16+25 = 55
Σxy = 1(3)+2(4)+3(6)+4(5)+5(8) = 3+8+18+20+40 = 89
```

**Step 4 — Write the normal equations.** For a line, `AᵀAx̂ = Aᵀb`
reduces to:

```
n·b + (Σx)·m = Σy      ->   5b + 15m = 26
(Σx)·b + (Σx²)·m = Σxy  ->  15b + 55m = 89
```

**Step 5 — Solve.** From the first equation, `b = (26 - 15m) / 5`.
Substitute into the second:

```
15 · (26 - 15m)/5 + 55m = 89
3(26 - 15m) + 55m = 89
78 - 45m + 55m = 89
78 + 10m = 89
10m = 11
m = 1.1
```

Back-substitute: `b = (26 - 15(1.1)) / 5 = (26 - 16.5) / 5 = 9.5/5 =
1.9`.

**Best-fit line:** `rating = 1.9 + 1.1 · syrup`.

**Step 6 — Check the residuals.** For each cup, compute the
prediction `1.9 + 1.1x`, then the residual `actual - predicted`:

| Cup | `x` | Actual `y` | Predicted | Residual |
|---|---|---|---|---|
| 1 | 1 | 3 | 3.0 | 0.0 |
| 2 | 2 | 4 | 4.1 | -0.1 |
| 3 | 3 | 6 | 5.2 | 0.8 |
| 4 | 4 | 5 | 6.3 | -1.3 |
| 5 | 5 | 8 | 7.4 | 0.6 |

Sum of squared residuals: `0² + 0.1² + 0.8² + 1.3² + 0.6² = 2.7`. No
other line, drawn any other way, makes this sum smaller. This is what
"best fit" means, made exact.

**Step 7 — What this buys the café.** The owner now has one trusted
line summarizing every customer's opinion, not a growing pile of
disagreeing trial batches. This is the payoff of the whole semester:
solve, represent, transform, compute, measure, and now approximate.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Adrien-Marie Legendre published the least-squares method first, in
1805, as an appendix to a book about calculating comet orbits. He
gave no probabilistic justification; he simply argued that
minimizing the sum of squared errors was a reasonable, computable
rule for choosing among many imperfect fits.

Carl Friedrich Gauss claimed he had already been using the same idea
since 1795, and he gave it a much more dramatic proof. The dwarf
planet Ceres was discovered in January 1801, tracked for a few weeks,
then lost behind the sun's glare. Astronomers had only a handful of
noisy position readings, not nearly enough to solve its orbit
exactly. Gauss used least squares to find the single best orbit
consistent with the noisy data, and predicted where Ceres would
reappear. When it was found again in December 1801, almost exactly
where Gauss said it would be, his method's reputation was made. He
published the full technique in 1809, in the same work referenced in
Week 1's origin story about Gaussian elimination — the same
mathematician, at both ends of this semester's toolkit.

A priority dispute followed: Legendre published first, but Gauss
claimed to have used the method years earlier without publishing.
Both names are still attached to different parts of the method today.

### 3.2 Where this shows up in real jobs

- **Data science:** almost every "trend line" or "line of best fit" reported in a dashboard is a least-squares fit, computed the same way as this week's café example.
- **Machine learning:** linear regression, one of the first models taught in any ML course, is exactly this week's method, often with many more input variables than one.
- **Sensor calibration:** engineers fit a clean conversion formula to a sensor's noisy raw readings, using the same normal equations.
- **Economics and finance:** analysts fit trend lines to noisy price or demand data to estimate an underlying pattern.
- **Surveying and GPS:** modern position systems still use least squares to combine multiple noisy signals into one best estimate, the same idea Gauss used for Ceres.

None of these show you "normal equations" on the surface. All of them
solve one, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Why does a data set with 6 points and only 2 unknowns usually have no exact solution to `Ax = b`?
2. A design matrix for fitting a line has columns `[1, x]`. What does the column of 1s represent?
3. Fit a line to the points `(1, 2)` and `(2, 4)` and `(3, 5)`. Find `Σx`, `Σy`, `Σx²`, `Σxy`, with `n = 3`.
4. Using your sums from Question 3, write the two normal equations for `b` and `m`.
5. Solve your normal equations from Question 4 for `b` and `m`.
6. For the line from Question 5, compute the predicted value at `x = 2` and its residual against the actual value `4`.

### Answers

1. **More equations (6) than unknowns (2).** The target vector `b` almost never lands exactly inside the 2-dimensional column space of `A`, so no exact solution exists.
2. **The intercept.** It lets the fitted line sit above or below the origin, instead of being forced through `(0, 0)`.
3. `Σx = 1+2+3 = 6`, `Σy = 2+4+5 = 11`, `Σx² = 1+4+9 = 14`, `Σxy = 1(2)+2(4)+3(5) = 2+8+15 = 25`.
4. `3b + 6m = 11` and `6b + 14m = 25`.
5. From the first equation, `b = (11 - 6m)/3`. Substitute: `6(11-6m)/3 + 14m = 25` → `2(11-6m) + 14m = 25` → `22 - 12m + 14m = 25` → `2m = 3` → `m = 1.5`. Then `b = (11 - 9)/3 = 2/3 ≈ 0.67`.
6. Predicted at `x = 2`: `0.67 + 1.5(2) = 3.67`. Residual: `4 - 3.67 = 0.33`. The fitted line slightly underpredicts this point.

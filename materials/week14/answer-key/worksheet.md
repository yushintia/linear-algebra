<!-- page break for print -->

## Professor Answer Key — do not hand out this section

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

<!-- page break for print -->

## Professor Answer Key (do not hand out this section)

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

### Part C

**Problem 1 (Plant Growth):**

```
Σx = 1+2+3+4+5 = 15
Σy = 4+4+7+8+12 = 35
Σx² = 1+4+9+16+25 = 55
Σxy = 1(4)+2(4)+3(7)+4(8)+5(12) = 4+8+21+32+60 = 125

Normal equations:
5b + 15m = 35
15b + 55m = 125
```

From the first equation: `b = (35 - 15m)/5 = 7 - 3m`. Substitute into
the second: `15(7 - 3m) + 55m = 125` → `105 - 45m + 55m = 125` →
`105 + 10m = 125` → `m = 2`. Back-substitute: `b = 7 - 3(2) = 1`.

**Answer: `b = 1`, `m = 2`. Best-fit line: `height = 1 + 2 · day`.**

**Question answer:** Predicted height on day 6: `1 + 2(6) = 13` cm.
This is **extrapolation**: day 6 is outside the observed range of
days 1 to 5.

**Problem 2 (Points Scored per Game):**

```
Σx = 15
Σy = 11+11+14+15+19 = 70
Σx² = 55
Σxy = 1(11)+2(11)+3(14)+4(15)+5(19) = 11+22+42+60+95 = 230

Normal equations:
5b + 15m = 70
15b + 55m = 230
```

From the first equation: `b = (70 - 15m)/5 = 14 - 3m`. Substitute:
`15(14 - 3m) + 55m = 230` → `210 - 45m + 55m = 230` →
`210 + 10m = 230` → `m = 2`. Back-substitute: `b = 14 - 3(2) = 8`.

**Answer: `b = 8`, `m = 2`. Best-fit line: `points = 8 + 2 · game`.**

**Question answer:** Predicted points for Game 3: `8 + 2(3) = 14`.
Actual points: `14`. Residual `= 14 - 14 = 0`. A residual of zero
means the best-fit line predicted that game's score exactly: no
error at all for that one data point.

**Problem 3 (Quarterly Price Index):**

```
Σx = 15
Σy = 106+110+113+120+126 = 575
Σx² = 55
Σxy = 1(106)+2(110)+3(113)+4(120)+5(126) = 106+220+339+480+630 = 1775

Normal equations:
5b + 15m = 575
15b + 55m = 1775
```

From the first equation: `b = (575 - 15m)/5 = 115 - 3m`. Substitute:
`15(115 - 3m) + 55m = 1775` → `1725 - 45m + 55m = 1775` →
`1725 + 10m = 1775` → `m = 5`. Back-substitute: `b = 115 - 3(5) = 100`.

**Answer: `b = 100`, `m = 5`. Best-fit line:
`price index = 100 + 5 · quarter`.**

**Question answer:** The slope `m = 5` means the commodity's price
index rises by about 5 points, on average, each quarter.

**Problem 4 (Velocity of a Rolling Cart):**

```
Σx = 15
Σy = 4+9+11+15+16 = 55
Σx² = 55
Σxy = 1(4)+2(9)+3(11)+4(15)+5(16) = 4+18+33+60+80 = 195

Normal equations:
5b + 15m = 55
15b + 55m = 195
```

From the first equation: `b = (55 - 15m)/5 = 11 - 3m`. Substitute:
`15(11 - 3m) + 55m = 195` → `165 - 45m + 55m = 195` →
`165 + 10m = 195` → `m = 3`. Back-substitute: `b = 11 - 3(3) = 2`.

**Answer: `b = 2`, `m = 3`. Best-fit line:
`velocity = 2 + 3 · time`.**

**Question answer:** The slope of a velocity-vs-time line is
acceleration, so this fit suggests an acceleration of about
`3 m/s²`.

**Problem 5 (Force Sensor Calibration):**

```
Σx = 15
Σy = 6+7+15+15+22 = 65
Σx² = 55
Σxy = 1(6)+2(7)+3(15)+4(15)+5(22) = 6+14+45+60+110 = 235

Normal equations:
5b + 15m = 65
15b + 55m = 235
```

From the first equation: `b = (65 - 15m)/5 = 13 - 3m`. Substitute:
`15(13 - 3m) + 55m = 235` → `195 - 45m + 55m = 235` →
`195 + 10m = 235` → `m = 4`. Back-substitute: `b = 13 - 3(4) = 1`.

**Answer: `b = 1`, `m = 4`. Best-fit calibration line:
`voltage = 1 + 4 · force`.**

**Question answer:** Solve `13 = 1 + 4 · force` → `12 = 4 · force` →
`force = 3` N.

## Answer Key

1. **B.** More equations (5 data points) than unknowns (2) makes this an overdetermined system.
2. **C.** `x̂` is chosen to make `Ax̂` as close to `b` as possible, in the sum-of-squared-residuals sense.
3. **B.** The column of 1s lets the fitted line sit above or below the origin — without it, the line is forced through `(0, 0)`.
4. **B.** `AᵀAx̂ = Aᵀb` is the normal equations, derived from requiring `b - Ax̂` to be orthogonal to every column of `A`.
5. **B.** A residual is the gap between one actual point and what the line predicts for it: `actual - predicted`.
6. **C.** `20` is far outside the observed range of `1` to `5`, so this is extrapolation — much less trustworthy than a prediction inside the data's range.
7. From the first equation: `b = (12 - 6m) / 3 = 4 - 2m`. Substitute into the second: `6(4 - 2m) + 14m = 26` → `24 - 12m + 14m = 26` → `24 + 2m = 26` → `2m = 2` → `m = 1`. Then `b = 4 - 2(1) = 2`. **`b = 2`, `m = 1`.**

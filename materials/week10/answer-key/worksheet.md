<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1 (guess and check):**

| m | l | 4m + 2l | m + 3l | Same direction? |
|---|---|---|---|---|
| 1 | 1 | 6 | 4 | No (6:4 ≠ 1:1) |
| 2 | 1 | 10 | 5 | Yes! (10:5 = 2:1) |

The point of Step 1 is that most guesses rotate off their starting
direction; only special ones do not. `(2, 1)` happens to land on one
of the real eigenvectors, which Step 3 will confirm.

**Step 2:**

```
B = [ 4  2 ]
    [ 1  3 ]
```

**Step 3 (characteristic equation):**

```
det(B - λI) = (4-λ)(3-λ) - (2)(1) = 0
λ² - 7λ + 12 - 2 = 0
λ² - 7λ + 10 = 0
(λ - 5)(λ - 2) = 0
```

**Answer: `λ = 5` and `λ = 2`.**

### Part B

**Task 1 (eigenvector for `λ = 5`):**

```
(B - 5I)v = 0
[ -1   2 ] [m]   [0]
[  1  -2 ] [l] = [0]
```

Both rows say `m = 2l`. Pick `l = 1`, so `m = 2`. Eigenvector:
`(2, 1)` — the same direction Step 1's lucky second guess found.

**Check:** `B(2,1) = (4·2+2·1, 1·2+3·1) = (10, 5) = 5(2, 1)`. ✓

**Task 2 (is `λ = 1` an eigenvalue?):**

- **Matrix 1:** `det([[0,0],[0,4]]) = (0)(4) - (0)(0) = 0`. **Yes**, `λ = 1` is an eigenvalue.
- **Matrix 2:** `det([[1,0],[0,2]]) = (1)(2) - (0)(0) = 2`. **No**, `λ = 1` is not an eigenvalue.
- **Matrix 3:** `det([[0,1],[0,0]]) = (0)(0) - (1)(0) = 0`. **Yes**, `λ = 1` is an eigenvalue.

**Discussion question answer:** Matrix 1 and Matrix 3 both have a `1`
somewhere on the diagonal (or, more precisely, subtracting `1` from
the diagonal makes the matrix singular, determinant zero). Matrix 2's
diagonal entries are `2` and `3`, so subtracting `1` never makes it
singular; `λ = 1` is not one of its eigenvalues.

### Part C

**Task 1 (vibration analysis):**

```
det(K - λI) = (5-λ)(2-λ) - (-2)(-2) = 0
λ² - 7λ + 10 - 4 = 0
λ² - 7λ + 6 = 0
(λ - 6)(λ - 1) = 0
```

**Answer: `λ = 6` and `λ = 1`.** For `λ = 6`:
`(K - 6I)v = 0` gives `[-1 -2][v] = 0`, so `v1 = -2v2`. Pick `v2 = 1`,
`v1 = -2`. Eigenvector: `(-2, 1)`.

Check: `K(-2,1) = (5·-2 + -2·1, -2·-2 + 2·1) = (-12, 6) = 6·(-2, 1)`. ✓

**Task 2 (population growth):** `G` is triangular, so
`det(G - λI) = (3-λ)(2-λ) = 0`, giving `λ = 3` and `λ = 2`. Dominant:
`λ = 3`. `(G - 3I)v = 0` gives `[0 1][v]=0`, so `v2 = 0`, `v1` free.
Eigenvector: `(1, 0)`. Since this eigenvector points entirely along
the first coordinate, the first species' population comes to
dominate the total the longer the rule runs.

**Task 3 (link network):**

```
det(N - λI) = (0-λ)(0-λ) - (1)(1) = λ² - 1 = 0
```

`λ = 1` and `λ = -1`. For `λ = 1`: `(N - I)v = 0` gives
`[-1 1][v] = 0`, so `v1 = v2`. Eigenvector: `(1, 1)`.

Check: `N(1,1) = (1, 1) = 1·(1, 1)`. ✓ Since `(1, 1)` is a fixed point
of `N` (eigenvalue 1), an equal starting split of importance stays
*exactly* equal, forever, no matter how many times the link-following
rule repeats.

**Task 4 (mechanical stability):** `S` is triangular, so
`det(S - λI) = (-1-λ)(-3-λ) = 0`, giving `λ = -1` and `λ = -3`. Both
eigenvalues are negative, so **yes, the system is stable** — small
errors shrink toward zero over time.

**Task 5 (weather model):**

```
det(W - λI) = (0.8-λ)(0.5-λ) - (0.5)(0.2) = 0
λ² - 1.3λ + 0.4 - 0.1 = 0
λ² - 1.3λ + 0.3 = 0
(λ - 1)(λ - 0.3) = 0
```

`λ = 1` and `λ = 0.3`. For `λ = 1`: `(W - I)v = 0` gives
`-0.2v1 + 0.5v2 = 0`, so `v1 = 2.5v2`. Pick `v2 = 2`, `v1 = 5`.
Eigenvector: `(5, 2)`.

Check: `W(5,2) = (0.8·5 + 0.5·2, 0.2·5 + 0.5·2) = (5, 2) = 1·(5, 2)`. ✓

Long-run ratio of sunny to rainy days: **5 : 2**.

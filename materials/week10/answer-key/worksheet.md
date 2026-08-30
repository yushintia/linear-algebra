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

<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1 (P and D):**

```
P = [ 1   1 ]     D = [ 3  0 ]
    [ 1  -1 ]         [ 0  1 ]
```

**Step 2 (P⁻¹):** `det(P) = (1)(-1) - (1)(1) = -2`.

```
P⁻¹ = [ 1/2   1/2 ]
      [ 1/2  -1/2 ]
```

**Step 3 (check A = PDP⁻¹):** Multiplying `PD` gives
`[ 3  1 ] / [ 3  -1 ]` (columns), then multiplying by `P⁻¹` returns
`A = [[2, 1], [1, 2]]`. Equivalently, `AP = PD` checks column by
column: `A(1,1) = (3,3) = 3·(1,1)` and `A(1,-1) = (1,-1) = 1·(1,-1)`,
both correct.

**Discussion question:** The first column of `P`, `(1, 1)`, is
matched with `3` in the first diagonal slot of `D`. Swapping the
column order of `P` without swapping `D` to match would pair `(1, 1)`
with `1` and `(1, -1)` with `3` — the wrong eigenvalue for each
eigenvector, giving a completely wrong `A` back out.

**Step 4 (A² two ways):**

Direct: `A² = [[2,1],[1,2]]² = [[5,4],[4,5]]`.

Via `PD²P⁻¹`: `D² = [[9,0],[0,1]]`. Working through
`P D² P⁻¹` gives `[[5,4],[4,5]]`. Both methods agree.

### Part B

**Task 1 (eigenvalues):**

`det(B - λI) = (4-λ)(3-λ) - (1)(2) = λ² - 7λ + 10 = 0`
`(λ - 5)(λ - 2) = 0`

`λ₁ = 5`, `λ₂ = 2`.

**Task 2 (eigenvectors):**

For `λ₁ = 5`: `(B - 5I)v = 0` gives `[-1  1][v] = 0`, `[2 -2][v] = 0`,
so `v = (1, 1)`.

For `λ₂ = 2`: `(B - 2I)v = 0` gives `[2  1][v] = 0`, `[2  1][v] = 0`,
so `v = (1, -2)`.

**Task 3 (P, D, P⁻¹):**

```
P = [ 1   1 ]     D = [ 5  0 ]     P⁻¹ = [ 2/3   1/3 ]
    [ 1  -2 ]         [ 0  2 ]           [ 1/3  -1/3 ]
```

(`det(P) = (1)(-2) - (1)(1) = -3`.)

**Task 4 (predict x₄):**

`P⁻¹ x₀ = P⁻¹ (10, 10) = (2/3·10 + 1/3·10, 1/3·10 - 1/3·10) = (10, 0)`.

`D⁴ (10, 0) = (5⁴·10, 2⁴·0) = (6250, 0)`.

`P (6250, 0) = (6250, 6250)`.

`x₄ = (6250, 6250)`.

**Discussion question:** `5` is the dominant eigenvalue of `B`,
since it is larger than `2`. As `n` grows, the `(1, 1)` direction
(matching `λ₁ = 5`) increasingly dominates, and the café's two group
counts trend toward growing in that same, equal ratio.

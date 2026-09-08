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

### Part C

**Task 1 (wildlife population):**

```
P = [ 1   1 ]     D = [ 4  0 ]     P⁻¹ = [ 1/2   1/2 ]
    [ 1  -1 ]         [ 0  2 ]           [ 1/2  -1/2 ]
```

(`det(P) = -2`.)

`P⁻¹ x₀ = P⁻¹(30, 10) = (1/2·30+1/2·10, 1/2·30-1/2·10) = (20, 10)`.

`D³(20, 10) = (4³·20, 2³·10) = (1280, 80)`.

`P(1280, 80) = (1280+80, 1280-80) = (1360, 1200)`.

`x₃ = (1360, 1200)`.

`λ₁ = 4` is dominant. After many more years, the population
approaches the `(1, 1)` direction, an equal **1:1** young:adult ratio.

**Task 2 (computer graphics):**

```
P = [ 2  0 ]     D = [ 4  0 ]     P⁻¹ = [ 1/2    0 ]
    [ 1  1 ]         [ 0  2 ]           [-1/2    1 ]
```

(`det(P) = 2`.)

`P⁻¹ x₀ = P⁻¹(2, 3) = (1/2·2+0·3, -1/2·2+1·3) = (1, 2)`.

`D³(1, 2) = (4³·1, 2³·2) = (64, 16)`.

`P(64, 16) = (2·64+0·16, 1·64+1·16) = (128, 80)`.

`x₃ = (128, 80)`.

**Task 3 (compound growth):**

```
P = [ 1   1 ]     D = [ 7  0 ]     P⁻¹ = [ 1/2   1/2 ]
    [ 1  -1 ]         [ 0  3 ]           [ 1/2  -1/2 ]
```

(`det(P) = -2`.)

`P⁻¹ x₀ = P⁻¹(600, 200) = (1/2·600+1/2·200, 1/2·600-1/2·200) = (400, 200)`.

`D²(400, 200) = (7²·400, 3²·200) = (19600, 1800)`.

`P(19600, 1800) = (19600+1800, 19600-1800) = (21400, 17800)`.

`x₂ = (21400, 17800)`.

**Task 4 (simplified spread model):**

```
P = [ 1   1 ]     D = [ 1   0  ]     P⁻¹ = [ 1/2   1/2 ]
    [ 1  -1 ]         [ 0  0.8 ]           [ 1/2  -1/2 ]
```

(`det(P) = -2`.)

`P⁻¹ x₀ = P⁻¹(900, 100) = (1/2·900+1/2·100, 1/2·900-1/2·100) = (500, 400)`.

`D²(500, 400) = (1²·500, 0.8²·400) = (500, 256)`.

`P(500, 256) = (500+256, 500-256) = (756, 244)`.

`x₂ = (756, 244)`.

Sum: `756 + 244 = 1000`, exactly the starting total (`900 + 100`).
The `λ = 1` eigenvalue leaves the `(1, 1)` "total" direction
unchanged, so the two counts redistribute but their sum is conserved.

**Task 5 (subscription service):**

```
P = [ 1   1 ]     D = [ 1   0  ]     P⁻¹ = [ 1/3   1/3 ]
    [ 2  -1 ]         [ 0  0.4 ]           [ 2/3  -1/3 ]
```

(`det(P) = -3`.)

`P⁻¹ x₀ = P⁻¹(900, 300) = (1/3·900+1/3·300, 2/3·900-1/3·300) = (400, 500)`.

`D²(400, 500) = (1²·400, 0.4²·500) = (400, 80)`.

`P(400, 80) = (400+80, 2·400-80) = (480, 720)`.

`x₂ = (480, 720)`.

The `(1, 2)` eigenvector for `λ = 1` says the steady-state split
favors **Premium**, roughly twice as many users as Free, in the
long run.

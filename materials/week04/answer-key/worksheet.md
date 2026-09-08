<!-- page break for print -->

## Professor Answer Key (do not hand out this section)

### Part A

**Task 1:**

```
AB = [ 2×1+1×1   2×2+1×0 ] = [ 3  4 ]
     [ 0×1+3×1   0×2+3×0 ]   [ 3  0 ]
```

Top-left: `2×1+1×1 = 3`. Top-right: `2×2+1×0 = 4`. Bottom-left:
`0×1+3×1 = 3`. Bottom-right: `0×2+3×0 = 0`.

**Task 2:**

```
H = [ 0.85   0 ]      C = [ 1    0.05 ]
    [  0     1 ]          [ 0     1   ]
```

`N = C × H`:

- Top-left: `1×0.85 + 0.05×0 = 0.85`
- Top-right: `1×0 + 0.05×1 = 0.05`
- Bottom-left: `0×0.85 + 1×0 = 0`
- Bottom-right: `0×0 + 1×1 = 1`

```
N = [ 0.85   0.05 ]
    [  0      1   ]
```

`N × p`: Latte = `0.85×800 + 0.05×900 = 680 + 45 = 725`. Mocha =
`0×800 + 1×900 = 900`.

**Answer: Latte = 725 won, Mocha = 900 won.**

**Step 3 (check):** `H × p = (680, 900)`. Then `C × (680, 900)`:
Latte = `1×680 + 0.05×900 = 680 + 45 = 725`. Mocha =
`0×680 + 1×900 = 900`. Same result as Task 2: `(725, 900)`. ✓

### Part B

**Task 1:**

`ad - bc = 2×1 - 1×1 = 1`.

```
A⁻¹ = [  1  -1 ]
      [ -1   2 ]
```

Check: `A × A⁻¹ = [[2×1+1×-1, 2×-1+1×2],[1×1+1×-1, 1×-1+1×2]] =
[[1,0],[0,1]] = I` ✓.

**Task 2:**

`x = A⁻¹ b`, with `b = (700, 450)`:

`p = 1×700 + (-1)×450 = 700 - 450 = 250`
`q = -1×700 + 2×450 = -700 + 900 = 200`

**Answer: `p = 250`, `q = 200`.** Check: `2(250)+200 = 700` ✓,
`250+200 = 450` ✓.

**Task 3:**

`T⁻¹ = [[1/3, 0],[0, 1/3]]`.

`T⁻¹ × (2400, 2700)`: Latte = `2400/3 = 800`. Mocha = `2700/3 = 900`.

**Recovered prices: Latte = 800 won, Mocha = 900 won.**

**Task 4:**

`ad - bc = 4×1 - 2×2 = 4 - 4 = 0`.

**Classification: singular** (no inverse exists).

### Part C

**Task 1:**

```
D = [ 1.08   0    ]      S = [ 1     0 ]
    [  0    1.05  ]          [ 0.10  1 ]
```

`N = S × D`:

- Top-left: `1×1.08 + 0×0 = 1.08`
- Top-right: `1×0 + 0×1.05 = 0`
- Bottom-left: `0.10×1.08 + 1×0 = 0.108`
- Bottom-right: `0.10×0 + 1×1.05 = 1.05`

```
M = [ 1.08   0    ]
    [ 0.108  1.05 ]
```

`M × c`: Part X = `1.08×1000 + 0×2000 = 1080`. Part Y =
`0.108×1000 + 1.05×2000 = 108 + 2100 = 2208`.

**Answer: Part X = 1080 won, Part Y = 2208 won.**

**Check:** `D × c = (1080, 2100)`. Then `S × (1080, 2100)`: Part X =
`1×1080 + 0×2100 = 1080`. Part Y = `0.10×1080 + 1×2100 = 108 + 2100 =
2208`. Same result as before: `(1080, 2208)`. ✓

**Task 2:**

`c = Kp`: `c1 = 3(4) + 2(7) = 12 + 14 = 26`. `c2 = 1(4) + 1(7) = 11`.
`c = (26, 11)`.

`ad - bc = 3×1 - 2×1 = 1`.

```
K⁻¹ = [  1  -2 ]
      [ -1   3 ]
```

`K⁻¹ c`: `p1 = 1(26) + (-2)(11) = 26 - 22 = 4`. `p2 = -1(26) + 3(11)
= -26 + 33 = 7`. Result: `(4, 7)`.

**Yes**, this matches the original message `p = (4, 7)` exactly.

**Task 3:**

`ad - bc = 0.8×0.1 - 0.4×0.2 = 0.08 - 0.08 = 0`.

**Classification: singular.**

**Question:** No. Since `T` is singular, `T⁻¹` does not exist, so
there is no way to invert the model and recover last year's exact
populations from this year's alone. Different starting populations
could, in principle, produce the same result, or none might.

**Task 4:**

`G⁻¹ = [[1/3, 0], [0, 1/3]]`.

`G⁻¹ × (450, 630)`: Alpha = `450/3 = 150`. Beta = `630/3 = 210`.

**Recovered scores: Alpha = 150, Beta = 210.** Matches the correct
scores exactly.

**Task 5:**

`M = Sc × R`:

- Top-left: `2×0 + 0×1 = 0`
- Top-right: `2×(-1) + 0×0 = -2`
- Bottom-left: `0×0 + 2×1 = 2`
- Bottom-right: `0×(-1) + 2×0 = 0`

```
M = [ 0  -2 ]
    [ 2   0 ]
```

`M(3, 1)`: `x' = 0(3) + (-2)(1) = -2`. `y' = 2(3) + 0(1) = 6`.
Result: `(-2, 6)`.

**Check:** `R(3, 1)`: `x' = 0(3) + (-1)(1) = -1`, `y' = 1(3) + 0(1) =
3`, giving `(-1, 3)`. Then `Sc(-1, 3)`: `x' = 2(-1) = -2`, `y' = 2(3)
= 6`, giving `(-2, 6)`. Same result. ✓

**Question:** `ad - bc = 0×0 - (-2)×2 = 0 + 4 = 4 ≠ 0`.
**Classification: invertible.**

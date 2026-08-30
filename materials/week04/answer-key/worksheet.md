<!-- page break for print -->

## Professor Answer Key — do not hand out this section

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

**Answer: Latte = 725원, Mocha = 900원.**

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

**Recovered prices: Latte = 800원, Mocha = 900원.**

**Task 4:**

`ad - bc = 4×1 - 2×2 = 4 - 4 = 0`.

**Classification: singular** (no inverse exists).

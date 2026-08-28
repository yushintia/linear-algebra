# Week 4 Worksheet: Combine and Undo

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

### Task 1: Multiply two matrices

Multiply `A` and `B` below, using the row-by-column rule from class.
Show each entry's calculation.

```
A = [ 2  1 ]      B = [ 1  2 ]
    [ 0  3 ]          [ 1  0 ]
```

`AB` = ______________________________

Top-left entry: ________________________________

Top-right entry: ________________________________

Bottom-left entry: ________________________________

Bottom-right entry: ________________________________

### Task 2: Combine two café price changes

The Campus Café runs a **holiday sale**. Friday prices stay the same
as before: Latte 800원, Mocha 900원.

- **Holiday discount `H`:** 15% off the Latte, no change to the Mocha.
- **Member bonus `C`:** adds 5% of the Mocha price onto the Latte
  price (a loyalty rule). The discount applies first, then the bonus.

Write `H` and `C` as matrices:

```
H = [        ]      C = [        ]
    [        ]          [        ]
```

Combine them into one matrix `N = C × H` (discount happens first, so
it goes on the right). Show your work.

_________________________________________________________________

_________________________________________________________________

`N` = ______________________________

Apply `N` to the price vector `p = (800, 900)`. What are the combined
holiday prices?

Latte: ______ 원   Mocha: ______ 원

### Step 3: Check

Apply `H` to `p` first, then apply `C` to that result. Do you get the
same combined prices as Task 2?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Find an inverse

Find the inverse of `A` below using the 2×2 formula. Show `ad - bc`
first.

```
A = [ 2  1 ]
    [ 1  1 ]
```

`ad - bc` = ______

`A⁻¹` = ______________________________

Check your answer: multiply `A × A⁻¹`. Does it equal `I`?

_________________________________________________________________

### Task 2: Use the inverse to solve a system

Using the **same** `A⁻¹` you just found, solve this system:

```
2p + q = 700
 p + q = 450
```

(Hint: this is `Ax = b` with `b = (700, 450)`. Compute `x = A⁻¹ b`.)

`p` = ______   `q` = ______

### Task 3: Undo a pricing glitch

A register glitch applied `T` below to Friday's prices `(800, 900)`,
producing `(2400, 2700)`.

```
T = [ 3  0 ]
    [ 0  3 ]
```

Find `T⁻¹` and use it to recover the original prices.

`T⁻¹` = ______________________________

Recovered prices: Latte = ______ 원   Mocha = ______ 원

### Task 4: Classify a matrix

Is the matrix below invertible or singular? Show `ad - bc`.

```
A = [ 4  2 ]
    [ 2  1 ]
```

`ad - bc` = ______

Classification: ___________________

---

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

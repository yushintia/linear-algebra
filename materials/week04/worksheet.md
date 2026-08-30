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

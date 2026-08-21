# Week 4 Handout: Matrix Algebra

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 4 slides. Keep it. You will use the
glossary and the worked example again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Matrix multiplication** | Combining two matrices into one matrix, using the row-by-column rule. |
| **Combine** | Doing two changes as if they were a single step. |
| **Inverse (`A⁻¹`)** | A matrix that undoes another matrix `A` exactly: `A × A⁻¹ = I`. |
| **Identity matrix (`I`)** | The "do nothing" matrix. Multiplying anything by `I` leaves it unchanged. |
| **Order** | The sequence changes happen in. For matrices, `AB` and `BA` can differ. |
| **Row-by-column** | The exact rule for multiplying two matrices: multiply matching entries, then add. |
| **Dimensions** | A matrix's size, written rows × columns. |
| **Square matrix** | A matrix with the same number of rows and columns. |
| **Commutative** | Doing two things in either order gives the same result. Matrix multiplication is **not**, in general. |
| **Invertible matrix** | A matrix that has an inverse. |
| **Singular matrix** | A matrix with no inverse (`ad - bc = 0` for a 2×2 matrix). |
| **Verify** | Check an answer by multiplying it back and confirming it matches. |

---

## 2. The Café's Weekend Prices, Solved Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café's Friday prices for a Latte and a
Mocha are 800원 and 900원, written as a price vector:

```
p = [ 800 ]
    [ 900 ]
```

On weekends, two rules apply, in this order:

- **Discount `D`:** 10% off the Latte, 5% off the Mocha.
- **Surcharge `S`:** adds 10% of the Latte price onto the Mocha price
  (a combo pricing rule).

**Step 1 — Write both rules as matrices.**

```
D = [ 0.90   0   ]      S = [ 1.00   0 ]
    [  0    0.95 ]          [ 0.10   1 ]
```

**Step 2 — Combine them into one matrix.** Since the discount applies
first, then the surcharge, multiply `S × D` (read right to left: `D`
happens first):

```
M = S × D
```

Multiply row-by-column:

- Top-left: `1.00 × 0.90 + 0 × 0 = 0.90`
- Top-right: `1.00 × 0 + 0 × 0.95 = 0`
- Bottom-left: `0.10 × 0.90 + 1 × 0 = 0.09`
- Bottom-right: `0.10 × 0 + 1 × 0.95 = 0.95`

```
M = [ 0.90    0   ]
    [ 0.09   0.95 ]
```

**Step 3 — Apply the combined matrix once.**

```
M × p = [ 0.90×800 + 0×900   ] = [ 720 ]
        [ 0.09×800 + 0.95×900 ]   [ 927 ]
```

**Step 4 — Check against doing it in two steps.** First `D`, then `S`:

```
D × p = [ 720 ]         S × (720, 855) = [ 720 ]
        [ 855 ]                          [ 927 ]
```

Both routes land on the same weekend prices: Latte 720원, Mocha 927원.
`M` replaces two full passes with one.

**Step 5 — Order matters.** Multiplying `D × S` instead (surcharge
first) gives a slightly different matrix:

```
D × S = [ 0.90    0    ]
        [ 0.095  0.95 ]
```

The bottom-left entry changed from `0.09` to `0.095`. The café's
policy fixes the order, and the matrix multiplication must match it.

**Step 6 — Undo a mistake with the inverse.** A register glitch
doubled every Saturday price:

```
G = [ 2  0 ]      G × p = [ 1600 ]
    [ 0  2 ]              [ 1800 ]
```

Its inverse undoes the glitch exactly:

```
G⁻¹ = [ 0.5   0  ]      G⁻¹ × (1600, 1800) = [ 800 ]
      [  0   0.5 ]                            [ 900 ]
```

Friday's correct prices come back exactly, with no re-typing.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Arthur Cayley published *A Memoir on the Theory of Matrices* in 1858.
He was studying what happens when one geometric change (like a
rotation or a scaling) is followed by another. To track this cleanly,
he defined a rule for "multiplying" two matrices so the result
matched doing one change, then the other, in a single object. That
same memoir gave matrices an inverse: not just a way to describe a
change, but a way to undo it.

By the 1950s, matrix multiplication was one of the first operations
programmed onto digital computers, because it is exact and
mechanical. By the 1990s, 3D graphics cards were multiplying chains of
matrices for every single frame of a video game, to combine moving,
rotating, and zooming into one step. Today, deep learning models
perform trillions of matrix multiplications every day; almost every
layer of a neural network is, underneath, a matrix multiplication.

### 3.2 Where this shows up in real jobs

- **Computer graphics and games:** every camera move, rotation, and zoom is a matrix. Game engines multiply several together every frame.
- **Robotics:** combining a robot arm's joint rotations into one final position uses the same combine-and-reverse idea.
- **Software "undo" features:** many undo systems work because the last action was invertible. Reversing it recovers the exact previous state.
- **Machine learning:** neural networks are, layer by layer, matrix multiplications. Understanding this rule is a foundation for that whole field.
- **Economics and operations:** combining several linked scaling rules (tax, discount, exchange rate) into one matrix speeds up large-scale calculations.

None of these look like "multiply two matrices" on the surface. All of
them are doing it, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. `A` is 3×2 and `B` is 2×4. Can you multiply `AB`? If so, what size is the result?
2. Multiply `A = [[2,0],[1,3]]` by `B = [[1,1],[0,2]]`. Find `AB`.
3. Using the same `A` and `B` from Question 2, find `BA`. Is it equal to `AB`?
4. Find the inverse of `A = [[1,2],[1,3]]` using the 2×2 formula.
5. Is `A = [[3,6],[1,2]]` invertible? Show your check.
6. A price vector `p = (500, 600)` is doubled by mistake, giving `(1000, 1200)`. Write the mistake as a matrix `G`, then find `G⁻¹` and use it to recover `p`.

### Answers

1. **Yes.** Columns of `A` (2) match rows of `B` (2). The result `AB` is 3×4.
2. `AB = [[2×1+0×0, 2×1+0×2],[1×1+3×0, 1×1+3×2]] = [[2,2],[1,7]]`.
3. `BA = [[1×2+1×1, 1×0+1×3],[0×2+2×1, 0×0+2×3]] = [[3,3],[2,6]]`. **No**, `BA ≠ AB`; the top-left entries alone differ (3 vs 2).
4. `ad-bc = 1×3 - 2×1 = 1`. `A⁻¹ = [[3,-2],[-1,1]]`. Check: `A × A⁻¹ = [[1×3+2×-1, 1×-2+2×1],[1×3+3×-1, 1×-2+3×1]] = [[1,0],[0,1]] = I` ✓.
5. **No.** `ad-bc = 3×2 - 6×1 = 0`. `A` is singular; it has no inverse.
6. `G = [[2,0],[0,2]]`. `G⁻¹ = [[0.5,0],[0,0.5]]`. `G⁻¹ × (1000,1200) = (500,600) = p` ✓.

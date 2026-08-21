# Week 2 Handout: Vector & Matrix

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 2 slides. Keep it. You will use the
glossary and the worked example again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Vector** | An ordered list of numbers, written as a column, like `[e, m, s]` written top to bottom. |
| **Matrix** | A rectangular grid of numbers, arranged in rows and columns. |
| **Entry (component)** | One single number inside a vector or matrix. |
| **Dimensions** | The size of a matrix, written as rows × columns. A 3×3 matrix has 3 rows and 3 columns. |
| **Zero vector** | A vector whose every entry is `0`. It still counts as a valid vector. |
| **Coefficient matrix (`A`)** | The matrix built from a system's unknown coefficients. |
| **Column vector** | A vector written top to bottom, one column, as opposed to sideways. |
| **Matrix-vector product** | The result of multiplying a matrix by a vector: one new vector. |
| **Ax = b** | The compact form of a linear system: coefficient matrix times unknown vector equals known vector. |
| **Linear combination** | Adding scaled copies of vectors together, like `2·[1,0] + 3·[0,1]`. |
| **Compatible sizes** | A matrix's column count must match the vector's entry count, or the product is undefined. |
| **Row view** | Reading `Ax = b` one equation (one row) at a time. |
| **Column view** | Reading `Ax` as a mix of the matrix's columns, scaled by `x`'s entries. |
| **Square matrix** | A matrix with the same number of rows and columns. |
| **Verify** | Checking a candidate answer by computing `Ax` and comparing it to `b`. |

---

## 2. The Campus Café, Written as Ax = b, Verified Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time. It reuses Week 1's café recipe: `e` shots espresso,
`m` units milk, `s` units syrup, and the same three house rules.

**Step 1 — Recall the system (from Week 1).**

```
e + m + s = 4      ... total liquid
e + m - s = 0      ... syrup = espresso + milk
e - m     = 0      ... equal espresso and milk
```

**Step 2 — Build the vector of unknowns, `x`.**

The three unknowns become one column, in a fixed order:

```
    [ e ]
x = [ m ]
    [ s ]
```

**Step 3 — Build the coefficient matrix, `A`.**

Each row of `A` holds one rule's coefficients, in the same order as
the equations above. A missing unknown gets a coefficient of `0`
(there is no `s` in rule 3, so its entry is `0`):

```
    [ 1  1  1 ]
A = [ 1  1 -1 ]
    [ 1 -1  0 ]
```

**Step 4 — Build the vector of known totals, `b`.**

`b` holds each rule's right-hand side, in the same row order:

```
    [ 4 ]
b = [ 0 ]
    [ 0 ]
```

**Step 5 — Write the whole system as one line.**

```
[ 1  1  1 ][ e ]   [ 4 ]
[ 1  1 -1 ][ m ] = [ 0 ]
[ 1 -1  0 ][ s ]   [ 0 ]
```

This is exactly the same information as Step 1's three equations,
just arranged for a computer.

**Step 6 — Recall the solution (from Week 1's row reduction).**

`e = 1`, `m = 1`, `s = 2`.

**Step 7 — Verify by matrix-vector multiplication.**

Multiply each row of `A` by `x` (row's entries times `x`'s entries,
in order, then add), and compare to `b`:

```
Row 1: 1(1) + 1(1) + 1(2) = 4     b's row 1 = 4    match
Row 2: 1(1) + 1(1) - 1(2) = 0     b's row 2 = 0    match
Row 3: 1(1) - 1(1) + 0(2) = 0     b's row 3 = 0    match
```

**Step 8 — Conclude.**

```
Ax = [ 4 ]      b = [ 4 ]
     [ 0 ]          [ 0 ]
     [ 0 ]          [ 0 ]
```

`Ax` equals `b` exactly. One multiplication replaced three separate
checks. This is the payoff of compact notation: the same verification
step works no matter how many unknowns the café ever adds.

**Step 9 — The column view (a second way to read the same thing).**

`Ax` is also a mix of `A`'s three columns, scaled by `x`'s entries:

```
      [1]        [ 1]        [ 1]
Ax =  e[1]   +   m[ 1]   +   s[-1]
      [1]        [-1]        [ 0]
```

Plugging in `e = 1`, `m = 1`, `s = 2` gives the same `[4, 0, 0]`
answer as the row view. Both views always agree; Week 3 uses the
column view again.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

The word "vector" comes from the Latin for "carrier." William Rowan
Hamilton and Hermann Grassmann, working independently in 1843 and
1844, each formalized the idea of a quantity with both size and
direction, motivated by physics problems: forces, velocities, and
positions in space all need more than one number to describe.

The word "matrix" was coined in 1850 by James Joseph Sylvester, from
the Latin for "womb," meaning something that gives rise to other
things (in his case, smaller grids called determinants, Week 6's
topic). Arthur Cayley then defined the rules for adding and
multiplying matrices as single objects in 1858, while studying how
geometric transformations combine. That work is the direct ancestor
of Week 3's topic, treating a matrix as an action, not just a system.

### 3.2 Where this shows up in real jobs

- **Every numerical computing library:** NumPy (Python), MATLAB, and R all store data as vectors and matrices first; nearly every function operates on `Ax = b` or something built from it.
- **Computer graphics:** every 3D model on screen is a list of vectors (point positions); every rotation, scale, or move is a matrix multiplying those vectors (Week 3).
- **Machine learning:** a model's input data is a matrix (rows = examples, columns = features); a prediction is often little more than a matrix-vector product.
- **Spreadsheets:** a table of numbers with a formula applied to every row is, structurally, a matrix, with the formula acting like a coefficient row.

None of these show you "a vector" or "a matrix" by that name on the
surface. All of them are built on this week's two objects underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Write `x` as a column vector for the unknowns `p`, `q`, `r`, in that order.
2. What are the dimensions of this matrix? `[[2, 0, 1], [4, 5, -3]]` (2 rows, given as row lists).
3. Write the system `3x + y = 7`, `x - 2y = 0` as `Ax = b`. What are `A`, `x`, and `b`?
4. `A` is a 3×4 matrix. Can it multiply a vector with 4 entries? If yes, how many entries does the answer have?
5. `A` is a 3×4 matrix. Can it multiply a vector with 3 entries? Why or why not?
6. Compute `Ax` by hand: `A = [[1, 2], [3, 0]]`, `x = [2, 5]`. Multiply row by column and add.

### Answers

1. `x = [p, q, r]`, written top to bottom, in that order.
2. **2×3.** Two rows, three columns (three numbers per row).
3. `A = [[3, 1], [1, -2]]`, `x = [x, y]`, `b = [7, 0]`.
4. **Yes.** A 3×4 matrix times a 4-entry vector gives a 3-entry vector (one entry per row of `A`).
5. **No.** `A`'s column count (4) must match the vector's entry count. A 3-entry vector does not fit.
6. `Ax = [1(2) + 2(5), 3(2) + 0(5)] = [12, 6]`.

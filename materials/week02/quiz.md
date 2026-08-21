# Week 2 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** Which best describes a vector?

A. A rectangular grid of numbers
B. An ordered list of numbers, written as a column
C. Any number multiplied by an unknown
D. A single row operation

**2.** A matrix has 4 rows and 2 columns. What are its dimensions?

A. 2 × 4
B. 4 × 2
C. 6 × 1
D. 8 × 1

**3.** To multiply a matrix by a vector, the correct rule is:

A. Column times row
B. Row times column
C. Add every entry together first
D. Multiply the two largest numbers only

**4.** `A` is a 2 × 3 matrix. `x` has 3 entries. How many entries
does `Ax` have?

A. 1
B. 2
C. 3
D. 6

**5.** `A` is a 2 × 3 matrix. `x` has 2 entries. Is `Ax` defined?

A. Yes, it has 2 entries
B. Yes, it has 3 entries
C. No, the sizes are not compatible
D. Yes, but only if `A` is square

**6.** The system `4x - y = 2` becomes one row of `Ax = b`. What is
that row's entry in `b`?

A. `4`
B. `-1`
C. `2`
D. `x`

**7. (Short answer)** Compute `Ax` by hand and show your steps:
`A = [[2, 1], [0, 3]]`, `x = [3, 4]`.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** A vector is an ordered list of numbers, written as a column.
2. **B.** Dimensions are rows × columns: 4 rows, 2 columns.
3. **B.** Multiply each row's entries by the vector's entries, in order, then add.
4. **B.** A 2×3 matrix times a compatible vector gives one entry per row of `A`, so 2 entries.
5. **C.** `A`'s column count (3) must match `x`'s entry count. 2 entries do not fit; the product is undefined.
6. **C.** `b`'s matching entry is the equation's right-hand side, `2`.
7. `Ax = [2(3) + 1(4), 0(3) + 3(4)] = [10, 12]`.

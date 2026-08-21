# Week 4 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** Which best describes matrix multiplication `AB`?

A. Multiply each matching entry of `A` and `B` together
B. Combine `A`'s change and `B`'s change into one matrix, row-by-column
C. Add every entry of `A` to every entry of `B`
D. Only possible when `A` and `B` are the same size

**2.** `A` is 2×4 and `B` is 4×3. What size is `AB`?

A. 2×3
B. 4×4
C. 2×4
D. Cannot multiply

**3.** For matrices, which statement is generally true?

A. `AB = BA`, always
B. `AB` and `BA` can be different matrices
C. `AB` is never defined
D. Matrix multiplication never changes a vector

**4.** What does the identity matrix `I` do when multiplied by a matrix `A`?

A. Doubles `A`
B. Leaves `A` unchanged
C. Turns `A` into a singular matrix
D. Reverses the rows of `A`

**5.** For `A = [[2,0],[0,4]]`, what is `ad - bc`?

A. `0`
B. `2`
C. `6`
D. `8`

**6.** A matrix has `ad - bc = 0`. What does this tell you?

A. The matrix is the identity matrix
B. The matrix has an inverse
C. The matrix is singular; it has no inverse
D. The matrix must be multiplied by itself

**7. (Short answer)** Find the inverse of `A = [[1,1],[0,1]]` and check
your answer by multiplying `A × A⁻¹`.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** Matrix multiplication combines two changes into one, using the row-by-column rule.
2. **A.** `2×3` (rows of `A`, columns of `B`).
3. **B.** Matrix multiplication is not generally commutative; order can change the result.
4. **B.** The identity matrix `I` is the "do nothing" matrix.
5. **D.** `ad - bc = 2×4 - 0×0 = 8`.
6. **C.** `ad - bc = 0` means the matrix is singular, with no inverse.
7. `ad - bc = 1×1 - 1×0 = 1`. `A⁻¹ = [[1,-1],[0,1]]`. Check: `A × A⁻¹ = [[1×1+1×0, 1×-1+1×1],[0×1+1×0, 0×-1+1×1]] = [[1,0],[0,1]] = I` ✓.

# Week 11 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** A diagonal matrix `D` has entries `4` and `2` on its diagonal.
What is `D³`?

A. `[[12, 0], [0, 6]]`
B. `[[64, 0], [0, 8]]`
C. `[[7, 0], [0, 5]]`
D. `[[4, 0], [0, 2]]`, unchanged

**2.** Why is `Dⁿ` so much easier to compute than `Aⁿ` for a general
matrix `A`?

A. `D` is always smaller than `A`
B. Multiplying diagonal matrices never creates cross terms, so each entry just raises to the power `n` on its own
C. `D` has no eigenvalues, so there is nothing to compute
D. `Dⁿ` is only an approximation, so it is faster but less accurate

**3.** In `A = PDP⁻¹`, what do the columns of `P` hold?

A. `A`'s eigenvalues
B. `A`'s eigenvectors
C. A copy of `A` itself
D. The rows of `D`

**4.** A matrix `A` has eigenvalues `7` and `2`. Which one is the
**dominant eigenvalue**, and why does that matter for large `n`?

A. `2`, because smaller numbers are always dominant
B. `7`, because as `n` grows, `7ⁿ` grows far faster than `2ⁿ`, so the `7`-direction controls almost all of the long-run answer
C. Neither; both eigenvalues always matter equally
D. `2`, because it appears second in the list

**5.** A 2×2 matrix has one repeated eigenvalue, and only one
independent eigenvector direction. Is it diagonalizable?

A. Yes, repeated eigenvalues are always fine
B. No, diagonalizing a 2×2 matrix needs 2 independent eigenvector directions
C. Yes, as long as the eigenvalue is not zero
D. Cannot tell without computing `P⁻¹`

**6.** If `A = PDP⁻¹`, what is `A⁵` in terms of `P`, `D`, and `P⁻¹`?

A. `A⁵ = P⁵D⁵P⁻⁵`
B. `A⁵ = PD⁵P⁻¹`
C. `A⁵ = P⁵DP⁻¹`
D. `A⁵ = 5PDP⁻¹`

**7.** Two eigenvectors of `A` point in genuinely different
directions, and neither is a scaled copy of the other. What term
describes this?

A. Similar
B. Diagonal
C. Linearly independent
D. Dominant

**8. (Short answer)** The Campus Café's growth matrix `A` has
eigenvalues `3` and `1`. Without recomputing `P`, `D`, or `P⁻¹`,
explain in one or two sentences why predicting week 20 costs barely
more work than predicting week 6.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** `D³ = [[64, 0], [0, 8]]` — each diagonal entry is cubed on its own: `4³ = 64`, `2³ = 8`.
2. **B.** Diagonal matrices multiply entrywise on the diagonal, with no cross terms mixing in.
3. **B.** `P` is built from `A`'s eigenvectors, placed side by side as columns.
4. **B.** `7` is dominant because it is larger; `7ⁿ` outgrows `2ⁿ` as `n` increases, so it controls the long-run answer.
5. **B.** One independent eigenvector direction is not enough for a 2×2 matrix; it needs two.
6. **B.** `A⁵ = PD⁵P⁻¹` — the middle `P⁻¹P` pairs cancel every time `A` is multiplied by itself.
7. **C.** Linearly independent eigenvectors point in genuinely different directions, none a repeat of another.
8. Once `P`, `D`, and `P⁻¹` are built, predicting any week `n` only needs raising the plain numbers `3` and `1` to the power `n` — going from week 6 to week 20 just means computing `3²⁰` instead of `3⁶`, one extra calculation, not fourteen more rounds of full matrix multiplication.

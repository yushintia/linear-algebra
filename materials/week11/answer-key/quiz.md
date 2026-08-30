## Answer Key

1. **B.** `D³ = [[64, 0], [0, 8]]` — each diagonal entry is cubed on its own: `4³ = 64`, `2³ = 8`.
2. **B.** Diagonal matrices multiply entrywise on the diagonal, with no cross terms mixing in.
3. **B.** `P` is built from `A`'s eigenvectors, placed side by side as columns.
4. **B.** `7` is dominant because it is larger; `7ⁿ` outgrows `2ⁿ` as `n` increases, so it controls the long-run answer.
5. **B.** One independent eigenvector direction is not enough for a 2×2 matrix; it needs two.
6. **B.** `A⁵ = PD⁵P⁻¹` — the middle `P⁻¹P` pairs cancel every time `A` is multiplied by itself.
7. **C.** Linearly independent eigenvectors point in genuinely different directions, none a repeat of another.
8. Once `P`, `D`, and `P⁻¹` are built, predicting any week `n` only needs raising the plain numbers `3` and `1` to the power `n` — going from week 6 to week 20 just means computing `3²⁰` instead of `3⁶`, one extra calculation, not fourteen more rounds of full matrix multiplication.

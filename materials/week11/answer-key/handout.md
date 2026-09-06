## Answer Key

1. `D³ = [[64, 0], [0, 27]]`. (Each diagonal entry is cubed on its own: `4³ = 64`, `3³ = 27`.)
2. `P = [[1, 1], [0, 1]]`, `D = [[5, 0], [0, 2]]`. (Eigenvectors go into `P` as columns, in the same order as their eigenvalues in `D`.)
3. **Yes.** All eigenvalues different from each other always guarantees enough independent eigenvectors.
4. **No.** Diagonalizing a 2×2 matrix needs 2 independent eigenvector directions. One direction is not enough, even though the eigenvalue itself is valid.
5. `A⁴ = PD⁴P⁻¹`. (The middle `P⁻¹P` pairs cancel every time `A` is multiplied by itself.)
6. `6` is dominant, because it is the larger eigenvalue. As `n` grows, `6ⁿ` grows far faster than `2ⁿ`, so the `6`-direction controls almost all of the long-run answer.

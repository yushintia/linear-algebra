## Answer Key

1. **B.** `A = LU`, the product of a lower- and an upper-triangular grid.
2. **B.** `L` always has 1s on its diagonal, by definition.
3. **C.** `U` is what is left after elimination simplifies `A`.
4. **B.** Forward substitution solves `Ly = b` first; back substitution solves `Ux = y` second.
5. **B.** `L` and `U` depend only on `A`, so they can be reused for any new `b`.
6. **B.** If elimination would divide by `0`, swapping rows first (pivoting) avoids the problem.
7. **B. False.** Reusing `L` and `U` skips elimination entirely; only two quick triangular solves are needed.
8. `y1 = 1000`; `0.5(1000) + y2 = 1400 → y2 = 900`; `x2 = 900/2.5 = 360`; `x1 = (1000 − 360)/2 = 320`. So `x1 = 320`, `x2 = 360`. (Check: `2(320) + 360 = 1000` ✓.)

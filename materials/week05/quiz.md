# Week 5 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** LU factorization writes a square grid `A` as:

A. The sum of two grids
B. The product of two triangular grids
C. The difference of two grids
D. A single number

**2.** In `A = LU`, what is always true about the diagonal of `L`?

A. All zeros
B. All 1s
C. All equal to `A`'s diagonal
D. It doesn't matter

**3.** What does `U` represent?

A. The original grid, unchanged
B. The multipliers used during elimination
C. The simplified grid elimination leaves behind
D. The right-hand side, `b`

**4.** When solving `Ax = b` with known `L` and `U`, which step comes
first?

A. Back substitution
B. Forward substitution
C. Re-factoring `A`
D. Pivoting

**5.** A system's left side (`A`) never changes, but the right-hand
side (`b`) changes every day. What should you do?

A. Refactor `A` every day
B. Factor `A` once, then reuse `L` and `U` every day
C. Guess the answer
D. Solve fresh, every single time

**6.** Why might pivoting be needed before factoring?

A. To make the answer larger
B. To avoid dividing by zero during elimination
C. To skip back substitution
D. Pivoting is never needed

**7.** True or false: reusing `L` and `U` for a new `b` still
requires redoing all of elimination.

A. True
B. False

**8. (Short answer)** Using `L = [1, 0; 0.5, 1]` and
`U = [2, 1; 0, 2.5]`, solve for `x` given `b = [1000, 1400]`. Show
your steps.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** `A = LU`, the product of a lower- and an upper-triangular grid.
2. **B.** `L` always has 1s on its diagonal, by definition.
3. **C.** `U` is what is left after elimination simplifies `A`.
4. **B.** Forward substitution solves `Ly = b` first; back substitution solves `Ux = y` second.
5. **B.** `L` and `U` depend only on `A`, so they can be reused for any new `b`.
6. **B.** If elimination would divide by `0`, swapping rows first (pivoting) avoids the problem.
7. **B. False.** Reusing `L` and `U` skips elimination entirely; only two quick triangular solves are needed.
8. `y1 = 1000`; `0.5(1000) + y2 = 1400 → y2 = 900`; `x2 = 900/2.5 = 360`; `x1 = (1000 − 360)/2 = 320`. So `x1 = 320`, `x2 = 360`. (Check: `2(320) + 360 = 1000` ✓.)

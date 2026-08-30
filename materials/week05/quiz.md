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

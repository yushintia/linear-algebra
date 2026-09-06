## Answer Key

1. Multiplier `= 2/4 = 0.5`. Row 2 becomes `[2, 5] − 0.5×[4, 2] = [0, 4]`. So `U = [4, 2; 0, 4]`, `L = [1, 0; 0.5, 1]`.
2. `y1 = 1200`; `0.5(1200) + y2 = 1800 → y2 = 1200`; `x2 = 1200/2.5 = 480 (s)`; `x1 = (1200 − 480)/2 = 360 (m)`. So `m = 360`, `s = 480`.
3. **False.** `L` and `U` come from the left side of the system. A new left side needs a fresh factoring.
4. **Yes.** The top-left entry is `0`. Elimination would need to divide by `0`, so the rows must be swapped first.
5. **3.** A 3-by-3 grid has 3 positions below the diagonal (rows 2 and 3, column 1; row 3, column 2), each holding one multiplier.
6. Factoring the shared left side is the only slow step, and it only has to happen once. Each of the 50 right-hand sides then needs just two quick triangular solves, instead of 50 full eliminations.

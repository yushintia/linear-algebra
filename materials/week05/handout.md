# Week 5 Handout: Factorization

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 5 slides. Keep it. You will use the
glossary and the worked example again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Factor (verb)** | To break one grid of numbers into two simpler grids that, multiplied together, rebuild the original. |
| **Factorization** | The result of factoring: two (or more) grids that multiply back to the original grid. |
| **LU factorization** | Writing a square grid `A` as `A = LU`, one lower-triangular grid times one upper-triangular grid. |
| **Triangular matrix** | A grid of numbers with zeros on one whole side of the diagonal. |
| **Lower triangular (`L`)** | A triangular grid with zeros above the diagonal, and 1s on the diagonal. It stores the elimination multipliers. |
| **Upper triangular (`U`)** | A triangular grid with zeros below the diagonal. It is the simplified grid elimination leaves behind. |
| **Diagonal** | The straight line of positions in a grid running from top-left to bottom-right. |
| **Multiplier** | The number used to scale one row before subtracting it from another, during elimination. |
| **Forward substitution** | Solving a lower-triangular system, `Ly = b`, one row at a time, top to bottom. |
| **Back substitution** | Solving an upper-triangular system, `Ux = y`, one row at a time, bottom to top. |
| **Pivoting** | Swapping two rows before elimination, to avoid dividing by zero. |
| **Right-hand side** | The known totals on the equations' right side, usually called `b`. |
| **Reuse** | Solving a new problem using work already done, instead of starting over. |
| **Operation count** | How many arithmetic steps a method needs. |
| **One-time cost** | Work done only once, no matter how many times the result gets reused. |
| **Repeat cost** | The small, extra work redone every time only the right-hand side changes. |

---

## 2. The Campus Café Recipe, Factored and Reused

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café sells two drinks, Latte and Mocha,
made from the same two ingredients: milk (`m`) and syrup (`s`). The
recipe amounts never change, but the price of milk and syrup changes
almost every day.

```
Latte: 2m + s = (Latte total)
Mocha: m + 3s = (Mocha total)
```

As a grid of numbers, the left side (the recipe) is:

```
A = [ 2  1 ]
    [ 1  3 ]
```

**Step 1 — Factor `A`, once.** Zero out the `1` in row 2 by scaling
row 1 by `0.5` and subtracting:

```
Row 2 = Row 2 − 0.5 × Row 1 = [1, 3] − 0.5×[2, 1] = [0, 2.5]
```

Save the multiplier `0.5` into `L`. The result becomes row 2 of `U`:

```
L = [ 1    0 ]        U = [ 2   1  ]
    [ 0.5  1 ]            [ 0  2.5 ]
```

Check: multiplying `L` by `U` rebuilds `A` exactly. This factoring
never needs to be redone, no matter how many days follow.

**Step 2 — Monday's receipts.** Latte totaled 800 원, Mocha totaled
900 원.

Forward substitution, solve `Ly = b`:

```
y1 = 800
0.5(800) + y2 = 900   →   y2 = 500
```

Back substitution, solve `Ux = y`:

```
2.5(x2) = 500           →   x2 = 200 (s)
2(x1) + 200 = 800        →   x1 = 300 (m)
```

Monday: `m = 300`, `s = 200`. (This matches the Week 1 answer key,
since it is the exact same recipe.)

**Step 3 — Tuesday's receipts changed.** Latte totaled 700 원, Mocha
totaled 1100 원. The recipe grid `A` is unchanged, so `L` and `U` are
reused, with no re-factoring:

```
y1 = 700
0.5(700) + y2 = 1100   →   y2 = 750
2.5(x2) = 750            →   x2 = 300 (s)
2(x1) + 300 = 700         →   x1 = 200 (m)
```

Tuesday: `m = 200`, `s = 300`.

**Step 4 — Wednesday's receipts changed again.** Latte totaled 900
원, Mocha totaled 1200 원. Reuse `L` and `U` a third time:

```
y1 = 900
0.5(900) + y2 = 1200   →   y2 = 750
2.5(x2) = 750            →   x2 = 300 (s)
2(x1) + 300 = 900         →   x1 = 300 (m)
```

Wednesday: `m = 300`, `s = 300`.

**The point.** Three different days, three different answers, one
factoring. Elimination happened exactly once, on Monday.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Myrick Hascall Doolittle worked at the U.S. Coast and Geodetic
Survey in the 1870s, where surveyors solved very similar systems of
equations again and again, one for nearly every pair of survey
stations. In 1878, Doolittle published a method that factored a
grid of numbers once, then reused that factoring for every new
survey, exactly the shortcut this week teaches.

Alan Turing revisited the same idea in 1948, in a paper called
"Rounding-Off Errors in Matrix Processes." Early digital computers
could only store numbers with limited precision, so Turing studied
how small rounding errors build up during factoring and
substitution, and how to keep the method reliable at machine scale.

By the 1970s, LU factorization was built into the first standard
numerical software libraries. Today, when you call a "solve" function
in Python, MATLAB, or almost any engineering software, it is very
likely factoring your grid into `L` and `U` behind the scenes.

### 3.2 Where this shows up in real jobs

- **Structural engineering:** simulating a bridge or building under load factors the same-shaped system once, then reuses it for every test case.
- **Computer graphics:** rendering software reuses a factored setup to move and light thousands of objects, frame after frame.
- **Power grids:** operators check grid stability by resolving a similar-shaped system many times a day, as demand shifts.
- **Weather forecasting:** models resolve a similar-shaped system every few minutes, all day, as new readings arrive.
- **Machine learning:** training and recommendation systems reuse earlier work as new data arrives, instead of starting over.

None of these announce "LU factorization" on the surface. All of
them are reusing one, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Factor `B = [4, 2; 2, 5]` (row 1: `4, 2`; row 2: `2, 5`) into `L` and `U`.
2. Using the Café's `L` and `U` from Section 2, Friday's receipts are: Latte 1200 원, Mocha 1800 원. Find `m` and `s`.
3. True or false: if a system's left side changes, you can still reuse the old `L` and `U`. Explain in one sentence.
4. Does the grid `[0, 1; 1, 2]` need pivoting before elimination? Why or why not?
5. A 3-by-3 grid is factored into `L` and `U`. How many multipliers does `L` store below its diagonal?
6. A system is solved fresh, from scratch, 50 times, once for each of 50 new right-hand sides that all share the same left side. In one or two sentences, explain why factoring once would save time.

### Answers

1. Multiplier `= 2/4 = 0.5`. Row 2 becomes `[2, 5] − 0.5×[4, 2] = [0, 4]`. So `U = [4, 2; 0, 4]`, `L = [1, 0; 0.5, 1]`.
2. `y1 = 1200`; `0.5(1200) + y2 = 1800 → y2 = 1200`; `x2 = 1200/2.5 = 480 (s)`; `x1 = (1200 − 480)/2 = 360 (m)`. So `m = 360`, `s = 480`.
3. **False.** `L` and `U` come from the left side of the system. A new left side needs a fresh factoring.
4. **Yes.** The top-left entry is `0`. Elimination would need to divide by `0`, so the rows must be swapped first.
5. **3.** A 3-by-3 grid has 3 positions below the diagonal (rows 2 and 3, column 1; row 3, column 2), each holding one multiplier.
6. Factoring the shared left side is the only slow step, and it only has to happen once. Each of the 50 right-hand sides then needs just two quick triangular solves, instead of 50 full eliminations.

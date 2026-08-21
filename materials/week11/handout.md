# Week 11 Handout: Diagonalization

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 11 slides. Keep it. You will use the
glossary and the worked example again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Diagonal matrix** | A matrix with nonzero numbers only on the line from top-left to bottom-right. Every other entry is zero. |
| **Diagonalizable** | A matrix that can be rewritten using its own eigenvectors, so repeating it becomes easy. |
| **Similar matrices** | Two matrices that describe the same transformation, viewed from different directions. |
| **Matrix power** | A matrix multiplied by itself, a chosen number of times, written `Aⁿ`. |
| **Eigenbasis** | A set of eigenvectors used as a new set of directions to measure from. |
| **Eigenvector matrix (P)** | A matrix's eigenvectors, placed side by side as columns. |
| **Eigenvalue matrix (D)** | A diagonal matrix holding the matching eigenvalues, in the same column order as `P`. |
| **Change of basis** | Describing the same vectors using a different set of directions. |
| **Linearly independent** | Eigenvectors that point in genuinely different directions; none is a repeat, or scaled copy, of another. |
| **Growth rate** | How much a quantity multiplies by, each round. |
| **Dominant eigenvalue** | The largest eigenvalue. It controls long-run growth the most. |
| **Long-run prediction** | The result after applying a transformation many, many times. |

---

## 2. The Campus Café's Loyalty Program, Solved Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café tracks two groups of regulars every
week: Classic-drink fans (`c`) and Vanilla-drink fans (`v`). Word of
mouth grows both groups the same way, week after week. Starting
counts: `c₀ = 30`, `v₀ = 10`.

**Where does the café come from?** The Campus Café is not a real
place — it is a running example invented for this course, and its
numbers are chosen to work out evenly. What is real is the method:
every step below is the general procedure you will use all semester
on any diagonalizable matrix, following Lay, Lay & McDonald, Ch. 5.3.

**Step 1 — Write the growth matrix.**

```
A = [ 2  1 ]
    [ 1  2 ]
```

Each week's counts come from last week's counts, multiplied by `A`.

**Step 2 — Find the eigenvalues and eigenvectors.**

Using last week's method (`det(A - λI) = 0`, then `(A - λI)v = 0` for
each `λ`) gives:

- `λ₁ = 3`, eigenvector `(1, 1)`
- `λ₂ = 1`, eigenvector `(1, -1)`

**Step 3 — Build P, D, and P⁻¹.**

Place the eigenvectors as columns of `P`, in the same order as their
eigenvalues in `D`:

```
P = [ 1   1 ]     D = [ 3  0 ]     P⁻¹ = [ 1/2   1/2 ]
    [ 1  -1 ]         [ 0  1 ]           [ 1/2  -1/2 ]
```

Check: `A = PDP⁻¹`. You can verify this by multiplying the three
matrices back together, or by checking `AP = PD` column by column.

**Step 4 — Use the shortcut formula.**

For any week `n`:

```
xₙ = P Dⁿ P⁻¹ x₀
```

`Dⁿ` only needs `3ⁿ` and `1ⁿ` — no repeated matrix multiplication.

**Step 5 — Predict week 6.** `3⁶ = 729`, `1⁶ = 1`. Working through
the formula:

```
x₆ = (14590, 14570)
```

**Step 6 — Check, the slow way.** Multiplying `A` by itself six
times, one round at a time, lands on the exact same answer:
`(14590, 14570)`. Both ways agree — but the slow way took six full
matrix multiplications, and the fast way took one power of `3`.

**Step 7 — Predict much further, for free.** Week 20 just needs
`3²⁰ ≈ 3.49 billion`, one calculation. The slow way would need twenty
full rounds of matrix multiplication. This is the entire payoff of
diagonalization: the hard work (finding `P`, `D`, and `P⁻¹`) happens
once, and after that, any number of weeks costs the same, small
amount of extra work.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Augustin-Louis Cauchy proved, in 1829, that a spinning rigid body
always has three special axes along which its motion is pure
stretching, with no rotation mixed in. These are called principal
axes, and finding them is exactly the same problem as diagonalizing a
matrix: find the directions where a transformation is simple, and
describe everything else in terms of them.

Not every matrix cooperates. In 1870, Camille Jordan worked out what
to do with matrices that resist diagonalization — matrices with
repeated eigenvalues and too few independent eigenvectors. His
"Jordan form" is the closest thing to a diagonal matrix that such a
matrix can be rewritten as. You will not need Jordan form in this
course, but it is good to know the gap has a name and a known fix.

Andrey Markov, in 1907, studied chains of repeated random steps —
what happens if you keep applying the same "next state" rule forever.
Diagonalization is exactly the tool that makes predicting the
long-run behavior of such a chain fast, instead of simulating step by
step.

### 3.2 Where this shows up in real jobs

- **Search ranking:** Google's original PageRank algorithm ranks web pages by repeating one "follow a link" step across billions of pages, over and over, until the ranking stops changing. Diagonalization (and closely related methods) is what makes computing that limit fast.
- **Population and ecology models:** biologists predict how age groups in a population change over many years using a growth matrix, then diagonalize it to jump straight to "50 years from now" instead of simulating year by year.
- **Computer animation:** applying the same transformation matrix once per video frame, for thousands of frames, is only fast because of exactly this shortcut.
- **Structural engineering:** predicting how a bridge or building vibrates under repeated stress uses the same "find the special directions, then reuse them" idea.
- **Machine learning:** some models repeatedly apply the same weight matrix (for example, in certain recurrent neural networks); understanding whether repeated applications grow, shrink, or stay stable depends on eigenvalues, exactly as in this week's café example.

None of these show you "diagonalize this matrix" on the surface. All
of them rely on it, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. A diagonal matrix is `D = [[4, 0], [0, 3]]`. What is `D³`?
2. A matrix `A` has eigenvalues `5` and `2`, with eigenvectors `(1, 0)` and `(1, 1)`. Write out `P` and `D`.
3. A 3×3 matrix has three different eigenvalues: `2`, `5`, and `-1`. Is it diagonalizable? Why or why not?
4. A 2×2 matrix has one repeated eigenvalue, `4`, but only one independent eigenvector direction. Is it diagonalizable?
5. If `A = PDP⁻¹`, what is `A⁴` in terms of `P`, `D`, and `P⁻¹`?
6. A matrix has eigenvalues `6` and `2`. Which one is the dominant eigenvalue, and why does that matter for large `n`?

### Answers

1. `D³ = [[64, 0], [0, 27]]`. (Each diagonal entry is cubed on its own: `4³ = 64`, `3³ = 27`.)
2. `P = [[1, 1], [0, 1]]`, `D = [[5, 0], [0, 2]]`. (Eigenvectors go into `P` as columns, in the same order as their eigenvalues in `D`.)
3. **Yes.** All eigenvalues different from each other always guarantees enough independent eigenvectors.
4. **No.** Diagonalizing a 2×2 matrix needs 2 independent eigenvector directions. One direction is not enough, even though the eigenvalue itself is valid.
5. `A⁴ = PD⁴P⁻¹`. (The middle `P⁻¹P` pairs cancel every time `A` is multiplied by itself.)
6. `6` is dominant, because it is the larger eigenvalue. As `n` grows, `6ⁿ` grows far faster than `2ⁿ`, so the `6`-direction controls almost all of the long-run answer.

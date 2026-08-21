---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 11: Diagonalization

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "Has anyone tried predicting something 10 steps ahead by
hand, and given up partway?" That frustration is today's hook.
-->

---

<!-- SLOT 2: Where we are (Act 0 / LOCATE) -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
<div class="wk"><div class="n">Wk 5</div><div class="t">Factorization</div></div>
<div class="wk"><div class="n">Wk 6</div><div class="t">Determinants</div></div>
<div class="wk"><div class="n">Wk 7</div><div class="t">Vector Spaces · Quiz 1</div></div>
<div class="wk review"><div class="n">Wk 8</div><div class="t">Midterm Exam</div></div>
<div class="wk"><div class="n">Wk 9</div><div class="t">Bases, Dimension</div></div>
<div class="wk"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk now"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One line: last week we found stretch directions one at a time; this week we reuse them, all at once, forever. -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE) -->

# Last Week, This Week

- **Last week delivered:** eigenvalues reveal the directions a transformation only stretches, one direction at a time
- **Last week left broken:** repeating that transformation many times by hand is still impractical

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), restates Week 10's Limit almost verbatim -->

# A Method That Still Does Not Scale

<div class="pain">

Eigenvalues reveal stretch directions one at a time, but repeating a
transformation many times by hand is still impractical.

The Campus Café wants to predict how its loyalty numbers change, week
after week, for a long time. Last week's method finds the stretch
directions once. But predicting week 6, or week 20, still means
multiplying the same matrix by itself, over and over, by hand.

Nobody on staff wants to redo that multiplication twenty times.

</div>

<!-- notes: This is Week 10's closing slide, restated as this week's opening problem. Let it land before moving on. -->

---

# Repeating By Hand Gets Worse Every Round

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">Predict 1 week ahead</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">one multiplication, fine</div>
</div>
<div class="bar-row">
  <div class="bar-label">Predict 6 weeks ahead</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 55%"></div></div>
  <div class="bar-value">six rounds, slow and error-prone</div>
</div>
<div class="bar-row">
  <div class="bar-label">Predict 20 weeks ahead</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">twenty rounds, nobody does this by hand</div>
</div>
</div>

Multiplying a matrix by itself many times does not scale. This week
finds a shortcut.

<!-- notes: Let the widening bars sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing (Act 1 / MOTIVATE) -->

# What This Actually Costs

- Recomputing next week's numbers from scratch wastes staff time, every single week
- A forecast that only reaches one week ahead is not a forecast at all
- Any system that repeats a transformation thousands of times grinds to a halt without a shortcut

<div class="why">
<strong>In industry:</strong> fast repeated transformations power search
ranking, population forecasting, and real-time computer graphics.
Interviewers often ask how to compute a matrix raised to a large power
quickly.
</div>

---

# Same Idea, Many Fields

<div class="appgrid">
<div class="app"><div class="name">Search ranking</div><div class="desc">Ranks billions of web pages by repeating one link-following step, many times over</div></div>
<div class="app"><div class="name">Population models</div><div class="desc">Predicts species or population counts many generations ahead, not just one</div></div>
<div class="app"><div class="name">Computer animation</div><div class="desc">Applies the same transformation again, once for every single video frame</div></div>
</div>

<!-- notes: One line: same shape as the café problem, bigger stakes. -->

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we make repeating a transformation many times fast?"</div>

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

1. Explain why a diagonal matrix is easy to raise to a power
2. Build a diagonalizing matrix from a set of eigenvectors
3. Diagonalize a matrix and use it to compute a fast matrix power
4. Tell whether a matrix can be diagonalized at all

---

<!-- NEW: Key Words for 차시 1 (Simplification Rule 2) -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Diagonal matrix:** a matrix with numbers only on the line from top-left to bottom-right, zeros everywhere else
- **Diagonalizable:** a matrix that can be rewritten using its own eigenvectors, so repeating it becomes easy
- **Similar matrices:** two matrices that describe the same transformation, viewed from different directions
- **Matrix power:** a matrix multiplied by itself, a chosen number of times
- **Eigenbasis:** a set of eigenvectors used as a new set of directions to measure from

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who first proved this shortcut exists?</div>

---

<!-- NEW: Key Words for 차시 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Eigenvector matrix (P):** a matrix's eigenvectors, placed side by side as columns
- **Eigenvalue matrix (D):** a diagonal matrix holding the matching eigenvalues, in the same column order
- **Change of basis:** describing the same vectors using a different set of directions
- **Linearly independent:** eigenvectors that point in genuinely different directions, none a repeat of another

---

# Recap: Finding Eigenvalues and Eigenvectors

<div class="thread">Before diagonalizing anything, we reuse last week's exact method.</div>

```
det(A - λI) = 0      solve for every eigenvalue λ
(A - λI)v = 0         solve for that eigenvalue's eigenvector v
```

- Every eigenvalue needs its own pass through this second step
- This week does not repeat that search; it reuses the answers directly

---

<!-- SLOT 8: Origin -->

# This Shortcut Is Not New

<div class="thread">You just felt this pain. One mathematician felt it too, nearly 200 years ago.</div>

- **1829, France:** Augustin-Louis Cauchy proves a spinning rigid body always has three special, unrotated axes
- Along those axes, the body's motion is just stretching, easy to describe and repeat
- **1870, France:** Camille Jordan works out what to do when a matrix has no full set of these directions

<div class="why">
Different problem, same shape: find the directions where a change is
simple, then reuse them instead of repeating the whole calculation.
</div>

---

# From Spinning Bodies to Ranking the Web

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1829</div><div class="d">Cauchy<br>rotating bodies, principal axes</div></div>
<div class="pt"><div class="dot"></div><div class="y">1870</div><div class="d">Jordan<br>handles matrices that resist this</div></div>
<div class="pt"><div class="dot"></div><div class="y">1907</div><div class="d">Markov<br>repeated steps predict future states</div></div>
<div class="pt"><div class="dot"></div><div class="y">1998</div><div class="d">Google PageRank<br>repeats one step, billions of times</div></div>
</div>

Nearly 200 years later, the same shortcut ranks the entire web.

---

<!-- SLOT 9: Core concept -->

# Diagonal Matrix & Diagonalization: Definition

<div class="thread">Now the exact, formal definitions.</div>

> A **diagonal matrix** has nonzero numbers only on its main diagonal;
> every other entry is zero.
>
> A square matrix `A` is **diagonalizable** if it can be written as
> `A = PDP⁻¹`, where `D` is diagonal and `P` is built from `A`'s
> eigenvectors.

- `D` holds `A`'s eigenvalues, in the same order as `P`'s columns
- Not every matrix is diagonalizable; this week teaches how to tell

---

<!-- Act 3 / BUILD -->

# Why a Diagonal Matrix Is Easy to Raise to a Power

<div class="thread">One fact does most of this week's work.</div>

Multiplying two diagonal matrices only multiplies matching diagonal
entries. Nothing else ever mixes in:

```
D = [ 2  0 ]     D² = [ 4   0 ]     D³ = [ 8    0 ]
    [ 0  5 ]          [ 0  25 ]          [ 0  125 ]
```

For any diagonal matrix, `Dⁿ` just raises each diagonal entry to the
power `n`. No cross terms, ever.

---

# Building P From Eigenvectors

<div class="thread">If a diagonal matrix is this easy, the goal is clear: get every matrix to look diagonal.</div>

Take a matrix `A`'s eigenvectors, and place them side by side as the
columns of a new matrix `P`:

```
eigenvector for λ₁, then eigenvector for λ₂, ... side by side

P = [ v₁  v₂  ...  vₙ ]
```

Put the matching eigenvalues on the diagonal of `D`, in that same
column order. `P` and `D` are now a matched pair.

---

# The Diagonalization Formula: A = PDP⁻¹

<div class="thread">P and D combine to rebuild A itself.</div>

<div class="stack">
<div class="layer view"><div class="h">P</div><div class="s">A's eigenvectors, as columns</div></div>
<div class="layer logical"><div class="h">D</div><div class="s">A's eigenvalues, on the diagonal</div></div>
<div class="layer physical"><div class="h">P⁻¹</div><div class="s">undoes P, switches back to A's own directions</div></div>
</div>

```
A = P · D · P⁻¹
```

Applying `P⁻¹`, then `D`, then `P`, has the exact same effect as
applying `A` once.

---

# Why This Makes Powers Fast: Aⁿ = PDⁿP⁻¹

<div class="thread">Multiply `A` by itself, and the middle `P⁻¹P` pair cancels every time.</div>

```
A² = (PDP⁻¹)(PDP⁻¹) = PD(P⁻¹P)DP⁻¹ = PD·I·DP⁻¹ = PD²P⁻¹
```

The same cancelling happens for any power `n`:

```
Aⁿ = PDⁿP⁻¹
```

Instead of multiplying full matrices `n` times, we only raise a few
plain numbers to the power `n`. That is the whole shortcut.

---

# Two Ways to Compute a Power

<div class="thread">Same final answer, two very different amounts of work.</div>

<div class="pipeline">
<div class="stage"><div class="h">Direct</div><div class="s">Multiply A by itself, one round at a time, n separate times</div></div>
<div class="arrow">vs</div>
<div class="stage"><div class="h">Diagonalized</div><div class="s">Build P and D once, then raise two plain numbers to the power n</div></div>
</div>

The diagonalized path does its hard work only once. Growing `n`
larger costs almost nothing extra.

---

# Not Every Matrix Is Diagonalizable

<div class="thread">The shortcut needs one more condition, checked first.</div>

`A` is diagonalizable only if it has a full set of linearly
independent eigenvectors, one genuinely new direction per row.

```
A = [ 2  1 ]
    [ 0  2 ]
```

This matrix has only one eigenvalue, `2`, repeated. But it has only
**one** independent eigenvector direction, not two. It cannot be
diagonalized.

---

# Diagonalizable vs Not: Quick Check

| Situation | Diagonalizable? |
|---|---|
| All eigenvalues different from each other | Always yes |
| A repeated eigenvalue, with enough independent eigenvectors | Yes |
| A repeated eigenvalue, with too few independent eigenvectors | No |

Always count independent eigenvectors first. Skipping this check is
the fastest way to build a wrong `P`.

---

# Diagonalizing a Matrix: The Checklist

<div class="thread">Five steps turn any diagonalizable matrix into fast powers.</div>

1. Find every eigenvalue of `A`
2. Find one eigenvector for each eigenvalue
3. Check there are enough independent eigenvectors
4. Build `P` from the eigenvectors, `D` from the eigenvalues, in matching order
5. Compute `P⁻¹`; now `A = PDP⁻¹`, and `Aⁿ = PDⁿP⁻¹` for any `n`

---

<!-- NEW: Try It, hands off to Worksheet Part A (Simplification Rule 4) -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week11/worksheet.html">Worksheet Part A</a>.</div>

You get a small matrix, its eigenvalues, and its eigenvectors already
found.

Build `P` and `D`, then check that `A = PDP⁻¹` really holds.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to compute A² two ways: directly, and using PD²P⁻¹, and compare. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: back to the café, predicting many weeks ahead.</div>

---

<!-- NEW: Key Words for 차시 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Growth rate:** how much a quantity multiplies by, each round
- **Dominant eigenvalue:** the largest eigenvalue; it controls long-run growth the most
- **Long-run prediction:** the result after applying a transformation many, many times

---

<!-- SLOT N-2: Worked example -->

# Case Study: The Café's Loyalty Program (1/5)

<div class="thread">Back to the café. Let's make the many-week prediction fast, for real.</div>

The café tracks two groups each week: Classic-drink fans (`c`) and
Vanilla-drink fans (`v`). Word of mouth grows both groups this way:

```
A = [ 2  1 ]
    [ 1  2 ]
```

Using last week's method on this matrix gives eigenvalues `3` and
`1`, with eigenvectors `(1, 1)` and `(1, -1)`.

<!-- notes: The Campus Café is invented; its numbers are picked to come
out even. Remind students the story is fictional, the method is the
real, general one they will use on any diagonalizable matrix. -->

---

# Case Study: The Café's Loyalty Program (2/5)

**Build P, D, and P⁻¹.** Place the eigenvectors as columns of `P`,
the eigenvalues on the diagonal of `D`, in matching order:

```
P = [ 1   1 ]     D = [ 3  0 ]     P⁻¹ = [ 1/2   1/2 ]
    [ 1  -1 ]         [ 0  1 ]           [ 1/2  -1/2 ]
```

This week, this replaces `A` for every future calculation.

---

# Case Study: The Café's Loyalty Program (3/5)

**Predict week 6, the fast way.** Start at `c₀ = 30`, `v₀ = 10`.
Diagonalization gives a direct formula:

```
xₙ = P Dⁿ P⁻¹ x₀
```

`Dⁿ` only needs `3ⁿ` and `1ⁿ`. For `n = 6`: `3⁶ = 729`, `1⁶ = 1`.
Working through the formula gives:

```
x₆ = (14590, 14570)
```

One power of `3`, not six rounds of matrix multiplication.

---

# Case Study: The Café's Loyalty Program (4/5)

**Which eigenvalue wins in the long run?** Compare how `3ⁿ` and `1ⁿ`
grow, week by week:

```
3ⁿ:  3, 9, 27, 81, 243, 729, ...   keeps growing
1ⁿ:  1, 1,  1,  1,   1,   1, ...   never changes
```

`3` is the **dominant eigenvalue**: the larger `n` gets, the more it
controls the answer. The `1` direction barely matters after a few
weeks.

---

# Case Study: The Café's Loyalty Program (5/5)

**Check, the slow way.** Multiplying `A` by itself six times, one
round at a time, lands on the same answer: `(14590, 14570)`.

Both ways agree. But the slow way took six full matrix
multiplications. The fast way took one power of `3`.

```
Week 20, the fast way: just 3²⁰ ≈ 3.49 billion, one calculation
Week 20, the slow way: twenty full rounds of matrix multiplication
```

No staff member wants to do the slow way twenty times.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week11/worksheet.html">Worksheet Part B</a>.</div>

Diagonalize a new matrix from scratch: find eigenvalues, eigenvectors,
then `P`, `D`, and `P⁻¹`.

Use it to predict a value several rounds ahead, the fast way.

You have about 15 minutes.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

- **Assuming every matrix is diagonalizable:** always count independent eigenvectors first; a repeated eigenvalue is a warning sign, not an automatic stop
- **Mismatching P and D's column order:** each column of `P` must line up with its own eigenvalue in `D`, in the same position
- **Multiplying `A` by itself anyway:** once `P`, `D`, and `P⁻¹` exist, use `PDⁿP⁻¹`; recomputing by hand defeats the entire point

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Why is `Dⁿ` so much easier to compute than `Aⁿ` directly?
2. A 2×2 matrix has one repeated eigenvalue, and only one independent eigenvector direction. Is it diagonalizable?

---

# Answers

1. **Because `D` is diagonal.** Multiplying diagonal matrices never creates cross terms, so each entry just raises to the power `n` on its own.
2. **No.** Diagonalizing an `n × n` matrix needs `n` independent eigenvector directions. One direction is not enough for a 2×2 matrix.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week11/quiz.html">Week 11 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 12 slot 4 -->

# What Diagonalization Cannot Do Yet

<div class="limits">
Diagonalization makes repeated transformations fast, but only
measures stretching, not angle or distance. Raising eigenvalues to a
power replaces raising a whole matrix to a power, so the café's
loyalty numbers now grow correctly, for any number of weeks. But
eigenvalues never say how far apart two customer patterns really are,
or what angle separates two directions. We can predict growth. We
still cannot measure distance.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 11 leaves one thing unsolved: **angle and distance are still
unmeasured.** **Week 12, Orthogonality**, addresses it. It gives us a
way to measure both, exactly.

---

<!-- SLOT 16: Summary -->

# Summary

- A diagonal matrix's power is trivial: just raise each diagonal entry, no cross terms
- `A = PDP⁻¹` rewrites `A` using its own eigenvectors; then `Aⁿ = PDⁿP⁻¹` makes any power fast
- Not every matrix is diagonalizable; it needs a full set of independent eigenvectors
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 5.3
- **Handout:** [materials/week11/handout.md](materials/week11/handout.html), glossary and the full café walkthrough
- **Reminder:** Assignment 2 is due this week
- **Prepare:** think of one situation where you would want to measure distance or angle between two vectors; bring it to Week 12

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You

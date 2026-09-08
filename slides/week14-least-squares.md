---
marp: true
theme: shintia
paginate: true
math: katex
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 14: Least Squares · Quiz 2

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · Room 610
</div>

<!--
notes: Remind students Quiz 2 happens near the end of today's third
session. It is short and covers Weeks 9-14. Today is the semester's
payoff: fitting a real line to real, noisy data.
-->

---

<!-- SLOT 2: Where we are -->

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
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk now"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: today we finally fit a line to messy, real data. This is the semester's payoff. -->

---

<!-- SLOT 3: Recap + open wound -->

# Last Week, This Week

- **Last week delivered:** projection finds the closest point in a subspace to a point outside it
- **Last week left broken:** real data rarely has an exact solution to project onto

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# No Line Fits Every Cup

<div class="pain">

The Campus Café ran a real taste test. Five customers each tried a
cup with a different amount of syrup. Each customer rated the taste
from 1 to 10.

The owner expects a clear pattern: more syrup, higher rating. Staff
plot the five results on paper and try to draw one straight line
through all five points.

No straight line touches every point. One rating is a little high,
another a little low. Every line staff try misses at least one cup.

The owner asks: "Just give me the one line that best matches what
customers said." Nobody knows which line counts as "best."

</div>

<!-- notes: Do not say "least squares" or "regression" yet. Let the
frustration of "no line fits" sit before naming anything. -->

---

# Real Data Never Lines Up Perfectly

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">Points a hand-drawn line misses</div>
  <div class="bar-track"><div class="bar-fill risk-high" style="width: 80%"></div></div>
  <div class="bar-value">4 of 5 cups, off the line</div>
</div>
<div class="bar-row">
  <div class="bar-label">Lines two staff members drew</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 50%"></div></div>
  <div class="bar-value">2 different lines, both "close"</div>
</div>
<div class="bar-row">
  <div class="bar-label">Agreed single best line, by feel</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 10%"></div></div>
  <div class="bar-value">none, no rule to pick one</div>
</div>
</div>

Eyeballing a line gives a different answer every time. This week
gives one exact rule for the single best line.

<!-- notes: Let the near-empty last bar sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Two staff draw two different "best" lines from the same data, and disagree on the answer
- A scientist who cannot fit noisy measurements to a model cannot trust any prediction from it
- A company that cannot summarize noisy survey data into one trend cannot act on it with confidence

<div class="why">
<strong>In industry:</strong> fitting the best line, or curve, to
noisy data sits behind trend forecasting and sensor calibration. It
is also the core training step in most machine learning models. "Fit
this data" is a common data science interview question.
</div>

---

# One Idea, Many Fields

<div class="appgrid">
<div class="app"><div class="name">Data science</div><div class="desc">Fits a trend line to noisy sales, traffic, or survey data</div></div>
<div class="app"><div class="name">Sensor calibration</div><div class="desc">Fits a clean reading to a sensor's noisy raw output</div></div>
<div class="app"><div class="name">Machine learning</div><div class="desc">Trains many models by minimizing the same kind of squared error</div></div>
</div>

<!-- notes: One line: same shape as the café's taste-test problem, bigger stakes. -->

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we find the single best-fitting line through noisy data that has no exact solution?"</div>

---

<!-- NEW: Key Words for Session 1 -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Noisy data:** real measurements that do not exactly follow any clean pattern
- **Best fit:** the line that comes closest to every data point overall
- **Residual:** the gap between one actual point and the line's prediction for it
- **Error:** another word for residual, the amount a prediction misses by
- **Least squares:** picking the line that makes the sum of squared residuals as small as possible

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

<div class="cardlist">
<div class="card"><div class="h">No Exact Solution</div><div class="d">Explain why noisy data has no exact linear solution</div></div>
<div class="card"><div class="h">Normal Equations</div><div class="d">Set up the normal equations for a best-fit line</div></div>
<div class="card"><div class="h">Solve for Slope &amp; Intercept</div><div class="d">Solve the normal equations for a slope and an intercept</div></div>
<div class="card"><div class="h">Fit a Line</div><div class="d">Fit a line to real, noisy Campus Café taste-test data</div></div>
</div>

---

<!-- NEW: preview hook, ends Session 1 -->

# Coming Up: Worksheet Part A

Next session, you set up and start solving a small least-squares
problem, in pairs.

You will fit a line to five noisy data points, the same shape as
today's café example.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- NEW: Key Words for Session 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Overdetermined system:** more equations (data points) than unknowns, usually with no exact solution
- **Design matrix:** the matrix $A$ built from the input data, one row per point
- **Normal equations:** the system $A^T A \hat{x} = A^T b$, solved to find the best fit
- **Sum of squared residuals:** the total error a least-squares line minimizes

---

<!-- SLOT 8: Origin -->

# This Problem Is Not New

<div class="thread">You just felt this pain. Two mathematicians raced to solve it, over 200 years ago.</div>

- **1805, France:** Adrien-Marie Legendre publishes the least-squares method, in a book about comet orbits
- **1809, Germany:** Carl Friedrich Gauss claims he used the same method since 1795. He uses it to predict the dwarf planet Ceres' orbit from a few noisy telescope readings

<div class="why">
This is the same Gauss, and almost the same story, from Week 1's
origin slide. There, exact elimination solved a clean system.
Here, noisy real measurements need a different tool: the best
approximate answer, not an exact one.
</div>

---

# From Exact Answers to Best Approximations

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1805</div><div class="d">Legendre<br>publishes least squares first</div></div>
<div class="pt"><div class="dot"></div><div class="y">1809</div><div class="d">Gauss, Ceres' orbit<br>predicts it from noisy data</div></div>
<div class="pt"><div class="dot"></div><div class="y">1900s</div><div class="d">Statistics<br>least squares becomes regression</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Machine learning<br>the same idea trains most models</div></div>
</div>

Two centuries later, the same rule still finds the best line through
noisy data.

---

<!-- SLOT 9: Core concept -->

# Least-Squares Solution: Definition

<div class="thread">Now the exact, formal definition.</div>

> For $Ax = b$ with no exact solution, the **least-squares solution**
> $\hat{x}$ makes $A\hat{x}$ as close as possible to $b$. It minimizes the sum of
> squared residuals, the squared length of $b - A\hat{x}$.

- $\hat{x}$ solves the **normal equations**:

$$
A^T A \hat{x} = A^T b
$$

- This is exactly last week's projection, applied to a system with no exact answer

---

<!-- Act 3 / BUILD -->

# When Ax = b Has No Solution

<div class="thread">Five points, two unknowns (slope and intercept): more facts than unknowns.</div>

Five data points give five equations, but a line has only two
unknowns: slope and intercept. This is an **overdetermined system**.

$b$, the column of five actual ratings, almost never sits exactly in
the column space of $A$. No $x$ makes $Ax$ equal $b$ exactly.

We cannot solve $Ax = b$ exactly. We can still ask for the closest
possible answer.

---

# Reusing Last Week's Idea: Projection

<div class="thread">This week does not need a new tool. It reuses last week's, on a harder target.</div>

Last week, projecting $b$ onto a subspace gave the closest point $p$
in that subspace. The leftover, $b - p$, was orthogonal to it.

Here, the subspace is the column space of $A$. The closest reachable
point is $p = A\hat{x}$, for the best $\hat{x}$ we can find.

$b - A\hat{x}$, the leftover residual, must be orthogonal to every column
of $A$.

---

# The Normal Equations

<div class="thread">One orthogonality condition, turned into a solvable system.</div>

"Orthogonal to every column of $A$" means:

$$
A^T(b - A\hat{x}) = 0
$$

Expand and rearrange:

$$
A^T A \hat{x} = A^T b
$$

This is the **normal equations**. Solve this smaller, always-solvable
system instead of the original, unsolvable one.

---

# The Normal Equations in Matrix Form: A Closer Look

<div class="thread">One reason this system is always solvable, unlike the original.</div>

$A^T A$ is always a square matrix, $n \times n$ for $n$ unknowns, no matter
how many rows $A$ itself has. As long as $A$'s columns are linearly
independent, $A^T A$ is invertible, and the normal equations have
exactly one solution.

---

# Worked Example: Normal Equations From Scratch (1/4)

<div class="thread">A tiny 3-point data set, walked through the matrix form directly.</div>

Fit a line to $(1, 2)$, $(2, 3)$, $(3, 5)$:

$$
A = \begin{bmatrix} 1 & 1 \\ 1 & 2 \\ 1 & 3 \end{bmatrix} \qquad b = \begin{bmatrix} 2 \\ 3 \\ 5 \end{bmatrix}
$$

---

# Worked Example: Normal Equations From Scratch (2/4)

Compute $A^T A$ and $A^T b$ directly, by matrix multiplication:

$$
A^T A = \begin{bmatrix} 3 & 6 \\ 6 & 14 \end{bmatrix} \qquad A^T b = \begin{bmatrix} 10 \\ 23 \end{bmatrix}
$$

Same numbers Week 14's summation shortcut would give: $n=3$, $\sum x=6$,
$\sum x^2=14$, $\sum y=10$, $\sum xy=23$.

---

# Worked Example: Normal Equations From Scratch (3/4)

Solve $A^T A \hat{x} = A^T b$:

$$
\begin{bmatrix} 3 & 6 \\ 6 & 14 \end{bmatrix} \begin{bmatrix} b \\ m \end{bmatrix} = \begin{bmatrix} 10 \\ 23 \end{bmatrix}
$$

Row reduction gives $b = 0.333$, $m = 1.5$. Best-fit line:
$y = 0.333 + 1.5x$.

---

# Worked Example: Normal Equations From Scratch (4/4)

Check the residuals:

$$
\begin{aligned}
x=1&: \text{ predicted } 1.833 \text{, actual } 2 \text{, residual } \phantom{-}0.167 \\
x=2&: \text{ predicted } 3.333 \text{, actual } 3 \text{, residual } -0.333 \\
x=3&: \text{ predicted } 4.833 \text{, actual } 5 \text{, residual } \phantom{-}0.167
\end{aligned}
$$

No residual is zero, but this line minimizes their squared sum, over
every possible line.

---

# Why Residuals Sum to Zero (With an Intercept)

<div class="thread">One elegant fact, true whenever a line includes an intercept term.</div>

Add up the worked example's residuals:

$$
0.167 + (-0.333) + 0.167 = 0.001 \approx 0
$$

Whenever a fitted line includes an intercept (the column of 1s), the
residuals always sum to (almost exactly) zero. Positive and negative
misses balance out, by construction of the normal equations.

---

# Setting Up the Design Matrix for a Line

<style scoped>
.thread p, .s p, .d p { margin: 0; }
</style>

<div class="thread">

Now apply this to fitting $\text{rating} = b + m \cdot \text{syrup}$.

</div>

Unknowns: intercept $b$, slope $m$. Each data point $(x_i, y_i)$ gives
one row of the **design matrix** $A$ and one entry of $b$:

$$
A = \begin{bmatrix} 1 & x_1 \\ 1 & x_2 \\ 1 & x_3 \\ \vdots & \vdots \end{bmatrix} \qquad b = \begin{bmatrix} y_1 \\ y_2 \\ y_3 \\ \vdots \end{bmatrix}
$$

The column of 1s picks out the intercept; the $x$ column picks out
the slope.

---

# Solving for Slope and Intercept

<div class="thread">Two unknowns, two normal equations. Always solvable.</div>

For a line, the normal equations reduce to:

$$
\begin{aligned}
n \cdot b + (\textstyle\sum x) \cdot m &= \sum y \\
(\textstyle\sum x) \cdot b + (\textstyle\sum x^2) \cdot m &= \sum xy
\end{aligned}
$$

$n$ is the number of points, and each $\sum$ sums over all data points.
Solve this 2x2 system for $b$ and $m$, exactly like Week 1's method.

---

# From Two Points to a Line: The Trivial Case

<div class="thread">One edge case is worth naming before moving to real, messier data.</div>

With exactly 2 data points, a line has exactly enough freedom to pass
through both exactly. The normal equations still work, but every
residual comes out zero: no approximation was needed at all.

Least squares only shows its real value once there are more points
than a line can satisfy exactly.

---

# Least Squares Also Works for Curves

<div class="thread">The method is not limited to straight lines.</div>

Adding an $x^2$ column to the design matrix fits a parabola instead of
a line, using the exact same normal equations:

$$
A = \begin{bmatrix} 1 & x_1 & x_1^2 \\ 1 & x_2 & x_2^2 \\ & \vdots & \end{bmatrix} \quad \text{fits} \quad y = b + m \cdot x + c \cdot x^2
$$

Same formula, $A^T A \hat{x} = A^T b$. Only the design matrix's columns change.

---

<!-- SLOT N-2: Worked example -->

# Case Study: The Café's Taste-Test Data

<div class="thread">Back to the pain: five customers, five ratings, no exact line.</div>

| Cup | Syrup units (x) | Rating (y) |
|---|---|---|
| 1 | 1 | 3 |
| 2 | 2 | 4 |
| 3 | 3 | 6 |
| 4 | 4 | 5 |
| 5 | 5 | 8 |

$n = 5$. Sums: $\sum x = 15$, $\sum y = 26$, $\sum x^2 = 55$, $\sum xy = 89$.

---

# Case Study: Solving the Normal Equations

Plug the sums into the 2x2 system:

$$
\begin{bmatrix} 5 & 15 \\ 15 & 55 \end{bmatrix} \begin{bmatrix} b \\ m \end{bmatrix} = \begin{bmatrix} 26 \\ 89 \end{bmatrix}
$$

Solve for $b$ and $m$ (row reduction, same three moves as Week 1):

$$
b = 1.9 \qquad m = 1.1
$$

Best-fit line: $\text{rating} = 1.9 + 1.1 \cdot \text{syrup}$.

---

# Case Study: The Best Line and Its Leftover Error

For each cup, the line predicts $1.9 + 1.1x$. The residual is the
actual rating minus this prediction:

| Cup | x | Actual y | Predicted | Residual |
|---|---|---|---|---|
| 1 | 1 | 3 | 3.0 | 0.0 |
| 2 | 2 | 4 | 4.1 | -0.1 |
| 3 | 3 | 6 | 5.2 | 0.8 |
| 4 | 4 | 5 | 6.3 | -1.3 |
| 5 | 5 | 8 | 7.4 | 0.6 |

No residual is zero for every cup. This line still beats every other
line: no other choice makes the squared residuals add up to less.

---

# Case Study: Predicting a New Cup

<div class="thread">The whole point of a best-fit line: predicting a rating nobody tasted yet.</div>

Using $\text{rating} = 1.9 + 1.1 \cdot \text{syrup}$, predict cup 6, at 3.5 syrup units:

$$
\text{rating} = 1.9 + 1.1(3.5) = 1.9 + 3.85 = 5.75
$$

The café can now estimate any customer's rating, for any syrup amount
within the tested range, without running a new taste test.

---

# Case Study: Comparing to a Flat-Rate Guess

<div class="thread">Proving the fitted line actually beats a lazy guess.</div>

Compare the fitted line's squared residuals to guessing the average
rating, $5.2$, for every cup:

$$
\begin{aligned}
\text{Fitted line's sum of squared residuals:} &\approx 2.70 \\
\text{Flat average guess's sum of squared residuals:} &\approx 12.80
\end{aligned}
$$

The least-squares line cuts the squared error by more than three
quarters, compared to ignoring syrup amount entirely.

---

# R²: How Good Is the Fit?

<div class="thread">One number, beyond residuals, that summarizes the whole fit.</div>

$$
R^2 = 1 - \frac{\text{fitted line's squared error}}{\text{flat-guess squared error}}
$$

$R^2$ ranges from 0 (no better than guessing the average) to 1 (a
perfect fit). It answers: "how much of the pattern does this line
actually explain?"

---

# R²: Computing It for the Café

Plug in the café's numbers from the last two slides:

$$
R^2 = 1 - (2.70 / 12.80) \approx 1 - 0.211 = 0.789
$$

About 79% of the variation in ratings is explained by syrup amount
alone. The remaining 21% is noise, or other factors the line does not
capture.

---

# Checking the Fit: Plotting Residuals

<div class="thread">A number is useful. A picture catches what a number can hide.</div>

Plotting each residual against its $x$ value should show no obvious
pattern, just scattered noise above and below zero. A clear curve or
trend in the residual plot is a sign the straight-line model itself is
wrong, not just noisy.

---

# Multiple Regression: More Than One Input

<div class="thread">The design matrix idea scales past one input variable.</div>

If the café also tracked ice amount, the design matrix grows one more
column:

$$
A = \begin{bmatrix} 1 & \text{syrup}_1 & \text{ice}_1 \\ 1 & \text{syrup}_2 & \text{ice}_2 \\ & \vdots & \end{bmatrix} \quad \text{fits} \quad \text{rating} = b + m_1 \cdot \text{syrup} + m_2 \cdot \text{ice}
$$

The exact same normal equations, $A^T A \hat{x} = A^T b$, now solve for three
unknowns instead of two.

---

# Multiple Regression: What Doesn't Change

<div class="thread">One method, one formula, no matter how many inputs.</div>

Adding inputs never changes the method: build a design matrix, form
$A^T A$ and $A^T b$, solve. Only the size of the matrices grows. This is
exactly how real-world sales, pricing, and forecasting models are
built, often with dozens of input columns.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week14/worksheet.html">Worksheet Part A</a>.</div>

Set up the design matrix and normal equations for a small, noisy
data set of your own.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask
them to predict whether their line will pass through every point
before they check. -->

---

<!-- NEW: Key Words for Session 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Interpolation:** predicting inside the range of data you already have
- **Extrapolation:** predicting outside that range, always riskier
- **Outlier:** one data point far from the rest, which can pull a fitted line off course

---

# How Far Can You Trust the Line?

<div class="thread">The line is the best fit. That does not make every prediction safe.</div>

The café's line only used syrup between 1 and 5 units. Predicting a
rating at 3 units is **interpolation**, inside the data's range.

Predicting a rating at 20 units is **extrapolation**, far outside it,
and much less trustworthy.

A single **outlier**, one unusual customer, can shift the whole line.
Always look at the data, not only the fitted line.

---

# Case Study: One Outlier Changes Everything

<div class="thread">A single unusual customer, added to the café's data.</div>

Add a sixth cup: 5 syrup units, but a rating of $1$ (a customer who
disliked the drink for an unrelated reason). Refitting the line pulls
the slope down noticeably, even though five of six points barely
moved. One unusual point can outweigh several ordinary ones.

---

# Industry Note: From Normal Equations to Machine Learning

<div class="thread">The exact formula scales down. Real datasets scale it back up.</div>

For millions of data points and thousands of inputs, computing $A^T A$
directly gets expensive. Machine learning training instead often uses
an iterative shortcut, gradient descent, that reaches nearly the same
best-fit answer without ever forming the full normal equations.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week14/worksheet.html">Worksheet Part B</a>.</div>

Solve your Part A normal equations for the slope and intercept, then
check one prediction against the actual data.

You have about 15 minutes.

---

# Try It: Compute R² for Your Fit

<div class="why">Same pairs. Quick pencil check, no new worksheet.</div>

For your Worksheet Part A line, compare its sum of squared residuals
to the flat-average guess. Compute $R^2$.

You have about 5 minutes.

---

# Common Mistakes

- **Trying to solve $Ax = b$ directly:** an overdetermined system usually has no exact solution; always move to the normal equations
- **Forgetting the column of 1s:** without it, the fitted line is forced through the origin, which is rarely correct
- **Trusting extrapolation like interpolation:** a best-fit line is least reliable far outside the data it was built from

---

# More Common Mistakes

<div class="cardlist">
<div class="card"><div class="h">Reading a high R² as proof of causation</div><div class="d">a strong fit only shows correlation; it never proves syrup <em>causes</em> a higher rating</div></div>
<div class="card"><div class="h">Ignoring one obvious outlier</div><div class="d">check the data and the residual plot, not only the fitted line's equation</div></div>
</div>

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Why does a noisy data set usually have no exact solution to $Ax = b$?
2. What does the least-squares solution $\hat{x}$ minimize?

---

# Answers

1. **More equations than unknowns, and real noise.** With more data points than unknowns, $b$ almost never lands exactly in the column space of $A$.
2. **The sum of squared residuals.** $\hat{x}$ makes $A\hat{x}$ as close to $b$ as possible, in this squared-length sense.

---

# Check Yourself: Round 2

1. A fitted line has $R^2 = 0.95$. What does that say about the fit?
2. Why do the residuals of a line fit with an intercept always sum to (about) zero?

---

# Answers: Round 2

1. **A very strong fit.** About 95% of the variation in the data is explained by the line; only 5% is left as unexplained noise.
2. **Because the normal equations require it.** The intercept's own equation, $n \cdot b + (\sum x) \cdot m = \sum y$, forces the positive and negative misses to balance out.

---

<!-- NEW: Quiz 2 logistics, before the self-check-quiz hand-off -->

# Quiz 2 Today

<div class="why">Quiz 2 is next: closed-book, covers Weeks 9-14, about 15 minutes.</div>

Put your notes away. Ask any questions now, not during the quiz.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week14/quiz.html">Week 14 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded, and is
separate from today's Quiz 2. It only shows you what you already
know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE) -->

# What This Week's Method Leaves Open

<div class="limits">
We can now fit the best approximate line through noisy data, the
practical payoff of the whole semester. But least squares still
assumes a straight-line relationship, using only one input variable,
syrup amount. Real products depend on many variables at once, and the
best pattern is not always a straight line. Later courses build on
exactly this idea, with more variables and curves instead of lines.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 14 completes the semester's toolkit: solve, represent, transform,
compute, measure, and now approximate. **Week 15** reviews Weeks 1-14
for the final exam, tying every method back to the Campus Café.

---

<!-- SLOT 16: Summary -->

# Summary

- Noisy, overdetermined data usually has no exact solution to $Ax = b$
- The least-squares solution $\hat{x}$ solves the normal equations $A^T A \hat{x} = A^T b$, minimizing squared residuals
- For a line, the normal equations reduce to a 2x2 system for slope and intercept
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 6
- **Handout:** [materials/week14/handout.md](materials/week14/handout.html), glossary and the full café walkthrough
- **Prepare:** review Weeks 1-14 for the final exam; bring one question about least squares to Week 15

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You

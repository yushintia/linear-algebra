# Week 6 Handout: Determinants

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 6 slides. Keep it. You will use the
glossary and the worked example again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Square matrix** | A grid of numbers with the same number of rows and columns, like 2x2 or 3x3. |
| **Determinant** | One number computed from a square matrix. |
| **Singular** | A system whose determinant is zero; not guaranteed to have one exact answer. |
| **Invertible** | The opposite of singular; guaranteed to have exactly one exact answer. |
| **Minor** | The smaller grid left after removing one row and one column from a matrix. |
| **Cofactor** | A minor's determinant, with a plus or minus sign attached. |
| **Sign pattern** | The plus/minus checkerboard used to assign each cofactor's sign. |
| **Expand along a row (or column)** | The method of building a larger determinant from smaller 2x2 or 3x3 pieces. |
| **Row swap** | Swapping two rows of a matrix; this flips the sign of the determinant. |
| **Duplicate row** | Two identical rows, or one row that is a scaled copy of another; this makes the determinant exactly zero. |
| **Scaled row** | A row multiplied by a number; this multiplies the whole determinant by that same number. |
| **Cramer's Rule** | A formula that writes each unknown as one determinant divided by another. It needs a nonzero determinant. |

---

## 2. The Campus Café's Determinants, Solved Step by Step

This is the full version of the in-class demos. Read it slowly, one
step at a time.

### 2.1 A 2x2 example: Latte and Mocha, checked first

From Week 1's worksheet, the café's Latte and Mocha prices came from
this system:

```
2m + s = 800      (Latte)
m + 3s = 900      (Mocha)
```

As a matrix:

```
[ 2  1 ]
[ 1  3 ]
```

**Step 1 — Compute the determinant.**

```
det = ad - bc = 2(3) - 1(1) = 6 - 1 = 5
```

**Step 2 — Read the result.** `5` is nonzero, so exactly one price for
milk and syrup exists. Week 1 found it by elimination: `m = 300` won,
`s = 200` won. The determinant predicted this before any solving
began.

### 2.2 A 3x3 example: the espresso-milk-syrup recipe

Week 1's original three-ingredient recipe, as a matrix:

```
[ 1   1   1 ]
[ 1   1  -1 ]
[ 1  -1   0 ]
```

**Step 1 — Expand along the top row.** Three 2x2 minors appear, one
per entry in row 1.

```
minor for entry (1,1): [ 1 -1 ; -1  0 ]  ->  det = (1)(0) - (-1)(-1) = -1
minor for entry (1,2): [ 1 -1 ;  1  0 ]  ->  det = (1)(0) - (-1)(1)  =  1
minor for entry (1,3): [ 1  1 ;  1 -1 ]  ->  det = (1)(-1) - (1)(1) = -2
```

**Step 2 — Apply the sign pattern (plus, minus, plus) and sum.**

```
det = (+1)(-1) - (1)(1) + (1)(-2) = -1 - 1 - 2 = -4
```

**Step 3 — Read the result.** `det = -4`, nonzero. This confirms Week
1's elimination result: exactly one answer, `e = 1`, `m = 1`, `s = 2`.

### 2.3 A zero-determinant example: the Mega Cup

The Mega Cup's recipe secretly doubled an existing rule:

```
[ 1   1   1 ]
[ 2   2   2 ]
[ 1  -1   0 ]
```

Row 2 is exactly row 1, scaled by 2. By the duplicate-row rule, the
determinant is exactly `0`, with no calculation needed. This predicts
that the recipe does not have exactly one exact answer, before anyone
runs a full shortcut on it.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

The idea behind the determinant appeared long before the word did.
In 1683, the Japanese mathematician **Seki Takakazu** wrote down a
determinant-like method for solving several linked equations at once.
Ten years later, in 1693, the German mathematician **Gottfried
Leibniz** described the same idea independently, in a private letter
about linear equations — the two mathematicians never met and had no
contact with each other.

In 1750, the Swiss mathematician **Gabriel Cramer** published a
formula, now called Cramer's Rule, that reads a system's exact answer
directly from its determinants. It appeared as an appendix to a book
about curves, not as a standalone theory.

It took until 1812 for the French mathematician **Augustin-Louis
Cauchy** to name the idea "determinant" and build it into a general
theory, the version taught today. The name is 129 years younger than
the idea itself.

### 3.2 Where this shows up in real jobs

- **Robotics:** a robot arm's control software checks a determinant-like quantity to avoid "singular" poses, positions where the arm briefly loses a degree of freedom.
- **Computer graphics:** a zero determinant on a transformation matrix means the transformation flattens 3D space into a plane or a line — objects vanish or overlap unexpectedly.
- **Structural engineering:** a building's support equations must have exactly one solution; a zero determinant flags a design that cannot be trusted as drawn.
- **Machine learning:** many training algorithms check whether a matrix is invertible before relying on it, to avoid unstable or undefined results.
- **Economics:** input-output models use determinants to confirm an economy's equations describe one consistent balance, not a contradiction.

None of these show you "compute a determinant" on the surface. All of
them run this same check, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Compute the determinant of `[[4, 1], [2, 3]]`.
2. Compute the determinant of `[[6, 3], [2, 1]]`. Does its system have exactly one solution?
3. Compute the determinant of `[[2, 0, 1], [1, 3, 0], [0, 1, 4]]` by cofactor expansion.
4. A recipe's matrix has two identical rows. What is its determinant, and why?
5. In plain words: what does a zero determinant tell you, and what does it not tell you?
6. For `[[1, 2], [2, 4]]`, compute the determinant. What extra check would tell you whether the system has no solution, or infinitely many?

### Answers

1. `det = 4(3) - 1(2) = 12 - 2 = 10`.
2. `det = 6(1) - 3(2) = 6 - 6 = 0`. **No.** A zero determinant means the system does not have exactly one solution.
3. Expand along the top row: minor for `(1,1)` is `[[3,0],[1,4]]`, `det = 12`; minor for `(1,2)` is `[[1,0],[0,4]]`, `det = 4`; minor for `(1,3)` is `[[1,3],[0,1]]`, `det = 1`. So `det = 2(12) - 0(4) + 1(1) = 24 + 1 = 25`.
4. **Zero.** Two identical rows are a duplicate row (a scaled copy with a factor of 1), so the determinant is exactly zero by the duplicate-row rule.
5. **Tells you:** the system does not have exactly one solution when the determinant is zero. **Does not tell you:** whether the system has no solution at all, or infinitely many; that needs more work, such as checking whether the equations' constants are also consistent with each other.
6. `det = 1(4) - 2(2) = 4 - 4 = 0`. To decide between "no solution" and "infinitely many," check whether the right-hand-side constants are proportional in the same way as the rows. If they are, there are infinitely many solutions; if not, there is no solution.

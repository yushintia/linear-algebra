# Week 1 Handout: Linear Systems

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 1 slides. Keep it. You will use the
glossary and the worked example again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Equation** | A math sentence with an equal sign, like `2x = 8`. |
| **Unknown (variable)** | A letter that stands for a number we do not know yet, like `x`. |
| **Linear** | Every unknown appears alone: not squared, not multiplied by another unknown, not inside a function like `sin(x)`. |
| **System (of linear equations)** | Two or more linear equations, considered together, sharing the same unknowns. |
| **Solution** | A value for every unknown that makes *all* equations in the system true at the same time. |
| **Solution set** | The complete list of every solution a system has. |
| **Row operation** | One of 3 legal moves on a system (or its matrix) that never changes the solution set: swap, scale, add. |
| **Augmented matrix** | The same system written as a grid of numbers, with a line marking where the "equals" sign was. |
| **Elimination** | The process of using row operations to remove one unknown at a time, until the system is easy to solve. |
| **Unique solution** | The system has exactly one correct answer. |
| **Infinitely many solutions** | The system has more than one correct answer — a whole family of them. |
| **No solution** | The equations contradict each other. Nothing satisfies all of them at once. |
| **Coefficient** | The known number multiplied by an unknown, like the `2` in `2x`. |

---

## 2. The Campus Café Recipe, Solved Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café's drink uses three ingredients:
espresso (`e`), milk (`m`), and syrup (`s`). Nobody wrote down the
exact recipe. Three test batches, mixed until they tasted right, gave
the barista three facts:

- One batch: `e + m + s = 4` (four units of ingredients total)
- Another batch: `2e - m = 1`
- Another batch: `m - s = -1`

**Step 1 — Write the system.**

```
e + m + s = 4      ... (1)
2e - m     = 1      ... (2)
    m - s = -1      ... (3)
```

Three equations, three unknowns.

**Step 2 — Remove one unknown using elimination.**

From equation (2): `2e - m = 1`, so `m = 2e - 1`.

Now put `m = 2e - 1` into equations (1) and (3). Every place `m`
appeared, we write `2e - 1` instead. This is legal because both sides
of (2) are equal — we are not changing anything, only rewriting it.

Equation (1) becomes: `e + (2e - 1) + s = 4` → `3e + s = 5` ... (4)

Equation (3) becomes: `(2e - 1) - s = -1` → `2e - s = 0` ... (5)

Now we have two equations, two unknowns (`e` and `s`).

**Step 3 — Remove the second unknown.**

Add equation (4) and equation (5):

```
  3e + s = 5
+ 2e - s = 0
-----------
  5e     = 5
```

So `5e = 5`, which gives `e = 1`.

**Step 4 — Back-substitute.**

Put `e = 1` into equation (5): `2(1) - s = 0` → `s = 2`.

Put `e = 1` into `m = 2e - 1`: `m = 2(1) - 1 = 1`.

So: `e = 1`, `m = 1`, `s = 2`.

**Step 5 — Check.** Put all three values back into the *original*
three equations:

- `1 + 1 + 2 = 4` ✓
- `2(1) - 1 = 1` ✓
- `1 - 2 = -1` ✓

All three are true. This is the solution, and it is the *only*
solution (Week 1's method always tells us this, see the "Three
Possible Outcomes" idea from the slides).

**Step 6 — Scale exactly, no guessing.** For 200 cups, multiply each
value by 200: `e = 200`, `m = 200`, `s = 400`. No trial batches, no
waste.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

*The Nine Chapters on the Mathematical Art* (China, roughly 200 BCE)
is one of the oldest surviving mathematics texts. Chapter 8, "Fangcheng"
(方程), lays out a method for solving several linked equations by
arranging their coefficients in a grid and combining rows — exactly
the row-operation idea from this week, roughly 2,000 years before
matrices were named. Chinese scholars used it for practical problems:
taxes, grain measures, and shared farm output.

Carl Friedrich Gauss rediscovered and formalized the same elimination
idea in 1809, while trying to solve a real astronomy problem: the
dwarf planet Ceres had been observed briefly in 1801, then lost behind
the sun. Gauss used a handful of noisy telescope readings to predict
where it would reappear — a system of equations with more facts than
unknowns, solved by the same kind of elimination this week teaches.
Astronomers found Ceres almost exactly where he predicted.

By the 1950s, the same method was one of the first things programmed
onto digital computers, because it is simple, exact, and mechanical:
perfect for a machine that never gets tired of repeating three moves.

### 3.2 Where this shows up in real jobs

- **GPS navigation:** your phone solves a small system of equations (signal timing from several satellites) to find your position, every second.
- **Computer graphics:** rotating, scaling, and moving objects on screen (Week 3's topic) is built on linear systems.
- **Economics:** input-output models balance an entire economy's production and demand using large linear systems.
- **Traffic and network flow:** engineers balance flow in and out of every intersection or network node the same way.
- **Machine learning:** almost every model you will train later in this major starts life as a linear system, before it grows more complex.

None of these show you "a system of equations" on the surface. All of
them are solving one, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Is `3x - 4y + z = 0` a linear equation? Why or why not?
2. Is `x/y = 5` a linear equation? Why or why not?
3. Solve: `x + y = 7` and `x - y = 1`. Find `x` and `y`.
4. Solve: `2a + b = 11` and `a - b = 1`. Find `a` and `b`.
5. A system reduces to `0 = 0`. What does this tell you about the number of solutions?
6. Solve the 3-unknown system: `p + q + r = 6`, `p - q = 0`, `q + r = 5`. Find `p`, `q`, `r`.

### Answers

1. **Yes.** Every unknown (`x`, `y`, `z`) appears only once, to the first power, never multiplied together.
2. **No.** `x` is divided by `y`, an unknown. Dividing by an unknown is not allowed in a linear equation.
3. `x = 4`, `y = 3`. (Add the two equations: `2x = 8`, so `x = 4`; then `y = 7 - 4 = 3`.)
4. `a = 4`, `b = 3`. (From the second equation, `a = b + 1`. Substitute: `2(b+1) + b = 11` → `3b = 9` → `b = 3`, so `a = 4`.)
5. **Infinitely many solutions.** `0 = 0` is always true, so one equation gave no new information — some freedom remains in choosing the unknowns.
6. `p = 1`, `q = 1`, `r = 4`. (From equation 2, `p = q`. From equation 3, `r = 5 - q`. Substitute both into equation 1: `q + q + (5 - q) = 6` → `q + 5 = 6` → `q = 1`. Then `p = 1` and `r = 4`. Check: `1+1+4=6` ✓, `1-1=0` ✓, `1+4=5` ✓.)

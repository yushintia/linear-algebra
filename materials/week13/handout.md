# Week 13 Handout: Projections

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 13 slides. Keep it. You will use the
glossary and the worked example again in Week 14 (Least Squares).

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Projection** | The closest point in a line or subspace to a given point. |
| **Line through the origin** | A straight line that passes through the zero point. |
| **Distance** | How far apart two points are, measured in a straight line. |
| **Residual (leftover)** | The part of a point that a subspace cannot reach. |
| **Closest point** | The one point in a subspace nearest to a given point. |
| **Orthogonal basis** | A set of basis vectors that are all at right angles to each other. |
| **Achievable set** | Every point a subspace can reach, like every drink the machine can mix. |
| **Orthogonal decomposition** | Splitting a vector into an in-subspace part plus a leftover part. |
| **Best approximation** | The closest possible match, whenever an exact match is not available. |
| **Minimum distance** | The shortest possible gap between a point and every point in a subspace. |
| **Error** | Another name for the leftover part; how far the closest match still is. |
| **Best approximation theorem** | The rule stating the projection is always the closest point, no exceptions. |

---

## 2. The Campus Café's Two Starter Mixes, Solved Step by Step

This is the full version of the in-class case study. Read it slowly,
one step at a time.

**The story.** The Campus Café's new blending machine only mixes
drinks from two fixed starter mixes, Mix P and Mix Q, in any amount.
In (espresso, milk, syrup) order:

```
P = (1, 1, 0)     equal espresso and milk, no syrup
Q = (0, 0, 1)     pure syrup, no espresso or milk
```

Week 12's method already confirmed `P · Q = 1(0) + 1(0) + 0(1) = 0`:
the two mixes are orthogonal. The machine can only make drinks of the
form `aP + bQ = (a, a, b)`, for any amounts `a` and `b`. That is the
machine's whole **achievable set**: a flat plane, since it always
needs equal espresso and milk.

A regular customer's usual drink is `y = (3, 1, 4)`. Check whether the
machine can make it exactly: it would need `a = 3` (matching
espresso) and `a = 1` (matching milk) at the same time, which is
impossible. `y` is not in the achievable set.

**Step 1 — Project onto each starter mix.**

Because `P` and `Q` are orthogonal, the projection onto their span
adds each line's own projection (the two-direction formula from the
slides):

```
proj_W(y) = ((y·P)/(P·P)) P + ((y·Q)/(Q·Q)) Q
```

**Step 2 — Compute each dot product.**

```
y·P = 3(1) + 1(1) + 4(0) = 4
P·P = 1(1) + 1(1) + 0(0) = 2
y·Q = 3(0) + 1(0) + 4(1) = 4
Q·Q = 0(0) + 0(0) + 1(1) = 1
```

**Step 3 — Scale each starter mix by its coefficient.**

```
(y·P)/(P·P) = 4/2 = 2       so   2P = (2, 2, 0)
(y·Q)/(Q·Q) = 4/1 = 4       so   4Q = (0, 0, 4)
```

**Step 4 — Add the two pieces.**

```
proj_W(y) = 2P + 4Q = (2, 2, 0) + (0, 0, 4) = (2, 2, 4)
```

The closest drink the machine can make is `(2, 2, 4)`.

**Step 5 — Find the leftover part.**

```
z = y - proj_W(y) = (3, 1, 4) - (2, 2, 4) = (1, -1, 0)
```

**Step 6 — Check.** The leftover `z` must be orthogonal to *both*
`P` and `Q` — that right angle is what proves `(2, 2, 4)` is really
the closest point, not just a plausible one.

```
z·P = 1(1) + (-1)(1) + 0(0) = 0   ✓
z·Q = 1(0) + (-1)(0) + 0(1) = 0   ✓
```

Both checks pass. `z = (1, -1, 0)` says exactly what does not fit:
one extra unit of espresso, one missing unit of milk, syrup already
correct. The barista serves `(2, 2, 4)` and knows exactly what
changed from the customer's usual order — no guessing, no wasted
syrup.

**Step 7 — Rebuild the original vector.** This is the orthogonal
decomposition in action:

```
y = proj_W(y) + z = (2, 2, 4) + (1, -1, 0) = (3, 1, 4)   ✓
```

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

The idea of finding the "closest match" when no exact answer exists
goes back to astronomy. In 1801, the dwarf planet Ceres was observed
briefly, then lost behind the sun. Astronomers across Europe raced to
predict where it would reappear using only a handful of scattered,
imperfect observations — too many facts for too few unknowns, so no
single orbit fit every observation exactly.

Adrien-Marie Legendre published a method for finding the
closest-fitting curve through such scattered data in 1805. Carl
Friedrich Gauss (the same mathematician behind Week 1's elimination
method) claimed in 1809 that he had used essentially the same idea
even earlier, while working on the Ceres problem itself. The dispute
between them over priority is one of the more famous rivalries in
mathematical history.

Over a century later, in 1907, Erhard Schmidt formalized the
procedure (building on earlier work by Gram) for turning any basis
into an **orthogonal basis** — the same construction that makes this
week's projection formula so simple to apply. Today this is usually
taught as the "Gram-Schmidt process."

### 3.2 Where this shows up in real jobs

- **Robotics:** motion planners project a desired end-effector position onto the set of positions the robot's joints can actually reach, then move to that closest reachable point.
- **Computer graphics:** shadows and mirror reflections are literally projections of a 3D point onto a 2D surface or plane.
- **Signal and image processing:** noise removal often works by projecting a noisy signal onto a "clean" subspace and discarding the leftover.
- **Data science interviews:** the geometric picture of projection (closest point, right-angle residual) is the standard way to explain why least-squares regression works, a very common interview topic.
- **GPS and sensor fusion:** combining several imperfect measurements into one best estimate is, geometrically, a projection onto the subspace of physically consistent answers.

None of these show you "a projection" on the surface. All of them are
finding the closest achievable point, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Project `y = (5, 0)` onto the line spanned by `u = (1, 1)`.
2. Project `y = (2, 6)` onto the line spanned by `u = (3, 0)`.
3. For Problem 1, compute the leftover `z = y - proj_u(y)` and verify `z · u = 0`.
4. `u1 = (1, 0, 0)` and `u2 = (0, 1, 0)` are orthogonal. Project `y = (2, 3, 5)` onto `span(u1, u2)`.
5. For Problem 4, find the leftover part `z` and identify which ingredient/coordinate it isolates.
6. True or false, with a one-sentence reason: the projection of `y` onto a subspace `W` can be farther from `y` than some other point in `W`.

### Answers

1. `y·u = 5(1)+0(1) = 5`, `u·u = 1+1 = 2`, so `proj_u(y) = (5/2)(1,1) = (2.5, 2.5)`.
2. `y·u = 2(3)+6(0) = 6`, `u·u = 9+0 = 9`, so `proj_u(y) = (6/9)(3,0) = (2/3)(3,0) = (2, 0)`.
3. `z = (5,0) - (2.5,2.5) = (2.5, -2.5)`. Check: `z·u = 2.5(1) + (-2.5)(1) = 0` ✓.
4. `(y·u1)/(u1·u1) = 2/1 = 2`, `(y·u2)/(u2·u2) = 3/1 = 3`, so `proj_W(y) = 2(1,0,0) + 3(0,1,0) = (2, 3, 0)`.
5. `z = (2,3,5) - (2,3,0) = (0, 0, 5)`. It isolates the third coordinate exactly, the one direction the subspace `span(u1,u2)` cannot reach.
6. **False.** The Best Approximation Theorem guarantees `proj_W(y)` is closer to `y` than every other point in `W` — it can never be farther than some alternative.

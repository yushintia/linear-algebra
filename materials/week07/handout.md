# Week 7 Handout: Vector Spaces

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 7 slides. Keep it. You will use the
glossary and the worked example again in Week 9.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Vector** | A list of numbers, like a point or a direction. |
| **Scalar** | A single plain number, used to stretch or shrink a vector. |
| **Vector space** | A collection of vectors you can add and scale, and always stay inside. |
| **Closure** | Staying inside a collection after adding two elements, or scaling one. |
| **Zero element (zero vector)** | The element of a vector space that changes nothing when added to another element. |
| **Subspace** | A smaller vector space that sits inside a bigger one. |
| **Linear combination** | A sum of scaled vectors, like `2v + 3w`. |
| **Span** | Every vector reachable by linear combinations of a given set. |
| **Null space** | Every solution to `Ax = 0`, gathered into one set. Always a subspace. |
| **Column space** | Every output `Ax` can produce, as `x` varies. |
| **Homogeneous system** | A system where every equation equals zero, like `Ax = 0`. |
| **Particular solution** | One specific answer to a system. |
| **General solution** | Every answer to a system, written as a particular solution plus the null space. |

---

## 2. The Café's Whole Solution Space, Solved Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café is testing a cheaper version of its
drink. Instead of three fixed house rules, only one rule is left,
linking espresso (`e`), milk (`m`), and syrup (`s`):

```
2e + 4m - 2s = 0
```

One equation, three unknowns. Last week's determinant could only have
told us whether this system's solution was unique. It is not: there
are infinitely many valid ratios. This week describes all of them at
once, as a single set.

**Where does the café come from?** The Campus Café is not a real
place — it is a running example invented for this course, and its
numbers are chosen to work out evenly. What is real is the method:
every step below is the general procedure you will use all semester
on any homogeneous linear system, following Lay, Lay & McDonald,
Ch. 4.

**Step 1 — Solve for one unknown.** Pick `e`, since its coefficient
is easiest to isolate:

```
2e + 4m - 2s = 0
2e = -4m + 2s
e = -2m + s
```

**Step 2 — Write the general point.** Every solution has the form
`(e, m, s) = (-2m + s, m, s)`, for any numbers `m` and `s`.

**Step 3 — Split into a linear combination.** Separate the `m` part
from the `s` part:

```
(e, m, s) = m(-2, 1, 0) + s(1, 0, 1)
```

Check this by expanding: `m(-2, 1, 0) = (-2m, m, 0)` and
`s(1, 0, 1) = (s, 0, s)`. Adding them gives `(-2m + s, m, s)`, which
matches Step 2 exactly.

**Step 4 — Name the result.** The set of all solutions is
`span{(-2, 1, 0), (1, 0, 1)}`, the null space of this café rule. It is
a subspace of R³: a flat plane through the origin, holding every
valid recipe ratio.

**Step 5 — Check with real numbers.** Pick `m = 1`, `s = 2`:

```
(e, m, s) = 1(-2, 1, 0) + 2(1, 0, 1) = (0, 1, 2)
```

Substitute back into the original rule: `2(0) + 4(1) - 2(2) = 0`. ✓
Any choice of `m` and `s` works the same way.

**Step 6 — What this buys the café.** The owner no longer needs a
growing list of tested batches. Any point on this plane is a valid
recipe ratio, described in one line instead of one trial at a time.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Hermann Grassmann's 1844 book *Die lineale Ausdehnungslehre*
("The Theory of Linear Extension") first treated quantities with more
than three dimensions as a single kind of object, adding and scaling
them by consistent rules. Few mathematicians of his time understood
the book; Grassmann was largely self-taught and worked as a high
school teacher in Stettin, far from the era's mathematical centers.

Giuseppe Peano rediscovered and sharpened the idea in his 1888 book
*Calcolo Geometrico*, writing down the same list of rules this week's
slides use, and giving the structure the name we still use today. He
noticed that geometric arrows, and other very different kinds of
objects, obeyed identical addition and scaling rules — one abstract
list could describe them all, instead of proving the same facts over
and over for each new setting.

In the early 1900s, David Hilbert and Stefan Banach extended the idea
further: functions themselves, not just finite lists of numbers, can
be treated as vectors, added and scaled the same way. This opened the
door to modern signal processing and, much later, machine learning,
where a photo, a sound clip, or a customer's purchase history can all
be treated as a single vector in some large space.

### 3.2 Where this shows up in real jobs

- **Image compression:** a photo is stored as a short combination of a small set of building-block patterns, instead of every pixel value.
- **Error-correcting codes:** phones and disk drives describe every valid signal pattern as a subspace, so a damaged signal can be corrected back onto it.
- **Circuit design:** engineers describe every current pattern a circuit's wiring rules allow, as a subspace, before choosing one to build.
- **Machine learning:** a model's inputs, often called "features," live in a vector space; many training techniques are really span and subspace arguments in disguise.
- **Computer graphics:** the same span idea from this week generates every point on a 3D surface from a handful of control vectors.

None of these show you "a vector space" on the surface. All of them
describe one, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Is the set of all pairs `(x, y)` with `y = -x` a vector space? Why or why not?
2. Is the set of all pairs `(x, y)` with `x² + y² = 1` a vector space? Why or why not?
3. Find the span of the single vector `(0, 3)`.
4. Find the span of the set `{(1, 1), (2, 2)}`.
5. Find the general solution to the homogeneous system `x - y + z = 0`. Write it as a span.
6. Is the set of all pairs `(x, y)` with `x = 2` a subspace of R²? Why or why not?

### Answers

1. **Yes.** It is a line through the origin `(0, 0)`; adding or scaling any point on it stays on it, and closure holds.
2. **No.** It is a circle, not a line through the origin. It has no zero element, and adding two points on the circle usually lands off the circle.
3. `span{(0, 3)} = {(0, b) : b any real number}` — the y-axis.
4. `span{(1, 1), (2, 2)} = {(a, a) : a any real number}` — still just one line, since `(2, 2)` points the same direction as `(1, 1)` and adds nothing new.
5. Solve for `x`: `x = y - z`. So `(x, y, z) = (y - z, y, z) = y(1, 1, 0) + z(-1, 0, 1)`. General solution: `span{(1, 1, 0), (-1, 0, 1)}`.
6. **No.** It does not contain the zero element `(0, 0)`, since `0 ≠ 2`. It is a vertical line that misses the origin.

# Week 12 Handout: Orthogonality

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 12 slides. Keep it. You will use the
glossary and the worked example again in Week 13.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Dot product** | Multiply matching numbers from two vectors, then add every result together: `u · v = u₁v₁ + u₂v₂ + ... + uₙvₙ`. |
| **Length (norm)** | How long a vector is, written `\|\|u\|\|`, found from `\|\|u\|\| = √(u · u)`. Never negative, zero only for the zero vector. |
| **Distance** | How far apart two vectors are: the length of one minus the other, `\|\|u - v\|\|`. |
| **Orthogonal** | Two vectors that meet at a right angle. Their dot product is exactly zero. |
| **Angle** | How far apart two vectors point, measured in degrees, found from the cosine formula. |
| **Cosine** | A formula that turns a dot product and two lengths into an angle: `cos(angle) = (u · v) / (\|\|u\|\| · \|\|v\|\|)`. |
| **Magnitude** | Another name for a vector's length. |
| **Unit vector** | A vector with length exactly 1. |
| **Normalize** | Shrink or stretch a vector to length 1, without changing its direction, by dividing it by its own length. |
| **Orthogonal set** | A group of vectors that are all orthogonal to each other, every pair. |
| **Orthonormal set** | An orthogonal set where every vector is also a unit vector. |

---

## 2. Case Study: Comparing Two Café Recipes, Solved Step by Step

This is the full version of the in-class demo from the slides. Read
it slowly, one step at a time.

**The story.** Recall the Campus Café's two original drinks from
Week 1, written as (milk, syrup) vectors:

```
Latte = (2, 1)      Mocha = (1, 3)
```

A regular customer asks whether these two drinks basically taste the
same, just bigger, or are truly different. Raw amounts alone cannot
answer that. We need the exact angle between the two recipe vectors.

**Step 1 — Compute the dot product.**

Multiply matching entries (milk with milk, syrup with syrup), then
add the results:

```
Latte · Mocha = (2)(1) + (1)(3) = 2 + 3 = 5
```

**Step 2 — Compute the length of each vector.**

Length is the square root of a vector dotted with itself:

```
||Latte|| = √(2² + 1²) = √(4 + 1) = √5
||Mocha|| = √(1² + 3²) = √(1 + 9) = √10
```

**Step 3 — Put the dot product and both lengths into the angle
formula.**

```
cos(angle) = (Latte · Mocha) / (||Latte|| · ||Mocha||)
           = 5 / (√5 · √10)
           = 5 / √50
```

**Step 4 — Simplify the fraction.**

`√50 = √(25 · 2) = 5√2`, so:

```
cos(angle) = 5 / (5√2) = 1 / √2 ≈ 0.707
```

**Step 5 — Turn the cosine into a degree.**

A calculator's inverse-cosine button turns `0.707` into:

```
angle ≈ 45°
```

**Step 6 — Read the result.** The Latte and Mocha lean 45° apart:
partly similar, partly different, neither identical (0°) nor
opposite (180°). Staff now have an exact number, not a guess, and
never had to taste-test either drink.

**Check the arithmetic makes sense.** `cos(angle)` must always sit
between `-1` and `1`. Here `0.707` is comfortably inside that range,
so the answer is plausible before you even reach for a calculator.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Euclid's *Elements* (~300 BCE, Greece) proves the Pythagorean
theorem: the first exact way to find a length from perpendicular
parts. Every time this week's length formula, `||u|| = √(u · u)`,
uses a square root of a sum of squares, it is quietly reusing
Euclid's 2,000-year-old proof.

Hermann Grassmann extended the idea in 1844: length and angle no
longer needed to live in 2 or 3 dimensions you could draw. His work
let mathematicians measure vectors with any number of entries, the
same way this week's formulas work whether a vector has 2 entries or
200.

In the 1880s, Josiah Willard Gibbs and Oliver Heaviside, working
independently on physics problems involving force and work, wrote
down the modern dot product notation used today. A formula built to
measure force in physics now measures how similar two customers'
tastes are, or how close two search results are to a query.

### 3.2 Where this shows up in real jobs

- **Recommendation engines:** compare a user's "taste vector" to every product's vector by angle, not by raw totals, so a light user and a heavy user with the same preferences still get matched.
- **Search ranking:** a search engine turns a query into a vector and ranks documents by the angle between the query vector and each document's vector.
- **Face and image search:** software compares feature vectors extracted from two photos; a small angle between them means a likely match.
- **GPS and robotics:** distance, in the exact sense from this week, is how a device computes how far it has moved or how far it is from a target.
- **Computer graphics:** orthonormal sets (Week 12's last topic) build the coordinate axes that screens and 3D engines rotate objects around.

None of these show you "a dot product" on the surface. All of them
compute one, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Compute the dot product of `u = (5, 2)` and `v = (1, 4)`.
2. Find the length of `w = (5, 12)`.
3. Find the distance between `p = (7, 1)` and `q = (3, 4)`.
4. Are `a = (3, -2)` and `b = (2, 3)` orthogonal? Show the dot product.
5. Normalize `u = (0, 7)` into a unit vector.
6. For `u = (1, 0)` and `v = (1, 1)`, find `cos(angle)` and the angle. (Hint: `cos(45°) ≈ 0.707`.)

### Answers

1. `u · v = (5)(1) + (2)(4) = 5 + 8 = 13`.
2. `||w|| = √(5² + 12²) = √(25 + 144) = √169 = 13`.
3. `p - q = (7 - 3, 1 - 4) = (4, -3)`; `||p - q|| = √(16 + 9) = √25 = 5`.
4. `a · b = (3)(2) + (-2)(3) = 6 - 6 = 0`. **Yes, orthogonal.**
5. Length of `u` is `√(0² + 7²) = 7`, so the unit vector is `(0/7, 7/7) = (0, 1)`.
6. `u · v = (1)(1) + (0)(1) = 1`; `||u|| = 1`, `||v|| = √2`; `cos(angle) = 1 / (1 · √2) = 1/√2 ≈ 0.707`, so `angle ≈ 45°`.

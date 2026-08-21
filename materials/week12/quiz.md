# Week 12 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** What is the dot product of `u = (2, 5)` and `v = (3, -1)`?

A. `1`
B. `6`
C. `11`
D. `17`

**2.** A student computes `u · u = 49` for a vector `u` and stops,
writing `||u|| = 49`. What went wrong?

A. Nothing; that is the correct length.
B. The student forgot to take the square root; `||u|| = 7`.
C. The dot product should have been negative.
D. `u · u` cannot equal `49`.

**3.** Two vectors have `cos(angle) = 0`. What does that tell you?

A. The vectors point in exactly the same direction.
B. The vectors point in exactly opposite directions.
C. The vectors are orthogonal.
D. The vectors have equal length.

**4.** Are `p = (4, 1)` and `q = (1, -4)` orthogonal?

A. Yes; `p · q = 4 - 4 = 0`.
B. No; `p · q = 4 + 4 = 8`.
C. Yes, but only because both vectors have the same length.
D. Cannot tell without a picture.

**5.** Which statement about the zero vector is true?

A. It is orthogonal to no other vector.
B. It is orthogonal to every vector, including itself.
C. It cannot be normalized or used in a dot product.
D. Its length is undefined.

**6.** To turn a vector into a unit vector, you should:

A. Multiply the vector by its own length.
B. Divide the vector by its own length.
C. Subtract the vector's length from each entry.
D. Square every entry of the vector.

**7. (Short answer)** Find the exact angle between `u = (1, 1)` and
`v = (1, -1)`. Show the dot product, both lengths, and the cosine
before giving the angle.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **A.** `u · v = (2)(3) + (5)(-1) = 6 - 5 = 1`.
2. **B.** The dot product of a vector with itself gives length *squared*; `||u|| = √49 = 7`.
3. **C.** A cosine of `0` corresponds to a 90° angle, which is exactly the orthogonal case.
4. **A.** `p · q = (4)(1) + (1)(-4) = 4 - 4 = 0`, so the dot product is zero and the vectors are orthogonal.
5. **B.** The dot product of the zero vector with any vector is always `0`, so it counts as orthogonal to everything, including itself.
6. **B.** Normalizing means dividing a vector by its own length, which keeps the direction and sets the length to exactly `1`.
7. `u · v = (1)(1) + (1)(-1) = 1 - 1 = 0`; `||u|| = √(1+1) = √2`, `||v|| = √(1+1) = √2`; `cos(angle) = 0 / (√2 · √2) = 0`, so `angle = 90°`. (`u` and `v` are orthogonal.)

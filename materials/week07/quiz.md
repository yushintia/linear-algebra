# Week 7 Self-Check Quiz

Linear Algebra (501976-001) · Not graded, and separate from today's
Quiz 1. Answer alone, no notes. About 10 minutes.

---

**1.** Which set is a vector space?

A. All pairs `(x, y)` with `x + y = 0`
B. All pairs `(x, y)` with `x ≥ 0`
C. All pairs `(x, y)` with `xy = 1`
D. All pairs `(x, y)` with `x + y = 3`

**2.** Which of these is **not** one of the three subspace checks?

A. Contains the zero element
B. Closed under addition
C. Closed under scalar multiplication
D. Contains at least 10 elements

**3.** What is the span of the vector `(3, 0)`?

A. The whole plane
B. The x-axis
C. Just the point `(3, 0)`
D. The y-axis

**4.** A system's solutions all have the form `x = (particular
solution) + (null space vector)`. What is this called?

A. Unique solution
B. General solution
C. Column space
D. Determinant

**5.** The null space of a matrix `A` is:

A. All outputs `Ax` can produce
B. All solutions to `Ax = 0`
C. All inputs that give a unique answer
D. Always just the zero vector

**6.** Does every subset of a vector space automatically form a
subspace?

A. Yes, always
B. No, it must pass three checks
C. Only if the subset is finite
D. Only if it contains negative numbers

**7. (Short answer)** Determine whether the set of all `(x, y, z)`
with `x - 2y + z = 0` is a subspace of R³. Show your reasoning.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **A.** `x + y = 0` is a line through the origin: closed under addition and scaling.
2. **D.** Set size is never one of the three checks; a subspace can be infinite or contain just the zero element.
3. **B.** Every scalar multiple of `(3, 0)` is a point `(a, 0)`, so the span is the x-axis.
4. **B.** This is the definition of a general solution.
5. **B.** The null space collects every solution to `Ax = 0`.
6. **B.** A subset must pass the zero-element, closed-addition, and closed-scaling checks.
7. **Yes, a subspace.** It contains `(0,0,0)` (since `0 - 0 + 0 = 0`); it is closed under addition and scalar multiplication because the equation is homogeneous (equals zero). It is a plane through the origin.

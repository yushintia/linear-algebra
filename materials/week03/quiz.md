# Week 3 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** Which property must every linear transformation have?

A. It must double every input
B. It must send the origin to itself
C. It must use only positive numbers
D. It must be written as a table, not a matrix

**2.** A transformation's matrix is `[ 2 0 ; 0 5 ]` (row 1: `2 0`,
row 2: `0 5`). What does it do?

A. Rotates every vector
B. Reflects every vector across the x-axis
C. Scales x by 2 and y by 5
D. Shifts every vector by (2, 5)

**3.** To build a transformation's matrix, what do you feed into the
rule first?

A. Any two random vectors
B. The standard basis vectors, `(1,0)` and `(0,1)`
C. The final answer you want
D. The number zero, twice

**4.** Which of these is **not** one of this week's four named
transformations?

A. Scaling
B. Rotation
C. Multiplication
D. Shear

**5.** A rule maps `(0, 0)` to `(3, 0)`. What can you conclude?

A. It is a linear transformation
B. It is not a linear transformation
C. It is a scaling transformation
D. Not enough information

**6.** In `T(x) = Ax`, what does the matrix `A` represent?

A. A single output vector
B. The fixed rule that transforms any input vector
C. A system of equations with no solution
D. The number of dimensions in the problem

**7. (Short answer)** A transformation's matrix has columns `(0, 1)`
and `(1, 0)`. Find the image of the vector `(4, 9)`. Show your work.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** A linear transformation must fix the origin; `T(0) = 0` always.
2. **C.** The first column, `(2, 0)`, scales x by 2. The second column, `(0, 5)`, scales y by 5.
3. **B.** Feeding in the standard basis vectors and reading off the results gives the matrix's two columns directly.
4. **C.** "Multiplication" is not one of this week's four named geometric transformations (scaling, rotation, reflection, shear). It is next week's topic for combining transformations.
5. **B.** The origin does not map to itself, so this rule cannot be a linear transformation.
6. **B.** The matrix `A` is the fixed rule; multiplying it by any input vector gives that input's image.
7. `(9, 4)`. (Matrix: `[ 0 1 ; 1 0 ]`. Row 1: `0·4 + 1·9 = 9`. Row 2: `1·4 + 0·9 = 4`.) This matrix swaps the two coordinates.

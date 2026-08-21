# Week 9 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** A set of vectors is linearly independent when:

A. Every vector in the set is the zero vector
B. The only combination of them that equals zero uses all-zero scalars
C. There are at least 3 vectors in the set
D. Every vector points in a different direction on a graph

**2.** Which set is linearly dependent?

A. `{(1, 0), (0, 1)}`
B. `{(1, 2), (2, 4)}`
C. `{(1, 1), (1, -1)}`
D. `{(3, 0), (0, 5)}`

**3.** A basis for a vector space must be:

A. Independent only
B. Spanning only
C. Both independent and spanning
D. Neither; any subset works

**4.** Two different bases are found for the same subspace. What must be true about them?

A. They always contain the exact same vectors
B. They always have the same number of vectors
C. One must be wrong
D. Nothing; their sizes can differ

**5.** What is the rank of a matrix?

A. The number of rows it has
B. The number of columns it has
C. The dimension of its column space
D. The largest entry in the matrix

**6.** A matrix has 6 columns and rank 4. What is its nullity?

A. 2
B. 4
C. 6
D. 10

**7.** The set `{(1, 0, 0), (0, 1, 0)}` is a basis for which space?

A. R² only
B. R³
C. A plane inside R³, not all of R³
D. It is not a basis for any space

**8. (Short answer)** Show that `{(1, 2), (3, 6)}` is linearly dependent, and write one vector as a combination of the other.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** This is the definition of linear independence.
2. **B.** `(2, 4) = 2 · (1, 2)`, a nonzero combination reaching zero: `2(1,2) - (2,4) = (0,0)`.
3. **C.** A basis needs both properties: independent (no redundancy) and spanning (reaches everything).
4. **B.** The Steinitz exchange lemma guarantees every basis of the same space has the same count, its dimension.
5. **C.** Rank is the dimension of the column space, not a row or column count by itself.
6. **A.** By rank-nullity, `rank + nullity = n = 6`, so `4 + nullity = 6`.
7. **C.** These 2 vectors only span the x-y plane inside R³; they cannot reach the z-direction, so they are not a basis for all of R³.
8. `(3, 6) = 3 · (1, 2)`, so the set is dependent. Check: `3(1,2) - (3,6) = (0,0)`, a nonzero combination reaching zero.

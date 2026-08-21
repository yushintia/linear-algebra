# Week 10 Handout: Eigenvalues

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 10 slides. Keep it. You will use the
glossary and the worked example again in Week 11.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Transformation** | A fixed rule that turns one vector into another. |
| **Direction** | Which way a vector points, ignoring how long it is. |
| **Stretch** | Making a vector longer or shorter, without turning it. |
| **Rotate** | Turning a vector to point a new way. |
| **Eigenvalue** | The number that says how much a special direction stretches or shrinks. |
| **Eigenvector** | The special direction itself, written as a vector: a nonzero `v` where `Av = λv`. |
| **Identity matrix** | A square grid that leaves every vector unchanged; 1s on the diagonal, 0s elsewhere. |
| **Characteristic equation** | The equation `det(A - λI) = 0`, solved to find a matrix's eigenvalues. |
| **Trivial solution** | The always-true but useless answer `v = 0`. Never counted as an eigenvector. |
| **Multiplicity** | How many times the same eigenvalue repeats as a root of the characteristic equation. |
| **Dominant eigenvalue** | The eigenvalue with the largest size. Its direction wins out under repeated use. |

---

## 2. The Café's Blend Machine, Solved Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café's new machine blends cherry syrup
(`c`) and vanilla syrup (`v`), then feeds the result back through
itself. The blending rule is:

```
new c = 2c + v
new v = c + 2v
```

As one matrix, this rule is:

```
A = [ 2  1 ]
    [ 1  2 ]
```

**Where does the café come from?** The Campus Café is not a real
place — it is a running example invented for this course, and its
numbers are chosen to factor evenly. What is real is the method:
every step below is the general procedure you use on any square
matrix, following Lay, Lay & McDonald, Ch. 5.1-5.2.

**Step 1 — Build the characteristic equation.** Subtract `λ` from
`A`'s diagonal, then take the determinant, and set it to zero:

```
A - λI = [ 2-λ    1  ]
         [  1    2-λ ]

det(A - λI) = (2-λ)(2-λ) - (1)(1) = 0
```

**Step 2 — Expand and solve for `λ`.**

```
(2-λ)(2-λ) - 1 = 0
λ² - 4λ + 3 = 0
(λ - 1)(λ - 3) = 0
```

Two eigenvalues: `λ = 1` and `λ = 3`.

**Step 3 — Find the eigenvector for `λ = 3`.** Solve `(A - 3I)v = 0`:

```
[ -1   1 ] [c]   [0]
[  1  -1 ] [v] = [0]
```

Both rows say the same thing: `c = v`. Pick `c = 1`, so `v = 1`.
Eigenvector: `(1, 1)`.

**Step 4 — Find the eigenvector for `λ = 1`.** Solve `(A - 1I)v = 0`:

```
[ 1  1 ] [c]   [0]
[ 1  1 ] [v] = [0]
```

Both rows say `c = -v`. Eigenvector: `(1, -1)`.

**Step 5 — Check.** Put each eigenvector back into `Av = λv`:

```
A(1, 1) = (2+1, 1+2) = (3, 3) = 3(1, 1)   ✓  (λ = 3)
A(1,-1) = (2-1, 1-2) = (1,-1) = 1(1,-1)   ✓  (λ = 1)
```

Both eigenvectors hold. Every other starting mix, like `(1, 0)`,
drifts toward the `(1, 1)` direction the more times the machine runs,
because `λ = 3` is the dominant eigenvalue.

**Step 6 — Read the result.** The direction `(1, 1)` (equal cherry
and vanilla) triples in strength every run. The direction `(1, -1)`
(equal amounts, opposite sign) never changes size. These are the only
two mixes the machine scales without tilting sideways — exactly what
the owner asked for.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Leonhard Euler studied spinning rigid bodies in 1743 and found that
every rotating solid has axes that never wobble as it turns — the
earliest known appearance of an eigenvector, though nobody called it
that yet. Augustin-Louis Cauchy found the same kind of special
direction in 1826, while studying how stress spreads inside a solid
material under load: certain directions carry pure stretching or
compressing force, with no twisting. David Hilbert finally gave the
idea its modern name in 1904, calling it *eigenwert* — German for
"own value" — while working on integral equations. English writers
kept the German prefix, giving us "eigenvalue" and "eigenvector"
today.

### 3.2 PageRank, in a little more detail

Google's original PageRank algorithm treats the entire web as a
directed graph: pages are nodes, links are arrows. Each page starts
by splitting its "importance" evenly among the pages it links to.
Repeating this redistribution, over and over, is mathematically the
same as multiplying a vector of importance scores by a large matrix,
again and again. That repeated multiplication is exactly next week's
topic — repeating a transformation many times, fast. The scores
eventually settle into one stable split that does not change under
another round: the dominant eigenvector of the link matrix, with
eigenvalue 1. That stable split is the page ranking you see in search
results.

### 3.3 Where this shows up in real jobs

- **Search engines:** ranking pages by a stable "importance" score, exactly PageRank's method.
- **Structural engineering:** finding the natural shaking frequencies of a bridge or aircraft wing, so designs avoid resonance.
- **Computer vision:** facial recognition and image compression both use the few directions that capture most of the variation in a dataset (principal component analysis).
- **Ecology and finance:** population models and Markov-chain models both use a dominant eigenvector to find a long-run stable state.
- **Vibration and control systems:** engineers use eigenvalues to check whether a system settles down or spirals out of control over time.

None of these show you "an eigenvalue" on the surface. All of them
compute one, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end. All use
the café's matrix `A = [[2,1],[1,2]]` unless stated otherwise.

1. Is `v = (3, 3)` an eigenvector of `A`? If so, which eigenvalue?
2. Is `v = (1, 2)` an eigenvector of `A`? Show your work.
3. Find the eigenvalues of the diagonal matrix `D = [[5,0],[0,-2]]`.
4. A matrix's characteristic equation is `λ² - 7λ + 10 = 0`. Find its eigenvalues.
5. For `E = [[3,1],[0,3]]`, is `λ = 3` an eigenvalue? (Compute `det(E - 3I)`.)
6. True or false: `v = (0, 0)` can be a valid eigenvector, as long as some `λ` makes `Av = λv` true.

### Answers

1. **Yes, eigenvalue 3.** `(3, 3)` is `(1, 1)` scaled by 3, the same special direction. `A(3,3) = (9,9) = 3(3,3)`.
2. **No.** `A(1,2) = (2+2, 1+4) = (4, 5)`. That is not any scalar multiple of `(1, 2)`, since `4/1 ≠ 5/2`. The direction rotated.
3. **`λ = 5` and `λ = -2`.** For a diagonal matrix, the eigenvalues are always the diagonal entries themselves.
4. **`λ = 5` and `λ = 2`.** The equation factors as `(λ - 5)(λ - 2) = 0`.
5. **Yes.** `det(E - 3I) = det([[0,1],[0,0]]) = (0)(0) - (1)(0) = 0`, so `λ = 3` is an eigenvalue.
6. **False.** `v = 0` is the trivial solution. It always satisfies `Av = λv` for any `λ`, but it is never counted as a valid eigenvector.

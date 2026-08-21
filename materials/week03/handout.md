# Week 3 Handout: Linear Transformation

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 3 slides. Keep it. You will use the
glossary and the worked examples again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Transformation** | A rule that takes a vector in and gives a vector out. |
| **Linear transformation** | A transformation that keeps the origin fixed and keeps straight lines straight. Formally, `T(u+v) = T(u)+T(v)` and `T(cu) = c·T(u)` for all vectors and numbers. |
| **Transformation matrix** | The one fixed matrix `A` that carries out a linear transformation, so that `T(x) = Ax`. |
| **Image (of a vector)** | The vector you get out, after the transformation. |
| **Standard basis vector** | One of the simple "one step" vectors, like `(1, 0)` or `(0, 1)`. |
| **Scaling** | Stretching or shrinking every vector by the same factor. |
| **Rotation** | Turning every vector by the same angle around the origin. |
| **Reflection** | Flipping every vector across a line, like a mirror. |
| **Shear** | Sliding one direction more than the other, tilting a shape. |
| **Unit square** | The square with corners `(0,0)`, `(1,0)`, `(0,1)`, `(1,1)`, used to see a transformation's effect at a glance. |
| **Order vector** | A list of quantities ordered, used as the input to a recipe matrix. |
| **Preserves the origin** | A required property of every linear transformation: `(0, 0)` must always map to `(0, 0)`. |

---

## 2. Worked Example 1: Resizing the Café's Logo

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** The Campus Café's logo is a small triangle with three
corners:

```
A = (1, 0)
B = (0, 1)
C = (1, 1)
```

A banner needs the logo exactly twice as big. The scaling matrix that
doubles both coordinates is:

```
    [ 2  0 ]
A = [ 0  2 ]
```

**Step 1 — Apply the matrix to corner A.**

```
[ 2  0 ]   [ 1 ]   [ 2·1 + 0·0 ]   [ 2 ]
[ 0  2 ] × [ 0 ] = [ 0·1 + 2·0 ] = [ 0 ]
```

Corner A moves from `(1, 0)` to `(2, 0)`.

**Step 2 — Apply the same matrix to corner B.**

```
[ 2  0 ]   [ 0 ]   [ 2·0 + 0·1 ]   [ 0 ]
[ 0  2 ] × [ 1 ] = [ 0·0 + 2·1 ] = [ 2 ]
```

Corner B moves from `(0, 1)` to `(0, 2)`.

**Step 3 — Apply the same matrix to corner C.**

```
[ 2  0 ]   [ 1 ]   [ 2·1 + 0·1 ]   [ 2 ]
[ 0  2 ] × [ 1 ] = [ 0·1 + 2·1 ] = [ 2 ]
```

Corner C moves from `(1, 1)` to `(2, 2)`.

**Result.** The new, doubled triangle has corners `(2, 0)`, `(0, 2)`,
`(2, 2)`. One matrix, applied the same way to every corner, resizes
the whole shape. This is exactly what a photo editor or game engine
does when it resizes or rotates an image, just with many more points.

---

## 3. Worked Example 2: From Orders to Ingredients

**The story.** The Campus Café's Regular cup needs 2 units milk and 1
unit syrup. The Large cup needs 3 units milk and 2 units syrup. Write
this as a matrix, one column per drink size:

```
    [ 2  3 ]
A = [ 1  2 ]
```

The first column, `(2, 1)`, is the Regular recipe. The second column,
`(3, 2)`, is the Large recipe.

**Step 1 — Write the order as a vector.** A customer orders 5 Regular
cups and 3 Large cups: `x = (5, 3)`.

**Step 2 — Apply the matrix.**

```
[ 2  3 ]   [ 5 ]   [ 2·5 + 3·3 ]   [ 19 ]
[ 1  2 ] × [ 3 ] = [ 1·5 + 2·3 ] = [ 11 ]
```

**Step 3 — Read the result.** The café needs 19 units of milk and 11
units of syrup to fill this exact order.

**Why this matters.** The same matrix `A` works for *any* order. Try a
different order, `x = (2, 4)`:

```
[ 2  3 ]   [ 2 ]   [ 2·2 + 3·4 ]   [ 16 ]
[ 1  2 ] × [ 4 ] = [ 1·2 + 2·4 ] = [ 10 ]
```

No re-deriving the recipe each time. Feed in any order, and the matrix
returns the exact ingredients needed, every time.

---

## 4. Optional Reading (not required, not on the quiz)

### 4.1 More history

Hermann Grassmann published *Die lineale Ausdehnungslehre* (roughly,
"The Theory of Linear Extension") in 1844. It laid out general rules
for combining and scaling directions in space, well before "vector"
and "matrix" were common words. Few mathematicians of his time
understood it; its full value was recognized only decades later.

Arthur Cayley, in 1858, was the first to write a linear transformation
as a square grid of numbers. He also defined a rule for combining two
transformations into one. That combining rule is matrix
multiplication, the subject of Week 4. Cayley's own words framed the
matrix as standing for the whole transformation, not just a table of
numbers.

Ivan Sutherland's *Sketchpad* (1963) was one of the first interactive
computer graphics programs. It let a user draw a shape, then move,
resize, or rotate it on screen in real time. All of that ran on
exactly this week's matrices, underneath.

### 4.2 Where this shows up in real jobs

- **Photo and design software:** resizing, rotating, or flipping an image is one matrix, applied to every pixel's position.
- **Video games:** every character, camera move, and animation frame is a sequence of transformation matrices.
- **Robotics:** a robot arm's joints each apply a rotation matrix to figure out where its hand ends up.
- **Computer vision:** straightens a tilted, scanned photo by undoing its transformation, using an inverse matrix (Week 4's topic).
- **Data science:** reshaping a dataset's coordinates, to remove hidden overlap between features, is a linear transformation.

None of these show you "a matrix" on the surface. All of them apply
one, constantly, underneath.

---

## 5. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. A transformation triples the y-coordinate and leaves x unchanged. Write its 2x2 matrix.
2. A transformation's matrix is `[ 0 1 ; 1 0 ]` (row 1: `0 1`, row 2: `1 0`). Find the image of `(3, 5)`.
3. Is "double every coordinate, then add 1 to x" a linear transformation? Why or why not?
4. A café order vector is `x = (10, 2)` (10 Regular, 2 Large cups). Using this week's recipe matrix `A = [ 2 3 ; 1 2 ]`, find the milk and syrup needed.
5. Which single word describes a transformation that flips every vector across a line, like a mirror?
6. A transformation matrix has columns `(1, 0)` and `(0, 1)`, unchanged. What does this transformation do to every vector?

### Answers

1. `[ 1  0 ; 0  3 ]`, meaning `[ 1  0 ]` on top, `[ 0  3 ]` below.
2. `(5, 3)`. (Row 1: `0·3 + 1·5 = 5`. Row 2: `1·3 + 0·5 = 3`.) This matrix swaps the two coordinates.
3. **No.** Adding 1 to x moves the origin `(0, 0)` to `(1, 0)`, so the origin is not fixed. A linear transformation must send the origin to itself.
4. Milk: `2·10 + 3·2 = 26` units. Syrup: `1·10 + 2·2 = 14` units.
5. **Reflection.**
6. **Nothing.** Every vector maps to itself; this is the identity transformation.

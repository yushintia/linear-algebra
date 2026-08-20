# Outline: Linear Algebra (501976-001)

DEU 2026-2, Tue 1-3교시 (3x50 min), 정보 610, 2nd-year, 지능형컴퓨팅학과.
Instructor: Yushintia Pramitarini. No formal prerequisite listed. Texts:
Lay, Lay & McDonald; Hefferon; Cherney, Denton, Thomas & Waldron.

Full pedagogical rules (chain-linking, slot structure) live in
`SPINE.md`; this file is the flat semester-level view.

| Wk | Topic | Deck | Format |
|---|---|---|---|
| 1 | Linear Systems | `slides/week01-introduction.md` | Full |
| 2 | Vector & Matrix | `slides/week02-vector-and-matrix.md` | Full |
| 3 | Linear Transformation | `slides/week03-linear-transformation.md` | Full |
| 4 | Matrix Algebra | `slides/week04-matrix-algebra.md` | Full — Assignment 1 due |
| 5 | Factorization | `slides/week05-factorization.md` | Full |
| 6 | Determinants | `slides/week06-determinants.md` | Full |
| 7 | Vector Spaces | `slides/week07-vector-spaces.md` | Full — Quiz 1 |
| 8 | Midterm (Wk 1-7) | `slides/week08-midterm-review.md` | Short review |
| 9 | Bases, Dimension | `slides/week09-bases-dimension.md` | Full |
| 10 | Eigenvalues | `slides/week10-eigenvalues.md` | Full |
| 11 | Diagonalization | `slides/week11-diagonalization.md` | Full — Assignment 2 due |
| 12 | Orthogonality | `slides/week12-orthogonality.md` | Full |
| 13 | Projections | `slides/week13-projections.md` | Full |
| 14 | Least Squares | `slides/week14-least-squares.md` | Full — Quiz 2 |
| 15 | Final Exam (Wk 1-14) | `slides/week15-final-review.md` | Short review |

## Chain (Limits -> Pain), see SPINE.md for full text

1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> (8 review) -> 9 -> 10 -> 11 -> 12 -> 13
-> 14 -> (15 review). The semester builds one capability at a time:
solve, represent, transform, compute efficiently, measure the solution
space, find special directions, measure angle and distance, and finally
approximate what real, noisy data cannot solve exactly.

## Running case study

"Campus Café" working out unknown per-cup ingredient amounts by trial
and error, made worse when a new ingredient is added. Week 1 poses the
problem in plain arithmetic; Week 2 represents it as `Ax = b`; later
weeks reuse the same recipe data for transformations, factorization,
eigen-analysis, and a final least-squares fit to real (noisy) customer
taste-test data.
Industry grounding threads through in parallel: image transforms
(Week 3), Google's PageRank as an eigenvector problem (Week 10), and
trend-line fitting in data science (Week 14).

## Status

Week 1 drafted, built, and timed. Weeks 2-15 not yet drafted.

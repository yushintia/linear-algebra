# The Spine: Standard Structure for Every Lecture Week

Linear Algebra (501976-001), 2026-2. This document is the standard. Every
week's deck (`slides/weekNN-*.md`) must follow it. If a deck and this
document disagree, fix the deck.

## Principle

**Motivation always precedes definition.** A student should never meet a
term before meeting the concrete problem that forced someone to invent it.
Every week opens with a broken scenario in plain language, not a formal
statement.

**Weeks chain.** The "Limits" slide that closes week N is, almost verbatim,
the "Pain" slide that opens week N+1. The semester should read as one
argument, not fourteen independent talks.

## The 17 slots

Acts 0, 1, 2, 4 are **mandatory and fixed**: same slot numbers, same order,
every full-spine week. Act 3 (Build) expands or contracts to fit the topic.

### Act 0: LOCATE

| # | Slide | Rule |
|---|---|---|
| 1 | Title | Week #, topic, course code, instructor, date |
| 2 | Where we are | Shared roadmap graphic (`_shared/roadmap.md`), current week highlighted |
| 3 | Recap + open wound | One sentence on what last week delivered, one sentence on what it left broken |

### Act 1: MOTIVATE

| # | Slide | Rule |
|---|---|---|
| 4 | The pain | Concrete broken scenario in the running case study. **Zero jargon.** If a technical term appears here, the slide is wrong |
| 5 | Cost of not knowing | What breaks downstream (wasted ingredients, wrong answers, wasted time) *and* where this bites in industry (interviews, real applications, job requirements) |
| 6 | Driving question | One sentence the week must answer. Repeat it verbatim on any section-divider slide inside Act 3 |
| 7 | Learning outcomes | 3-4 verbs, each traceable to a syllabus objective |

**Hard rule:** no formal definition before slot 8. If you need one earlier,
the pain slide (4) is too abstract, so fix it instead of breaking the rule.

### Act 2: GROUND

| # | Slide | Rule |
|---|---|---|
| 8 | Origin | Who, when, what forced it. Ideas are answers to historical pain, not arbitrary convention |
| 9 | Core concept | First formal definition of the week |

### Act 3: BUILD (flexible)

| # | Slide | Rule |
|---|---|---|
| 10..N-3 | Mechanics | Stepwise, as many slides as the topic needs |
| N-2 | Worked example | Same running case study, continued from prior weeks; see `slides/_shared/case-study.md` |
| N-1 | Common mistakes | Anti-patterns and why each is tempting |
| N | Check yourself | 2-3 questions; put the answers on the slide immediately after, not the same slide |

### Act 4: CLOSE

| # | Slide | Rule |
|---|---|---|
| N+1 | Limits | What this week's technique cannot do. **This text becomes next week's slot 4** |
| N+2 | Bridge | "Week N leaves X unsolved -> Week N+1 addresses it." Explicit, one sentence |
| N+3 | Summary | Takeaways + reading assignment + what to prepare |
| N+4 | Thank You | Template end slide |

## The semester chain

| Wk | Topic | Limit (leads to next pain) |
|---|---|---|
| 1 | Linear Systems | Row reduction solves any system exactly by hand, but there is no compact, computable way to write or scale it to dozens or hundreds of unknowns -> **W2** |
| 2 | Vector & Matrix | Ax=b organizes any system compactly, but nothing yet says whether a solution even exists, or is unique -> **W3** |
| 3 | Linear Transformation | We can describe one transformation as a matrix, but not yet combine or reverse them -> **W4** |
| 4 | Matrix Algebra | We can multiply and invert matrices, but for large systems this is still just slow arithmetic -> **W5** |
| 5 | Factorization | LU factorization speeds up solving, but tells us nothing about which directions in space a system actually reaches -> **W6** |
| 6 | Determinants | A determinant tells us if a solution is unique, but not what the whole space of solutions looks like -> **W7** |
| 7 | Vector Spaces · Quiz 1 | We can describe the whole solution space abstractly, but not yet measure how "big" or independent that space is -> **W9** |
| 8 | Midterm | review only, no chain link |
| 9 | Bases, Dimension | We can count independent directions, but not yet find the special directions a transformation stretches without rotating -> **W10** |
| 10 | Eigenvalues | Eigenvalues reveal stretch directions one at a time, but repeating a transformation many times by hand is still impractical -> **W11** |
| 11 | Diagonalization | Diagonalization makes repeated transformations fast, but only measures stretching, not angle or distance -> **W12** |
| 12 | Orthogonality | We can measure angle and length, but not yet find the closest point in a subspace to a point outside it -> **W13** |
| 13 | Projections | Projection finds the closest point in theory, but real data rarely has an exact solution to project onto -> **W14** |
| 14 | Least Squares · Quiz 2 | We can now fit the best approximate line through noisy data, the practical payoff of the whole semester -> **W15** |
| 15 | Final Exam | review only, no chain link |

Weeks 8 and 15 use the **short review variant**: Act 0 (slots 1-3) + Act 3
slot "Check yourself" (expanded into full review questions) + Act 4 (slots
N+1..N+4, "Limits" replaced by "What to focus on next"). No Pain or Ground
acts: there is no new concept to motivate. Weeks 7 and 14 carry an embedded
quiz but keep the full spine: new content is still taught that day.

## Enforcement

- Copy `slides/_template/week-XX.md` for every new week. It carries all 17
  slots as HTML comments; fill them in, don't renumber them.
- `slides/_shared/roadmap.md`: single source for the Act 0 roadmap graphic.
- `slides/_shared/case-study.md`: the running example as it stands after
  each week; update it when a week changes it materially.
- Course logistics (grading, textbook, policies) live in an appendix block
  in Week 1 only, outside the spine numbering. Administrative content must
  never sit between the roadmap and the pain slide.

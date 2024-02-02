## definition

A monorepo is a single repository containing multiple distinct projects, with well-defined relationships

✋ Monorepo ≠ is different fromMonolith
A good monorepo is the opposite of monolithic!

## Misconceptions about Monorepos: Monorepo != Monolith.

### Monorepo style

- You develop multiple projects in the same repository.
- The projects can depend on each other, so they can share code.
- When you make a change, you do not rebuild or retest every project in the monorepo.
  Instead, you only rebuild and retest the projects that can be affected by your change.
- It makes the CI faster. On a large scale, it can be 1000 times faster.
- It gives teams working in the monorepo independence.
  If two projects A and B, do not depend on each other, they cannot affect each other — ever. Team A will be able to develop their project, test it, build it, merge PRs into master without ever having to run any code written by Team B. Team B can have flaky tests, poorly typed code, broken code, broken tests. None of it matters to Team A.

# Backlog

The roadmap this project follows, plus the intake queue for new feature
requests and bug reports — kept separate from the
[architecture blueprint](./blueprints/architecture.md) since this is a
living plan, not a description of the system as it stands. For what's
actually built today, see
[`blueprints/features.md`](./blueprints/features.md); for what shipped
when, see [`CHANGELOG.md`](../CHANGELOG.md).

## Phased roadmap

<!-- Optional. Keep only if the project has a real phased plan worth
tracking; delete this section otherwise. -->

| Phase | Status | Scope |
|-------|--------|-------|
| 0 | planned | <what this phase delivers> |

## Feature requests

Every new feature request lands here first, in status `proposed`, and
moves through the stages below in order. See the mandatory workflow in
[`CLAUDE.md`](../CLAUDE.md) for what each status transition requires.

Status values: `proposed` → `prioritized` → `in design` → `building` → `done`.
Small, self-contained changes can skip `in design` and go straight from
`prioritized` to `building` — see the small-change exception in
[`CLAUDE.md`](../CLAUDE.md).

| # | Feature | Status | Priority | Design doc / notes |
|---|---------|--------|----------|---------------------|
| 1 | <one-line description> | proposed | — | — |

For a small change qualifying for the exception, put the agreed summary,
impact, and design directly in the "Design doc / notes" cell (a sentence
or two) instead of linking a file under `docs/designs/`.

## Bugs

Every bug report lands here first, in status `reported`, and moves
through the stages below in order. See the mandatory workflow in
[`CLAUDE.md`](../CLAUDE.md) for what each status transition requires.

Status values: `reported` → `prioritized` → `in design` → `fixing` → `fixed`.
Small, self-contained fixes can skip `in design` and go straight from
`prioritized` to `fixing` — see the small-fix exception in
[`CLAUDE.md`](../CLAUDE.md).

| # | Bug | Status | Priority | Design doc / notes |
|---|-----|--------|----------|---------------------|
| 1 | <observed behavior> | reported | — | — |

For a small fix qualifying for the exception, put the agreed root cause
and fix approach directly in the "Design doc / notes" cell (a sentence or
two) instead of linking a file under `docs/designs/`.

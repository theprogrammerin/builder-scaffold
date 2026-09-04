# Project conventions

## Feature workflow (mandatory)

Whenever a new feature is requested, follow this sequence in order. Do
not skip ahead to building. Steps 2, 3+4, and 5 are checkpoints — stop and
get the user's explicit agreement before moving to the next one; don't
collapse them into a single turn.

1. **Log it**: add a row to the "Feature requests" table in
   [`docs/backlog.md`](docs/backlog.md), status `proposed`.
2. **Prioritize**: discuss and agree with the user where it sits relative
   to other pending backlog items. Update status to `prioritized` once
   agreed.
3. **Feature-set impact**: describe how it would change
   [`docs/blueprints/features.md`](docs/blueprints/features.md) — from the
   user's point of view, before writing any code.
4. **Architecture impact**: describe how it would change
   [`docs/blueprints/architecture.md`](docs/blueprints/architecture.md) —
   which components are affected or new. Present 3 and 4 together, then
   get agreement.
5. **Design doc**: once the user agrees on the component-level changes,
   copy [`docs/designs/TEMPLATE.md`](docs/designs/TEMPLATE.md) to
   `docs/designs/<feature-slug>.md`, fill it in, and get it agreed. This
   is a permanent record — it stays after the feature ships. Update the
   backlog row to `in design`, then `building` once the doc is agreed.
6. **Build**: only after the design doc is agreed. Landing the change
   also means updating `docs/blueprints/features.md`, the relevant
   component blueprint(s), and `CHANGELOG.md` (see below) — and marking
   the backlog row `done`.

## Bug workflow (mandatory)

Whenever a bug is reported, follow this sequence in order — the same
discipline as the feature workflow above, applied to bugs. Do not skip
ahead to fixing. Steps 2, 3+4, and 5 are checkpoints — stop and get the
user's explicit agreement before moving to the next one; don't collapse
them into a single turn.

1. **Log it**: add a row to the "Bugs" table in
   [`docs/backlog.md`](docs/backlog.md), status `reported`, describing the
   observed behavior.
2. **Prioritize**: discuss and agree with the user where it sits relative
   to other pending backlog items. Update status to `prioritized` once
   agreed.
3. **Root cause + feature-set impact**: identify the root cause, and
   describe whether/how the fix changes
   [`docs/blueprints/features.md`](docs/blueprints/features.md) — from the
   user's point of view — before writing any code.
4. **Architecture impact**: describe whether/how the fix changes
   [`docs/blueprints/architecture.md`](docs/blueprints/architecture.md) —
   which components are affected. Present 3 and 4 together, then get
   agreement.
5. **Design doc**: once the user agrees on the root cause and the fix
   approach, copy [`docs/designs/TEMPLATE.md`](docs/designs/TEMPLATE.md) to
   `docs/designs/<bug-slug>.md`, fill it in, and get it agreed. Update the
   backlog row to `in design`, then `fixing` once the doc is agreed.
6. **Fix**: only after the design doc is agreed. Landing the fix also
   means updating `docs/blueprints/features.md`, the relevant component
   blueprint(s), and `CHANGELOG.md` (see below) — and marking the backlog
   row `fixed`.

## Docs

- Blueprints under [`docs/blueprints/`](docs/blueprints/) describe the
  system as it stands — concise, pointing at real code paths rather than
  restating implementation detail. No roadmap/plan content in them.
- The roadmap and feature-request queue live in
  [`docs/backlog.md`](docs/backlog.md), not in the blueprints.
- Agreed per-feature design docs live in
  [`docs/designs/`](docs/designs/), one file per feature, kept
  permanently as a record.

## Changelog

Whenever a feature is added or changed, add an entry to
[`CHANGELOG.md`](CHANGELOG.md) and update
[`docs/blueprints/features.md`](docs/blueprints/features.md) if the
current-capabilities summary is now stale. Do this in the same turn as
the change, not as a separate follow-up.

<!--
Copy this file to docs/designs/<short-feature-slug>.md when a backlog item
reaches the "in design" stage. Fill in every section before asking for
agreement — this doc is the record of what was agreed, kept permanently
even after the feature ships. See the mandatory workflow in ../../CLAUDE.md.
-->

# Design: <Feature Name>

- **Backlog item**: [`docs/backlog.md`](../backlog.md) — # <row number>
- **Status**: draft | agreed | implemented

## Summary

One or two sentences: what this feature is and why it's being built.

## Feature-set impact

What changes in [`docs/blueprints/features.md`](../blueprints/features.md)
— described from the user's point of view, not implementation detail.

## Architecture impact

What changes in [`docs/blueprints/architecture.md`](../blueprints/architecture.md)
— new components, changed data flow, updated diagrams if needed.

## Components affected

List every component that needs to change, with what changes in each.
One bullet per component; link to its blueprint under
[`docs/blueprints/components/`](../blueprints/components/).

- `component-name` — what changes and why

## Design

The actual agreed design for the component-level changes: API shapes,
data model changes, key files to add/modify. This is the section that
must be agreed before building starts.

## Out of scope

What this deliberately does not cover (defer explicitly rather than
leaving it ambiguous).

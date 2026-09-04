---
name: adopt-governance
description: Adopt the backlog/blueprints/design-doc governance workflow (from builder-scaffold) into the current project — installs the CLAUDE.md conventions and docs/ scaffolding (backlog, feature/architecture blueprints, design-doc template, changelog), merging carefully with anything already present rather than overwriting it. As an optional second step, drafts real content for backlog.md, blueprints/features.md, and blueprints/architecture.md from the existing codebase. Trigger on requests like "adopt the governance template here", "set up the backlog/blueprint workflow", "bring in the CLAUDE.md process", or "populate the backlog/architecture docs from this codebase".
---

# Adopt the governance template

This skill installs the governance workflow documented in
[`builder-scaffold`](https://github.com/theprogrammerin/builder-scaffold)
into whatever project you're currently in. It always runs **Step 1**
(structure). **Step 2** (populating docs with real content) only runs if
the user asked for it — explicitly in their request, in `args`, or by
answering yes when you ask at the end of Step 1. Never run Step 2 without
that signal; it makes claims about the codebase that need a human check.

Everything this skill copies lives under `assets/` next to this file —
it's self-contained, so this skill directory can be copied on its own
into any project's `.claude/skills/`.

## Step 1 — Install the structure

Work out the target project root first (the current working directory,
unless the user named a different one).

1. **`CLAUDE.md`**
   - If the project has no `CLAUDE.md`: copy `assets/CLAUDE.md` in as-is.
   - If it already has one: do **not** overwrite it. Read it, then insert
     the "Feature workflow (mandatory)", "Bug workflow (mandatory)",
     "Docs", and "Changelog" sections from `assets/CLAUDE.md` — verbatim,
     small-change exceptions included — under a `# Project conventions`
     heading (create one if none exists). Keep everything already in the
     file. If a section with the same name already exists (e.g. the
     project already has its own "Changelog" rule), stop and ask the user
     how to reconcile the two rather than guessing — silently picking one
     can throw away an existing convention.

2. **`CHANGELOG.md`**
   - Missing: copy `assets/CHANGELOG.md` in.
   - Present: leave it untouched. A changelog already has real history;
     don't touch its content, just confirm the "Unreleased" section
     exists (add the heading if not) since `CLAUDE.md`'s Changelog rule
     depends on it.

3. **`docs/backlog.md`, `docs/blueprints/features.md`,
   `docs/blueprints/architecture.md`,
   `docs/blueprints/components/TEMPLATE.md`, `docs/designs/TEMPLATE.md`**
   - Missing: copy the matching file from `assets/` in, preserving the
     same relative path under `docs/`.
   - Present: leave it untouched and note the conflict to the user at the
     end — don't merge these; they carry real project content that
     shouldn't be guessed at.

4. Report a short summary: what was created, what already existed and
   was left alone, and any section-name conflicts in `CLAUDE.md` that
   need the user's call. Then ask whether to proceed with Step 2.

## Step 2 — Populate docs from the codebase (optional)

Only do this when asked. Treat everything you write here as a **draft
for the user to correct**, not a finished blueprint — say so explicitly
when you present it, and follow this project's own checkpoint discipline
(don't just write the files silently; show what you found and get
agreement before treating them as final, the same way the workflow in
`CLAUDE.md` asks for agreement before treating a design as final).

1. **Survey the codebase**: entry points, package manifests
   (`package.json`, `pyproject.toml`, `go.mod`, ...), top-level
   directories that look like components/services, and any existing
   README or docs describing what the project does.

2. **`docs/blueprints/architecture.md`**: describe the system *as it
   actually stands* — what's really wired up, not aspirational. Include
   a `mermaid flowchart` of the real components and how they talk to
   each other, following the shape already in the file (Current
   implementation, optionally Target architecture only if the user
   states an agreed direction — don't invent one).

3. **`docs/blueprints/features.md`**: describe what the system can
   actually do today, from a user's point of view — not implementation
   detail, not roadmap items.

4. **`docs/blueprints/components/<name>.md`**: for each
   architecturally-significant component you found, copy
   `assets/docs/blueprints/components/TEMPLATE.md` to
   `docs/blueprints/components/<component-name>.md` and fill in Purpose
   and Key files from what you actually read in the code.

5. **`docs/backlog.md`**: only seed this from *real, already-stated*
   intent — existing `TODO`/`FIXME` markers, a `ROADMAP.md`, open GitHub
   issues the user points you at, or things the user tells you directly.
   Never invent feature requests or a phased roadmap to make the table
   look populated; an empty backlog is a more honest starting point than
   a fabricated one. Leave the "Phased roadmap" section out entirely
   unless the user actually has one.

6. Present what you drafted (or a diff/summary of it) and ask the user to
   confirm before considering it done — this mirrors the checkpoint
   discipline the workflow itself requires for every other doc change.

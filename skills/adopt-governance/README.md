# adopt-governance

A Claude Code skill that installs the
[builder-scaffold](https://github.com/theprogrammerin/builder-scaffold)
governance workflow — feature/bug checkpoints, backlog, blueprints,
design docs, changelog — into any existing project, and can optionally
draft the initial docs from the real codebase.

## Install

The skill is self-contained: the template files it installs are bundled
under `assets/`, so this one folder is all you need.

**Globally (available in every project):**

```bash
mkdir -p ~/.claude/skills
cp -R skills/adopt-governance ~/.claude/skills/adopt-governance
```

**Single project only:**

```bash
mkdir -p <project>/.claude/skills
cp -R skills/adopt-governance <project>/.claude/skills/adopt-governance
```

## Use

From inside the target project, run `/adopt-governance`, or just ask
Claude something like "adopt the governance template here" or "set up
the backlog/blueprint workflow".

### Step 1 — Install the structure (always)

| File | If missing | If it already exists |
|------|-----------|----------------------|
| `CLAUDE.md` | Created from the template | Governance sections are merged in; existing content is kept. A same-named section triggers a question, not a guess |
| `CHANGELOG.md` | Created | Left alone (an `Unreleased` heading is added if absent) |
| `docs/backlog.md` | Created | Left alone |
| `docs/blueprints/features.md`, `architecture.md` | Created | Left alone |
| `docs/blueprints/components/TEMPLATE.md`, `docs/designs/TEMPLATE.md` | Created | Left alone |

Nothing that already holds real project content is overwritten. The skill
reports what it created, what it skipped, and any conflicts that need
your call.

### Step 2 — Populate the docs (optional)

Only runs if you ask for it (in your request, as an arg like
`/adopt-governance populate`, or by saying yes when Step 1 finishes).
Claude surveys the codebase and drafts:

- `docs/blueprints/architecture.md` — the system as it stands, with a
  mermaid diagram of the real components
- `docs/blueprints/features.md` — current capabilities, from the user's
  point of view
- `docs/blueprints/components/<name>.md` — one per significant component
- `docs/backlog.md` — seeded only from intent that already exists
  (TODO/FIXME markers, a roadmap file, issues you point to). Never
  invented

The output is a draft: Claude presents it and asks you to confirm before
treating it as final.

## Layout

```
adopt-governance/
├── SKILL.md      # instructions Claude follows
├── README.md     # this file
└── assets/       # bundled copy of the template files
```

## Keeping it in sync

`assets/` is a copy of the template at the root of builder-scaffold. When
the root template changes, re-copy the changed files into
`skills/adopt-governance/assets/`, then re-install the skill wherever you
use it.

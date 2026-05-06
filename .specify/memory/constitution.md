<!--
SYNC IMPACT REPORT
==================
Version change: (uninitialized template) → 1.0.0
Bump rationale: Initial ratification — first concrete fill of the project
constitution. All placeholder tokens replaced with project-specific values.

Modified principles:
  - [PRINCIPLE_1_NAME]            → I. Documentation-First (NON-NEGOTIABLE)
  - [PRINCIPLE_2_NAME]            → II. Upstream Diff Discipline
  - [PRINCIPLE_3_NAME]            → III. Reproducible Builds
  - [PRINCIPLE_4_NAME]            → IV. Conventional Commits & Lint Gates
  - [PRINCIPLE_5_NAME]            → V. Knowledge-Graph Coherence

Added sections:
  - Quality Standards (replaces [SECTION_2_NAME])
  - Development Workflow (replaces [SECTION_3_NAME])
  - Governance (filled with concrete amendment + version policy)

Removed sections: none

Templates requiring updates:
  - .specify/templates/plan-template.md     ✅ no rewrite needed (Constitution
    Check section is abstract; principles map to it directly)
  - .specify/templates/spec-template.md     ✅ no rewrite needed (focuses on
    user stories, no constitution-coupled wording)
  - .specify/templates/tasks-template.md    ✅ no rewrite needed (phase model
    independent of these principles)
  - CLAUDE.md (project instructions)         ✅ no rewrite needed (already
    references plan + graphify; consistent with Principle V)
  - README.md                                ✅ no rewrite needed (upstream
    docs preserved; consistent with Principle II)

Follow-up TODOs: none
-->

# go-admin-doc Constitution

## Core Principles

### I. Documentation-First (NON-NEGOTIABLE)

This repository IS documentation. Every change MUST either add, correct, or
improve documentation content, examples, or the doc-site infrastructure that
serves it. Changes that do not advance the docs (e.g., speculative tooling,
unused dependencies, experimental code without a doc target) MUST be rejected.

**Rationale**: The project's sole product is the rendered site at build time;
non-doc work has no user-facing payoff and dilutes the diff history.

### II. Upstream Diff Discipline

This repo is a fork of `go-admin-team/go-admin-doc`. Changes MUST preserve the
ability to compare against and (when needed) merge from upstream:

- Do NOT rename, relocate, or restructure files that exist upstream unless the
  change is itself the documented goal.
- Local-only files (fork metadata, session logs, Spec Kit artifacts) MUST live
  in clearly fork-scoped paths or be marked with an `x_fork.` prefix so they
  are easy to identify and exclude during merges.
- The `master` branch is preserved verbatim as the upstream mirror; `main` is
  the active branch (see `x_fork.branch-origin.md`).

**Rationale**: Hard-to-revert structural changes turn future upstream merges
into manual reconciliations. A small amount of discipline up front keeps the
fork tractable.

### III. Reproducible Builds

A fresh clone MUST build successfully with the documented commands. Every
contributor and CI run MUST be able to execute, without hidden state:

- `pnpm install` (lockfile is authoritative; do NOT commit changes that break
  `pnpm install --frozen-lockfile`)
- `pnpm dev` for local preview
- `pnpm build` for the production site

Adding a dependency MUST update `package.json` and `pnpm-lock.yaml` in the
same commit. Adding a build step MUST update `README.md` if it changes the
contributor workflow.

**Rationale**: A docs site that cannot be rebuilt from `main` is a docs site
no one can publish or trust.

### IV. Conventional Commits & Lint Gates

All commits MUST follow Conventional Commits (enforced by the existing
`@commitlint/config-conventional` configuration). Staged files MUST pass the
`lint-staged` pipeline (Prettier on `*.{md,json}`) before commit.

- Husky hooks MUST NOT be bypassed (`--no-verify`) in normal work. If a hook
  fails, fix the underlying issue and create a new commit; do not amend past
  hook failures into the previous commit.
- Commit subjects SHOULD describe the *why* in 1–2 sentences; the body is the
  place for detail, not the subject.

**Rationale**: Consistent commit history is the only navigation aid this fork
will get. Bypassed hooks turn the lint gate into theater.

### V. Knowledge-Graph Coherence

The repository ships a graphify knowledge graph at `graphify-out/` that is
treated as a first-class artifact, not a generated throwaway:

- After non-trivial structural changes (file moves, renames, large content
  rewrites), contributors MUST run `graphify update .` and commit the result
  in the same PR.
- AI assistants and reviewers MUST consult `graphify-out/GRAPH_REPORT.md` (or
  `graphify-out/wiki/index.md` if present) before answering architecture or
  cross-file questions, in line with the project `CLAUDE.md` rules.
- Graph drift (graph claims X exists, repo no longer has X) is a defect and
  MUST be fixed before merge.

**Rationale**: The graph is the project's machine-readable map; letting it
rot defeats the reason it was committed.

## Quality Standards

- **Markdown style**: Prettier is the source of truth. Hand-formatted edits
  that re-flow paragraphs or change list bullet style are rejected if they
  diverge from `prettier --check`.
- **Links**: Internal links MUST be relative paths that the dumi build
  resolves; broken links found at build time block merge.
- **Images & assets**: Prefer HTTPS sources for external embeds (consistent
  with the upstream HTTPS migration). Do not commit large binary assets
  without explicit approval.
- **Localization**: When adding zh-CN/zh-TW/en variants, mirror the file path
  conventions already used by upstream; do not invent a parallel scheme.

## Development Workflow

- **Planning**: Non-trivial features (any change touching more than docs
  copy or a single config file) use the Spec Kit flow:
  `/speckit-specify` → `/speckit-clarify` (if gaps) → `/speckit-plan` →
  `/speckit-tasks` → `/speckit-implement`.
- **Branching**: Feature branches branch from `main`; `master` is reserved
  for upstream sync only. The `speckit-git-feature` extension creates
  conformant branch names.
- **Review**: Every PR MUST verify (a) all five core principles still hold,
  (b) `pnpm build` succeeds, and (c) the graphify graph is in sync if the
  PR moved or renamed files.
- **Auto-commit hooks**: Spec Kit's `before_*`/`after_*` git hooks (see
  `.specify/extensions.yml`) MAY be used to keep WIP organized; the
  resulting commits MUST still satisfy Principle IV.

## Governance

This constitution supersedes ad-hoc conventions and informal style
preferences. Where it conflicts with a contributor's habits, the constitution
wins; where it conflicts with explicit user instructions in a session,
user instructions win (per `CLAUDE.md` priority rules).

**Amendment procedure**:

1. Open a PR that modifies `.specify/memory/constitution.md` and includes an
   updated Sync Impact Report at the top of the file.
2. Justify any MAJOR or MINOR bump in the PR description.
3. Update or re-verify each template listed in the Sync Impact Report.

**Versioning policy**:

- **MAJOR** — A principle is removed, a NON-NEGOTIABLE rule is relaxed, or
  governance changes in a backward-incompatible way.
- **MINOR** — A new principle or section is added, or an existing principle
  is materially expanded.
- **PATCH** — Wording fixes, clarifications, typo repairs, or non-semantic
  refinements.

**Compliance review**: At the start of every Spec Kit `/speckit-plan` run,
the plan template's Constitution Check gate evaluates the current plan
against these five principles. Violations MUST be either resolved or
captured in the plan's Complexity Tracking table with explicit
justification.

**Version**: 1.0.0 | **Ratified**: 2026-05-07 | **Last Amended**: 2026-05-07

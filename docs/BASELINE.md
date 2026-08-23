# Project Baseline — asadullah48/asadullah48

> Frozen snapshot recorded **2026-08-22**. This is the "known state" to compare
> every future experiment against. Do not rewrite history in this file — append
> a new dated snapshot below if the baseline itself is intentionally moved.

---

## 1. What this repository is

A **GitHub profile repository**. Because the repo name matches the username
(`asadullah48/asadullah48`), GitHub renders `README.md` **from the default
branch** at the top of the user's profile page.

There is **no application code** — no `package.json`, no source tree, no tests,
no build. The deliverable is one Markdown file. Everything else is tooling
config that came along for the ride.

**Consequence:** the only thing the public ever sees is `README.md` on `main`.
Any work on another branch is invisible until merged.

---

## 2. Tracked inventory (26 files)

| Path | Purpose | Status |
|:-----|:--------|:-------|
| `README.md` | The profile page. **The only public-facing artifact.** | Active |
| `CLAUDE.md` | Project instructions for Claude Code | Active |
| `.github/workflows/snake.yml` | Daily contribution-graph snake → `output` branch | Active, working |
| `.github/workflows/neon-preview-branches-*.yml` | Neon DB preview branch per PR | **Dead config** — see §5 |
| `.claude/agents/kfc/*.md` (7 files) | Spec-workflow subagents | Branch-only — see §4 |
| `.claude/system-prompts/spec-workflow-starter.md` | Spec workflow system prompt | Branch-only |
| `.claude/settings/kfc-settings.json` | Spec workflow paths/views | Branch-only |
| `.claude/settings.local.json` | Local permission allowlist | Branch-only |
| `tmpclaude-*-cwd` (12 files) | Claude Code scratch files | **Accidentally committed** — see §5 |

Untracked at snapshot time: `.claude/worktrees/`, `nul`.
No `.gitignore` exists.

---

## 3. Branch state — THE CENTRAL ISSUE

Both branches diverged from `8e95e23` on **2026-02-13** and have been edited
**in parallel for six months**. They are not "feature branch + trunk". They are
**two competing drafts of the same README**.

```
                                    main (default → this is what the public sees)
                    ┌── 915e55c ── bcdfba3 ── a29cb1f ── 12ff5d2 ── d82d050
                    │   03-23       04-27      04-27      06-09      08-07
8e95e23 ────────────┤
 02-13  (merge base)│
                    └── cb7f293 ── 4f2c307 ── 1724995 ── f36cbb4 ── 0235ffd ── 456d212
                        02-15       02-15      03-24      04-20      04-27      08-07
                                    enhance-profile-design (current checkout, NOT public)
```

- `main` is ahead by **5** commits; `enhance-profile-design` is ahead by **6**.
- A merge **will conflict** on `README.md` (verified with `git merge-tree`).
- Both branches independently implemented the *same two ideas*:
  - "Textile ERP Platform" → `bcdfba3` (main) **and** `0235ffd` (branch)
  - "Harness × Loop × Graph" → `d82d050` (main) **and** `456d212` (branch)
  - The work was done twice, separately.

### Content comparison

| Section | on `main` | on `enhance-profile-design` |
|:--------|:---------:|:---------------------------:|
| About Me / Who I Am | ✅ "About Me" | ✅ "Who I Am" (redesigned) |
| 🏭 The Agent Factory Vision | ✅ | ❌ **missing** |
| 🧭 Harness × Loop × Graph | ✅ | ✅ |
| Flagship Project | ✅ | ✅ |
| 🔧 Engineering Expertise | ✅ | ❌ **missing** |
| 🏭 Founder — Texcot Embroidery | ❌ **missing** | ✅ |
| 🚀 Latest Ship — Textile ERP | ✅ | ✅ |
| 🚀 Live Projects | ✅ | ❌ **missing** |
| Other Projects | ✅ | ✅ |
| Tech Stack | ✅ | ✅ |
| 🌐 Domain Expertise | ❌ **missing** | ✅ |
| 2026 Focus / Roadmap | ✅ | ✅ |
| GitHub Stats / Analytics | ✅ | ✅ |
| Goals · Philosophy · Writing | ✅ | ✅ |

**Summary of the trade-off:**
- `main` carries **more content** — 3 sections the branch lacks (Agent Factory
  Vision, Engineering Expertise, Live Projects).
- `enhance-profile-design` carries **more design** — capsule-render gradient
  header/footer, animated typing SVG, GIF section icons, `<table>` two-column
  layouts, horizontal rule images, `<details>` progressive disclosure — plus 2
  sections main lacks (Founder callout, Domain Expertise).

Neither is a superset. **Merging requires a human content decision**, not a
mechanical resolution.

---

## 4. Documentation / reality mismatch

`CLAUDE.md` is **byte-identical on both branches** and documents the `.claude/`
spec-driven workflow in detail (agents, settings, `.claude/specs/{feature}/`).

But the entire `.claude/` tree exists **only on `enhance-profile-design`**.
On `main`, `CLAUDE.md` describes agents and config files that are not there.

Additionally, `.claude/settings/kfc-settings.json` points at
`.claude/specs` and `.claude/steering` — **neither directory exists** on any
branch. The spec workflow is configured but has never been used.

---

## 5. Known debris

| Item | Detail | Risk |
|:-----|:-------|:-----|
| `tmpclaude-*-cwd` × 12 | Committed scratch files, each containing the literal string `/d/asadullah48`. Tracked in git on the branch. | Cosmetic — clutters a public repo |
| No `.gitignore` | Why the scratch files got committed in the first place. Nothing stops it recurring. | Will recur |
| `nul` (0 bytes) | Windows artifact — created when a command redirected to `NUL` under a POSIX shell that treated it as a filename. Untracked. | Harmless, delete |
| Neon workflow | Runs on every PR; creates/deletes a Neon Postgres branch. Requires `NEON_API_KEY` secret + `NEON_PROJECT_ID` var. **This repo has no database.** | Dead config; fails or no-ops on every PR |
| Stale worktree | `.claude/worktrees/beautiful-elion` pinned at `8e95e23` (the Feb merge base), branch `claude/beautiful-elion`. Six months stale. | Confusing; holds an old tree on disk |
| Stash | `stash@{0}` — "temp-settings", a 3-line change to `.claude/settings.local.json` only. | Trivial, safe to drop |

---

## 6. Restore points

Every state described above is reachable by SHA. Nothing here is lost as long
as these are recorded:

```
8e95e23   merge base — last common ancestor, 2026-02-13
d82d050   tip of main (public profile as of 2026-08-07)
456d212   tip of enhance-profile-design (current checkout)
```

To inspect any version of the README without changing anything:

```bash
git show main:README.md              # what the public sees
git show enhance-profile-design:README.md
git show 8e95e23:README.md           # the pre-split original
```

To recover the working tree to a known state:

```bash
git switch --detach <sha>            # look around, changes nothing
git switch -                         # come back
```

---

## 7. Open decision (blocking, human-only)

**Which README wins?** This cannot be resolved mechanically. The options:

1. **Merge branch → main**, resolving conflicts by hand — keeps main's 3 extra
   sections *and* adopts the branch's design. Most work, best result.
2. **Adopt the branch wholesale** (`git switch main && git checkout
   enhance-profile-design -- README.md`) — gains the design, **loses** Agent
   Factory Vision, Engineering Expertise, Live Projects.
3. **Keep main, discard the branch** — loses six months of design work plus the
   Founder and Domain Expertise sections.
4. **Port section-by-section** — cherry-pick individual sections from the
   branch into main. Slowest, fully controlled, no history rewrite.

Record the choice in `docs/EXPERIMENTS.md` when made.

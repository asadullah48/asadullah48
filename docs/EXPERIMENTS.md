# Experiment Log

Running record of things tried on this repo, and whether they were **kept** or
**discarded**. Compare everything against `docs/BASELINE.md` (snapshot of
2026-08-22).

**Rule: one experiment per entry, newest at the top. Never delete an entry —
a discarded experiment is the most valuable kind of record, because it stops
you retrying the same thing in three months.**

---

## How to run an experiment safely

```bash
# 1. Anchor where you are — you can always come back to this
git tag exp/<name>-before

# 2. Work on a throwaway branch, never directly on main
git switch -c exp/<name>

# ... make changes, commit them ...

# 3a. KEEP  → merge it, then record the verdict below
git switch main && git merge exp/<name>

# 3b. DISCARD → walk away; the branch stays as a record
git switch main
#    (do NOT delete the branch — it IS the record. Just stop using it.)
```

To preview a rendered README without publishing it, push the branch and view
it at `github.com/asadullah48/asadullah48/blob/<branch>/README.md`. GitHub
renders Markdown on any branch; it only *publishes to your profile* from the
default branch.

---

## Keep / discard criteria

<!--
  TODO — YOUR INPUT NEEDED. See the note at the bottom of this file.
  Fill in the rules that decide whether an experiment stays. These are
  personal judgment calls about YOUR profile, not something to infer from
  the code. Replace this comment block with 4-6 concrete criteria.
-->

| # | Criterion | Keep if... | Discard if... |
|:-:|:----------|:-----------|:--------------|
| 1 | _(to fill in)_ | | |
| 2 | _(to fill in)_ | | |
| 3 | _(to fill in)_ | | |

---

## Entries

### EXP-001 — MCP call-to-action and evidence refresh

| | |
|:--|:--|
| **Date** | 2026-09-25 |
| **Branch** | `claude/admiring-lovelace-vps5dp` |
| **Anchor** | `main` = `7b8f072` |
| **Verdict** | **PENDING** |

**What I tried:** Four targeted README edits, no redesign:
1. New "Ask your AI about me" section with the one-line Claude Code command
   for the portfolio's MCP server.
2. Two new evidence rows: the live MCP server (6 read-only tools) and the
   portfolio's 49 backend tests, now a blocking CI gate.
3. The case-studies link now points to `#flagship-case-studies`, where the
   three architecture reviews moved to. It pointed to `#projects` before.
4. CMT Stitching System added to Selected systems.

**Why:** A profile you can connect to from your own AI is a stronger
agentic-AI signal than more badges, and every new claim links to source.
This matches the portfolio changes merged the same day (portfolio PRs #7–#9).

**What actually happened:** _(fill in after merging: profile views,
enquiries or MCP connections mentioning it)_

**Verdict reasoning:** _(pending; keep/discard criteria above are not yet
filled in)_

**Check before keeping:** the MCP endpoint must answer `initialize` with 200,
not 421, after the portfolio's Render backend redeploys (portfolio PR #8).

### EXP-000 — Baseline recorded _(not an experiment)_

| | |
|:--|:--|
| **Date** | 2026-08-22 |
| **Branch** | `enhance-profile-design` |
| **Anchor** | `main` = `d82d050` · `enhance-profile-design` = `456d212` · merge base = `8e95e23` |
| **Verdict** | **N/A — baseline** |

Full analysis captured in `docs/BASELINE.md`. Nothing changed in the repo
except the addition of `docs/`.

**Findings carried forward as open items:**

| ID | Open item | Status |
|:---|:----------|:-------|
| O-1 | `main` and `enhance-profile-design` are two competing README drafts, diverged 6 months, will conflict on merge | **OPEN — blocking, needs your decision** |
| O-2 | `CLAUDE.md` on `main` documents a `.claude/` tree that does not exist on `main` | OPEN |
| O-3 | 12 `tmpclaude-*-cwd` scratch files committed to git | OPEN |
| O-4 | No `.gitignore`, so O-3 will recur | OPEN |
| O-5 | Neon Postgres preview-branch workflow runs on every PR but this repo has no database | OPEN |
| O-6 | Stale worktree `.claude/worktrees/beautiful-elion` pinned at Feb's `8e95e23` | OPEN |
| O-7 | `nul` (0-byte Windows artifact) untracked in repo root | OPEN |
| O-8 | `.claude/specs` and `.claude/steering` are configured in `kfc-settings.json` but never created — spec workflow unused | OPEN |

---

<!--
  ══════════════════════════════════════════════════════════════════
  TEMPLATE — copy this block for each new experiment.
  ══════════════════════════════════════════════════════════════════

### EXP-00N — <short name>

| | |
|:--|:--|
| **Date** | YYYY-MM-DD |
| **Branch** | `exp/<name>` |
| **Anchor** | tag/SHA to return to if this is discarded |
| **Verdict** | **KEEP** / **DISCARD** / **PENDING** |

**What I tried:**

**Why:**

**What actually happened:**

**Verdict reasoning:** (which criterion above decided it)

**If discarded — what to avoid repeating:**

  ══════════════════════════════════════════════════════════════════
-->

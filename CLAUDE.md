# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a GitHub profile repository (`asadullah48/asadullah48`). The main README.md serves as the profile page displayed on GitHub. The repository also contains configuration for Claude Code spec-driven development workflows.

## Repository Structure

- `README.md` - GitHub profile page with portfolio information, tech stack, and project highlights
- `.github/workflows/` - GitHub Actions for automated tasks
- `.claude/` - Claude Code configuration for spec-driven development

## GitHub Actions

### Snake Animation (`snake.yml`)
Generates contribution graph snake animation daily and on manual trigger. Outputs to `output` branch.

### Neon Preview Branches (`neon-preview-branches-*.yml`)
Creates/deletes Neon database preview branches for PRs. Requires `NEON_API_KEY` secret and `NEON_PROJECT_ID` variable.

## Spec-Driven Development Workflow

This repository includes a spec workflow system in `.claude/`. The workflow transforms feature ideas into structured specifications through three phases:

1. **Requirements** → Creates EARS-format requirements document
2. **Design** → Develops comprehensive design based on requirements
3. **Tasks** → Creates actionable implementation checklist

### Spec Agents

Located in `.claude/agents/kfc/`:
- `spec-requirements` - Requirements gathering and refinement
- `spec-design` - Design document creation
- `spec-tasks` - Task list planning
- `spec-judge` - Evaluates parallel spec outputs
- `spec-impl` - Task implementation
- `spec-test` - Test creation

### Spec Configuration

- Specs stored in: `.claude/specs/{feature-name}/`
- Settings: `.claude/settings/kfc-settings.json`
- Workflow system prompt: `.claude/system-prompts/spec-workflow-starter.md`

### Using the Spec Workflow

When creating specs, the workflow supports parallel agent execution (1-128 agents) for requirements, design, and tasks phases. Each document requires explicit user approval before proceeding to the next phase.

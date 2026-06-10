---
title: CLAUDE.deps.yaml — AI Instruction Dependency Manifest
created: 2026-06-05 13:28:12
modified: 2026-06-05 13:28:12
tags:
  - status/draft
  - type/idea
aliases:
  - AI dependency manifest
  - pom.xml for AI
  - Claude playbook loader
---

# CLAUDE.deps.yaml — AI Instruction Dependency Manifest

## Context

> Where did this idea come from? What prompted you to capture it?

- **Origin**: Personal design — evolved from the observation that LLMs make mistakes and corrections require repeated manual intervention
- **Date captured**: 2026-06-05
- **Why now**: Working on technical projects where Claude needs consistent context about multiple technologies — currently this context has to be re-established every session manually
- **Parent insight**: Like `pom.xml` declares Java library dependencies, a manifest file should declare which AI instruction sets (playbooks) a project needs — and Claude should load them automatically

## Main Idea

> The core concept in your own words. One atomic idea.

A grouped YAML manifest file (`CLAUDE.deps.yaml`) per project that Claude reads at the start of every session and automatically loads the relevant technology playbooks before starting any work. Each playbook is a markdown file with conventions, patterns, and corrections for a specific technology — versioned, reusable, and shareable across projects.

## Problem Statement

> What problem does this solve?

- LLMs make mistakes, and fixing them requires developer or user intervention every time
- Corrections made in one session do not carry forward to the next
- There is no portable, versioned, composable way to declare "this project uses EKS, Helm, and GitHub Actions — here is how to handle them"
- Teams have to re-teach Claude the same conventions repeatedly across projects and sessions

## The Format (Finalized)

> Grouped YAML — concise, organized, unambiguous

```yaml
# CLAUDE.deps.yaml
version: 1
repo: ~/technical-playbooks

load:
  aws:        [eks, ecr, cdk, strimzi, cnpg]
  kubernetes: [helm]
  ci:         [actions]
```

**Resolution rule**: `{repo}/{category}/{entry}.md`

| Entry | Resolves to |
|-------|-------------|
| `aws → eks` | `~/technical-playbooks/aws/eks.md` |
| `aws → ecr` | `~/technical-playbooks/aws/ecr.md` |
| `kubernetes → helm` | `~/technical-playbooks/kubernetes/helm.md` |
| `ci → actions` | `~/technical-playbooks/ci/actions.md` |

## CLAUDE.md Integration

> The instruction that makes auto-loading work

```markdown
## Playbook Dependencies

At the start of every session, read `CLAUDE.deps.yaml` from the project root.
For each category and entry under `load`, read the file at
`{repo}/{category}/{entry}.md` before starting any work.
Do not proceed until all listed playbooks are loaded.
```

## Supporting Details

> Key design decisions made

**Why grouped YAML (Option C):**
- Concise — category acts as namespace, entries are short
- Organized — grouped by technology domain (aws, kubernetes, ci)
- Single resolution rule: `{repo}/{category}/{entry}.md` — no ambiguity
- Scales cleanly as more technologies are added

**Three artifacts to build:**
1. `CLAUDE.deps.yaml` — the manifest file (per project)
2. `~/technical-playbooks/{category}/{entry}.md` — playbook files (shared repo)
3. `CLAUDE.md` instruction — the auto-load trigger (per project)

**Playbooks first planned:**
- `aws/eks.md` — EKS cluster operations
- `aws/ecr.md` — Container registry
- `aws/cdk.md` — CDK infrastructure as code
- `aws/strimzi.md` — Kafka on Kubernetes
- `aws/cnpg.md` — CloudNativePG postgres
- `kubernetes/helm.md` — Helm chart management
- `ci/actions.md` — GitHub Actions CI/CD

## Connections

- **Related to**: [[20260603133753-gaptalk-ai-voice-exam-gap-companion]] — both address AI behavior correction and persistence
- **Related to**: [[report-card-based-personalized-learning-app]] — shares the local specialized LLM / domain-specific instruction concept
- **Inspired by**: Maven `pom.xml`, npm `package.json` — dependency declaration patterns
- **Extends**: CLAUDE.md pattern — this makes CLAUDE.md composable and technology-aware

## Questions

> What remains unclear or worth exploring further?

- What happens when a playbook file is missing — error or silent skip?
- Should playbooks support versioning? e.g. `aws: [eks@1.2, ecr@2.0]`
- How to handle conflicts between two playbooks that give contradictory instructions?
- Should `repo` support remote URLs (GitHub) not just local paths?
- Can playbooks declare their own sub-dependencies (playbook composition)?
- How to validate that Claude actually loaded all playbooks vs. skipping silently?
- Should there be a global `~/.claude/CLAUDE.deps.yaml` for user-wide defaults that projects can extend?
- Order of loading — does it matter? Should foundational playbooks load before technology-specific ones?

## Next Steps

- [ ] Create `~/technical-playbooks/` directory structure
- [ ] Write first playbook: `aws/eks.md`
- [ ] Write remaining 6 planned playbooks
- [ ] Create `CLAUDE.deps.yaml` for the active project
- [ ] Add auto-load instruction to project `CLAUDE.md`
- [ ] Test: start a session, verify Claude loads playbooks before working
- [ ] If pursuing as a tool: build a CLI that validates `CLAUDE.deps.yaml` and checks all referenced playbook files exist

---

## Metadata

**Status**: #status/draft
**Type**: Inbox capture (design concept — ready to build)
**Review Date**: 2026-06-05 — move to `05-Projects/` when actively building

---
title: Hub-Spoke Production Support Agentic System
created: 2026-06-17
modified: 2026-06-18
status: requirements
tags:
  - status/draft
  - type/project
---

# Hub-Spoke Production Support Agentic System — Agents of Agents

> One living document: requirements, decisions, ideas, and change log.

---

## Table of Contents

1. [Project Header](#project-header)
2. [Vision & Problem](#vision--problem)
3. [Architecture Overview](#architecture-overview)
4. [Functional Requirements (FR)](#functional-requirements-fr)
5. [Non-Functional Requirements (NFR)](#non-functional-requirements-nfr)
6. [Idea Evolution](#idea-evolution)
7. [Decision Log](#decision-log)
8. [Open Questions](#open-questions)
9. [Review Changes](#review-changes)

---

## Project Header

| Field | Value |
|-------|-------|
| **Project Name** | Hub-Spoke Production Support Agentic System |
| **Owner** | Sai Nagaraju Vaduka |
| **Status** | Requirements |
| **Started** | 2026-06-17 |
| **Phase** | Phase 0 — Requirements Gathering |
| **Origin** | [[20260617183527-hub-spoke-production-support-agentic-system]] |

---

## Vision & Problem

### Problem
- Production incidents require manual investigation across logs, databases, infrastructure, and application layers
- Knowledge from past incidents is lost — every RCA starts from scratch
- Night-shift / off-hours support is expensive (full-time L1/L2 engineers)
- Multiple tools, no single orchestration — context switching kills MTTR

### Vision
A generalized, extensible AI agent system that **detects, investigates, diagnoses, fixes, and learns** from production incidents — autonomously, with human approval gates at critical decision points.

### Value Proposition
> "Replace your night-shift L1 with an agent that never sleeps, remembers every incident, and gets smarter with every fix."

---

## Architecture Overview

```
                         INCIDENT INGESTION
                         (API / Webhook / Poll)
                                │
                                ▼
                    ┌───────────────────────┐
                    │      HUB AGENT        │
                    │    (Orchestrator)      │
                    └───────────┬───────────┘
           ┌──────────┬────────┼────────┬──────────┐
           ▼          ▼        ▼        ▼          ▼
      ┌─────────┐┌─────────┐┌─────────┐┌─────────┐┌─────────┐
      │  LOG    ││  DB     ││  INFRA  ││  APP    ││  DEPLOY │
      │  AGENT  ││  AGENT  ││  AGENT  ││  AGENT  ││  AGENT  │
      └─────────┘└─────────┘└─────────┘└─────────┘└─────────┘
                               │
                    ┌──────────▼──────────┐
                    │   KNOWLEDGE BASE    │
                    └─────────────────────┘
```

### Incident Lifecycle
```
DETECT → TRIAGE → INVESTIGATE → RCA → FIX → 🔒REVIEW → TEST → 🔒EXECUTE → LEARN
```

### Tiered LLM Strategy
```
Tier 1: Local LLM (cheap, fast)     → 80% of tasks (routine investigation)
Tier 2: Cloud LLM (capable, costly) → 20% of tasks (complex RCA, code fixes)
```

---

## Functional Requirements (FR)

### FR-001: Incident Ingestion
**Priority**: P0 (Must have)
**Description**: System must accept incidents from multiple sources and normalize them into a common format.

**Acceptance Criteria**:
- [ ] Accept incidents via REST API (webhook)
- [ ] Accept incidents via polling (configurable interval)
- [ ] Accept manual incident trigger (CLI or chat command)
- [ ] Normalize all sources to a common incident object schema
- [ ] Deduplicate alerts for the same underlying incident
- [ ] Assign unique incident ID

**Incident Object Schema**:
```json
{
  "id": "INC-YYYY-MM-DD-NNN",
  "source": "pagerduty | datadog | manual | ...",
  "severity": "P1 | P2 | P3 | P4",
  "title": "string",
  "timestamp": "ISO-8601",
  "metadata": {
    "service": "string",
    "environment": "string",
    "cluster": "string"
  },
  "raw_payload": {}
}
```

---

### FR-002: Hub Agent (Orchestrator)
**Priority**: P0 (Must have)
**Description**: Central orchestrator that triages incidents, dispatches to spoke agents, correlates findings, and drives the RCA workflow.

**Acceptance Criteria**:
- [ ] Classify incident severity and affected domains
- [ ] Select and dispatch to appropriate spoke agents
- [ ] Run multiple spokes in parallel
- [ ] Receive and correlate findings from all spokes
- [ ] Generate RCA document with root cause, timeline, evidence chain
- [ ] Propose fix (hotfix, config change, rollback, or scaling)
- [ ] Enforce approval gates before fix execution
- [ ] Monitor post-fix for regression (observation window)
- [ ] Store RCA + fix in knowledge base
- [ ] Close incident

---

### FR-003: Spoke Agents
**Priority**: P0 (Must have)
**Description**: Specialized domain agents that investigate specific layers of the system.

**Acceptance Criteria — All Spokes**:
- [ ] Implement standardized spoke interface (input/output contract)
- [ ] Return structured findings with confidence score and evidence
- [ ] Handle timeouts gracefully (return partial findings)
- [ ] Be addable via spoke definition YAML without hub code changes

**FR-003a: Log Agent**
- [ ] Search logs by time range, service, keyword
- [ ] Detect error patterns and anomalies
- [ ] Correlate log entries across services
- [ ] Return timeline of relevant log events

**FR-003b: DB Agent**
- [ ] Identify slow queries in the time window
- [ ] Check connection pool health
- [ ] Detect schema or migration issues
- [ ] Report database resource utilization

**FR-003c: Infra Agent**
- [ ] Check pod/node health (Kubernetes)
- [ ] Report resource utilization (CPU, memory, disk)
- [ ] Detect network issues
- [ ] Check recent scaling events

**FR-003d: App Agent**
- [ ] Analyze stack traces and error rates
- [ ] Check APM data for latency spikes
- [ ] Identify code-level issues from traces
- [ ] Correlate errors with recent code changes

**FR-003e: Deploy Agent**
- [ ] List recent deployments and config changes
- [ ] Compare current vs. previous deployment
- [ ] Prepare rollback plan
- [ ] Execute rollback (with approval)

---

### FR-004: Approval Gates
**Priority**: P0 (Must have)
**Description**: Human-in-the-loop checkpoints before irreversible actions.

**Acceptance Criteria**:
- [ ] Gate 1 — Fix Review: Present RCA + proposed fix + risk assessment
- [ ] Gate 2 — Execute: Present test results + deployment plan + rollback strategy
- [ ] Deliver approval requests via Slack/Teams/Email
- [ ] Support APPROVE / REJECT / MODIFY responses
- [ ] On REJECT: Hub re-routes for alternative approach
- [ ] Timeout handling: escalate if no response within configurable window
- [ ] Audit log every gate decision (who, when, what)

---

### FR-005: Knowledge Base
**Priority**: P1 (Should have)
**Description**: Persistent store of past RCAs, fixes, and runbooks that the system learns from.

**Acceptance Criteria**:
- [ ] Store every completed RCA with structured metadata
- [ ] Search past incidents by similarity (embedding + keyword)
- [ ] Surface similar past incidents during new investigation
- [ ] Track fix effectiveness (did the fix hold?)
- [ ] Update runbooks when new patterns are detected

---

### FR-006: Spoke Extensibility
**Priority**: P1 (Should have)
**Description**: Allow adding new spoke agents without modifying hub code.

**Acceptance Criteria**:
- [ ] Define spoke via YAML configuration
- [ ] Spoke definition includes: name, domain, capabilities, tools, triggers
- [ ] Hub auto-discovers registered spokes
- [ ] New spoke can be added at runtime (hot-plug)

**Spoke Definition Format**:
```yaml
name: custom-agent
domain: "domain description"
capabilities:
  - capability_1
  - capability_2
tools:
  - tool_name_1
triggers:
  - incident_type
  - keyword_pattern
```

---

### FR-007: Notification & Communication
**Priority**: P1 (Should have)
**Description**: Keep stakeholders informed throughout the incident lifecycle.

**Acceptance Criteria**:
- [ ] Send incident status updates to configurable channels (Slack/Teams)
- [ ] Notify on severity escalation/de-escalation
- [ ] Send RCA summary on incident closure
- [ ] Configurable notification rules per severity level

---

### FR-008: Local LLM Integration
**Priority**: P2 (Nice to have — Phase 3)
**Description**: Tiered inference model with a company-local LLM for cost reduction.

**Acceptance Criteria**:
- [ ] Route routine tasks (log parsing, pattern matching, known issue lookup) to local LLM
- [ ] Route complex tasks (RCA generation, code fix) to cloud LLM
- [ ] Configurable routing rules (which tasks go where)
- [ ] Fine-tune local model on customer's past incidents and runbooks
- [ ] Track cost per incident (local vs. cloud token usage)

---

## Non-Functional Requirements (NFR)

### NFR-001: Response Time
- Hub must begin triage within **30 seconds** of incident ingestion
- Spoke investigation should complete within **5 minutes** per spoke
- Full RCA cycle (detect → proposed fix) target: **< 15 minutes** for P1

### NFR-002: Availability
- Ingestion API must be **99.9% available** (this is production support — it can't go down)
- Spoke failures must not crash the hub — graceful degradation with partial findings

### NFR-003: Security
- Least-privilege access per spoke (each spoke only gets permissions it needs)
- All actions logged in immutable audit trail
- Secrets management for tool credentials (Vault or equivalent)
- Customer data stays in customer's environment (no data exfiltration)

### NFR-004: Scalability
- Handle **50+ concurrent incidents** without degradation
- Support **20+ registered spokes** per deployment
- Knowledge base must handle **10,000+ past incidents** with sub-second search

### NFR-005: Extensibility
- Adding a new spoke: < 1 hour (YAML + tool integration)
- Adding a new ingestion source: < 4 hours (adapter pattern)
- Adding a new notification channel: < 2 hours

### NFR-006: Observability
- The system that monitors production must itself be observable
- Metrics: incidents handled, MTTR, spoke response times, LLM token usage, fix success rate
- Dashboard for system health and incident trends

### NFR-007: Cost
- Track LLM token cost per incident
- Target: < $5 per P1 incident resolution (with local LLM at scale)
- Report monthly cost breakdown: local LLM vs. cloud LLM

---

## Idea Evolution

> Track how the idea has changed over time

| Date | Change | Reason |
|------|--------|--------|
| 2026-06-17 | Initial idea captured | Personal insight — need for autonomous production support |
| 2026-06-17 | Added business model: managed service vs. token billing | Need revenue model before building |
| 2026-06-17 | Added local LLM strategy: tiered inference (80/20 split) | Reduce cost, increase margin, create competitive moat |
| 2026-06-17 | Added key takeaways summary | Crystallize the core value propositions |
| 2026-06-18 | Moved to project status, created requirements document | Ready to formalize and build |

---

## Decision Log

> Record every significant decision with context

| ID | Date | Decision | Options Considered | Rationale |
|----|------|----------|-------------------|-----------|
| D-001 | 2026-06-17 | Hub-Spoke over flat agent pool | Hub-Spoke, Flat pool, Hierarchical tree | Hub-Spoke balances specialization with central coordination. Flat pool lacks orchestration. Tree adds unnecessary complexity. |
| D-002 | 2026-06-17 | Two business models (managed + token) | Managed only, Token only, Both | Both gives flexibility — enterprise wants managed, startups want pay-per-use. |
| D-003 | 2026-06-17 | Tiered LLM (local + cloud) | Cloud only, Local only, Tiered | Cloud-only is expensive at scale. Local-only lacks capability for complex RCA. Tiered gives best of both. |
| D-004 | 2026-06-18 | Single idea.md as living document | Separate PRD + decision log + changelog, Single file | Single file reduces context switching. Everything about the project lives in one place. |

---

## Open Questions

> Unresolved questions that need answers before or during build

| ID | Question | Priority | Status |
|----|----------|----------|--------|
| Q-001 | Which framework: Claude Agent SDK, LangGraph, CrewAI, or custom? | P0 | Open |
| Q-002 | Which open-source LLM to fine-tune for local tier? (Llama 3, Mistral, Qwen) | P2 | Open |
| Q-003 | How do spokes communicate — only through hub or peer-to-peer? | P1 | Open |
| Q-004 | Where does incident state live — DB, in-memory, event log? | P1 | Open |
| Q-005 | How to deduplicate alerts from multiple monitoring sources? | P1 | Open |
| Q-006 | What pricing makes a "virtual support candidate" competitive vs. hiring? | P2 | Open |
| Q-007 | How to validate proposed fixes don't introduce regressions? | P1 | Open |
| Q-008 | Approval gate timeout — escalate to whom? | P1 | Open |
| Q-009 | Target customer segment — SaaS, enterprise, or own team first? | P0 | Open |
| Q-010 | MVP: which 2 spokes to build first? | P0 | Open |

---

## Review Changes

> Log every review and what changed

| Date | Reviewer | Changes Made | Notes |
|------|----------|-------------|-------|
| 2026-06-18 | Sai | Initial requirements document created | Moved from inbox idea to project. FR-001 through FR-008, NFR-001 through NFR-007 defined. |

---

*Last updated: 2026-06-18*

---
title: Hub and Spoke Production Support Agentic System — Agents of Agents
created: 2026-06-17 18:35:27
modified: 2026-06-17 19:00:00
tags:
  - status/draft
  - type/idea
aliases:
  - Production support agents
  - Hub spoke agentic bots
  - Agents of agents
  - Autonomous production support
---

# Hub and Spoke Production Support Agentic System — Agents of Agents

## Context

- **Origin**: Personal design / professional need
- **Date captured**: 2026-06-17
- **Why now**: AI agents are capable enough to handle production support workflows — from detection through RCA to fix. No generalized, extensible framework exists for orchestrating multiple specialized agents around production incidents.

## Main Idea

Build a **generalized, extensible** production support system using a **Hub and Spoke architecture** where a central orchestrator agent (Hub) coordinates specialized domain agents (Spokes) to detect, investigate, diagnose, fix, and learn from production incidents — autonomously, with human approval gates at critical decision points.

The system follows the full incident lifecycle: **Detect → Triage → Investigate → RCA → Fix → Review → Test → Execute → Learn**.

## Architecture

### Hub and Spoke Model

```
                         INCIDENT INGESTION
                         (API / Webhook / Poll)
                                │
                                ▼
                    ┌───────────────────────┐
                    │      HUB AGENT        │
                    │    (Orchestrator)      │
                    │                       │
                    │  • Triage & classify   │
                    │  • Route to spokes     │
                    │  • Correlate findings  │
                    │  • Drive RCA workflow  │
                    │  • Enforce gates       │
                    │  • Report & learn      │
                    └───────────┬───────────┘
           ┌──────────┬────────┼────────┬──────────┐
           ▼          ▼        ▼        ▼          ▼
      ┌─────────┐┌─────────┐┌─────────┐┌─────────┐┌─────────┐
      │  LOG    ││  DB     ││  INFRA  ││  APP    ││  DEPLOY │
      │  AGENT  ││  AGENT  ││  AGENT  ││  AGENT  ││  AGENT  │
      │         ││         ││         ││         ││         │
      │ Search  ││ Query   ││ K8s     ││ Code    ││ CI/CD   │
      │ Parse   ││ Explain ││ Health  ││ Trace   ││ Rollback│
      │ Pattern ││ Perf    ││ Scale   ││ Profile ││ Deploy  │
      └─────────┘└─────────┘└─────────┘└─────────┘└─────────┘
           │          │        │        │          │
           └──────────┴────────┴────────┴──────────┘
                               │
                    ┌──────────▼──────────┐
                    │   KNOWLEDGE BASE    │
                    │  (Past RCAs, fixes, │
                    │   runbooks, patterns)│
                    └─────────────────────┘
```

### Full Incident Lifecycle

```
DETECT ──► TRIAGE ──► INVESTIGATE ──► RCA ──► FIX ──► REVIEW ──► TEST ──► EXECUTE ──► LEARN
  │          │            │           │        │        │          │         │           │
  │          │            │           │        │        │          │         │           │
Ingestion  Hub classifies Spokes run  Hub     Spoke    🔒 GATE   Spoke    🔒 GATE    Hub stores
API polls  severity,     parallel    correlates generates Approval runs     Approval   RCA + fix
alerts     routes to     investigation findings  hotfix  required  tests   required   in knowledge
           right spokes                         or fix                                 base
```

### Approval Gates (Human-in-the-Loop)

```
🔒 GATE 1: Fix Review
   Hub presents: RCA summary + proposed fix + risk assessment
   Human: APPROVE / REJECT / MODIFY
   On REJECT: Hub re-routes to spokes for alternative approach

🔒 GATE 2: Execute
   Hub presents: Test results + deployment plan + rollback strategy
   Human: APPROVE / REJECT
   On REJECT: Hub halts, preserves state for manual intervention
```

## Spoke Agents (Extensible)

> Each spoke is a specialized agent. New spokes can be added as needed.

### Core Spokes (Ship with v1)

| Spoke | Domain | Capabilities |
|-------|--------|-------------|
| **Log Agent** | Observability | Search logs, pattern match, anomaly detection, correlation |
| **DB Agent** | Database | Query analysis, slow query detection, connection pool health, schema checks |
| **Infra Agent** | Infrastructure | K8s pod/node health, resource utilization, network, storage |
| **App Agent** | Application | Stack traces, error rates, APM data, code-level investigation |
| **Deploy Agent** | CI/CD | Recent deployments, config changes, rollback capability |

### Extension Spokes (Add per team's needs)

| Spoke | Domain | Capabilities |
|-------|--------|-------------|
| **Security Agent** | Security | CVE scan, access anomalies, secrets exposure |
| **Network Agent** | Networking | DNS, load balancer, latency, certificate expiry |
| **Cloud Agent** | Cloud Provider | AWS/Azure/GCP resource health, billing anomalies |
| **Dependency Agent** | External | Third-party API health, SLA tracking |
| **Comms Agent** | Communication | Status page updates, stakeholder notifications |

### How to Add a New Spoke

```yaml
# spoke-definition.yaml
name: custom-agent
domain: "custom domain description"
capabilities:
  - capability_1
  - capability_2
tools:
  - tool_name_1
  - tool_name_2
triggers:
  - incident_type_1
  - keyword_pattern
```

## Incident Ingestion

> Multiple ingestion channels, all normalizing to a common incident object

**Ingestion Sources:**
- **Webhook API**: PagerDuty, OpsGenie, Datadog, CloudWatch → POST to ingestion endpoint
- **Polling Agent**: Periodically checks monitoring systems for new alerts
- **Manual**: Engineer triggers investigation via CLI or chat command
- **Event Stream**: Subscribe to Kafka/SQS topic for real-time events

**Normalized Incident Object:**
```json
{
  "id": "INC-2026-06-17-001",
  "source": "pagerduty",
  "severity": "P1",
  "title": "API latency spike > 5s on /orders endpoint",
  "timestamp": "2026-06-17T18:30:00Z",
  "metadata": {
    "service": "order-service",
    "environment": "production",
    "cluster": "eks-prod-01"
  },
  "raw_payload": { }
}
```

## RCA Workflow (Hub Orchestration)

> The Hub drives this end-to-end, coordinating spokes at each step

```
Step 1: CLASSIFY
  Hub reads incident → determines severity, affected domain(s)
  Hub selects which spokes to activate

Step 2: PARALLEL INVESTIGATION
  Hub dispatches to 2-5 spokes simultaneously
  Each spoke returns structured findings:
  {
    "spoke": "log-agent",
    "findings": [...],
    "confidence": 0.85,
    "evidence": [...]
  }

Step 3: CORRELATE & DIAGNOSE (RCA)
  Hub receives all spoke findings
  Hub cross-references: timeline, causality, blast radius
  Hub generates RCA document:
  - Root cause
  - Contributing factors
  - Timeline of events
  - Affected systems
  - Evidence chain

Step 4: PROPOSE FIX
  Hub determines fix type:
  - Hotfix: code change (App Agent generates patch)
  - Config fix: infrastructure change (Infra Agent generates manifest)
  - Rollback: revert deployment (Deploy Agent prepares rollback)
  - Scaling: temporary mitigation (Infra Agent scales resources)

Step 5: 🔒 APPROVAL GATE — Fix Review
  Hub presents RCA + proposed fix to human
  Human approves / rejects / modifies

Step 6: TEST
  Spoke runs fix in staging / dry-run
  Spoke reports test results

Step 7: 🔒 APPROVAL GATE — Execute
  Hub presents test results + deployment plan
  Human approves execution

Step 8: EXECUTE
  Spoke applies fix in production
  Hub monitors for regression (5-15 min observation window)

Step 9: LEARN
  Hub stores RCA + fix in Knowledge Base
  Hub updates runbooks if new pattern detected
  Hub closes incident
```

## Generalization & Extensibility

> Designed to be technology-agnostic and extensible

**Generalization Principles:**
- Spoke interface is standardized — any tool/platform can be wrapped as a spoke
- Hub orchestration logic is domain-agnostic — it reasons about findings, not technologies
- Incident object is normalized — any monitoring source can feed in
- Knowledge Base grows with every incident — the system gets smarter over time

**Extension Points:**
1. Add new spoke agents (via spoke definition YAML)
2. Add new ingestion sources (via webhook or adapter)
3. Add custom approval workflows (more gates, different approvers per severity)
4. Add notification channels (Slack, Teams, email, PagerDuty)
5. Add custom RCA templates per team/domain

## Connections

- **Related to**: [[20260605132812-claude-deps-yaml-ai-instruction-dependency-manifest]] — spoke definitions are similar to dependency declarations
- **Related to**: Hub and spoke architecture patterns in distributed systems
- **Related to**: SRE / DevOps incident management workflows
- **Related to**: Multi-agent orchestration (Claude Agent SDK, LangGraph, CrewAI)

## Questions

> What remains unclear or worth exploring further?

**Architecture:**
- What framework to build on — Claude Agent SDK? LangGraph? Custom?
- How do spokes communicate with each other (only through hub, or peer-to-peer for correlated investigation)?
- State management — where does incident state live during investigation? (DB? In-memory? Event log?)
- How to handle spoke failures or timeouts mid-investigation?

**Ingestion:**
- Which monitoring tools to integrate first?
- How to deduplicate alerts that fire multiple times for the same incident?
- Alert fatigue — how does the hub distinguish noise from real incidents?

**RCA & Fix:**
- How autonomous should the fix generation be? (Suggest only vs. generate code patch?)
- How to validate a proposed fix doesn't introduce regressions?
- Rollback strategy if the fix makes things worse?
- How to handle incidents that span multiple domains (e.g., DB + Infra + App)?

**Knowledge Base:**
- What data structure for storing past RCAs for retrieval?
- How does the hub search for similar past incidents? (Embedding similarity? Keyword? Both?)
- How to prevent knowledge base from becoming stale?

**Trust & Safety:**
- Least-privilege: what permissions does each spoke need?
- Audit trail: how is every action logged for compliance?
- Blast radius limits: what's the maximum action a spoke can take without approval?

## Business Model & Monetization (2026-06-17 update)

> Two revenue model options — not mutually exclusive

**Option A — Managed Service (Production Support Candidate):**
- We provide a fully managed "production support candidate" — the agentic system acts as a virtual L1/L2 support engineer
- Customer pays a flat monthly fee (like hiring a support person, but cheaper)
- We handle hosting, LLM costs, spoke maintenance, knowledge base updates
- Pricing: fraction of a full-time support engineer salary
- Value prop: "Replace your night-shift L1 with an agent that never sleeps"

**Option B — LLM Token Cost Pass-Through:**
- Customer runs the system, we charge based on LLM token usage
- Markup on token costs (our margin) + platform fee
- Customer pays per incident or per token consumed
- Lower upfront commitment, usage-based scaling

**Local LLM Strategy (Cost Reduction):**
- Build/fine-tune a **company-local LLM** deployed on-premise or in their VPC
- Dramatically reduces per-token cost vs. API calls to Claude/GPT
- The local LLM handles routine spoke tasks (log parsing, pattern matching, known issue lookup)
- Escalate to a more capable model (Claude/GPT) only for complex RCA and fix generation
- This creates a **tiered inference model**:
  ```
  Tier 1: Local LLM (cheap, fast)     → 80% of tasks (routine investigation)
  Tier 2: Cloud LLM (capable, costly) → 20% of tasks (complex RCA, code fixes)
  ```
- Research needed: which open-source base model to fine-tune? (Llama, Mistral, Qwen?)
- Training data: past RCAs, runbooks, incident logs from the customer's own environment
- The more incidents the system handles, the better the local model becomes — flywheel effect

**Combined Model (Recommended):**
- Offer both options: managed service OR self-hosted with token billing
- Local LLM reduces cost for both models — our margin improves, customer pays less
- Upsell: "Start with cloud LLM → we fine-tune a local model after 100 incidents → your costs drop 60%"

## Tech Stack (Potential)

- **Hub**: Claude Agent SDK or custom orchestrator
- **Spokes**: Individual Claude agents with MCP tools per domain
- **Local LLM**: Fine-tuned open-source model (Llama/Mistral) for routine spoke tasks
- **Cloud LLM**: Claude API for complex reasoning (RCA, fix generation)
- **Ingestion**: FastAPI webhook server + polling adapters
- **State**: PostgreSQL or event log (Kafka)
- **Knowledge Base**: Vector DB (pgvector) + structured RCA store
- **Communication**: Slack/Teams integration for approval gates
- **Deployment**: Kubernetes (the agents manage K8s, and run on K8s)

## Next Steps

- [ ] Design the spoke interface contract (input/output schema)
- [ ] Design the hub orchestration state machine
- [ ] Build prototype: Hub + 2 spokes (Log Agent + Infra Agent)
- [ ] Build ingestion API (webhook endpoint)
- [ ] Test with a simulated P1 incident
- [ ] Research open-source LLMs for local fine-tuning (Llama 3, Mistral, Qwen)
- [ ] Estimate token cost savings: cloud-only vs. tiered local+cloud model
- [ ] Define pricing: managed service monthly fee vs. per-token billing
- [ ] If pursuing: move to `05-Projects/2026-06-Production-Support-Agents/`

---

## Metadata

**Status**: #status/draft
**Type**: Inbox capture (architecture + product concept — ready to design & implement)
**Review Date**: 2026-06-17 — move to `05-Projects/` when actively building

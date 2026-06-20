# Tools, Metrics, KPIs, and Team Structures for Production Support

> Research compiled: 2026-06-20
> Purpose: Catalog the tooling landscape, key metrics, and team models to inform agent system design

---

## 1. Monitoring & Observability Tools

### Infrastructure Monitoring

| Tool | Type | Key Strengths | Pricing Model |
|------|------|---------------|---------------|
| **Datadog** | Full-stack observability | Unified platform (metrics, logs, traces, APM, RUM, security), 700+ integrations | Per host/month ($15 infra, $31 APM, $0.10/GB logs) |
| **Dynatrace** | AI-powered APM | Davis AI auto-RCA, OneAgent auto-discovery, full-stack topology mapping | Per host ($69/8GB host full-stack, $21 infra-only) |
| **New Relic** | Full-stack observability | Consumption-based pricing, free tier (100GB/mo), strong APM | Per GB ingested ($0.30-$0.50/GB) + per user ($549-$699/mo) |
| **Grafana + Prometheus** | Open-source metrics | De facto K8s monitoring stack, highly customizable, large community | Free (OSS), Grafana Cloud from $29/user/mo |
| **CloudWatch** | AWS native | Deep AWS integration, no additional agents needed, cost-effective for AWS-only | Pay per metric/alarm/dashboard |
| **Azure Monitor** | Azure native | Application Insights for APM, Log Analytics, deep Azure integration | Pay per GB ingested |
| **AppDynamics** (Cisco) | Enterprise APM | Business iQ correlates app perf with business metrics, strong Java/.NET | Per CPU core ($33-$60/core/mo) |
| **Zabbix** | Open-source infra | Agent-based, good for traditional/on-prem infrastructure, free | Free (OSS), enterprise support available |

### Log Management

| Tool | Key Strengths | Pricing |
|------|---------------|---------|
| **Splunk** | Market-leading SIEM + log analytics, SPL query language, 85+ of Fortune 100 | $150-$250/GB/day (varies by commitment) |
| **ELK Stack** (Elastic) | Open-source, Kibana visualization, Beats collectors | Free (OSS), Elastic Cloud from $95/mo |
| **Loki** (Grafana) | Label-based log aggregation, pairs with Grafana, K8s-native | Free (OSS), Grafana Cloud included |
| **Sumo Logic** | Cloud-native, built-in compliance dashboards | $2.08-$3.60/GB/day |
| **Fluentd / Fluent Bit** | Log forwarding/routing (CNCF), lightweight, pluggable | Free (OSS) |

### Distributed Tracing

| Tool | Key Strengths | Notes |
|------|---------------|-------|
| **Jaeger** | CNCF project, popular for K8s microservices | Free (OSS) |
| **Zipkin** | Lightweight, easy setup, broad language support | Free (OSS) |
| **OpenTelemetry** | Vendor-neutral standard for metrics, logs, traces | Free (OSS), backed by CNCF |
| **Tempo** (Grafana) | Pairs with Grafana, cost-effective large-scale tracing | Free (OSS) |

### Synthetic Monitoring

| Tool | Purpose |
|------|---------|
| **Datadog Synthetics** | API + browser tests from global locations |
| **Checkly** | Developer-focused, Playwright-based browser checks |
| **Pingdom** | Simple uptime monitoring, alerting |
| **Better Uptime** (Better Stack) | Status page + uptime monitoring combined |
| **UptimeRobot** | Free tier for basic HTTP monitoring |

---

## 2. Incident Management Tools

### Alerting & On-Call

| Tool | Market Position | Key Features | Pricing |
|------|----------------|--------------|---------|
| **PagerDuty** | Market leader | Event intelligence (ML correlation), 700+ integrations, runbook automation, stakeholder notifications | Free (5 users), $21-$59/user/mo |
| **OpsGenie** (Atlassian) | Strong #2 | Deep Jira integration, heartbeat monitoring, lower cost | Free (5 users), $9.45-$35.45/user/mo |
| **Splunk On-Call** (VictorOps) | Cisco/Splunk ecosystem | Integrated with Splunk observability suite | Free (starter), ~$9/user/mo |
| **Grafana OnCall** | Open-source | Pairs with Grafana stack, ChatOps native, free for Grafana Cloud users | Free (OSS), included in Grafana Cloud |

### Incident Response Platforms

| Tool | Key Features | Notes |
|------|--------------|-------|
| **incident.io** | Slack-native incident management, automated workflows, post-incident reporting | Popular with modern SaaS companies |
| **Rootly** | Slack-based, automated status page updates, retrospective templates | Strong automation features |
| **FireHydrant** | Full incident lifecycle, service catalog, change tracking, analytics | Comprehensive platform |
| **Blameless** | SLO management + incident response + retrospectives combined | SRE-focused |

### ITSM Platforms

| Tool | Market Position | Key Features | Pricing |
|------|----------------|--------------|---------|
| **ServiceNow** | Dominant enterprise ITSM | ITSM, ITOM, CMDB, GRC, Security Ops, AIOps — used by 80%+ of Tier-1 banks and 55-65% of Tier-1 telecom carriers | Custom ($100-$150/user/mo typical) |
| **Jira Service Management** | Strong mid-market | Deep Jira Software integration, SLA tracking, asset management | Free (3 agents), $22-$49/agent/mo |
| **Freshservice** | Growing mid-market | AI agent Freddy, intuitive UI, fast setup | $19-$119/agent/mo |
| **BMC Helix** (Remedy) | Enterprise legacy | Strong in telecom and government, ITIL-heavy | Custom enterprise pricing |
| **Zendesk** | Customer support focus | More customer-facing than IT-facing, strong ticketing and knowledge base | $55-$115/agent/mo |

---

## 3. Runbook Automation & Chaos Engineering

### Runbook Automation

| Tool | Key Features | Notes |
|------|--------------|-------|
| **PagerDuty Runbook Automation** (Rundeck) | Job scheduling, SSH/WinRM execution, approval workflows, audit trail | Formerly Rundeck, acquired by PagerDuty |
| **StackStorm** | Event-driven automation, IFTTT for ops, pack ecosystem | Open-source, strong community |
| **AWS Systems Manager** | Run Command, Automation, Patch Manager, Parameter Store | AWS native, free for EC2 instances |
| **Ansible** (Red Hat) | Agentless automation, playbooks, idempotent execution | Free (OSS), Ansible Tower/AAP for enterprise |
| **Shoreline.io** | Real-time automated remediation, Op packs for common issues | Focuses on auto-remediation |

### Chaos Engineering

| Tool | Key Features | Notes |
|------|--------------|-------|
| **Gremlin** | Enterprise chaos platform, GameDay exercises, safety controls | Commercial, most mature |
| **LitmusChaos** | CNCF project, K8s-native, ChaosHub experiment library | Free (OSS) |
| **Chaos Monkey** (Netflix) | Original chaos tool, random instance termination | Free (OSS), part of Simian Army |
| **AWS Fault Injection Simulator** | Managed chaos engineering on AWS, integrates with CloudWatch | AWS native, pay per action-minute |
| **Steadybit** | Reliability platform with experiment marketplace | Commercial |

---

## 4. AIOps Tools

| Tool | Key Capability | Adoption |
|------|---------------|----------|
| **Moogsoft** (BMC) | AI-driven event correlation, 90%+ alert noise reduction | Pioneered AIOps category |
| **BigPanda** | Open Box ML for alert correlation, 95% noise reduction, change correlation | Enterprise focus |
| **Dynatrace Davis AI** | Deterministic (not probabilistic) AI — important for auditable decisions in regulated industries | Built into Dynatrace platform |
| **ServiceNow AIOps** | Predictive AIOps, event management, metric anomaly detection | Add-on to ServiceNow ITOM |
| **IBM Watson AIOps** | Topology-aware analytics, natural language incident querying | Part of IBM Cloud Pak for Watson AIOps |
| **Datadog Watchdog** | Automatic anomaly detection across all Datadog metrics | Built into Datadog platform |

---

## 5. Key Metrics & KPIs

### Incident Metrics

| Metric | Formula | Industry Benchmark | What It Measures |
|--------|---------|-------------------|-----------------|
| **MTTD** (Mean Time to Detect) | Avg(incident_start → first_alert) | Elite: < 5 min, Good: < 30 min | Monitoring effectiveness |
| **MTTA** (Mean Time to Acknowledge) | Avg(first_alert → human_ack) | Elite: < 5 min, Good: < 15 min | On-call responsiveness |
| **MTTI** (Mean Time to Investigate) | Avg(ack → root_cause_identified) | Varies by complexity | Investigation efficiency |
| **MTTR** (Mean Time to Resolve) | Avg(detection → full_resolution) | Elite: < 1 hr, Good: < 4 hrs | Overall incident handling |
| **MTBF** (Mean Time Between Failures) | Total_uptime / number_of_failures | Higher is better — target increasing trend | System reliability |
| **Incident Volume** | Count of incidents per period | Trend should decrease over time | System stability |
| **Recurrence Rate** | Repeated incidents / total incidents | < 10% is healthy | Fix effectiveness |
| **Escalation Rate** | Escalated incidents / total incidents | < 20% is healthy | L1 effectiveness |

### DORA Metrics (DevOps Research & Assessment)

| Metric | Elite | High | Medium | Low |
|--------|-------|------|--------|-----|
| **Deployment Frequency** | On-demand (multiple/day) | Weekly to monthly | Monthly to 6-monthly | > 6 months |
| **Lead Time for Changes** | < 1 hour | 1 day to 1 week | 1 week to 1 month | > 1 month |
| **Change Failure Rate** | < 5% | 5-15% | 15-30% | > 45% |
| **MTTR** (Failed deployment recovery) | < 1 hour | < 1 day | < 1 week | > 1 week |

### Four Golden Signals (Google SRE)

| Signal | What to Measure | Example SLI |
|--------|----------------|-------------|
| **Latency** | Time to serve a request | p50 < 100ms, p99 < 500ms |
| **Traffic** | Demand on the system | Requests/sec, transactions/sec |
| **Errors** | Rate of failed requests | Error rate < 0.1% |
| **Saturation** | How "full" the system is | CPU < 70%, memory < 80% |

### SLA/SLO Performance

| Metric | What It Tracks |
|--------|---------------|
| **SLA Compliance %** | Percentage of time SLA targets were met |
| **Error Budget Remaining** | How much allowed downtime remains in the window |
| **Error Budget Burn Rate** | Rate of error budget consumption (alert when > 1x) |
| **SLA Credits Issued** | Financial impact of SLA breaches |

### On-Call Health Metrics

| Metric | Target |
|--------|--------|
| Pages per on-call shift | < 5 (Google SRE recommends < 2 during sleeping hours) |
| False positive rate | < 20% of all pages |
| Time to acknowledge | < 5 minutes for P1 |
| On-call satisfaction score | Track via survey — leading indicator of attrition |
| Handoff completeness | All ongoing issues documented at shift change |

### Cost Metrics

| Metric | Purpose |
|--------|---------|
| Cost per incident | Total cost (people time + tool cost + revenue impact) |
| LLM token cost per incident | Track AI agent cost per resolution |
| Infrastructure cost efficiency | Spend / number of transactions served |
| Alert noise ratio | Non-actionable alerts / total alerts |

---

## 6. Team Structures

### Tiered Support Model (Traditional)

```
┌──────────────────────────────────────────────┐
│  L1 — First Responder / Service Desk        │
│  • Handle known issues from runbooks         │
│  • Basic triage and ticket logging           │
│  • Resolve 60-70% of incidents              │
│  • Escalate unknowns to L2                   │
├──────────────────────────────────────────────┤
│  L2 — Domain Expert                          │
│  • Deep investigation, system-specific       │
│  • Requires 2-5 years experience             │
│  • Resolve 20-30% of incidents              │
│  • Escalate code-level issues to L3          │
├──────────────────────────────────────────────┤
│  L3 — Engineering                            │
│  • Code-level debugging, architectural fixes │
│  • Developers who built the system           │
│  • Resolve remaining 5-10%                   │
│  • Create permanent fixes, update codebase   │
└──────────────────────────────────────────────┘
```

**Pros**: Clear escalation path, L1 is cost-effective, specialization at each tier
**Cons**: Knowledge silos, slow escalation, L1 burnout from repetitive work, context lost between tiers

### SRE Model (Google-Style)

```
┌──────────────────────────────────────────────┐
│  SRE Team (embedded or centralized)          │
│  • Own service reliability (SLOs, error      │
│    budgets, on-call, incident response)      │
│  • 50% ops work / 50% engineering work       │
│  • Toil budget: < 50% of time on toil       │
│  • Software engineering approach to ops      │
│  • Write automation to eliminate toil        │
├──────────────────────────────────────────────┤
│  Product Engineering Team                     │
│  • Own feature development                   │
│  • Share on-call when error budget exhausted  │
│  • Participate in incident response for      │
│    their services                            │
└──────────────────────────────────────────────┘
```

**Pros**: Engineering-driven, reduces toil over time, shared ownership
**Cons**: Requires senior engineers (expensive), can create tension with product teams, not every org is ready

### DevOps / "You Build It, You Run It" Model

```
┌──────────────────────────────────────────────┐
│  Cross-Functional Product Team               │
│  • Developers own their services end-to-end  │
│  • Team handles their own on-call            │
│  • No separate ops team                      │
│  • Full ownership: build, deploy, monitor,   │
│    support, fix                              │
├──────────────────────────────────────────────┤
│  Platform Engineering Team (optional)        │
│  • Provide shared tooling and infrastructure │
│  • Build internal developer platform         │
│  • Don't own product services                │
└──────────────────────────────────────────────┘
```

**Pros**: Fastest feedback loop, no handoff delays, full ownership
**Cons**: High on-call burden on developers, inconsistent practices across teams, requires mature tooling

### NOC (Network Operations Center) Model

```
┌──────────────────────────────────────────────┐
│  NOC — 24/7 Staffed Operations Center        │
│  • Real-time monitoring of all systems       │
│  • Follow standardized runbooks              │
│  • Triage and escalate to engineering        │
│  • Handle routine tasks (cert renewals,      │
│    restarts, scaling)                        │
│  • Maintain dashboards and status pages      │
├──────────────────────────────────────────────┤
│  Engineering On-Call (L2/L3)                 │
│  • NOC escalates when runbooks are           │
│    insufficient                              │
│  • Engineers respond to novel incidents      │
└──────────────────────────────────────────────┘
```

**Pros**: 24/7 coverage without developer on-call, standardized procedures, good for compliance-heavy industries
**Cons**: Expensive (staff + facilities), limited troubleshooting depth, can become bottleneck

### Follow-the-Sun Model

```
┌────────────────────────────────────────────────────────┐
│  APAC (UTC+8 to +12)   │  EMEA (UTC+0 to +3)  │  Americas (UTC-5 to -8) │
│  8:00-17:00 local       │  8:00-17:00 local      │  8:00-17:00 local       │
│                         │                        │                         │
│  Team handles all       │  Team handles all      │  Team handles all       │
│  incidents during       │  incidents during      │  incidents during       │
│  their business hours   │  their business hours  │  their business hours   │
└────────────────────────────────────────────────────────┘
                     ↻ 24-hour continuous coverage ↻
```

**Pros**: No night shifts, each team works normal hours, global coverage
**Cons**: Requires 3 teams (expensive), handoff quality critical, cultural/communication challenges, knowledge gaps between regions

### Hybrid Model (Most Common in Practice)

```
┌──────────────────────────────────────────────┐
│  Platform/SRE Team (Core Hours)              │
│  • Own shared infrastructure and tooling     │
│  • Incident coordination for P0/P1          │
│  • Automation and reliability engineering    │
├──────────────────────────────────────────────┤
│  Product Teams (Core Hours)                  │
│  • Own their services' on-call              │
│  • Handle service-specific incidents         │
├──────────────────────────────────────────────┤
│  NOC / Managed Service (Off Hours)           │
│  • Monitor dashboards after hours           │
│  • Execute runbooks for known issues        │
│  • Escalate to on-call engineers for novel  │
│    issues                                   │
└──────────────────────────────────────────────┘
```

**Pros**: Balances cost and capability, developers own their services but aren't on-call 24/7, NOC provides coverage
**Cons**: Complex to coordinate, requires clear escalation paths, handoff points can cause delays

---

## 7. Team Sizing & Staffing Ratios

### Industry Benchmarks

| Model | Typical Ratio | Notes |
|-------|---------------|-------|
| L1 Support : Services | 1 : 5-10 | Depends on incident volume and automation level |
| L2 Support : Services | 1 : 10-20 | Domain experts cover broader area |
| SRE : Developers | 1 : 8-10 | Google's original ratio; varies widely |
| On-call roster minimum | 4-6 engineers per rotation | Prevents burnout (1 week in 4-6 rotation) |
| NOC staffing (24/7) | 5-6 FTEs minimum per seat | Covers shifts, weekends, PTO, training |
| Follow-the-sun minimum | 3-4 engineers per region | 3 regions x 3-4 = 9-12 people minimum |

### Team Composition (Typical 10-Person Production Support Team)

| Role | Count | Responsibilities |
|------|-------|-----------------|
| Team Lead / Manager | 1 | Coordination, stakeholder management, process improvement |
| Senior Engineers (L2/L3) | 3 | Complex investigation, mentoring, architecture input |
| Support Engineers (L1/L2) | 4 | Day-to-day incident handling, monitoring, runbook execution |
| SRE / Automation Engineer | 1 | Tooling, automation, reliability improvements |
| Knowledge Manager / Technical Writer | 1 | Runbooks, documentation, training materials |

---

## 8. On-Call Best Practices

### Rotation Design
- **Minimum roster size**: 4-6 people to maintain 1-in-4 to 1-in-6 rotation
- **Shift length**: 1 week is most common; some teams use 3-4 day rotations
- **Primary + Secondary**: Secondary only paged if primary doesn't ACK within threshold
- **Handoff protocol**: Document all active incidents, known risks, pending changes
- **Shadow shifts**: New engineers shadow experienced on-call for 1-2 rotations before going primary

### Compensation Models

| Model | Structure | Notes |
|-------|-----------|-------|
| Flat rate | $200-$500/week on-call | Predictable cost, simple |
| Per-page | $50-$100 per page received | Incentivizes reducing false alerts |
| Time-off | Comp day after on-call week | Popular with engineers |
| Hybrid | Flat rate + per-page + comp time | Most comprehensive |
| No explicit comp | Reduced sprint load during on-call week | Common at startups |

### On-Call Health Indicators
- Pages per shift trending down over time
- < 2 pages during sleeping hours per shift (Google SRE target)
- False positive rate < 20%
- Engineer satisfaction scores stable or improving
- No single person carrying disproportionate on-call load

---

## 9. Post-Incident Tools & Practices

### Post-Incident Review Tools

| Tool | Key Features |
|------|--------------|
| **incident.io** | Automated post-incident reports, follow-up tracking, Slack timeline capture |
| **Jeli** (now PagerDuty) | Incident analysis platform, narrative timeline, learning reviews |
| **Blameless** | SLO tracking + retrospectives, action item tracking, templates |
| **Rootly** | Automated retrospective creation, Slack-based, integrates with Jira for action items |
| **Confluence / Notion** | Manual but flexible — many teams use templates in their wiki |

### Post-Incident Review Process
1. **Timeline reconstruction** (within 24 hours) — What happened, when, who did what
2. **Root cause analysis** (within 48-72 hours) — 5 Whys, Fishbone, Fault Tree
3. **Blameless review meeting** (within 1 week) — All involved parties discuss
4. **Action items assigned** — Specific, owned, time-bound
5. **Action item tracking** — Follow up until all items are complete
6. **Metrics update** — Update MTTR, recurrence tracking, SLA impact
7. **Knowledge base update** — Add new runbook entry or update existing

### Common Post-Incident Metrics
- Action item completion rate (target: > 80% within 30 days)
- Recurrence rate for same root cause (target: < 10%)
- Time from incident close to postmortem document completion
- Number of process improvements implemented per quarter

---

## 10. Status Page & Communication Tools

| Tool | Key Features | Pricing |
|------|--------------|---------|
| **Statuspage.io** (Atlassian) | Most popular, component-level status, subscriber notifications, scheduled maintenance | Free (1 page), $29-$399/mo |
| **Instatus** | Modern alternative, faster setup, multiple pages | Free, $20-$80/mo |
| **Better Stack** (Better Uptime) | Status page + uptime monitoring + on-call combined | Free, $24-$84/mo |
| **Cachet** | Open-source, self-hosted status page | Free (OSS) |
| **Sorry** | Simple status page with incident management | From $29/mo |

---

## 11. Compliance & Security Monitoring

### Compliance Automation

| Tool | Supported Frameworks | Key Features |
|------|---------------------|--------------|
| **Vanta** | SOC 2, ISO 27001, PCI DSS, HIPAA, GDPR, SOX, NIST | Automated evidence collection, continuous monitoring, vendor risk management |
| **Drata** | SOC 2, ISO 27001, PCI DSS, HIPAA, GDPR, SOX, NIST, CMMC | 100+ native integrations, GRC dashboards |
| **Secureframe** | SOC 2, ISO 27001, PCI DSS, HIPAA, GDPR, NIST | Developer-friendly, strong startup fintech adoption |
| **ServiceNow GRC** | All major frameworks | Integrated with ITSM, enterprise-grade |
| **Laika** | SOC 2, ISO 27001, PCI DSS, HIPAA | White-glove compliance management + software |

### Security Monitoring

| Tool | Focus Area | Notes |
|------|-----------|-------|
| **Splunk Enterprise Security** | SIEM market leader | Used by 85%+ of large banks for security ops |
| **IBM QRadar** | Enterprise SIEM | Strong in regulated industries (banking, government) |
| **Microsoft Sentinel** | Cloud-native SIEM | Fastest growing, native Azure integration |
| **CrowdStrike Falcon** | Endpoint detection & response (EDR) | Leader in endpoint security |
| **Wiz** | Cloud security posture management (CSPM) | Agentless, full cloud visibility |
| **Snyk** | Developer security (SAST, SCA, container) | Shift-left security |

---

## 12. Tool Selection Matrix by Organization Size

### Startup (< 50 engineers)

| Category | Recommended | Why |
|----------|-------------|-----|
| Monitoring | Datadog or Grafana Cloud | Full-stack in one tool, manageable cost |
| Alerting | PagerDuty (Free) or Grafana OnCall | Free tier covers small teams |
| Incident Mgmt | incident.io or Rootly | Slack-native, minimal setup |
| ITSM | Jira Service Management (Free) | Already using Jira for development |
| Status Page | Instatus or Better Stack (Free) | Simple, fast setup |
| Compliance | Vanta or Drata | Automated SOC 2 prep |

### Mid-Market (50-500 engineers)

| Category | Recommended | Why |
|----------|-------------|-----|
| Monitoring | Datadog or New Relic | Full observability, team collaboration features |
| Alerting | PagerDuty Professional | Event intelligence, team routing |
| Incident Mgmt | FireHydrant or incident.io | Full lifecycle management |
| ITSM | Jira Service Management Premium | SLA tracking, CMDB, automation |
| Status Page | Statuspage.io | Subscriber management, integrations |
| Compliance | Vanta or Drata | Multiple framework support |

### Enterprise (500+ engineers)

| Category | Recommended | Why |
|----------|-------------|-----|
| Monitoring | Dynatrace + Splunk | AI-powered RCA + security/compliance logging |
| Alerting | PagerDuty Enterprise | Event orchestration, AIOps, runbook automation |
| Incident Mgmt | ServiceNow + PagerDuty | ITSM integration, enterprise workflow |
| ITSM | ServiceNow | Industry standard, CMDB, GRC, ITOM |
| Status Page | Statuspage.io Business | Component-level, subscriber management |
| Compliance | ServiceNow GRC + Vanta | Enterprise compliance management |
| AIOps | Moogsoft or BigPanda | Alert noise reduction at scale |

---

## 13. Tool Integration Patterns

### Common Integration Architecture

```
┌─────────────────────────────────────────────────────┐
│                    DATA SOURCES                      │
│  CloudWatch │ Datadog │ Prometheus │ Custom Metrics  │
└──────────┬──────────┬──────────┬──────────┬─────────┘
           │          │          │          │
           ▼          ▼          ▼          ▼
┌─────────────────────────────────────────────────────┐
│                ALERTING LAYER                        │
│          PagerDuty / OpsGenie / Grafana             │
│  • Route alerts to correct team                     │
│  • Deduplicate and correlate                        │
│  • Escalation policies                              │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│              INCIDENT MANAGEMENT                     │
│      incident.io / FireHydrant / ServiceNow         │
│  • Create incident record                           │
│  • Open war room (Slack channel)                    │
│  • Track timeline                                   │
│  • Post-incident review                             │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│              COMMUNICATION                           │
│    Statuspage.io │ Slack │ Teams │ Email             │
│  • Customer-facing status updates                   │
│  • Internal stakeholder notifications               │
│  • War room coordination                            │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│          POST-INCIDENT & KNOWLEDGE                   │
│    Confluence │ Notion │ Jeli │ Blameless            │
│  • Postmortem documentation                         │
│  • Action item tracking                             │
│  • Knowledge base updates                           │
│  • Metrics and trend analysis                       │
└─────────────────────────────────────────────────────┘
```

### Key Integration Points for the Agent System
- **Ingestion**: Webhooks from PagerDuty/OpsGenie/Datadog/CloudWatch → Hub Agent
- **Investigation**: API access to Datadog/Splunk/Grafana for metrics and logs
- **Communication**: Slack/Teams API for approval gates and status updates
- **ITSM**: ServiceNow/Jira API for ticket creation and updates
- **Knowledge**: Vector DB + structured store for past RCA retrieval
- **Deployment**: CI/CD API (GitHub Actions/ArgoCD/Jenkins) for rollback execution

---

## Summary: Tool Category Coverage for Agent System

| Category | Required for Agent System | Purpose |
|----------|--------------------------|---------|
| Monitoring API | Yes — P0 | Spoke agents need metrics and logs for investigation |
| Alerting Integration | Yes — P0 | Incident ingestion source |
| ITSM API | Yes — P1 | Ticket creation, status updates, closure |
| Communication API | Yes — P0 | Approval gates, status notifications |
| CI/CD API | Yes — P1 | Deployment info and rollback execution |
| Knowledge Store | Yes — P1 | Past RCA storage and retrieval |
| Status Page API | Nice to have — P2 | Automated status page updates |
| Compliance Tools | Nice to have — P2 | Audit trail integration |

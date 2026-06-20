# Incident Management — Patterns, Frameworks, and Best Practices

> Research compiled: 2026-06-20
> Purpose: Understand incident management patterns to define agent system behavior

---

## 1. Frameworks

### ITIL v4 — Incident Management Practice
- **Goal**: Restore normal service as quickly as possible, minimize business impact
- **Key process**: Identification → Logging → Categorization → Prioritization → Investigation → Resolution → Closure
- **Major Incident Process**: Separate fast-track process for P1/P0 — dedicated incident manager, war room, continuous updates
- **Problem Management**: Post-incident — identify root cause, create known error records, permanent fixes
- **Known Error Database (KEDB)**: Repository of known issues with workarounds — directly relevant to agent knowledge base

### SRE (Google) — Incident Management
- **Adapted from ICS (Incident Command System)** — originally fire/emergency response
- **Key roles**: Incident Commander (IC), Operations Lead, Communications Lead
- **Principles**: Clear chain of command, defined roles, regular status updates, blameless postmortems
- **Error Budgets**: SLOs define reliability targets; error budget = 1 - SLO. When budget is consumed, freeze changes
- **Toil reduction**: Automate repetitive incident response tasks

### PagerDuty Incident Response
- **Full lifecycle**: Triage → Mobilize → Investigate → Remediate → Postmortem
- **On-call first responder**: Engineer who gets paged makes initial assessment
- **Escalation**: Automatic if no acknowledgment within threshold (typically 5-15 min)
- **Severity levels**: SEV-1 through SEV-5 with defined response expectations per level

---

## 2. Severity Classification Systems

### Standard P0-P4 Model

| Level | Name | Impact | Response Time | Resolution Target | Update Freq |
|-------|------|--------|---------------|-------------------|-------------|
| P0 | Critical | Total outage, all users affected, data loss | Immediate (<15 min) | 1-4 hours | Every 15 min |
| P1 | Major | Major feature broken, large user impact, no workaround | 15-30 min | 4-8 hours | Every 30 min |
| P2 | Moderate | Feature impaired, workaround exists, subset of users | 30 min - 2 hours | 8-24 hours | Every 2-4 hours |
| P3 | Minor | Minor issue, workaround available, limited impact | 4-8 hours | 3-5 business days | Daily |
| P4 | Informational | Cosmetic, feature request, no impact | 1-2 business days | 5-10 business days | Weekly |

### ITIL Priority Matrix (Impact × Urgency)

|  | High Urgency | Medium Urgency | Low Urgency |
|---|---|---|---|
| **High Impact** | P1 - Critical | P2 - High | P3 - Medium |
| **Medium Impact** | P2 - High | P3 - Medium | P4 - Low |
| **Low Impact** | P3 - Medium | P4 - Low | P5 - Planning |

### Company-Specific Examples

**Google Cloud Support:**
- P1 Critical (Premium): 15 min response, 24/7
- P2 High (Premium): 2 hour response, 24/7
- P3 Medium: 4 hour response, business hours
- P4 Low: 8 hour response, business hours

**AWS Support (Enterprise):**
- Business-critical system down: 15 min response
- Production system down: 1 hour response
- Production system impaired: 4 hour response
- System impaired: 12 hour response
- General guidance: 24 hour response

**Meta/Facebook:**
- SEV-0 (Site Event): Extremely rare, total platform outage (e.g., Oct 2021 6-hour global outage)
- SEV-1: Large-scale degradation affecting millions
- SEV-2: Significant impact, subset of users
- SEV-3: Limited impact, small subset
- SEV-4: Cosmetic/low

---

## 3. Alerting Patterns

### Alert Design Principles
- **Alert on symptoms, not causes**: Alert on "API latency > 5s" not "CPU > 90%"
- **Actionable alerts only**: Every alert should require human action — if not, it's noise
- **Use multiple signal types**: Metrics, logs, traces, synthetic checks
- **Multi-window, multi-burn-rate**: Alert when error budget consumption rate threatens SLO
- **Alert grouping**: Combine related alerts into one incident to reduce noise
- **Alert deduplication**: Suppress duplicate alerts for the same root issue

### Alert Fatigue Prevention
- **Problem**: Too many alerts → ignoring alerts → missing real incidents
- **Solutions**:
  - Review and prune alerts quarterly
  - Measure signal-to-noise ratio (actionable / total alerts)
  - Target: < 5 pages per on-call shift
  - Use anomaly detection instead of static thresholds where possible
  - Implement alert routing — different teams for different services
  - Use "warning" vs "critical" — warnings don't page, they notify

### Alerting Tools
- **PagerDuty**: De facto standard for alert routing and on-call management
- **OpsGenie** (Atlassian): Strong Jira integration, cost-effective
- **Grafana Alerting**: Unified alerting across metrics, logs, traces
- **CloudWatch Alarms**: AWS native, good for AWS-heavy environments
- **Prometheus Alertmanager**: Open source, pairs with Prometheus metrics
- **Datadog Monitors**: Integrated with Datadog's observability platform

---

## 4. Escalation Patterns

### Time-Based Escalation
- If no ACK within X minutes → escalate to secondary on-call
- If no ACK from secondary within Y minutes → escalate to team lead
- If no resolution within Z minutes → escalate to engineering manager
- Typical chain: On-call → Secondary → Team Lead → Director → VP (for P0/P1)

### Severity-Based Escalation
- P4/P3: On-call handles during business hours
- P2: On-call handles immediately, team lead notified
- P1: War room opened, multiple teams engaged, stakeholders notified
- P0: All hands, executive notification, external communication prepared

### Functional Escalation
- L1 (First responder): Initial triage, known issue lookup, basic troubleshooting
- L2 (Domain expert): Deep investigation, requires specific system knowledge
- L3 (Engineering): Code-level debugging, requires access to source code and deployment pipeline

### Cross-Team Escalation
- When incident spans multiple domains (e.g., network + database + application)
- Incident Commander coordinates across teams
- Each team provides a representative to the war room / bridge call

---

## 5. Incident Command System (ICS) for IT

### Roles (adapted from emergency services to tech)

**Incident Commander (IC):**
- Owns the incident end-to-end
- Makes decisions on priorities and resource allocation
- Does NOT do the technical investigation — delegates to others
- Communicates status upward and outward
- Declares incident resolved/closed

**Operations Lead (Ops Lead):**
- Leads the technical investigation and remediation
- Coordinates between different technical teams
- Executes the recovery plan
- Reports findings to IC

**Communications Lead (Comms Lead):**
- Manages all stakeholder communication
- Updates status page, Slack channels, email distribution lists
- Drafts customer-facing communications
- Shields the technical team from interruptions

**Scribe:**
- Documents the timeline of events in real-time
- Records all actions taken, decisions made, findings discovered
- This timeline becomes the foundation for the postmortem

### War Room / Bridge Call
- Opened for P0/P1 incidents
- Dedicated Slack channel or video call
- Only essential personnel — avoid "too many cooks"
- IC controls who speaks and what actions are taken
- Regular check-ins (every 15-30 min)

---

## 6. Post-Incident Patterns

### Blameless Postmortem
- **Core principle**: Focus on systems and processes, not individuals
- **Goal**: Learn from the incident to prevent recurrence
- **Who attends**: All involved parties — engineers, IC, management
- **When**: Within 48-72 hours of incident resolution (while memory is fresh)

### Postmortem Document Structure
1. **Incident summary**: What happened, impact, duration, severity
2. **Timeline**: Detailed chronological events with timestamps
3. **Root cause analysis**: What caused the incident (5 Whys, Fishbone diagram)
4. **Contributing factors**: What made it worse or delayed resolution
5. **What went well**: Recognition of what worked
6. **What went poorly**: Where processes or systems failed
7. **Action items**: Specific, assigned, time-bound follow-up tasks
8. **Lessons learned**: Key takeaways for the organization

### Root Cause Analysis Methods
- **5 Whys**: Ask "why" iteratively until root cause is found
- **Fishbone (Ishikawa) Diagram**: Categorize causes: People, Process, Technology, Environment
- **Fault Tree Analysis**: Boolean logic tree of failure modes
- **Timeline analysis**: Map events chronologically to find the trigger

### Post-Incident Metrics
- **Recurrence rate**: Does this type of incident keep happening?
- **Action item completion rate**: Are postmortem actions actually followed through?
- **MTTR trend**: Is resolution time improving over time?
- **Customer impact**: Quantify business impact (revenue lost, SLA credits, customer complaints)

---

## 7. SLA/SLO/SLI Management

### Definitions
- **SLI (Service Level Indicator)**: The actual measurement (e.g., request latency p99, error rate, availability %)
- **SLO (Service Level Objective)**: Internal target (e.g., 99.9% availability over 30 days)
- **SLA (Service Level Agreement)**: Contractual commitment with financial penalties (e.g., "99.9% uptime or service credits")

### Error Budget Model
- Error budget = 1 - SLO
- Example: SLO = 99.9% → Error budget = 0.1% = 43.2 min/month of allowed downtime
- When error budget is consumed → freeze deployments, focus on reliability
- When error budget is healthy → deploy faster, take more risks

### Common Uptime Tiers

| Uptime % | Downtime/Year | Downtime/Month | Downtime/Week |
|----------|---------------|----------------|---------------|
| 99% | 3.65 days | 7.31 hours | 1.68 hours |
| 99.9% | 8.77 hours | 43.83 min | 10.08 min |
| 99.95% | 4.38 hours | 21.92 min | 5.04 min |
| 99.99% | 52.60 min | 4.38 min | 1.01 min |
| 99.999% | 5.26 min | 26.30 sec | 6.05 sec |

### SLA Penalties (Typical)
- Miss by < 0.1%: 10% service credit
- Miss by 0.1-0.5%: 25% service credit
- Miss by > 0.5%: 50% service credit
- Extended outage (>24h): Full month credit or contract termination clause

---

## 8. Key Metrics (The Four Golden Signals + DORA)

### Four Golden Signals (Google SRE)
1. **Latency**: Time to serve a request (distinguish success vs. error latency)
2. **Traffic**: Demand on the system (requests/sec, transactions/sec)
3. **Errors**: Rate of failed requests (HTTP 5xx, application errors)
4. **Saturation**: How "full" the system is (CPU, memory, disk, queue depth)

### DORA Metrics (DevOps Research & Assessment)
1. **Deployment Frequency**: How often code reaches production
2. **Lead Time for Changes**: Time from commit to production
3. **Change Failure Rate**: % of deployments causing incidents
4. **Mean Time to Recovery (MTTR)**: Time from incident detection to resolution

### Incident-Specific Metrics
- **MTTD (Mean Time to Detect)**: Time from incident start to first alert
- **MTTA (Mean Time to Acknowledge)**: Time from alert to human acknowledgment
- **MTTI (Mean Time to Investigate)**: Time from acknowledgment to root cause identified
- **MTTR (Mean Time to Resolve)**: Time from detection to full resolution
- **MTBF (Mean Time Between Failures)**: Average time between incidents

### Industry Benchmarks (approximate)
- **Elite performers**: MTTR < 1 hour, Change failure rate < 5%, Deploy daily+
- **High performers**: MTTR < 24 hours, Change failure rate < 15%
- **Medium performers**: MTTR < 1 week, Change failure rate < 30%
- **Low performers**: MTTR > 1 week, Change failure rate > 45%

---

## 9. Communication Patterns During Incidents

### Status Update Cadence
- P0/P1: Every 15-30 minutes
- P2: Every 1-2 hours
- P3: Every 4-8 hours or daily
- P4: As needed

### Communication Channels
- **Internal (engineering)**: Dedicated Slack channel per incident, bridge call for P0/P1
- **Internal (business)**: Email to stakeholder distribution list, Slack business channel
- **External (customers)**: Status page update, email to affected customers, social media (for major outages)

### Status Page Best Practices
- Update within 5 minutes of incident detection
- Use clear language — avoid jargon
- State: what's affected, current status, next update time, workaround if any
- Be honest — don't downplay severity
- Update when resolved, and post RCA summary within 48 hours

### Tools for Communication
- **Statuspage.io** (Atlassian): Most popular hosted status page
- **Instatus**: Modern alternative, faster setup
- **Better Stack (Better Uptime)**: Status page + monitoring combined
- **Cachet**: Open-source, self-hosted status page
- **PagerDuty Stakeholder Notifications**: Built into PagerDuty
- **incident.io / FireHydrant**: Automate Slack-based incident comms

---

## 10. On-Call Patterns

### Rotation Models
- **Weekly rotation**: Most common — each engineer is on-call for 1 week
- **Daily rotation**: Higher burden per shift but shorter commitment
- **Follow-the-sun**: Teams in different time zones cover their business hours
- **Primary/Secondary**: Two engineers on-call — secondary only activated if primary doesn't respond

### On-Call Best Practices
- Maximum: 1 week on-call out of every 4 (Google SRE recommendation)
- Target: < 2 pages per on-call shift during sleeping hours
- Handoff procedure: Document ongoing issues, current state, known risks
- Shadow on-call: New engineers shadow an experienced on-call before going solo
- Post-on-call review: Discuss pages received, were they actionable?

### On-Call Burnout Prevention
- Fair rotation — equal distribution across the team
- Compensation for on-call (flat fee per shift + per-page bonus)
- Count on-call as real work — reduce sprint commitments for on-call week
- Invest in alert quality — reduce false positives
- Automate common responses — on-call should handle novel issues, not repetitive ones

### Compensation Models
- **Flat rate**: $200-500/week for being on-call, regardless of pages
- **Per-page**: $50-100 per page received (incentivizes reducing false alerts)
- **Time-off**: Comp day after on-call week
- **Hybrid**: Flat rate + per-page + comp time
- Some companies: No explicit compensation but reduced sprint load

---

## 11. Automation Patterns for Incident Response

### Runbook Automation
- Convert manual runbooks into automated scripts
- Trigger automatically on specific alert conditions
- Tools: PagerDuty Runbook Automation (formerly Rundeck), StackStorm, AWS Systems Manager
- Start simple: auto-restart, auto-scale, auto-rollback for known issues

### Auto-Remediation Tiers
- **Tier 0**: Fully automated — no human involved (e.g., auto-restart crashed pod)
- **Tier 1**: Automated with notification — action taken, human informed (e.g., auto-scale + notify)
- **Tier 2**: Automated diagnosis, human approves fix (e.g., agent identifies issue, presents fix, waits for approval)
- **Tier 3**: Automated diagnosis, manual fix (e.g., agent gathers context, human executes fix)

### ChatOps
- Incident management through Slack/Teams
- Bot commands: `/incident create`, `/incident escalate`, `/incident resolve`
- Timeline automatically captured from chat messages
- Approvals via Slack reactions or buttons
- Tools: PagerDuty, incident.io, Rootly, FireHydrant

---

## 12. Disaster Recovery Patterns

### DR Strategies (by cost and RTO)
1. **Backup & Restore**: Cheapest, slowest RTO (hours to days)
2. **Pilot Light**: Minimal standby environment, moderate RTO (10-30 min)
3. **Warm Standby**: Scaled-down active copy, faster RTO (5-15 min)
4. **Multi-Site Active/Active**: Full redundancy, near-zero RTO (seconds)

### DR Testing
- **Tabletop exercise**: Walk through DR plan verbally, identify gaps
- **Simulated failover**: Test failover to DR site but don't serve production traffic
- **Live failover**: Actually switch production traffic to DR site
- **Chaos engineering**: Randomly inject failures to test resilience (Chaos Monkey, Gremlin, LitmusChaos)

### RPO/RTO Targets by Tier

| Tier | RPO | RTO | Examples |
|------|-----|-----|---------|
| Tier 1 (Critical) | Near zero | < 15 min | Payment processing, core API |
| Tier 2 (Important) | < 1 hour | < 1 hour | User dashboard, reporting |
| Tier 3 (Standard) | < 4 hours | < 4 hours | Internal tools, batch jobs |
| Tier 4 (Non-critical) | < 24 hours | < 24 hours | Dev environments, docs |

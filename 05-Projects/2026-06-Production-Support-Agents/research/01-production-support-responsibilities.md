# Production Support — Full Scope of Responsibilities

> Research compiled: 2026-06-20
> Purpose: Identify ALL responsibilities of a production support team to inform agent system requirements

---

## 1. Incident Management (Core)

**What it involves:**
- Detect, acknowledge, triage, investigate, resolve, and close production incidents
- Classify severity (P0-P4) based on impact and urgency
- Follow structured incident lifecycle: Detect → Triage → Investigate → Resolve → Close
- Coordinate across teams during major incidents

**Why it matters:**
- Directly impacts customer experience and business revenue
- Unresolved incidents cascade — a P2 becomes a P1 if ignored

**Common tools:** PagerDuty, OpsGenie, ServiceNow, Jira Service Management, Freshservice

---

## 2. Monitoring & Observability

**What it involves:**
- Proactive monitoring of infrastructure, application, and business metrics
- Setting up and tuning alerts (thresholds, anomaly detection)
- Dashboard management — health views for services, infrastructure, and SLAs
- Log aggregation and analysis
- Distributed tracing for microservices
- Synthetic monitoring (proactive health checks)

**Why it matters:**
- Reduces MTTD (Mean Time to Detect) — catch issues before users report them
- Proactive monitoring prevents incidents from escalating

**Common tools:** Datadog, Grafana, Prometheus, New Relic, Splunk, ELK Stack, CloudWatch, Dynatrace, AppDynamics, Jaeger, Zipkin

---

## 3. User Onboarding & Support

**What it involves:**
- Onboard new users/customers onto the platform
- Provision accounts, roles, permissions, and access
- Provide guided setup and initial configuration assistance
- Handle user queries and troubleshooting (L1 support)
- Maintain user-facing documentation and FAQs
- Conduct training sessions for end users
- Manage self-service portals and knowledge bases

**Why it matters:**
- First impression of the product — poor onboarding drives churn
- Reduces ongoing support ticket volume through proper initial setup
- Often overlooked as a production support responsibility

**Common tools:** Zendesk, Intercom, Freshdesk, Confluence, Notion, WalkMe, Pendo

---

## 4. Change Management

**What it involves:**
- Review and approve changes to production systems
- Maintain change calendar (scheduled maintenance windows)
- Risk assessment for proposed changes
- Change Advisory Board (CAB) participation
- Emergency change procedures for critical fixes
- Post-change validation and monitoring
- Rollback planning and execution

**Why it matters:**
- 70-80% of production incidents are caused by changes (deployments, config changes, infra updates)
- Structured change management reduces change failure rate

**Common tools:** ServiceNow Change Management, Jira, GitOps tools (ArgoCD, Flux), Terraform, Ansible

---

## 5. Release Management & Deployment Support

**What it involves:**
- Coordinate production deployments with development teams
- Validate deployment readiness (pre-deployment checklists)
- Execute or oversee production deployments
- Monitor deployments for regression (canary, blue-green, rolling)
- Rollback deployments when issues are detected
- Maintain deployment runbooks
- Manage release notes and communication

**Why it matters:**
- Bad deployments are the #1 cause of production incidents
- Production support team is often the last line of defense before code reaches users

**Common tools:** Jenkins, GitHub Actions, GitLab CI, ArgoCD, Spinnaker, Octopus Deploy, Harness

---

## 6. Knowledge Management

**What it involves:**
- Create and maintain runbooks (step-by-step resolution guides)
- Document known issues and workarounds
- Maintain architecture diagrams and system documentation
- Build and curate internal knowledge base / wiki
- Document RCAs (Root Cause Analyses) from past incidents
- Create troubleshooting guides per service/component
- Knowledge transfer during team transitions

**Why it matters:**
- Institutional knowledge is lost when people leave
- Runbooks enable faster resolution and consistent handling
- Reduces dependency on specific individuals (bus factor)

**Common tools:** Confluence, Notion, GitBook, Backstage, internal wikis, PagerDuty Runbook Automation

---

## 7. Capacity Planning & Performance Management

**What it involves:**
- Monitor resource utilization trends (CPU, memory, disk, network)
- Forecast capacity needs based on growth projections
- Plan scaling events (seasonal traffic, product launches)
- Identify and resolve performance bottlenecks
- Right-size infrastructure (cost optimization)
- Load testing and stress testing support
- Database performance tuning

**Why it matters:**
- Running out of capacity during peak traffic = outage
- Over-provisioning wastes money
- Proactive planning prevents reactive firefighting

**Common tools:** Kubernetes HPA/VPA, AWS Auto Scaling, Grafana, CloudWatch, k6, JMeter, Gatling

---

## 8. Security Incident Response

**What it involves:**
- Detect and respond to security incidents (breaches, intrusions, vulnerabilities)
- Coordinate with security team (SOC/SIRT)
- Execute containment procedures (isolate affected systems)
- Manage patching and vulnerability remediation in production
- Handle access-related incidents (unauthorized access, credential leaks)
- Incident reporting for compliance (GDPR, HIPAA, PCI-DSS breach notifications)
- Security audit support

**Why it matters:**
- Security incidents can have legal, financial, and reputational consequences
- Production support is often first to detect anomalous behavior
- Regulatory compliance requires documented incident response

**Common tools:** CrowdStrike, Splunk SIEM, Wiz, Snyk, HashiCorp Vault, AWS GuardDuty, OWASP ZAP

---

## 9. Compliance & Audit Support

**What it involves:**
- Maintain audit trails for all production changes and access
- Ensure production systems meet regulatory requirements (SOC 2, ISO 27001, HIPAA, PCI-DSS, GDPR, SOX)
- Support internal and external audits with evidence collection
- Enforce access controls and least-privilege policies
- Data retention and purging per compliance requirements
- Document control procedures and change history

**Why it matters:**
- Non-compliance = fines, lawsuits, loss of certifications
- Auditors need evidence that production is managed properly
- Many industries require specific production support controls

**Common tools:** ServiceNow GRC, Vanta, Drata, Splunk (audit logs), AWS CloudTrail, Azure Activity Log

---

## 10. Communication & Stakeholder Management

**What it involves:**
- Notify stakeholders during incidents (business owners, executives, customers)
- Provide regular status updates during ongoing incidents (every 15-30 min for P1)
- Manage customer-facing status pages
- Send RCA summaries to stakeholders post-incident
- SLA reporting to business teams
- Change communication (planned maintenance notices)
- Coordinate war rooms / bridge calls for major incidents

**Why it matters:**
- Reduces panic and duplicate inquiries during outages
- Maintains trust with business and customers
- Poor communication during incidents is a top driver of customer churn

**Common tools:** Statuspage.io, PagerDuty (stakeholder notifications), Slack, Microsoft Teams, email distribution lists

---

## 11. On-Call Management

**What it involves:**
- Design and maintain on-call rotation schedules
- Primary and secondary on-call assignments
- Escalation policies (time-based auto-escalation)
- On-call handoff procedures (shift transitions)
- On-call compensation and burnout prevention
- Shadow on-call for training new team members
- On-call metrics tracking (pages per shift, sleep interruptions)

**Why it matters:**
- 24/7 coverage is essential for production systems
- Poor on-call practices lead to burnout and attrition
- Structured rotations ensure consistent coverage

**Common tools:** PagerDuty, OpsGenie, VictorOps/Splunk On-Call, custom scheduling tools

---

## 12. Disaster Recovery & Business Continuity

**What it involves:**
- Maintain and test disaster recovery (DR) plans
- Execute failover procedures (region failover, database failover)
- Conduct DR drills (tabletop exercises, live failover tests)
- Backup management (schedule, verify, restore testing)
- Define and maintain RPO (Recovery Point Objective) and RTO (Recovery Time Objective)
- Coordinate with infrastructure teams on redundancy
- Document recovery procedures per service

**Why it matters:**
- When disaster strikes, there is no time to figure things out
- Untested DR plans fail when needed most
- Regulatory requirements often mandate DR testing

**Common tools:** AWS Backup, Azure Site Recovery, Velero (K8s), pgBackRest, custom DR scripts

---

## 13. Environment Management

**What it involves:**
- Manage production, staging, UAT, and development environments
- Ensure environment parity (prod-like staging)
- Configuration management across environments
- Secret and credential management
- Environment provisioning and teardown
- Data masking for non-production environments

**Why it matters:**
- Environment drift causes "works on staging, breaks on prod" scenarios
- Proper environment management reduces deployment risk

**Common tools:** Terraform, Ansible, AWS CDK, Kubernetes namespaces, HashiCorp Vault, AWS Secrets Manager

---

## 14. Database Administration & Support

**What it involves:**
- Monitor database health (connections, locks, replication lag)
- Handle database incidents (connection pool exhaustion, deadlocks, corruption)
- Backup and restore operations
- Schema migration support
- Query performance optimization
- Data integrity checks and reconciliation
- Database scaling (read replicas, sharding)

**Why it matters:**
- Database is often the bottleneck and single point of failure
- Data loss is catastrophic and often irrecoverable
- Slow queries cascade into application-wide latency

**Common tools:** pgAdmin, MySQL Workbench, MongoDB Compass, CloudNativePG, AWS RDS, Datadog DBM

---

## 15. Batch Job & Scheduled Task Management

**What it involves:**
- Monitor scheduled jobs (cron, Airflow, batch processors)
- Handle batch job failures (retry, restart, skip, manual intervention)
- Manage job dependencies and sequencing
- Ensure data processing pipelines complete within SLA windows
- Handle end-of-day, end-of-month, end-of-year batch processing
- Job scheduling and conflict resolution

**Why it matters:**
- Batch failures are silent — no user sees them until downstream impact
- Financial systems rely heavily on batch processing (EOD reconciliation, reports)
- Often the most neglected area of production support

**Common tools:** Apache Airflow, Kubernetes CronJobs, AWS Step Functions, Control-M, Autosys, cron

---

## 16. Third-Party & Vendor Management

**What it involves:**
- Monitor third-party service health (APIs, SaaS dependencies, payment gateways)
- Manage vendor incident communication (open tickets with vendors, escalate)
- Track vendor SLAs and hold vendors accountable
- Maintain fallback procedures when vendors are down
- Coordinate with vendors during joint troubleshooting
- License management and renewal tracking

**Why it matters:**
- Modern systems depend on dozens of third-party services
- A vendor outage is still YOUR outage from the customer's perspective
- Vendor response times can be slow — need escalation playbooks

**Common tools:** StatusGator (aggregate vendor status), Vendor status pages, contract management tools

---

## 17. Proactive Maintenance & Preventive Measures

**What it involves:**
- Scheduled patching (OS, middleware, application, security patches)
- Certificate renewal management (SSL/TLS, service-to-service)
- Log rotation and cleanup
- Database maintenance (vacuum, index rebuild, statistics refresh)
- Credential rotation
- Infrastructure refresh and upgrades
- Technical debt tracking and remediation

**Why it matters:**
- Expired certificates cause outages
- Unpatched systems are security vulnerabilities
- Preventive maintenance reduces incident volume over time

**Common tools:** AWS Systems Manager Patch Manager, Ansible, cert-manager (K8s), custom automation scripts

---

## 18. Cost Management & Optimization

**What it involves:**
- Monitor cloud infrastructure costs
- Identify unused or underutilized resources
- Right-size compute instances
- Reserved instance / savings plan management
- Tag enforcement for cost allocation
- Cost anomaly detection (sudden spike in spend)
- Budget alerting

**Why it matters:**
- Cloud costs can spiral without oversight
- Production support team has the best visibility into resource utilization
- Cost optimization is increasingly a production support KPI

**Common tools:** AWS Cost Explorer, CloudHealth, Kubecost, Infracost, Spot.io

---

## 19. Data Management & Governance

**What it involves:**
- Data backup verification and restore testing
- Data retention policy enforcement
- Data masking and anonymization for compliance
- Data migration support
- Data quality monitoring
- Handle data correction requests (production data fixes)
- GDPR/CCPA data subject access requests (DSARs)

**Why it matters:**
- Data is the most valuable asset — loss or exposure is catastrophic
- Regulatory requirements around data are increasing
- Production data fixes are high-risk operations that need controls

**Common tools:** AWS Backup, Velero, custom data pipelines, Great Expectations, dbt

---

## 20. Training & Knowledge Transfer

**What it involves:**
- Cross-training team members on different systems/services
- Onboarding new team members to production support processes
- Creating training materials and documentation
- Shadowing programs (new members shadow experienced engineers)
- Lunch-and-learn sessions on system architecture
- Post-incident knowledge sharing (lessons learned sessions)
- Skill gap assessment and development plans

**Why it matters:**
- Reduces single-point-of-failure on individual team members
- Accelerates new hire ramp-up time
- Continuous learning keeps the team effective as systems evolve

**Common tools:** Confluence, internal wikis, recorded sessions, pair programming, war game exercises

---

## 21. SLA/SLO/SLI Management & Reporting

**What it involves:**
- Define and track Service Level Indicators (SLIs) — actual measurements
- Set Service Level Objectives (SLOs) — internal targets
- Manage Service Level Agreements (SLAs) — contractual commitments
- Error budget management (SRE approach)
- Generate SLA compliance reports for stakeholders
- Alert when error budget is being consumed too fast
- Review and renegotiate SLAs periodically

**Why it matters:**
- SLAs are contractual — breaching them has financial penalties
- SLOs/error budgets balance reliability with velocity
- Without measurement, you can't improve

**Common tools:** Datadog SLO tracking, Nobl9, Blameless, custom dashboards

---

## Summary: The 21 Responsibilities

| # | Responsibility | Often Overlooked? |
|---|---------------|-------------------|
| 1 | Incident Management | No — core |
| 2 | Monitoring & Observability | No — core |
| 3 | User Onboarding & Support | Yes |
| 4 | Change Management | No |
| 5 | Release Management & Deployment Support | No |
| 6 | Knowledge Management | Yes |
| 7 | Capacity Planning & Performance | Sometimes |
| 8 | Security Incident Response | Sometimes |
| 9 | Compliance & Audit Support | Yes |
| 10 | Communication & Stakeholder Management | Sometimes |
| 11 | On-Call Management | No |
| 12 | Disaster Recovery & Business Continuity | Yes |
| 13 | Environment Management | Yes |
| 14 | Database Administration & Support | Sometimes |
| 15 | Batch Job & Scheduled Task Management | Yes |
| 16 | Third-Party & Vendor Management | Yes |
| 17 | Proactive Maintenance & Preventive Measures | Yes |
| 18 | Cost Management & Optimization | Yes |
| 19 | Data Management & Governance | Yes |
| 20 | Training & Knowledge Transfer | Yes |
| 21 | SLA/SLO/SLI Management & Reporting | Sometimes |

# Domain-Specific Production Support Requirements

> Research compiled: 2026-06-20
> Purpose: Map production support requirements across 10+ industries to identify universal and domain-specific agent behaviors

---

## 1. FinTech / Financial Services

### Regulatory Requirements
- **PCI-DSS v4.0**: 12 core requirements for cardholder data protection; MFA for all CDE access; 12-month log retention (3 months immediately available); quarterly ASV scans; annual pen testing; patches within 30 days for critical vulnerabilities
- **SOX (Sarbanes-Oxley)**: Internal controls over financial reporting; ITGCs (Access, Change, Operations, Development); 7-year record retention; quarterly access reviews; segregation of duties between dev and prod
- **SOC 1/2 Type II**: Annual attestation of controls; SOC 2 covers Security, Availability, Processing Integrity, Confidentiality, Privacy
- **BSA/AML**: SAR filing within 30 days ($5K+ threshold for banks); CTR filing for $10K+ cash transactions within 15 days; 5-year record retention
- **Basel III / BCBS 239**: Risk data aggregation and reporting; 2-hour RTO for systemically important FMUs (Regulation HH)
- **DORA (EU)**: Mandatory RTOs/RPOs per function; incident reporting within 4 hours; threat-led penetration testing every 3 years; effective January 2025

### Domain-Specific Incident Types
- Payment processing failures and transaction timeouts
- Fraud detection false positives blocking legitimate transactions
- Core banking system outages
- Real-time transaction monitoring system failures
- Settlement/clearing system delays
- API rate limit exhaustion on payment gateways

### SLA Expectations
- Core banking: 99.99% availability
- Payment processing: < 2 second response time
- P1 MTTR: < 1 hour for payment-affecting incidents
- Regulatory reporting systems: must meet filing deadlines (daily/weekly/monthly)

### Key Tools
- Monitoring: Datadog, Splunk, Dynatrace
- ITSM: ServiceNow, Jira Service Management
- Compliance: Vanta, Drata, ServiceNow GRC
- Fraud: Featurespace ARIC, Feedzai, SAS

---

## 2. Healthcare / Life Sciences

### Regulatory Requirements
- **HIPAA Security Rule (45 CFR 164)**: Administrative, Physical, Technical safeguards; audit controls; access controls; transmission security; 6-year documentation retention
- **HIPAA Breach Notification**: 60-day notification to individuals; immediate HHS notification for 500+ breaches; 72-hour supervisory authority notification (GDPR equivalent)
- **21 CFR Part 11**: Electronic records and signatures; computer-generated audit trails; system validation; access controls; tamper-proof audit logs
- **FDA Software Validation**: GAMP 5 risk-based categories (1-5); IQ/OQ/PQ testing; change control for validated systems
- **HITECH Act**: Tiered penalty structure up to $2M/year per violation category; direct BA liability; state AG enforcement authority
- **21st Century Cures Act**: Information blocking penalties up to $1M/violation for IT developers; mandatory FHIR APIs; 8 exceptions including Health IT Performance

### Domain-Specific Incident Types
- EHR system outages requiring paper-based downtime procedures
- HL7/FHIR integration failures between clinical systems
- PHI exposure or unauthorized access events
- Medical device connectivity failures
- Telehealth platform outages during active patient sessions
- Ransomware attacks (healthcare is the #1 targeted sector)
- Drug interaction alert system failures

### SLA Expectations
- EHR systems: 99.9% availability; < 4 hour RTO
- Clinical decision support: real-time response required
- Lab systems: results delivery within SLA windows
- Pharmacy systems: zero tolerance for incorrect dispensing data
- Average healthcare breach cost: $10.93M (highest of any industry, IBM 2023)

### Key Tools
- EHR: Epic, Oracle Health (Cerner), MEDITECH
- Monitoring: Splunk, Datadog, Azure Monitor
- Compliance: Vanta, Drata, HITRUST CSF
- Security: CrowdStrike, Microsoft Defender for Cloud

---

## 3. Government IT / Public Sector

### Regulatory Requirements
- **FedRAMP**: Cloud authorization at Low/Moderate/High impact levels; 125-421 controls based on level; continuous monitoring; annual 3PAO assessment
- **FISMA**: NIST SP 800-53 Rev 5 controls; Risk Management Framework (RMF); Authority to Operate (ATO); continuous monitoring per SP 800-137
- **NIST SP 800-53**: 20 control families including AU (Audit), IR (Incident Response), CM (Configuration Management), CP (Contingency Planning)
- **CDM (Continuous Diagnostics and Mitigation)**: CISA program for asset management, identity management, network security, data protection
- **Section 508**: WCAG 2.0 AA accessibility compliance; DOJ Title II rule requires WCAG 2.1 AA by April 2026
- **CISA BODs**: BOD 22-01 (KEV patching); BOD 23-01 (asset discovery every 7 days, vuln scanning every 14 days)

### Domain-Specific Incident Types
- Citizen-facing service outages (IRS, SSA, Healthcare.gov)
- FedRAMP authorization boundary violations
- FISMA incident reporting within 1 hour for major incidents
- Section 508 accessibility compliance failures
- Cross-agency data sharing failures
- Classified system incidents with special handling requirements

### SLA Expectations
- FedRAMP High: 99.95-99.999% availability
- FedRAMP Moderate: 99.9% availability
- Federal website page load: < 3 seconds
- Citizen portal availability during peak periods: 99.9%+
- FITARA Scorecard grades influence budget allocations

### Key Tools
- Cloud: AWS GovCloud, Azure Government, Google Assured Workloads
- ITSM: ServiceNow (FedRAMP High authorized), BMC Helix
- Monitoring: Splunk GovCloud, Datadog US1-FED, Elastic Cloud Gov
- Security: CrowdStrike Falcon GovCloud, Tenable.io

---

## 4. Gaming

### Domain-Specific Challenges
- **Server scaling**: Launch day can see 10-100x normal traffic in seconds; New World hit 913K concurrent on Steam; FFXIV Endwalker had 17K+ player queues
- **Anti-cheat production issues**: Kernel-level drivers (Vanguard, EAC, BattlEye) can cause BSODs; false positive ban waves; 0.01% false positive rate across 100M players = 10K wrongly banned
- **DDoS attacks**: Gaming is heavily targeted; Overwatch 2 launch hit by massive DDoS; Akamai reports gaming as top DDoS target sector
- **Live service operations**: Always-on games require 24/7 support; content updates and patches can break existing functionality; hot fixes must deploy without downtime
- **Matchmaking and server allocation**: Sub-3-second server allocation target; standby pool starvation during demand spikes

### Domain-Specific Incident Types
- Launch day server crashes and queue systems
- Anti-cheat false positive ban waves
- DDoS attacks during peak hours or esports events
- Game economy exploits (gold duplication, item duplication)
- Matchmaking service failures
- Patch deployment failures requiring emergency rollback
- Cross-platform synchronization issues

### SLA Expectations
- Game servers: 99.9-99.99% availability during active hours
- Matchmaking: < 30 second queue times (target)
- Server allocation: < 3 seconds
- Patch deployment: zero-downtime for live service games
- P1 response during live events: < 5 minutes

### Key Tools
- Cloud: AWS GameLift, Azure PlayFab, Google Cloud for Gaming
- Monitoring: Datadog, Grafana + Prometheus, custom dashboards
- Anti-cheat: Riot Vanguard, Easy Anti-Cheat, BattlEye, Ricochet
- CDN: Akamai, CloudFront, Fastly

---

## 5. SaaS / Multi-Tenant Cloud

### Domain-Specific Challenges
- **Multi-tenant isolation**: Noisy neighbor problems; blast radius containment; cell-based architecture limits failures to 2-5% of customers per cell
- **Tenant-aware incident management**: Incidents may affect one tenant, a subset, or all tenants; per-tenant SLA tracking required
- **Feature flag management**: Progressive rollouts can cause partial service degradation; feature flags as instant mitigation tool
- **Status page communication**: 85% of customers say proactive communication reduces frustration (Atlassian); status updates every 15-30 min for P1

### Domain-Specific Incident Types
- Noisy neighbor: one tenant consuming disproportionate shared resources
- Multi-tenant data isolation breach
- Feature flag misconfiguration causing partial outage
- Subscription/billing system failures
- SSO/authentication service failures affecting all tenants
- Database connection pool exhaustion under concurrent tenant load

### SLA Expectations
- Platform availability: 99.95-99.99% (contractual SLA with service credits)
- API response time: < 200ms for catalog APIs, < 500ms for order APIs
- P1 MTTR: < 1 hour (DORA elite benchmark)
- Status page update: within 5 minutes of incident detection

### Key Tools
- Architecture patterns: Cell-based (AWS), Deployment Stamps (Azure), Bulkhead
- Monitoring: Datadog, New Relic, Grafana Cloud
- Incident Management: PagerDuty, incident.io, Rootly, FireHydrant
- Feature Flags: LaunchDarkly, Split.io, Flagsmith

---

## 6. Enterprise ERP / CRM

### Regulatory Requirements
- **SOX compliance**: ITGCs for access, change, operations, development; quarterly access reviews; 7-year retention
- **GDPR / CCPA**: Right to erasure (anonymization over deletion for ERP); data portability; 72-hour breach notification
- **FDA 21 CFR Part 11** (pharma/life sciences): Audit trails, electronic signatures, system validation for ERP systems in regulated environments
- **COBIT 2019**: 40 governance/management objectives; BAI06 for change management; DSS05 for security

### Domain-Specific Incident Types
- ERP batch job failures (billing, payroll, reporting)
- EDI integration failures (X12, EDIFACT) with trading partners
- Master data synchronization errors across modules
- Governor limit exhaustion (Salesforce: 100 SOQL queries per transaction)
- API throttling (Dynamics 365: 6,000 requests per 5-minute window)
- Dual-write synchronization failures between ERP and CRM
- SOX-relevant configuration changes requiring emergency CAB

### SLA Expectations
- Core ERP: 99.9% availability; 99.95% for cloud ERP
- Batch processing: completion within defined windows (EOD, EOM)
- Integration: < 5 minute sync latency between systems
- Dynamics 365 planned downtime: max 8 hours/month

### Key Tools
- ERP: SAP S/4HANA, Oracle Cloud ERP, Microsoft Dynamics 365
- CRM: Salesforce, Dynamics 365, Oracle CX
- Monitoring: Dynatrace, AppDynamics, Azure Monitor
- Integration: MuleSoft, Dell Boomi, Azure Logic Apps

---

## 7. Manufacturing / IoT

### Regulatory Requirements
- **IEC 61508**: Safety Integrity Levels (SIL 1-4); proof testing intervals; hardware fault tolerance requirements
- **IEC 62443**: Industrial cybersecurity for IACS; 4 security levels; mandatory for critical infrastructure
- **NERC CIP**: Energy sector; patch evaluation within 35 days; incident reporting to E-ISAC within 1 hour; penalties up to $1M/day
- **NIST SP 800-82 Rev 3**: Guide to OT security; Purdue Model for network segmentation

### Domain-Specific Challenges
- **IT/OT convergence**: Production support must span both IT and OT systems
- **Safety-critical systems**: Failures can cause physical harm; SIL levels dictate redundancy requirements
- **Edge computing**: Real-time control runs locally; cloud is for analytics only; latency requirements < 10ms for safety systems
- **Predictive maintenance**: ML model drift; 20-50% initial false positive rates; tiered alert systems (Advisory/Warning/Critical)
- **OTA firmware updates**: A/B partitioning for rollback; bricking risk; regulatory requirements (UNECE WP.29 for automotive, FDA for medical devices)

### Domain-Specific Incident Types
- SCADA/DCS system failures affecting production lines
- PLC/HMI communication failures
- Sensor data pipeline failures
- OTA firmware update failures requiring field intervention
- Digital twin synchronization issues (up to 10-second query consistency gap on Azure)
- Predictive maintenance false positives disrupting production schedules

### SLA Expectations
- Safety-critical systems: 99.999% availability (SIL 3-4)
- SCADA: < 15 minute RTO with hot standby
- Production line monitoring: real-time (< 1 second latency)
- Automotive downtime cost: $1.3-2M per hour
- Semiconductor fab downtime: $1-3.8M per hour

### Key Tools
- IIoT: PTC ThingWorx, Siemens MindSphere, AWS IoT SiteWise, Azure IoT Hub
- SCADA: Siemens WinCC, Ignition (Inductive Automation), AVEVA
- Security: Dragos, Claroty, Nozomi Networks, Microsoft Defender for IoT
- MES: SAP Digital Manufacturing, Plex (Rockwell), Dassault DELMIA

---

## 8. Telecom

### Regulatory Requirements
- **FCC Part 4 (NORS)**: Report outages affecting 900,000+ user-minutes within 120 minutes; initial report within 72 hours; final report within 30 days
- **TM Forum eTOM**: Telecom-specific process framework; Service Problem Management; Resource Trouble Management
- **ITU-T Standards**: E.800 series for QoS; M.3400 for management functions; X.733 for alarm reporting
- **OFCOM (UK)**: Outages affecting 1,000+ users for 1+ hour must be reported within 24 hours
- **3GPP**: 5G QoS Identifiers (5QI); network slicing SLAs; URLLC requires 99.9999% for ultra-reliable services

### Domain-Specific Challenges
- **Massive alarm volumes**: Large carriers generate 1-10 million alarms/day; alarm correlation reduces by 90-99%
- **5G complexity**: Network slicing with per-slice SLAs; NFV/CNF lifecycle management; O-RAN multi-vendor integration
- **Carrier-grade availability**: "Five nines" (99.999%) is the standard = 5.26 minutes downtime/year
- **NOC operations**: 24/7 staffing; tiered support (L0-L4); follow-the-sun models for global carriers

### Domain-Specific Incident Types
- Core network element failures (MSC, HSS, PGW)
- RAN outages (cell site clusters, baseband failures)
- 5G network slice degradation
- SS7/Diameter signaling failures
- Submarine cable cuts affecting international traffic
- Billing/mediation system failures

### SLA Expectations
- Core network (voice): 99.999% availability
- Mobile network (data): 99.99%
- P1 MTTR: 2-4 hours for carrier-grade equipment
- MTBF: 100,000-500,000 hours for core equipment
- Cost of downtime: $5,600-$11,000+ per minute for large carriers

### Key Tools
- NMS: IBM Netcool/OMNIbus, Nokia NetAct, Ericsson ENM
- OSS/BSS: Amdocs (27-30% market share), Netcracker, Comarch
- ITSM: ServiceNow (55-65% of Tier 1 carriers), BMC Helix/Remedy
- AIOps: Moogsoft, Huawei AUTIN, Nokia AVA

---

## 9. Media / Streaming

### Regulatory Requirements
- **FCC CVAA**: Closed captioning for previously-broadcast content on streaming; 99% accuracy for pre-recorded
- **ADA Title III**: Full accessibility for digital services; 100% content captioning
- **DMCA Section 1201**: Anti-circumvention provisions; criminal penalties up to $500K + 5 years
- **EU Copyright Directive (Article 17)**: Direct liability for content-sharing platforms
- **AVMSD**: 30% European content quota; minor protection; advertising limits
- **Studio DRM mandates**: MovieLabs ECP tiers; Widevine L1 for 4K; HDCP 2.2 for UHD outputs; forensic watermarking mandatory for premium content

### Domain-Specific Challenges
- **CDN performance**: Multi-CDN strategies improve QoE by 15-30% (Conviva data); CDN outages can affect millions simultaneously (Fastly June 2021)
- **DRM complexity**: Multi-DRM packaging (Widevine + FairPlay + PlayReady); HDCP handshake failures; license server SLAs of 99.99%
- **Live event scaling**: PPV events go from 0 to millions in < 60 seconds; Netflix Tyson/Paul fight hit 65M concurrent streams
- **QoE metrics**: Video Start Time < 2s; Buffering Ratio < 0.5%; 1% buffering increase = 14.5% higher abandonment (Conviva)

### Domain-Specific Incident Types
- CDN cache miss storms during live event start
- DRM license server overload or key rotation failures
- Encoder/transcoder pipeline failures during live broadcast
- Audio/video sync drift during live streams
- HDCP handshake failures on specific device families
- Multi-CDN switching logic failures
- Content geo-restriction misconfigurations

### SLA Expectations
- Premium live events: 99.99% during event window
- VOD platform: 99.95% availability
- Video Start Time: < 2 seconds
- License acquisition: < 500ms p95
- P1 response for live events: < 5 minutes

### Key Tools
- QoE Analytics: Conviva, Mux Data, NPAW/YOUBORA
- CDN: Akamai, Cloudflare, Fastly, CloudFront
- Encoding: AWS Elemental MediaLive, Harmonic VOS360, Bitmovin
- DRM: PallyCon, BuyDRM KeyOS, Irdeto
- Incident: PagerDuty, Grafana OnCall

---

## 10. E-Commerce / Retail

### Regulatory Requirements
- **PCI-DSS v4.0**: Same requirements as FinTech for payment processing
- **GDPR / CCPA**: Customer data privacy; right to erasure; 72-hour breach notification
- **PSD2 / SCA (EU)**: Strong Customer Authentication for payments > 30 EUR; 10-25% checkout drop-off if not implemented smoothly
- **ADA / WCAG**: Accessibility lawsuits increased 450% from 2017-2023; 4,605 ADA web accessibility lawsuits in 2023

### Domain-Specific Challenges
- **Peak traffic management**: Black Friday can see 3-10x normal traffic; Amazon processes 12.5M+ transactions/day during peak
- **Cart abandonment**: 69.99% average abandonment rate (Baymard Institute); 17% due to website errors/crashes
- **Inventory synchronization**: Real-time sync across stores, website, marketplaces; industry average only 63% SKU-level accuracy (Auburn RFID Lab)
- **Third-party integration dependencies**: Payment gateways, shipping APIs, tax calculation services, search engines all external dependencies

### Domain-Specific Incident Types
- Complete checkout unavailability (P1 revenue-blocking)
- Payment gateway timeouts during peak traffic
- Inventory overselling due to race conditions
- Cart/session management failures under load
- Third-party API failures cascading to primary platform
- Shipping rate calculation or tax service outages
- Price update propagation failures across channels

### SLA Expectations
- Platform: 99.95-99.99% uptime
- Homepage load: < 2 seconds
- Checkout: < 5 seconds end-to-end
- API response: < 200ms for catalog, < 500ms for orders
- Revenue loss: $10K-$50K/minute during peak for large retailers
- Amazon estimated: $13,805/minute in lost revenue during outage

### Key Tools
- Platforms: Shopify, Salesforce Commerce Cloud, BigCommerce, Adobe Commerce
- Monitoring: Datadog, New Relic, Sentry, ContentSquare
- CDN: Cloudflare, Akamai, Fastly
- Payments: Stripe, Adyen, PayPal/Braintree
- Load Testing: k6, JMeter, Locust, Gatling

---

## Cross-Domain Summary: Universal vs. Domain-Specific Requirements

### Universal (Every Domain Needs)
- Incident detection, triage, and resolution workflows
- On-call rotation and escalation management
- Change management with rollback capability
- Monitoring and alerting (metrics, logs, traces)
- Post-incident review and knowledge base
- SLA/SLO tracking and reporting
- Communication during incidents (internal and external)

### Domain-Specific (Varies by Industry)
- Regulatory compliance frameworks and reporting deadlines
- Industry-specific SLA targets and penalty structures
- Specialized incident types unique to the domain
- Domain-specific tooling integrations
- Safety and human-impact considerations (healthcare, manufacturing)
- Data sovereignty and residency requirements (government, finance)
- Content protection and rights management (media, gaming)

### Regulatory Severity Comparison

| Domain | Highest Penalty | Key Regulation |
|--------|----------------|----------------|
| Healthcare | $2M/year per violation category + 10yr prison | HIPAA/HITECH |
| Financial Services | $5M + 20yr prison (individual) | SOX |
| Government | Loss of ATO, contract termination | FISMA/FedRAMP |
| Telecom | $1M/day per violation | NERC CIP / FCC |
| E-Commerce | 4% global revenue | GDPR |
| Manufacturing | $1M/day (energy sector) | NERC CIP / IEC 61508 |
| Gaming | $500K + 5yr (DRM circumvention) | DMCA |
| Media/Streaming | $100K/day (FCC captioning) + contract revocation | CVAA / Studio DRM |

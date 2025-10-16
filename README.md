# Claims Reporting Data Product (Cardif Italy → CTDF)

## One-breath description
Cardif Italy is migrating **Claims domain reporting** to **CTDF (Cardif Trusted Data Fabric)** as a governed Claims Reporting Data Product.  
- **Sources:** Appian & Gipsy  
- **ETL:** SSIS  
- **Transfers:** CFT  
- **Reporting:** Power BI  
- **Metadata:** Collibra  
- **Legacy tools:** BO, Board, SAS, old DWs (phased out)  
- **Fallback path:** SharePoint → Power BI (manual, no secret data)

---

## Why
- Deliver governed, trusted reporting data
- Retire legacy warehouses/tools and reduce costs
- Strengthen governance (ownership, lineage, catalog, security)
- Standardize on CTDF + Power BI

---

## Target product
- **CTDF Claims Reporting Data Product**
  - Mediation (CFT agent, workflows/jobs)
  - Raw → Refined → Optimized layers
  - Data Exploration (ad-hoc)
- **Integrations**
  - Power BI dashboards (DB connection)
  - Collibra via REST API (metadata, lineage)

---

## Data flows

### Normal flow
```
Appian / Gipsy → SSIS (DB or files)
SSIS → CFT → CTDF Mediation
CTDF: Raw → Refined → Optimized
Power BI → DB connection
Collibra → REST metadata
```

### Contingency flow
```
Operator downloads file from Appian/Gipsy
→ Uploads to SharePoint
→ Power BI reads from SharePoint
```
- No secret data in contingency path
- Manual & temporary fallback
- Actors: Cardif Operator (prep/load), Cardif User (consume dashboards)

---

## Roadmap
- Initial slice reviewed in ITSVC
- Next: reporting needs assessment, SAP/BO decommissioning
- Dependencies with other initiatives
- Official doc tracks IT project cost (k€), run cost (k€), milestones (IC INIT / ITSVC VALID / IC END)

---

## Security & continuity
- **Authentication:** SSO via IAM
- **Traceability/Audit:** Compliant
- **Confidentiality/Integrity/Availability:** Compliant at **C3** classification
- **Continuity:** Mostly compliant (phase 1 adequate, must improve later)
- **Contingency:** SharePoint/Power BI fallback with no secret data

---

## Compliance
### Enterprise Architecture
- Overall: Compliant / Mostly compliant
- Risks: vague dashboard requirements, cross-domain stewardship issues, draft architecture

### Technical ITG
- Platform: Compliant (CTDF + PBI + SSIS + CFT)
- Performance: Warning → tests required
- Mutualisation: Compliant (managed services)

### Infrastructure ITGP
- Hosting: Compliant (cloud managed)
- Network/Telecom: Compliant
- Backup/Operability: Compliant

### Security (Cardif)
- Authentication, authorization, traceability, confidentiality, integrity, availability: Compliant
- IT Continuity: Mostly compliant (adequate for phase 1, must improve)
- Classification: **C3**

### Production readiness
- Backup, volumetry, operability: Compliant
- Load/performance tests: Planned

---

## Risks & reservations
- Performance/scale unknowns (Power BI refresh/concurrency) → tests required
- Ownership/stewardship: SSIS extracts cross-domain → fix contracts/RACI
- Continuity: raise RTO/RPO, perform restore drills
- Ambiguous dashboard requirements threaten design
- Contingency path: manual → enforce DLP/retention
- Coupling: clarify producer/consumer boundaries, avoid point-to-point

---

## Definition of Done
- Product contract in Collibra (schema, SLAs, RLS, PII classification, retention)
- Performance test results meeting agreed SLOs
- Continuity plan with RTO/RPO evidence, backup/restore drills, documented fallback runbook
- Fully specified interfaces (file formats, checksums, idempotency, error handling)
- RACI resolving stewardship issues
- Legacy tools decommissioned tied to data-quality signoff

---

## Acronym Crib Sheet
- **CTDF** – Cardif Trusted Data Fabric
- **SSIS** – SQL Server Integration Services
- **CFT** – File Transfer Tool
- **PBI** – Power BI
- **IAM/SSO** – Identity & Access Management / Single Sign-On
- **CIAT** – Confidentiality, Integrity, Availability, Traceability
- **ITSVC / ITG / ITGP** – Governance bodies
- **C3** – Data classification level

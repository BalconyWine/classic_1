# Meeting Minutes — PIMS Technical Assessment & DMZR/MCR Migration

**Date:** 27 April 2026  
**Scope:** PIMS ecosystem migration to DMZR / MCR as Code — Mexico scope  
**Format:** Condensed meeting minutes  

---

## 1. Summary

The meeting focused on the remaining open points of the PIMS Technical Assessment for the migration to DMZR / MCR as Code.

The main conclusion is that the PIMS ecosystem should not be managed under one single AP code. The applications in the ecosystem, such as PIMS, Ada/Adam, PNT and CRS, should be split into separate AP codes, likely with separate namespaces. This impacts provisioning, flow definition, Cloud Review preparation and CI/CD organization.

The target remains to have the Technical Assessment ready by Thursday, provided that the AP code split, Excel provisioning files, architecture diagrams and OneNote open points are updated.

---

## 2. Main Decisions

| # | Decision |
|---:|---|
| 1 | Split the PIMS ecosystem into several AP codes instead of using one global AP code. |
| 2 | Create one provisioning Excel file per AP code/application. |
| 3 | Adapt the flow matrix for each AP code, including cross-namespace flows. |
| 4 | Keep the Thursday target for Technical Assessment completion, subject to documentation updates. |
| 5 | The Technical Assessment does not need a full detailed test campaign, but must identify test types, ownership and key security requirements. |
| 6 | Penetration testing is mandatory because the application handles sensitive/secret data. |

---

## 3. Key Technical Points

### 3.1 AP Codes, Namespaces and Flow Matrix

The architecture recommendation is to split the PIMS ecosystem by application/AP code. This provides clearer segregation and provisioning, but requires explicit documentation of flows between applications and namespaces.

Example: if the PIMS web portal and Ada/Adam are deployed in different namespaces, their communication flows must be listed in the flow matrix.

The flow matrix is one of the most critical deliverables and must be replicated and adapted in each provisioning Excel file.

### 3.2 Provisioning Files

The current Excel provisioning file must be split into one file per AP code. Lines related to applications that now belong to separate AP codes must be removed from the original file and moved to the appropriate new file.

Each file should include:
- application-specific resources;
- required flows;
- dependencies with other namespaces/applications;
- security and access requirements.

### 3.3 Cloud Review / ITSBC

The Cloud Review is still open. With several AP codes, multiple Cloud Review cards or sessions may be required.

A key point to confirm is whether one global Cloud Review / ITSBC session can cover the whole PIMS ecosystem, since the applications are technically linked.

This point could become blocking if the target DMZR/MCR platform eligibility is not confirmed.

### 3.4 Security, Encryption and Access

Access to DMZR / IBM Cloud must be requested through the official access portal, referred to during the meeting as My Technical Access / My Technical Access Express. The exact name must be confirmed.

Some permissions, such as Kafka topic access, may require a manager-approved request through the access process.

For file exchanges:
- CRS does not encrypt the information directly.
- The country application, such as Mexico, is responsible for file-level encryption.
- PGP is the expected mechanism for file encryption.
- CFT/STCP may provide secure transport, but this does not replace file-level encryption.

MTLS is required for relevant flows, especially with Confluent/Kafka and MCR as Code components. Certificates should use the official PKI service instead of self-signed certificates.

### 3.5 Runtime, Java 8 and Ingress

The application will remain on Java 8 for now. Java 8 Docker images are still available and no blocking point was identified.

No session affinity is required at this stage.

For ingress configuration:
- pass-through may be acceptable for a simple single-context application;
- re-encrypt may be needed when multiple contexts or services are exposed behind the same route.

The exact MQ encryption mechanism in DMZR remains to be confirmed in the platform documentation.

### 3.6 Batches, CFT Pod and S3

The target pattern discussed is:
1. a CFT pod receives or transfers files;
2. files are stored in S3;
3. batch processes read and process the files from S3.

Two implementation options are possible:
- adapt the batch code to use the S3 API directly;
- mount S3/storage as a volume to keep behavior close to the current filesystem model.

This requires later detailed analysis but does not block the Technical Assessment.

### 3.7 Database and Data Migration

No specific Oracle optimization or non-standard configuration is currently known, which is positive.

A data purge is ongoing. The Mexico target volume is estimated around 1 TB, to be confirmed.

The main risks are:
- complex SQL queries;
- unknown response time on the target architecture;
- large data transfer during switchover;
- unclear ownership between LATAM DBAs and France/MCR teams.

Recommended migration approach:
- transfer most data before switchover;
- transfer only the delta during final cutover;
- split exports into several compressed packages;
- avoid one large transfer file.

A Parquet-based data migration POC is ongoing with David Silva’s team and must be reviewed.

### 3.8 Authentication, Scans, Monitoring and Operations

The target authentication mechanism is ITG Web SSO.

Current scans to document:
- Sonar;
- Fortify;
- Vulnerability Advisor, currently on-premise.

For the target pipeline, Docker/container image scanning must be included.

Dynatrace is expected for monitoring. If advanced end-to-end or user performance monitoring is required, the dedicated monitoring/performance team should be involved.

LATAM/local operational and regulatory constraints for sensitive or secret data must be clarified.

### 3.9 CI/CD and Tests

The current on-premise model uses global CI/CD for all components, which is not ideal for the target architecture.

Recommended target:
- at minimum, one pipeline per AP code;
- ideally, one CI/CD pipeline per application component.

Testing must cover:
- integration tests;
- user acceptance tests;
- performance tests;
- security tests;
- mandatory penetration testing;
- technical validation before rollout.

The existing PIMS test team can likely be reused. A COE/test center may be contacted early for guidance and budget estimation.

---

## 4. Main Risks

| # | Risk | Impact | Mitigation |
|---:|---|---|---|
| 1 | AP code split adds documentation and provisioning workload. | Technical Assessment closure may slip. | Prioritize Excel split, flow matrix and diagrams. |
| 2 | Multiple Cloud Reviews may be required. | Governance cycle may become longer. | Ask whether one global Cloud Review / ITSBC can cover all AP codes. |
| 3 | Cross-namespace flows may be missed. | Runtime communication failures. | Update the flow matrix per AP code and namespace. |
| 4 | Latency between MCR/DMZR and LATAM on-premise is unknown. | Possible response-time degradation. | Run measurements and performance tests on the target platform. |
| 5 | Mexico data transfer at switchover is too large. | Cutover delay or failure. | Pre-transfer data and transfer only the delta at cutover. |
| 6 | Complex SQL queries may perform differently. | Database performance issues. | Run load and response-time tests. |
| 7 | Batch migration to S3/CFT pod is not detailed yet. | Rework or batch execution issues. | Analyze batch by batch and choose S3 API or mounted volume. |
| 8 | MQ encryption mechanism is unclear. | Security or documentation gap. | Confirm through DMZR documentation. |
| 9 | LATAM regulatory rules are not confirmed. | Compliance risk. | Validate with local security/compliance experts. |
| 10 | Pen test may not be planned early enough. | Security/governance blocker. | Plan penetration testing early. |

---

## 5. Action Log

| # | Action | Owner | Status |
|---:|---|---|---|
| 1 | Create or initiate separate AP codes for PIMS ecosystem applications. | Andres / Architecture | Open |
| 2 | Split the provisioning Excel into one file per AP code. | Andres | Target Thursday |
| 3 | Adapt the flow matrix in each provisioning file. | Andres | Critical |
| 4 | Update architecture diagrams with AP code split, namespaces and Mexico scope. | Andres | Open |
| 5 | Update OneNote and close clarified points. | Andres | Before next review |
| 6 | Confirm whether one global Cloud Review / ITSBC is possible. | Andres / Architecture | Open |
| 7 | Create DMZR / IBM Cloud access request. | Andres | To initiate |
| 8 | Document DMZR access and Kafka permission process. | Andres | For TA |
| 9 | Document file-level encryption responsibilities. | Andres | For TA |
| 10 | Confirm MQ encryption mechanism in DMZR. | Andres / ITG | Open |
| 11 | Confirm Java 8 Docker image/version details. | Andres / DevOps | Open |
| 12 | Document ingress mode: pass-through or re-encrypt. | Andres / Architecture | Open |
| 13 | Analyze CFT pod / S3 / batch migration impact. | Technical team | Later |
| 14 | Confirm Mexico database volume and purge status. | Andres / DBA | Open |
| 15 | Clarify LATAM DBA access to the MCR database. | Andres / DBA teams | Open |
| 16 | Review Parquet migration POC with David Silva’s team. | Andres | Open |
| 17 | Document ITG Web SSO target authentication. | Andres | For TA |
| 18 | Document current scans and target image scanning. | Andres / DevOps | For TA |
| 19 | Clarify LATAM/local operational rules for sensitive data. | Andres / Security | Open |
| 20 | Define target CI/CD model, ideally per component. | Andres / DevOps | Open |
| 21 | Confirm test ownership and required test categories. | Andres / Test team | For TA |
| 22 | Plan mandatory penetration testing. | Andres / Security | Required |

---

## 6. Points to Confirm

| # | Point |
|---:|---|
| 1 | Exact application name: Ada or Adam. |
| 2 | Exact current AP code name. |
| 3 | Official access portal name. |
| 4 | Exact MQ encryption mechanism in DMZR. |
| 5 | Whether one global Cloud Review / ITSBC can cover all AP codes. |
| 6 | Whether LATAM DBAs can access/manage the MCR database directly. |
| 7 | LATAM/local operational and regulatory constraints for sensitive/secret data. |
| 8 | Final test ownership and possible COE/test center involvement. |

---

## 7. Conclusion

The Technical Assessment can still target Thursday, but the AP code split is now the critical path.

The immediate priorities are:
1. split the provisioning Excel by AP code;
2. update the flow matrices;
3. update the architecture diagrams;
4. clarify Cloud Review / ITSBC expectations;
5. document the remaining security, database, CI/CD and test points.

The main risks are identified and manageable if tracked during the migration project: cross-namespace flows, data migration, database performance, encryption, access rights, CI/CD modularity and mandatory security testing.

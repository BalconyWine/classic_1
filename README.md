CRIT101 — Team Contacts
Squad D4W must provide the DE/DI with a summary of the main application contacts: PO, application contacts, mailing lists, support / Snow groups, and operations contacts. The DE/DI header section must clearly identify the relevant contacts for the ROAD Data Quality application.
CRIT102 — Application Identity Card
The application was identified as Cardiff ROAD Data Quality / Data Quality Gateway, linked to project INE0954. It corresponds to a Collibra Data Quality add-on module, deployed as a separate application because it is standalone and cloud native, with a different confidentiality level and user population from ROAD DGC.
CRIT103 — Business Criticality
The application is driven by a BCBS regulatory constraint and requires a fast production deployment: users must be able to start working before June, with a target deployment around mid-May. The application was considered “low” criticality during the discussions, but this does not exempt it from the mandatory PACT deliverables.
CRIT104 — IC Plan
An IC Plan is required, even if the application is low criticality. There is no longer an exemption for this point. No individual ICP failover exercise is expected within the PAS V4 scope; the application should participate in the grouped exercise if applicable. However, the IC Plan documentation remains mandatory and must be provided, potentially with support from the Continuity team.
CRIT105 — Functional Architecture
The functional architecture diagram can be taken from the ITSVC / architecture support file. The functional diagram remains usable even if some technical elements have evolved compared with the initial strategy. A screenshot of the AP1765 Functional Architecture diagram can be used as evidence.
CRIT106 — Asset Management / ASC Sheet
Squad D4W, with support from the security referent / security expert, must provide the ASC security review. The identified security contact is Germain Poitier. If the ASC already contains the attached reviews, they can be used as evidence.
CRIT107 — Technical Architecture & Security Schema / SAT
ITG Apps CARDIF must provide the SAT/SATS. This deliverable is expected to frame the technical and security architecture before resource requests, flow openings, and production deployment. Even though some historical deployments may have been performed before the SATS was finalized, the SATS is still strongly expected before actual production operation.
CRIT108 — Risk Management / Risk Analysis
The security risk analysis must be handled with the security expert, notably Germain Poitier. The expected security acceptance report must cover any reservations, accepted risks, remediation commitments, and remaining points to be followed after production deployment if a light production deployment is decided.
CRIT109 — List of Application URLs
The operations file must contain the list of application URLs: user URLs, exposed URLs, and technical URLs where applicable. The application exposes a front-end / Web UI ingress through a VIP. The production FQDN is still expected in order to finalize the associated request.
CRIT110 — IAM Applications Rights
Squad D4W must provide evidence of application rights management through IAM / MyAccess. A MyAccess screenshot showing the catalog entry used to request access to ROAD Data Quality is considered acceptable evidence.
CRIT111 — Server Connections / Monitoring / Alerting
ITG Apps CARDIF must confirm the implementation of Sysdig alerting, especially automatic email alert notifications. The objective is to demonstrate that a technical monitoring and alerting mechanism is operational for production support.
CRIT112 — Storage / Secret Management
ITG Apps CARDIF must provide, in the DE/DI, a summary of the HVault secrets used by the application. This point is owned by Apps because it concerns the technical management of secrets and their integration into the operating environment.
CRIT113 — List of APIs Consumed and Exposed
Criterion bypassed: the APIs are considered proprietary / native to the Collibra ROAD Data Quality solution and do not go through an IPG-type API catalog. API exchanges are direct between applications, notably toward ROAD DGC. However, it is possible to add a summary of the APIs used or the required flows in the DE/DI, mainly to document network openings.
CRIT114 — List of Servers
Criterion not applicable / bypassed: the application is cloud native on Kubernetes / PAS V4 and does not rely on a classic list of application servers to maintain. The infrastructure elements should instead be described in the DE/DI through namespaces, Kubernetes components, Postgre instances, and PAS V4 resources.
CRIT116 — Launch Procedures, Including Stop/Restart
Squad D4W and ITG Apps CARDIF must provide the stop/restart procedure in the DE. For a microservices application, a classic stop/restart procedure is not very meaningful, but the operating procedure still needs to document how to stop the application, restart pods, or restart components if necessary.
CRIT118 — IAM Technical Account
Criterion bypassed / not applicable: no specific IAM technical account need was identified during the discussion. The point was explicitly dismissed during the review.
CRIT119 — Compliance with Development Rules
The criterion does not concern software development rules, but IT Group rules: governance, architecture, urbanization, and solution compliance. Since this is a new application, the PAS V4 resource provisioning payloads / information must be provided, as well as the ITSVC validation note. The ITSVC validation will formalize acceptance of the solution before production deployment.
CRIT121 — Technical Supervision Devices and Availability Measurement
ITG Apps CARDIF must provide the Dynatrace production supervision dashboard. The key point is not only the availability rate, but the existence of effective technical supervision: at minimum a dashboard, ideally synthetic, with supervision scenarios. The match zone can only be created once production is available.
CRIT124 — Description of Kubernetes Applications
Squad D4W must provide the DE with the description of the Kubernetes applications. ITG Apps CARDIF must complete it with the technical information related to PAS V4: namespaces, components, Postgre instances, resources, and identification elements required for operations.
CRIT133 — Purge Policy
Criterion not applicable / bypassed: no specific purge policy was identified during the discussion. Retention or purge constraints are more likely to fall under source applications or underlying service offerings, if applicable.
CRIT135 — Configuring Application Servers
Criterion bypassed: classic application server configuration is not directly applicable because the application is cloud native / Kubernetes-based and relies on a third-party vendor solution. The relevant information must be covered in the DI through deployment elements, prerequisites, flows, and application configuration.
CRIT136 — Configuring Virtual Host
Criterion bypassed: the classic notion of a virtual host is not directly applicable. The application is exposed through the ingress, VIP, and FQDN. The useful information must be documented in the DI or DE.
CRIT137 — Configuring Installation Clusters
Criterion bypassed: detailed cluster configuration is handled by PAS V4 / Kubernetes. The DI only needs to document the elements required for application deployment: namespace, resources, prerequisites, components, and specific parameters.
CRIT139 — Directory Configuration / File Systems
This point was not discussed in detail specifically. It was included in the DI logic: if the application requires specific directories, volumes, mounts, or file systems, they must be described in the installation file. Otherwise, the criterion can remain to be treated as not applicable or covered by PAS V4 depending on the case.
CRIT143 — Configuring Databases
Squad D4W must provide in the DI the information required for database creation and configuration: Postgre instances, initial size, extension parameters, encoding, and useful technical characteristics. This point is close to the “Description of databases” criterion, but here the expected content is more about technical creation and configuration.
CRIT150 — Configuration Verification
ITG Apps CARDIF must provide configuration evidence, notably a screenshot of the DevOps space home page. This evidence shows that the environment and configuration elements have been created and are visible.
CRIT152 — Retrieving Sources
No clear oral comment was specifically identified for this criterion during the discussion. The point was not covered in detail during the meeting.
CRIT155 — Configuration SSO
The DI must contain the information related to the Web SSO Group configuration. The application is compatible only with an IDP-initiated mode, which is not supported by César; this is why authentication goes through Web SSO Group. This point must be documented in the installation / operations file.
CRIT158 — Post-Production Control Procedure
A post-production control procedure must be planned to verify that the production environment works and that the solution is operational. This point is linked to the acceptance report and the post-deployment checks expected before the service is effectively opened to users.
CRIT159 — Rollback Procedure
Rollback was not discussed explicitly in detail. The topic was addressed indirectly through the production change: if a technical operation conditions service opening, for example final delivery, DNS switch, or data import, it must be covered by a change and include rollback procedures if necessary.
CRIT165 — Actual Evolutions with Declared and Planned PROD Change
A change number will be required to frame the production deployment / service activation operations. Build actions performed before real business use can be considered “hidden production” and are not necessarily expected as PACT evidence. However, the final operation enabling service opening must be covered by a change.
CRIT169 — Compliance with Technical Roadmaps and Obsolescence
This point is sensitive because PAS V4 is reaching the end of its trajectory and a migration to ROX will probably need to be planned around 2027. The exact date still needs to be confirmed, with some discussions mentioning late 2026 / early 2027 or late 2027. For PACT, the expected evidence is the ITSVC passage note confirming that the solution can be accepted despite this technical trajectory.
CRIT170 — Support Has Been Well Informed
The criterion is kept. It must be demonstrated that support has been properly informed about the application, its scope, and the required evolutions, with the elements needed for operational takeover.
CRIT171 — CAPA Plan
ITG Apps CARDIF must contact Maxime Frolov to obtain a screenshot of the APS equipment plan. The objective is to demonstrate that the ordered resources are properly tracked, identified, and consistent with the application needs.
CRIT173 — Asset Management / Inventory Excluding Docker Containers
Criterion bypassed: this point was not considered applicable to the application in this Kubernetes / PAS V4 context. A classic asset inventory excluding containers is not requested for this scope.
CRIT174 — Referencing and Maintaining Asset Inventories / Network Solution
Criterion bypassed: no specific need for network inventory referencing was identified for the application. The useful network elements are instead covered by flow requests, VIP, FQDN, ingress, and DE/DI documentation.
CRIT175 — Referencing and Maintaining Inventories of Workstation Assets
Criterion bypassed: no workstation or specific user asset needs to be inventoried for this application scope.
CRIT176 — Asset Management / ITG Product Reference
Criterion bypassed: ITG Product Reference / service catalog referencing was not retained as applicable during the discussion.
CRIT178 — Vulnerability Management / Internal Vulnerability Scan — Technical Scan
Criterion bypassed: the technical vulnerability management part was not retained as applicable in this context. The application is not exposed to the Internet, and several classic technical checks were excluded.
CRIT179 — Vulnerability Management / IVS WAS or EVS Application Scan
ITG Apps CARDIF must submit a URL scan request through the security catalog and then provide the associated report. This point remains to be handled even though pentest, hardening, and SAST were bypassed.
CRIT181 — Hardening / STS / Health Checking
Criterion bypassed: no specific STS hardening is expected. The point was explicitly excluded during the review.
CRIT182 — Application Security / Pentest
Criterion bypassed: the application is not exposed to the Internet, so no pentest is expected.
CRIT183 — Application Security / Code Audit SAST and SCA
Criterion bypassed: this is a vendor software / proprietary Collibra solution, so no SAST/SCA code audit is requested from the project side.
CRIT184 — Vulnerability Management / Security Monitoring
Criterion bypassed: security vulnerability monitoring was not retained as applicable during the discussion.
CRIT185 — Cyber Events and Alerts Management
Criterion bypassed: no specific cyber event management mechanism was requested for this scope. The topic was excluded during the review.
CRIT186 — IT Outsourcing / Third Party Management
Squad D4W must check with Purchasing or the application PO for the support contract number with the vendor. Only the contract number is expected, not the contract terms. The objective is to demonstrate that a contract exists and that due diligence was performed as part of the contracting process.
CRIT188 — Data Security / Non-Production Data / Anonymization
Criterion overridden: no exchange of production data toward non-production environments was identified as problematic. The flow direction discussed is rather from non-prod / dev to prod, which is less sensitive than copying production data down to a development environment. The point nevertheless remains to be confirmed with the security expert / security acceptance report.
CRIT189 — Data Security / Data Encryption
Encryption remains expected as a standard. The point must be covered by the security acceptance report or by the elements provided by the security expert. Unlike anonymization, encryption was not excluded.
CRIT190 — Generic and Specific Steering Instructions and Alert Sheets
Criterion bypassed during the review. No detailed oral comment was given regarding specific steering instructions or alert sheets.
CRIT191 — Application and DB Backup Procedures
Criterion bypassed: application and database backup procedures are considered included in the platform’s standard services / service offerings. No specific deliverable was requested from the project side.
CRIT192 — Customer Functional Acceptance Report / Technical Acceptance Report
Squad D4W must provide the acceptance report. This document must confirm that the environment works, that the solution is operational, and that the required checks have been performed before production deployment / service activation. This acceptance report is one of the important pieces of evidence before opening the service to users.
CRIT193 — Description of Databases and Accesses
Squad D4W must provide in the DE the description of the databases and associated accesses, notably the Postgre instances used by the application. This point complements CRIT143: CRIT143 is more about configuration / creation, while CRIT193 is about the operational description of the databases and their accesses.

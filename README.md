Subject: LATAM POC – Scenarios Presented and Required Validations

Dear Team,

Following our discussion yesterday, here is a summary of the deployment scenarios we presented and the remaining steps required before we can proceed with the POC:

Deployment Scenarios Considered:

Use of the Sandbox on Cluster 246 – This is the preferred solution, provided the sandbox is available.

Standard Deployment on Cluster 246 – If the sandbox is not an option, we can still move forward by reducing pod CPU usage below 1 vCPU, subject to TEO validation of available capacity.

Deployment on Cluster 1045 – This remains the fallback scenario, requiring a full onboarding process and additional validation efforts.

Next Steps & Outstanding Items:

FinOps Coordination: Our FinOps contact will be looped in early next week to provide further clarification and ensure alignment on governance.

Access: We currently do not have the necessary credentials to begin. This has been flagged before — access must be granted before any activity can start.

Networking Validation: From our side (ADM/ZR), the data flow will be outbound only, requiring minimal security exposure. However, from the LATAM side, incoming flow needs to be opened. We are currently awaiting confirmation from your networking/security team on this point.

Once these items are confirmed, we are fully ready to proceed with the deployment.

Best regards,
[Your Name]
SRE & Coordination Team

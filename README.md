Subject: LATAM POC – Deployment Options & Next Steps

Hi Team,

Thank you for your time in yesterday’s LATAM call. Building on Wednesday’s FinOps deep-dive, here’s a concise professional summary of our proposed deployment paths and the critical validations we still need before kicking off the POC.

1. Deployment Options

Sandbox on Cluster 246 (Preferred):
Leverage the existing sandbox slot on 246 for a rapid, low-overhead start.

Standard Deploy on Cluster 246:
If the sandbox is occupied, we can still use 246 by reducing each pod’s CPU request below 1 vCPU. The Technical Office (TEO) must confirm there’s capacity.

Fallback to Cluster 1045:
Only if Cluster 246 proves unviable. This path requires full onboarding and additional infrastructure validations.

2. Outstanding Validations

Sandbox/246 Capacity: TEO to confirm sandbox availability or reduced-footprint capacity on Cluster 246.

Network Security: LATAM networking/security teams to approve the necessary inbound flow; our outbound-only traffic poses minimal risk.

Access Credentials: Dev/Admin to issue POC credentials—deployment cannot commence until these are in place.

FinOps Coordination: We will include our FinOps contact on next week’s follow-up to finalize internal billing and governance.

Once these items are addressed, we’re ready to launch immediately. Please update the channel with status on each validation so we can stay aligned and move forward without delay.

Best regards,

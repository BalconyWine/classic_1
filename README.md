# classic_1
A classic PRoject 
Hi Team,

Following our meeting yesterday (Thursday) with LATAM, and based on the deep-dive we did during Wednesday’s FinOps call, here’s a clear recap of the key findings we presented:

🔍 What We Uncovered
After analyzing the current cost model, resource planning, and billing structure, we shared the following insights with LATAM:

Cluster Cost Misalignment

Cluster 1045 is invoiced at €3 100/month, regardless of usage.

Our projected POC usage equates to only €300–€460/month, a massive gap.

LATAM would absorb the full invoice unless an internal correction is made.

Alternative Cluster Option

Cluster 246 is ~75% utilized.

Could support the POC if pod vCPU requests are lowered below 1 vCPU — TEO must validate this.

POC Resource Profile

2 pods (Backend + UI), each with 3 vCPU / 8 GB RAM → total: 6 vCPU / 16 GB RAM.

~10 images expected → €5/month in registry storage.

Ancillary Services Estimate

Kafka: LATAM’s estimated share: ~€150/month.

COS: Minimal impact expected.

ExaCC: Small instance without backup → €160–234/month.

Cardiff Budget Context

Cardiff GIE already spends ~€122 000/month on non-prod infrastructure.

The POC adds a negligible delta — a drop in the ocean.

For this reason, it was advised not to cross-charge LATAM for this POC, or at least apply usage-based billing (~€300/month).

✅ Recommendations Shared
Negotiate billing: Push for internal cost sharing based on real usage — not flat invoices.

Optimize resource requests: Reducing to 0.1–0.5 vCPU/pod can drastically cut costs (~30–60%).

Idle time savings: Explore pod shutdown during nights/weekends to further reduce footprint.

📌 What Needs to Happen Next
Area	Action
TEO	Confirm Cluster 246 capacity if vCPU is lowered
Networking	Validate connectivity to chosen cluster
Dev Team	Finalize vCPU/RAM specs, Kafka volume, COS I/O profile
Finance/Internal	Align with Cardiff GIE to avoid incorrect or inflated cross-charging

This POC is small, but if we don’t act on the internal billing logic, it becomes needlessly expensive. We now need confirmation from the Networking team and TEO to finalize the direction.

Let’s keep the momentum going.

Best,
SRE & FinOps Coordination Team

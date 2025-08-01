Subject: LATAM POC – Deployment Scenarios and Pending Inputs

Hi Team,

Following our discussion yesterday, here’s what was presented regarding the POC launch plan:

We’re considering three deployment scenarios:

Use the sandbox on Cluster 246 (preferred option, assuming availability).

If the sandbox isn’t available, fall back to a standard deployment on 246 with reduced CPU requirements (< 1 vCPU/pod), pending validation from TEO.

As a last resort, deploy on Cluster 1045, which would require full onboarding.

This was the structure shared during the call. We agreed to loop in our FinOps contact next week for further clarification and to finalize governance.

On our side, we’re ready. Traffic will be outbound only from ADM (ZR), so very limited exposure — no heavy security concerns expected.

On the LATAM side, traffic will be inbound, so we’re waiting for feedback from your networking team regarding approval of that flow. This is currently the main blocker.

Also important: we still don’t have access, so we can’t start anything yet. This has already been communicated before — no access, no deployment.

We’re standing by. Once we get confirmation on access and networking, we’re good to go.

Best regards,

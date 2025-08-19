Subject: Cluster Usage Decision for PIMS PoC

Hi all,

Following our latest discussions with the TO, we’ve aligned on the cluster strategy for the PIMS PoC. The consensus is that we will use the existing (old) cluster rather than moving to the new one, since:

Network openings and ecosystem are already in place on the old cluster, making setup simpler and faster.

The new cluster would require fresh flux-opening requests and additional validations, which would delay progress.

That said, we need to be mindful of resource consumption. The old cluster is already heavily used (~75% CPU reservations, ~60% RAM), and over-allocation could impact other applications. To avoid exceeding quota and to ensure stability, we will:

Start small (minimal CPU/RAM, 1–2 pods per component) for the PoC phase.

Monitor usage closely and adjust only as strictly necessary.

Scale up resources progressively in line with real needs once the solution is validated.

This approach allows us to move forward quickly while keeping costs and risks under control.

Please confirm alignment so we can inform Networking and move ahead with the required actions.

Best regards,

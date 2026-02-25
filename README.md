Hello Team,

Following our internal review of SaaS incidents over the last four months, we have analyzed the volume and nature of the tickets currently reaching our team. We have identified areas where the current alert thresholds are creating unnecessary noise and where applicative issues are being misdirected.

To improve efficiency and system stability, we propose the following updates and require your assistance with a necessary cleanup:

1. Disk Space & Slow Disk Alerts (Infrastructure)

Current Status: We have been receiving a massive volume of automated incidents regarding disk space and "slow disk" warnings.


Root Cause Discovery: During our investigation, we found files dating back more than 12 years with individual sizes exceeding 15GB. These legacy files are one of the main causes of slowing down the app, slowing the disk, causing application errors, and triggering these constant incidents.


Action Taken: We have temporarily disabled some of the automated alerting for the disk size to reduce the false positive noise.


Action Required from Your Team: We need your team to urgently review these older files. Please check which files are still relevant to the business and which are no longer needed so they can be permanently deleted. Addressing this is necessary to stabilize the disk performance and app speed.

2. Control-M and CFT Incidents (Applicative)

Current Status: We frequently receive automated incidents regarding Control-M jobs and CFT file transfers.



Observation: These are predominantly applicative issues—such as blocked file systems from heavy database loads or scripts needing a simple restart.



Proposal: We propose changing the routing of these incidents so they are assigned directly to the Applicative Support team (Jawad's team / Data.ai) rather than the infrastructure team. Since resolving these often requires validating the application logic or business flows, it is more efficient for the applicative team to receive them first.


Next Steps
File Cleanup: Please let us know when you can review the >15GB legacy files for cleanup.


Routing Validation: Please confirm if you agree with re-routing the Control-M/CFT incidents directly to your support group.

Best regards,

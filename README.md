Technical Documentation: Datalab Infrastructure Monitoring (AERL_APS_DAI-99)
1. Document Overview & Context
This document outlines the final implementation of the monitoring and alerting infrastructure for the AP88355 Datalab project. The original scope of this ticket was to integrate the Datalab infrastructure into Dynatrace monitoring and include it in the squad's daily checks. However, due to platform limitations, the strategy was pivoted to utilize IBM Cloud Monitor as the primary observability platform. This document was created to fulfill the request by Oussama BENNORA to thoroughly document the ticket's output upon reopening.

2. Feasibility Study & Dynatrace Limitations
Initial attempts to implement the monitoring within Dynatrace revealed several technical blockers. After consulting with the Performance Expert team and internal squad members, Dynatrace integration was deemed unfeasible for the following components:

Redis Monitoring: It is not possible to monitor Redis using Dynatrace. Loc Nguyen from the Performance Expert team confirmed that we cannot install a Dynatrace agent within the IBM Cloud cluster environment where Redis resides. Furthermore, tests by Ravindra utilizing a Dynatrace configuration (AP88355-DOMINO CARDIF DATALAB PLATFORM (C)-dMZR-Prod - dMZR-Prod - Dynatrace) failed to fetch Redis-related data.

CFT Monitoring: Ravindra investigated and confirmed that it is not possible to monitor CFT status or transfer errors using Dynatrace.

COS Bucket Monitoring: Tracking the available status and usage of the COS Bucket is impossible in Dynatrace. Yassine el Fachtali confirmed that the required JavaScript/Python scripts for fetching COS size are disabled within Dynatrace. Additionally, the API swagger documentation does not expose relevant information for our specific use case.

3. Implemented Architecture: IBM Cloud Monitor
To overcome the Dynatrace limitations, the monitoring stack was successfully built natively within IBM Cloud Monitor (sd-bnpp-eu - eu-fr2).

3.1 Dashboard Configuration
A centralized dashboard named AP88355 - Datalab was created. The dashboard scope is filtered by ibm_resource_group_name in rg-ec002i002948.

3.2 Monitored Metrics
The following metrics have been successfully integrated into the dashboard as visual panels:

Redis Memory usage

Redis CPU usage

Redis Connected clients vs 1 week ago

Redis Disk usage

CFT Liveness

CFT - Storage (Use larger timeframe)

4. Alerting Rules & Thresholds
Based on the requirements outlined in the 16/02 weekly sync Meeting Minutes by Mickael ALLAIN, specific thresholds were requested for Redis CPU and Disk. Two active alerts have been configured and enabled within IBM Cloud Monitor.

4.1 AP88355 REDIS CPU Alert
Status: Enabled

Severity: Low

Scope: ibm_resource_group_name in rg-ec002i002948

Target Metric: ibm_databases_for_redis_cpu_used_percent

Condition: Triggers if CPU usage is greater than 80% on average over the last 5 minutes.

Exact Query: avg(avg_over_time(ibm_databases_for_redis_cpu_used_percent{ibm_resource_group_name=~"rg-ec002i002948"}[300s])) > 0.8

Duration/Trigger: Triggers immediately when the condition is satisfied.

Data Unavailable Handling: Set to "Ignore".

Active Alert Occurrence Stopped Reporting Data: Set to "Keep Firing".

4.2 AP88355 REDIS DISK Alert
Status: Enabled

Severity: Low

Condition Requirement Note: The squad requested a hard limit of Disk > 200 GB. The implemented solution utilizes a dynamic percentage-based threshold, triggering when disk capacity exceeds 80%.

Exact Query: ( avg ( ibm_databases_for_redis_disk_used_bytes{ibm_service_instance_name="rd002i000423"} ) / avg ( ibm_databases_for_redis_disk_total_bytes{ibm_service_instance_name="rd002i000423"} ) ) * 100 > 80.0

Duration/Trigger: 0 secs (Immediate trigger upon threshold breach).

5. Notification Matrix
A centralized notification strategy was deployed to ensure the appropriate team members are informed of infrastructure anomalies.

Notification Channel Name: CHAA - AP88355 - alerts

Delivery Method: Email

Recipients: Amine, Rodrigo, Ilhem, and Kumar

Notification Lifecycle Configuration: The system is configured to notify users on the initial trigger, upon acknowledgment, and upon resolution of the alert. If an alert remains active and unresolved, the system will re-notify the recipients every 2 hours.

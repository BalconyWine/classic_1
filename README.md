Subject: [Action Required] CIDP "Follow the Sun" Monitoring - Scope, Access, and Next Steps

To: Danilo FERNANDEZ; Wesley Val; Astrid Melendez
CC: José Cáceres

Hi Danilo, Wesley, and Astrid,

Following up on my chat with Danilo, I am sharing this email to ensure proper traceability as we establish the "Follow the Sun" monitoring process for the CIDP application.

To outline the workflow, I have created a Confluence page detailing the sanity check process, which includes the necessary dashboards and the status email template:
[Insert Link Here: CIDP - Sanity check process - OPS CARDIF - Confluence]

To get this fully operational across our time zones, there are two main areas we need to align on:

1. Monitoring Scope & Dashboard Alignment
Danilo noted that the complete CIDP perimeter includes the Dynatrace LATAM dashboard (managed by CIB), on-prem components (IDP/DBB), and components in IBM FS Cloud for LATAM. To properly monitor the application, we need visibility across this entire scope.

Currently, we have an access gap:

Our team in Europe does not have access to the CIB Dynatrace where the LATAM CIDP monitoring resides.

I am unsure if the LATAM team has access to our European dashboard: [CARDIF][AP62809][CIDP & EIS]-email compatible - dMZR-Prod - Dynatrace.

Proposed Solution: If both regional dashboards cover the exact same scope, each team can use the dashboard for their respective zone. If they do not, we will need to either facilitate cross-access to the Dynatrace environments (between LATAM and Europe) or create a single, unified dashboard that aggregates all the necessary monitoring data.

2. Pending Action Items
To finalize the setup, we need your help with the following logistics:

Senders: Identify the specific individuals from the LATAM team who will send the daily status emails.

Access Configuration: Confirm the process for our APS to get access to the LATAM Dynatrace.

Distribution List: Finalize the emailing list of the people and teams who should receive the daily updates.

(Note: Once we have this successfully running for CIDP, we will also be looking to implement the same setup for the CTDF project).

Wesley and Astrid, as Danilo is starting his vacation tomorrow, could you please review the dashboard options and let me know how we should proceed with the action items? I am happy to set up a quick meeting to discuss this further if needed.

Danilo, wishing you a great vacation!

Best regards,

Ahmed Amine CHAKROUN
SRE, Benendo Team

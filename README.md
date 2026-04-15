Subject: CIDP "Follow the Sun" Monitoring - Status and Next Steps

To: Wesley Val, Astrid Melendez, Danilo FERNANDEZ
CC: José Cáceres

Hi Wesley, Astrid, and Danilo,

Following up on my chat with Danilo, I am synthesizing our discussion here to ensure proper traceability for the "Follow the Sun" monitoring process for the CIDP application, especially as Danilo goes on vacation.

Current Progress & Logistics
To facilitate the cross-regional checks, I have documented the sanity check process, email templates, and current dashboards here:

Confluence Page: [Insert Link to your CIDP - Sanity check process page]

To operationalize this, our pending action items are:

Identify the specific team members in LATAM who will perform the checks and send the emails during their shift.

Finalize the mailing list of stakeholders who will receive these daily status updates.

Monitoring Scope & Dashboard Access Alignment
Danilo highlighted that the CIDP perimeter includes the Dynatrace LATAM dashboard (managed by CIB), on-prem components (IDP/DBB), and components deployed in IBM FS Cloud for LATAM.

Here is our current status regarding dashboard access:

European Dashboard: Danilo confirmed the LATAM team successfully has access to our dashboard: [CARDIF][AP62809][CIDP & EIS]-email compatible - dMZR-Prod - Dynatrace.

LATAM Dashboard: I currently do not have access to the LATAM on-prem dashboard for DBB (dynatrace-prd.americas.echonet/...). I am currently looking into the process to request this access.

Next Steps
In the meantime, Danilo provided the DBB_Monitoring_V1.pdf detailing the LATAM monitored components. I will review this document and compare it with what we currently have on the DMZR Dynatrace.

If the dashboards cover different scopes, we will eventually need to either ensure reciprocal access for all involved teams or create a single, unified dashboard. Wesley/Astrid, we can align on this once I have completed the comparison.

Danilo, wishing you a great vacation!

Best regards,

Ahmed Amine CHAKROUN
SRE, Benendo Team

As requested, we reviewed the recent spike in ServiceNow incidents.

Summary

49 incidents are currently assigned to our team; 29 are Control-M related.

A significant portion of the remainder are not incidents. They are routine requests or non-production (dev/qualification) items that should be handled in JIRA or as Service Requests, not as Incidents.

Many tickets are underspecified (missing server/job name, timestamps, error snippets) and are followed by ad-hoc meeting invites, which adds overhead without improving resolution time.

Examples (from the queue)

INC29535869 — “[DH/DOS] Server Qualif is down.” Request to restart a qualification server (Env: Qualification; Service: AP7630 – DATAHUB DOS – Qualification; Impact 3; Urgency 5).

INC29454901 — “[DH/DOS] Audit Production server.” Request to run/skip an audit with a Confluence link and a list of servers.

INC28980006 — “File retrieval.” “Besoin de récupérer le fichier de prod … DOMINO_2025-10-28.”

INC2778907 — “EICC anonymizer / affiliation model.” Ask to send/update a model in EICC.

These are service requests/operational tasks, not production incidents.

Observed pattern

Teams are opening incidents for dev/qualification issues to gain faster attention and for long jobs/audit activities (Control-M or otherwise).

Impact/Urgency are often set low (e.g., Impact 3, Urgency 5) but the ticket type is still “Incident.”

Missing triage data leads to repeated back-and-forth and meetings.

Recommendations

Routing rules:

Dev/Qualification issues → JIRA (qualification/QA issue type).

Operational asks (audit runs, long-running jobs, file retrievals, anonymizer/model updates) → Service Request/JIRA, not Incident.

Gatekeeping: Have Service Desk reclassify misrouted items on intake; reject incidents without minimum triage data.

Minimum data for true incidents: server/VM, job name (for batch/Control-M), exact timestamp, user impact, and first error/log excerpt; expected vs. actual behavior; “what changed.”

Tooling guardrails (short list):

ServiceNow UI policy to block “Incident” when Environment = Dev/Qualification.

Simple templates for common requests (audit, file retrieval, long job follow-up).

Control-M status

We’ve started analysis. The flow involves a ~700-line script supplied by a partner. We’re checking Control-M filters and job criteria that appear to be auto-creating incidents, and validating which jobs should/shouldn’t raise tickets.

We will come back with options (e.g., adjust thresholds, disable auto-ticketing for long-running jobs, or route to a request queue) once we finish the review.

Decisions needed

Approve the routing policy above (Incident reserved for production impact only).

Allow us to reclassify/close misrouted items in the current queue and move them to the correct tracker.

Green-light the ServiceNow/JIRA guardrails and the intake gatekeeping step.

Happy to provide a short deck with counts and examples if helpful.

Best regards,

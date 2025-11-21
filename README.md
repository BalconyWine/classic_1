*** CRITICAL VULNERABILITY ALERT: CVE-2023-37920 (certifi) ***

SEVERITY: Critical (CVSS v3.1 Score: 9.8)
DUE DATE FOR REMEDIATION: 14/08/2025

This is an urgent patch required for the certifi Python package on affected host(s).

VULNERABILITY OVERVIEW

CVE ID: CVE-2023-37920

Component: certifi (Python package)

Vulnerable Version: 2022.12.7 (and all versions prior to 2023.07.22)

Required Version: 2023.07.22 or later

Impact Summary: The vulnerable versions contain untrusted "e-Tugra" root certificates, potentially enabling MitM (Man-in-the-Middle) attacks by validating untrusted SSL certificates.

Vector: Network (AV:N), Low Complexity (AC:L), No Privileges Required (PR:N)

AFFECTED SYSTEMS

Hostname: S01VL9923029

Operating System: Red Hat Enterprise Linux 7.9

Environment: Production

Owner: CAMPAN Patrice (Tribe Data & AI)

Scan Date: 24/09/2025

AFFECTED PATH:
The vulnerable package is specifically within the Oracle AHF (Autonomous Health Framework) Python virtual environment:

/opt/oracle.ahf/common/venv/lib/python3.10/site-packages/certifi-2022.12.7.dist-info/METADATA

REMEDIATION ACTIONS (EXECUTE THESE COMMANDS)

The fix requires an immediate upgrade of the certifi package within the specific Python Virtual Environment (venv) used by the Oracle AHF service.

STEP 1: Log in to the Host:

ssh user@S01VL9923029


STEP 2: Locate and Activate the Venv:

cd /opt/oracle.ahf/common/venv/
source bin/activate


STEP 3: Perform the Upgrade:
Use pip to upgrade the package to a safe version.

pip install --upgrade certifi


STEP 4: Verify the Installation:
Confirm that the new version is 2023.07.22 or higher.

pip show certifi


(Check the output for Version: 2023.07.22 or greater)

STEP 5: Deactivate the Venv:

deactivate


DOCUMENTATION

Please update the corresponding Jira ticket ([TICKET_ID]) with evidence of successful verification immediately after applying the patch.

Meeting Recap: Port 8443 & Protocol Issue
The Issue

Tomcat is starting on port 8443, but the app is expecting HTTP instead of HTTPS.

External requests fail because the application cannot process the secure payload, though a local curl directly to the pod works.

What Changed

The Dockerfile and application.yml were updated to use port 8443 shortly before the meeting.

There is a possibility the Atom Pipeline deploy is overriding the YAML config.

Action Items

Andres: Replicate the deployment locally to test HTTPS/certificate configurations.

Andres: Review the startup logs and compare the current setup against the working "My Optima" CI configuration (shared via Teams).

Team: Revert the configurations back to port 8080 temporarily if needed while Andres investigates.

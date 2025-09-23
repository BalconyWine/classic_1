Dear all,

Following our recent calls, a short status and the specific information we now require.

Context (as agreed)

Ecosystem: proceed on sandbox …1239 (not the Sugar ecosystem).

Kafka: reuse Kafka Event Streams in ITG Cloud; topic requests via the CCC Swagger portal.

Integration: default to Kafka Connect; REST Proxy only if explicitly needed.

Auth: SESAM is out of scope for the POC.

Network: LATAM ↔ DMZR connectivity is established for the POC.

Blocking prerequisite

Cost center 6081 – LAM IT – RUN has been provided (thank you, Reginaldo and Andrés). It must be filled in ServiceNow for our requests to proceed. I have asked Reginaldo and Brito Simone to complete this step, as the team cannot continue without it being set in ServiceNow.

Information requested
1) Events to be produced and consumed (POC)

Please confirm the following so we can size/create the right topics and configure Kafka Connect:

Event source(s): Which systems emit the events (e.g., application components, DB change events, logs)?

Event type(s): What categories of events are in scope for the POC?

Format: Expected payload format (JSON, Avro, other).

Sample payload: One or two concrete examples of the event(s) as they will be produced.

Keying/partitioning: Field(s) to use as the message key / partition key (if any).

Volume & rate (POC): Approx. average and peak messages per second, and typical payload size.

Latency expectation (POC): Acceptable end-to-end delay (e.g., ≤5 minutes / ≤10 minutes).

Retention (POC): Desired topic retention window.

2) Target data model in ExaCC (Oracle) — if ExaCC is the POC sink

If the POC will store events in ExaCC, please provide the intended structure:

Exact table design: table name(s), columns with datatypes, primary keys, indexes, and any constraints.

Payload mapping: how the event fields map into the table(s) (flattening rules, nested fields handling).

Example row / DDL: a short CREATE TABLE and one example row (or CSV snippet) reflecting the expected data.

Write pattern: expected insert rate and any upsert/merge logic.

If ExaCC is not the POC sink, please confirm the POC datastore (e.g., MongoDB) and share a sample document that corresponds to the event sample above.

Once the cost center is recorded in ServiceNow and we have the items above, we will proceed with:

Raising the Kafka topic request(s) via CCC,

Configuring the Kafka Connect flow(s), and

Coordinating with Audrey’s team on the datastore provisioning.

Thank you in advance for the confirmations.

Best regards,

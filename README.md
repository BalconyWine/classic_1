Gemini a dit
Based on the "Collibra - Gap Analysis" document, the Italian team wants to build a highly granular, operational Managed File Transfer (MFT) and IT routing catalog directly inside Collibra. Instead of focusing on high-level data governance, they want to map the exact technical topology of their systems.

Here is a summary of exactly what they are asking to model and manage:

1. IT Infrastructure & Systems
Servers: Physical and virtual nodes, tracking their hostname, ip_address, and environment (PROD, QUAL, INTEG).

IT Systems: Logical containers like MFT Platforms or Partner Systems.

2. Network Endpoints & Storage
Communication Endpoints: Specific contact points including hostnames, IP addresses, and exact port_numbers.

Data Resources: Physical storage locations like File System Folders, MFT Mailboxes, and S3 Buckets, including the exact resource_path.

3. Protocols & PeSIT Details
Protocols: Technical transport methods like SFTP, HTTPS, and PeSIT.

PeSIT Segments: Custom assets dedicated to tracking highly specific PeSIT parameters like record_length, local_data_code, and file_format.

4. Granular Flow Definition (Routing & Hops)
Logical Flows: End-to-end data flows including the scheduler job name (job_tws), source paths, and destination paths.

Technical Segments (Hops): The individual topological steps of a transfer, mapping exactly where a file moves, including materialized_path, path depth, and exact file_name_patterns.

5. Deep Interconnectivity (Relations)
They want to create a massive web of technical relationships, defining exactly how these components interact. For example: endpoints are "deployed on" servers, segments "read from" or "write to" data resources, and segments "originate from" or "terminate at" specific endpoints.

6. Heavy Collibra Customization
To achieve this, they are asking to create a dedicated "File Exchange & MFT" community, multiple technical domains (e.g., "Systems & Infrastructure"), and several Custom Asset Types (like MFT Flow Segment and Communication Endpoint) to force the tool to accept this data model.

The Underlying Issue (The "Gap"):
The document itself highlights why Oussama's hesitation is justified. In their "Mandatory Fields Not Mapped" section, it shows that their source database completely lacks standard data governance fields required by Collibra, such as "IT Asset Responsible", "Business Asset Responsible", "Confidentiality", and "Personal Data Flag". This confirms they are treating Collibra as an operational CMDB (Configuration Management Database) rather than a business-level governance platform.

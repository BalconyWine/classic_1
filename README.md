Hi team,

I went through the docs, and here’s my simple read of what this project is about:

We’re moving Claims reporting into CTDF (Cardif Trusted Data Fabric), which will be our new “home” for data. Right now reports depend on old tools (BO, SAS, DW), and the idea is to replace those step by step.

Source data: comes mainly from Appian (and Gipsy).

Ingestion: SSIS + CFT move the data into CTDF.

Storage in CTDF: data gets organized in layers (Raw → Refined → Optimized).

Consumption: Power BI connects directly to the Claims Data Product for dashboards.

Governance: Collibra catalogs the data, ownership, and lineage.

Contingency path: if the pipeline fails, Appian/Gipsy can export a file, drop it in SharePoint, and Power BI can still render reports (manual but keeps continuity).

Main things flagged for the review:

We still need clear reporting/dashboard requirements.

Ownership of data (especially cross-domain) needs to be sorted.

Performance tests for Power BI are not done yet.

Continuity (RTO/RPO, backup/restore) must be tightened in next phases.

Bottom line: The direction makes sense—CTDF + Power BI + Collibra is the right setup. The review will check whether we have the contract, performance plan, and continuity plan nailed down enough to move forward.

Thanks,

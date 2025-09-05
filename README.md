Subject: PIMS PoC — Parallel plan (Networking + Infra) on cluster 246

Hello all,

Quick alignment after our exchanges with TO and Networking:

We will run the PoC on cluster 246 with a minimal footprint; moving to 10xx remains an option later if/when capacity/governance requires it.

The architecture is DMZR (IBM Event Streams + REST Proxy) → LATAM (Kafka Connect + Camel HTTP Sink) → LATAM Kafka (PIMS topics).

Both tracks proceed in parallel:

Networking: BP2i + ITG/WIN + LATAM network teams (path DMZR ↔ WIN/ITG ↔ LATAM).

Infra/Code: CARD12 + TO + LATAM DevOps (containers, CI/CD, Connect/Camel, topics).

At the end we will run joint end-to-end tests (network + infra together).

Key contacts (for context): BP2i/DMZR: Mohamed Bouzenada • ITG/WIN: Morgan Sauvaget / François Dufour (mgr. Stéphane Bonney); routing: Fayçal Labrani • TO: Houssein Jaber, Yassine El Fachtali • PIMS/LATAM: local DevOps • FinOps: Erik L., Erik G.

High-level timeline (indicative; subject to change windows & availability)
Window	Networking (BP2i / ITG/WIN / LATAM)	Infra / Code (CARD12 / TO / LATAM)	Milestone
Now → Mid-Sept	Confirm owners and path DMZR ↔ WIN/ITG ↔ LATAM; draft firewall/routing asks; collect LATAM site info (CO/BR/US) and egress IP/CIDR.	Confirm namespace & quotas on 246; prep repos & CI/CD; baseline manifests; confirm REST Proxy endpoint/auth; agree minimal sizing.	Gate 0: prerequisites lined up.
Week of 15-Sept	Progress FW/routing requests, path validation, schedule change windows (WIN + BP2i).	OOO on infra/code (light doc only if needed).	Requests submitted; tentative network test slots penciled.
Late-Sept → Early-Oct	Apply openings; basic end-to-end path checks (traceroute/DNS).	Deploy Kafka Connect + Camel HTTP Sink on 246; smoke test DMZR → LATAM on a test topic.	Gate 1: first E2E events observed.
October	Fine-tune routing if needed; confirm steady path.	Stabilize PoC; basic monitoring; validate LATAM consumers on PIMS topics.	PoC usable for demos.
November	Maintain path; prepare incremental rules only if required.	Right-size resources with FinOps; summarize usage/cost; document scale options.	Gate 2: sizing & runbook agreed.
Dec → Jan	Reserve windows for any next-stage network needs.	Optional hardening (retries/alerts); small volume ramp if needed.	Ready for next-stage decision.
Q1 2026	If chosen: prep/execute network work for 10xx.	If chosen: move or stay on 246 with adjusted quotas.	Decision: 246 vs 10xx.

Notes:

We will keep resource requests intentionally low on 246 during the PoC to avoid quota pressure; scale only on demonstrated need.

Both paths are required: networking proceeds while infra/code proceeds; success criteria are based on joint E2E validation.

Decommissioning considerations (late-2025 / early-2026) are tracked; we’ll align cut-over options in Q1-2026 if needed.

Immediate next steps (this week):

PIMS/LATAM: confirm site (Colombia/Brazil/USA) and egress IP/CIDR; share any blackout/change windows.

Networking: BP2i/ITG to validate the draft openings and propose first test window.

CARD12/TO: confirm namespace & initial quotas on 246; share minimal sizing for the PoC pods.

If this parallel plan works for you, we’ll attach named owners to each line and lock the first test window.

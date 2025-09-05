Subject: PIMS PoC — Cluster 246 confirmed & proposed high-level timeline

Hello team,

Following our latest exchanges and the TO session, we have alignment to start the PoC on the existing EKS cluster “246” with a minimal footprint. This keeps costs under control and lets us start sooner; moving to the 10xx cluster remains an option later if/when capacity or segregation requires it.

We understand Gianluca is asking for a clear outlook. Below is a realistic, high-level plan that runs Networking and Code/Infra in parallel. Dates are indicative and will be adjusted with change windows and team availability.

PIMS PoC – High-Level Timeline (subject to change)
Window (target)	Networking (BP2I / ITG / LATAM)	Code & Infra (CARD12 / TO / LATAM)	Milestone
Now → Mid-Sept	Confirm owners and path DMZR ↔ WIN/ITG ↔ LATAM; draft firewall/routing asks.	Prep repos/manifests; confirm namespace & quotas on 246; agree on minimal sizing.	Gate 0: prerequisites lined up.
Week of 15-Sept	Progress FW/routing requests and path validation.	No build (OOO for infra/code). Light documentation only if needed.	Requests submitted; tentative change window penciled.
Late-Sept → Early-Oct	Apply openings; basic end-to-end path check.	Deploy minimal PoC stack on 246; smoke test DMZR → LATAM event flow.	Gate 1: first E2E events observed.
October	Fine-tune routing as needed; confirm steady path.	Stabilize PoC; basic monitoring; validate consumers with LATAM.	PoC usable for demos.
November	Maintain path; prepare incremental rules only if required.	Right-size resources; summarize usage/cost; document scale options.	Gate 2: PoC sizing & runbook agreed.
Dec → Jan	Reserve windows for any network refinements for next stage.	Optional hardening (retries/alerts); small volume ramp if needed.	Ready for next-stage decision.
Q1 2026	If chosen: prep/execute network work for 10xx.	If chosen: move or keep on 246 with adjusted quotas.	Decision: remain on 246 vs move to 10xx.

Notes

We’ll keep resource requests on 246 intentionally low during the PoC to avoid quota pressure; we’ll scale only on demonstrated need.

Networking activities continue while infra/code is paused the week of 15 September.

Decommissioning considerations (late-2025 / early-2026) are tracked; we’ll align cut-over options in Q1-2026 if required.

Weekly short sync proposed; a brief “Gate” note at each milestone.

Next steps (this week)

CARD12/TO: confirm namespace and initial quotas on 246 and share the minimal sizing.

Networking: validate owners on both sides (BP2I + ITG + LATAM) and confirm the draft list of openings.

LATAM: share any constraints or blackout windows that could affect the plan.

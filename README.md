Program context. “Digital Backbone” is the flagship LATAM transformation. It was reviewed at a LATAM seminar; high visibility; Pauline is pressing for results.

Roadmap decision. The “accelerated” 3-year scenario was challenged and dropped. Expect +12–18 months to the overall plan. A compromise scenario will be communicated next week and then presented at a SteerCo / CGP validation soon after.

Near-term scope unchanged. Focus countries remain Chile and Mexico. Brazil is delayed/unclear. No brand-new use cases were added.

Where LATAM needs central help / dates.

LINK – the inter-cloud/file/data transfer program (owned centrally by Damien Thibault) → LATAM wants a date/visibility to plan around.

Secret Data Management – encryption/tokenization approach and key management; they want a date/trajectory. Stopgap considered: Voltage (not a group standard but “good enough” interim).

CTDF – data warehouse/platform migration support and country roadmaps; there’s a disconnect between Paris and LATAM on what’s in scope and who starts.

24×7 “follow-the-sun” support – define L1/L2/L3 split across Colombia, Portugal, India, Paris, with access/monitoring and language constraints documented. Don’t outsource to Manila; build this internally.

Cloud placement & classification (hot potato).

DMZR for Partners / CIDP is claimed to be Cloud Type 2 (“Special Green”, hosted in our DC), therefore hosting secret data is allowed in theory.

BUT even in Type 2, for secret data: application-level encryption/tokenization is still required, with master keys under our control (HSM / CipherTrust). Database-at-rest encryption alone is not sufficient.

“Digital by Cardif” MZR sits elsewhere (different classification).

Security tech options.

Voltage (tokenization/format-preserving encryption) can work, and keys could live in the group HSM.

Thales CipherTrust can do tokenization either via code libraries or REST proxy (less intrusive) — but needs ProcSec acceptance. “HPCS hybride” mentioned if VPC constraints exist.

Governance & cadence.

One program SteerCo only (no parallel governance). Timothée acts as SPOC to consolidate central topics and report to Martine (who remains accountable for risks).

A cross-org “All-parties” session was tentatively 29 Oct; might move to 30–31 Oct. Also establish a 30-min weekly central sync (ProdSec, Architecture, Telecom, CTDF, BP2I, etc.).

Deadlines & risks.

ITSVC (architecture/security committee) needs full validation in ~1 month. Real risk that LINK patterns and Secret Data solution won’t be completely ready; may proceed with reservations noted.

GAD (architecture dossier) must be filled now; bring Chile architects in to co-write.

Key person risk: LATAM architect Marcos Turiano is out ~1 month for health reasons.

Budget. 2025 under-consumed; 2026 central budget exists for Digital Backbone (exact amount to confirm). If needed, extra central funding could be added to unblock critical streams.

Go-live pressure. MVP already live (friend-and-family) with Coppel in MX; full rollout of ~1500 branches expected around early Q1 (one quote also said Feb 2026—needs confirmation). Support model must be defined before scale-up.

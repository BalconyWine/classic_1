Ticket plan
Ticket 1 — Activate RUM and migrate configurations

Purpose: migrate the RUM application configuration to prod.

Likely fields

Sujet: AP23985 – Activation RUM et migration des configurations RUM vers la production

Criticité: Annoying

Offre/Composant: Activation RUM

DYNATRACE TENANT: very likely INSLOANS PROD, but please verify because one screenshot also shows DMZR PROD in the dropdown

AUID: use the exact AUID from Sonia’s procedure screenshot for AP23985

Description: use the text below

Ready draft

Subject

AP23985 – Activation RUM et migration des configurations RUM vers la production

Description

Contexte :
Demande de migration vers la production de la configuration RUM de l’application AP23985 dans le cadre du projet CF Monitoring Dynatrace.

Merci de migrer / reproduire en production les éléments configurés en environnement de staging pour l’application AP23985.

Eléments de référence :
- Lien vers le RUM en staging : [ajouter le lien exact de la page Sonia]
- Lien vers la documentation des configurations RUM : [ajouter le lien Confluence exact]
- Contact en cas de besoin de support / clarification : Sonia AIT BENAMER

Checklist des settings à migrer :
- Activation session replay (100%)
- Data privacy settings : mask all pour recording et replay
- Ajustement des key performance metrics (visually complete) pour load actions et xhr actions
- User tag mData.id_demande
- Placeholders et règles de nommage :
  - Load actions
  - Xhr actions
  - Custom actions
- Conversion goals
- Session and useraction properties
- Activation capture xhr
- Metrics
- Anomaly detection : activer traffic spikes and drops et reporter les seuils existants
- Liste des key user actions
- Migration du SLO existant de type UX Score (à renommer en prod selon convention cible)

Remarque :
Les réglages doivent être reproduits à l’identique sur la prod, avec adaptation uniquement si nécessaire au contexte de production.
Merci de confirmer s’il manque des droits spécifiques ou des prérequis côté tenant prod.
Ticket 2 — Migrate ADE and SolPrev dashboards to production

Purpose: recreate/copy the business dashboards in prod.

Likely fields

Sujet: AP23985 – Migration des dashboards ADE et SolPrev vers la production

Criticité: Annoying

Offre/Composant: for this one I am less certain from the photos. It may be a generic support/dashboard category. If Sonia’s page shows a specific value, use that exact one.

DYNATRACE TENANT: likely INSLOANS PROD

AUID: same application scope as AP23985

Description: below

Ready draft

Subject

AP23985 – Migration des dashboards ADE et SolPrev vers la production

Description

Contexte :
Demande de migration vers la production des dashboards métiers AP23985 réalisés en staging dans le cadre du projet CF Monitoring Dynatrace.

Merci de migrer / recréer en production les dashboards suivants :
- ADE
- SolPrev

Eléments de référence :
- Dashboard SolPrev en staging : [ajouter le lien exact]
- Dashboard ADE en staging : [ajouter le lien exact]
- Documentation de réalisation du dashboard : [ajouter le lien Confluence exact]
- Contact en cas de besoin de support / clarification : Sonia AIT BENAMER

Attendu :
- Recréation des dashboards en production
- Reprise des visualisations existantes
- Remplacement / mise à jour des IDs nécessaires côté prod
- Vérification de cohérence des tuiles, filtres, audiences et liens éventuels
- Vérification de l’accès aux dashboards après création

Merci de confirmer une fois les dashboards disponibles sur le tenant de production.
Ticket 3 — Migrate notifications / alerting to production

Purpose: move the alerting defined in staging to prod.

Likely fields

Sujet: AP23985 – Migration des notifications / alerting vers la production

Criticité: Annoying

Offre/Composant: Alerting

DYNATRACE TENANT: likely INSLOANS PROD

AUID: same as AP23985 app

Description: below

Ready draft

Subject

AP23985 – Migration des notifications / alerting vers la production

Description

Contexte :
Demande de migration vers la production des notifications / alertes Dynatrace configurées en staging pour AP23985 dans le cadre du projet CF Monitoring Dynatrace.

Merci de migrer / recréer en production les notifications et paramétrages d’alerting existants en staging.

Eléments de référence :
- Lien vers les metric events à migrer : [ajouter le lien exact]
- Lien vers l’alerting profile à migrer : [ajouter le lien exact]
- Lien vers la configuration RUM / anomaly detection associée : [ajouter le lien exact]
- Liste des contacts à notifier : [ajouter selon doc Sonia]
- Contact en cas de besoin de support / clarification : Sonia AIT BENAMER

Périmètre fonctionnel des alertes existantes :
- Détection de multiples échecs d’upload FranceConnect sur fenêtre glissante
- Détection de multiples échecs d’envoi de demande sur fenêtre glissante
- Détection de baisse anormale de trafic
- Dégradation anormale des temps de chargement

Remarque importante :
Les seuils / critères d’alerte devront être revus et adaptés selon le comportement observé en production.

Merci de confirmer une fois les notifications actives en production.
Ticket 4 — Migrate services dashboard to production

Purpose: move the services dashboard into prod.

Likely fields

Sujet: AP23985 – Migration du dashboard services vers la production

Criticité: Annoying

Offre/Composant: likely generic support/dashboard category, but I cannot confirm the exact dropdown value from the photos

DYNATRACE TENANT: likely INSLOANS PROD

AUID: same as AP23985

Description: below

Ready draft

Subject

AP23985 – Migration du dashboard services vers la production

Description

Contexte :
Demande de migration vers la production du dashboard services AP23985 réalisé en environnement de développement dans le cadre du projet CF Monitoring Dynatrace.

Merci de migrer / recréer en production le dashboard services associé à AP23985.

Eléments de référence :
- Lien vers le dashboard services en dev : [ajouter le lien exact]
- Lien vers la documentation de réalisation du dashboard services : [ajouter le lien Confluence exact]
- Contact en cas de besoin de support / clarification : Sonia AIT BENAMER

Points d’attention :
- Vérifier / revalider les endpoints monitorés en production
- Vérifier l’architecture technique si différente de la prod
- Ajuster les SLOs selon le comportement réel observé en production
- Vérifier la cohérence des key requests et des services critiques suivis

Merci de confirmer une fois le dashboard disponible et vérifié sur le tenant de production.
Possible Ticket 5 — GMON request for custom metrics

One screenshot explicitly says the custom metrics will only be effective if a request is made to GMON to mark them as custom metrics.

So I strongly recommend a separate follow-up ticket if this was not already included elsewhere.

Draft

Subject

AP23985 – Demande GMON pour activation / prise en compte des custom metrics

Description

Contexte :
Dans le cadre du projet CF Monitoring Dynatrace AP23985, des custom metrics ont été définies côté dashboard / monitoring.

Merci de prendre en compte / activer le besoin GMON nécessaire afin que ces custom metrics soient effectives en environnement cible.

Eléments de référence :
- Lien vers la documentation associée : [ajouter le lien exact]
- Lien vers l’analyse multidimensionnelle / custom metrics : [ajouter le lien exact]
- Contact de référence : Sonia AIT BENAMER

Merci de confirmer le traitement attendu côté GMON ainsi que les éventuels prérequis complémentaires.
What is still slightly uncertain

From the photos alone, I am not 100% sure about these fields:

the exact tenant to select between DMZR PROD and INSLOANS PROD

the exact AUID wording

the exact Offre/Composant value for dashboard tickets 2 and 4

But I am confident about:

the number and purpose of the tickets

the subjects

the description content

the fact that ticket creation is the main action requested from your side

My recommendation before submitting

Use Sonia’s Confluence migration pages and fill these three things exactly from there:

the final tenant

the final AUID

the exact links to paste in each description

Everything else can already be prepared now.

If you want, I can next turn this into a final ready-to-send checklist, ticket by ticket, with:

exact field names

what to select in each dropdown

and a clean copy-paste version in French for all 4 tickets.

It's asking me for a app type and url, do i have those ?
Thought for 26s

Yes — now we can infer them much better from your screenshots.

What you already have confirmed

For this ticket, the form is now clearly:

Sujet: AP23985 - Activation RUM et migration des configuration RUM vers la production

Criticité: Annoying

Offre/Composant: Activation RUM

DYNATRACE TENANT: INSLOANS PROD

AUID: CA7415 – SOCLE PORTAIL FRANCE CLIENT (C)

App type

The dropdown shows:

Intranet

Extranet

Internet

From the screenshots and labels like:

SOCLE PORTAIL FRANCE CLIENT

public-facing user journeys

FranceConnect

user upload / demande / indemnisation paths

this looks like an external customer-facing portal, not an internal employee tool.

So the most likely value is:

Type d’application: Internet

I would not choose Intranet.
I would also not choose Extranet unless your company specifically classifies this client portal as extranet internally. Based on the wording in the screenshots, Internet is the safest choice.

URL

Yes, you do have it in the screenshots indirectly.

The Confluence page for step 1 says the description should include the link to the RUM in staging for:

[CARDIF][AP23985] SOCLE PORTAIL FRANCE CLIENT C - indemnisation-c05.staging.cardif.fr - Staging - Dynatrace

That strongly suggests the application URL to enter is:

https://indemnisation-c05.staging.cardif.fr

This is the best candidate from what is visible in your screenshots.

So for this specific ticket, fill:

Type d’application: Internet

URL: https://indemnisation-c05.staging.cardif.fr

Important nuance

Because this ticket is for activation RUM and migration to production, sometimes teams put:

the current staging URL as source reference, or

the target prod URL if already known and if the form expects the production application

From your screenshots, the process documentation references the staging RUM application, so I think the form likely expects the application currently monitored and used as reference. That means the staging URL above is the right one unless Sonia told you to use the prod URL.

What I recommend you put now

Use:

Type d’application: Internet
URL: https://indemnisation-c05.staging.cardif.fr

Then in the Description, explicitly say that this is a request to reproduce the staging RUM configuration in production.

Paste this:

Contexte :
Demande d’activation RUM et de migration des configurations RUM vers la production pour l’application AP23985.

Application de référence en staging :
https://indemnisation-c05.staging.cardif.fr

Merci de reproduire en production la configuration RUM existante en staging pour AP23985, conformément à la documentation projet.

Références :
- RUM staging : [CARDIF][AP23985] SOCLE PORTAIL FRANCE CLIENT C - indemnisation-c05.staging.cardif.fr - Staging - Dynatrace
- Documentation des configurations RUM : Documentation - Réalisations - dynatrace_cardif - Confluence
- Contact support / clarification : Sonia AIT BENAMER

Checklist des settings à migrer :
- Activation session replay (100%)
- Data privacy settings : mask all pour recording et replay
- Ajustement des key performance metrics (visually complete) pour load actions et xhr actions
- User tag mData.id_demande
- Placeholders et règles de nommage
- Conversion goals
- Session and useraction properties
- Activation capture xhr
- Metrics
- Anomaly detection
- Key user actions
- SLO UX score à migrer / adapter en production

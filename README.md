# Compte rendu de réunion / Meeting Minutes — PIMS Technical Assessment & DMZR/MCR Migration

**Date :** 27 avril 2026  
**Durée :** ~1h14  
**Périmètre :** Migration de l’écosystème PIMS vers DMZR / MCR as Code — périmètre Mexique  
**Source :** Audio complet de la réunion + transcription avec attribution des intervenants, retraitée au mieux  

> **Note :** Certains noms et acronymes proviennent d’une transcription automatique et doivent être confirmés. En particulier : **Xiose/José**, **Ada/Adam**, **DMZR/DMCR/MCR**, **MGR/HACC**, ainsi que le nom exact du portail d’accès.

---

# Partie 1 — Français

## 1. Synthèse exécutive

La réunion a porté sur les points ouverts du **Technical Assessment PIMS** dans le cadre de la migration vers **DMZR / MCR as Code**, avec un focus sur le **périmètre Mexique**.

La clarification principale est que l’écosystème PIMS ne doit **pas être traité avec un seul AP code**. Les principales applications de l’écosystème, notamment **PIMS**, **Ada/Adam**, **PNT** et **CRS**, doivent être traitées via des **AP codes séparés**, probablement associés à des namespaces distincts.

Cette décision impacte directement le provisioning : le fichier Excel actuel doit être découpé en **un fichier Excel de provisioning par AP code/application**. Chaque fichier devra contenir les ressources concernées ainsi qu’une **flow matrix** adaptée, en particulier pour les communications inter-applications et inter-namespaces.

L’objectif reste de clôturer ou d’avoir un Technical Assessment suffisamment complet d’ici **jeudi**, sous réserve de finaliser le découpage AP code, les fichiers Excel, les diagrammes d’architecture et les points ouverts dans OneNote.

---

## 2. Participants mentionnés

| Nom / rôle | Commentaire |
|---|---|
| Andres | Porte les sujets PIMS, provisioning, Excel, coordination et points ouverts. |
| Xiose / José (?) | Intervenant technique principal, nom à confirmer. Apporte les clarifications sur architecture, sécurité, cloud review, DB, CI/CD et tests. |
| Johan | Présent dans la réunion, intervient sur certains points de confirmation. |
| Amine | Présent, probablement intervention courte en fin de réunion. |
| Julius César | Présent, intervention peu distinguable dans la transcription. |

---

## 3. Décisions principales

| # | Décision |
|---:|---|
| 1 | L’écosystème PIMS doit être découpé en plusieurs AP codes au lieu d’utiliser un AP code global unique. |
| 2 | Un fichier Excel de provisioning doit être créé par AP code/application. |
| 3 | La **flow matrix** est un livrable critique et doit être adaptée pour chaque AP code, y compris les flux inter-namespaces. |
| 4 | L’objectif de finalisation du Technical Assessment pour jeudi est maintenu, sous réserve de la mise à jour des AP codes et de la documentation. |
| 5 | Le Technical Assessment ne nécessite pas encore la campagne de tests détaillée complète, mais doit identifier les grandes catégories de tests, les responsables et les tests de sécurité obligatoires. |
| 6 | Le test d’intrusion est obligatoire car l’application manipule des données sensibles/secrètes. |
| 7 | Le modèle CI/CD cible doit être plus modulaire que le modèle on-premise actuel, idéalement avec une pipeline par composant applicatif. |

---

## 4. Points techniques principaux

### 4.1 AP codes, namespaces et flux

L’équipe Architecture LATAM recommande de séparer l’écosystème PIMS par application/AP code. Cela permet une meilleure ségrégation, clarifie le provisioning et facilite la compréhension des ressources réellement nécessaires par application.

Cette décision implique toutefois de documenter plus précisément les flux entre namespaces.

Exemple : si le portail web PIMS est déployé dans un namespace et que l’application Ada/Adam est dans un autre namespace, les flux nécessaires entre ces deux namespaces doivent être explicitement décrits dans la flow matrix.

### 4.2 Fichiers Excel de provisioning

Le fichier Excel actuel doit être découpé en plusieurs fichiers, avec **un fichier par AP code**.

Les lignes correspondant aux applications désormais traitées séparément doivent être retirées du fichier initial et déplacées dans le fichier de provisioning correspondant.

La partie la plus critique à répliquer et adapter est la **flow matrix**. Les informations de ressources doivent également être revues application par application.

### 4.3 Cloud Review et ITSBC

La Cloud Review reste ouverte.

Avec plusieurs AP codes, il pourrait être nécessaire de créer plusieurs cartes ou sessions Cloud Review. Il a été proposé de vérifier s’il est possible de faire une **Cloud Review / ITSBC globale** couvrant l’ensemble de l’écosystème PIMS.

La Cloud Review doit confirmer que les applications sont éligibles à la plateforme cible DMZR/MCR. Si la réponse est négative, cela deviendrait un point bloquant.

### 4.4 Accès DMZR / IBM Cloud

L’accès à DMZR / IBM Cloud doit être demandé via un portail mentionné comme **My Technical Access** ou **My Technical Access Express**. Le nom officiel exact reste à confirmer.

Le modèle d’accès semble nécessiter l’association d’un profil business avec un profil technique.

Certaines permissions, comme les droits sur des topics Kafka DMZR, peuvent nécessiter une demande via le manager dans le portail d’accès.

### 4.5 Sécurité, chiffrement et certificats

CRS ne chiffre pas directement l’information. Le chiffrement est réalisé côté application pays, par exemple par l’application Mexique.

L’exigence principale est le **chiffrement au niveau fichier**, probablement via **PGP**.

Même si CFT/STCP fournit un transport sécurisé, cela ne remplace pas nécessairement le chiffrement du fichier lui-même lorsqu’il est stocké ou échangé.

Le **MTLS** est requis pour les flux concernés, notamment entre Confluent/Kafka et les composants MCR as Code.

Les certificats doivent s’appuyer sur le service PKI disponible plutôt que sur des certificats auto-signés.

### 4.6 Java 8, images Docker et runtime

L’application restera sur **Java 8** pour le moment.

Les images Docker Java 8 sont encore disponibles et aucun point bloquant n’a été identifié. Si des bibliothèques spécifiques sont nécessaires, l’équipe DevOps pourra être sollicitée pour les intégrer ou confirmer l’image de base à utiliser.

### 4.7 Ingress, routes et session affinity

Aucune **session affinity** n’est requise actuellement.

Pour les routes / ingress :

- le mode **pass-through** peut convenir pour une application simple avec un seul contexte ;
- le mode **re-encrypt** peut être nécessaire si plusieurs contextes ou services sont exposés derrière une même route.

Le mode de routage doit être documenté dans le provisioning ou l’architecture cible.

### 4.8 MQ, Kafka et Confluent

Le besoin de MTLS est confirmé pour certains flux, notamment ceux impliquant Confluent/Kafka et MCR as Code.

Le mécanisme exact de chiffrement côté MQ dans DMZR reste à confirmer via la documentation DMZR.

### 4.9 Batchs, pod CFT et S3

Le schéma cible discuté est le suivant :

1. un pod CFT reçoit ou transfère les fichiers ;
2. les fichiers sont stockés dans S3 ;
3. les batchs lisent et traitent les fichiers depuis S3.

Deux options techniques sont possibles :

- adapter le code des batchs pour utiliser directement l’API S3 ;
- monter S3/le stockage comme un volume afin de conserver un comportement proche du filesystem actuel.

La migration des batchs nécessite une analyse complémentaire, mais ne bloque pas le Technical Assessment.

### 4.10 Base de données et migration des données

Aucune optimisation Oracle spécifique ou configuration non standard n’est connue à ce stade, ce qui est positif.

Une purge de données est en cours. Le volume cible estimé pour le Mexique est d’environ **1 To**, à confirmer.

De nombreuses requêtes SQL sont complexes. Des tests de temps de réponse et de charge seront nécessaires sur l’architecture cible.

Il reste à clarifier si les DBA LATAM pourront accéder ou gérer directement la base MCR, ou si cette responsabilité restera côté France.

Le transfert complet de la base Mexique au moment du switchover est considéré comme risqué. La stratégie recommandée est :

- transférer la majorité des données avant le switchover ;
- transférer uniquement le delta lors du cutover final ;
- découper les exports en plusieurs paquets compressés ;
- éviter un transfert massif unique.

Un POC mené par l’équipe de David Silva est en cours, avec des fichiers `.parquet` et une réplication vers une instance cible. Les acronymes exacts comme MGR/MCR et HACC doivent être confirmés.

### 4.11 Authentification, scans et monitoring

Le mécanisme d’authentification cible est **ITG Web SSO**.

Les scans actuels à documenter sont :

- Sonar ;
- Fortify ;
- Vulnerability Advisor, actuellement on-premise.

Dans la cible DMZR/MCR, le scan des images Docker/conteneurs devra être intégré à la pipeline.

Dynatrace est prévu pour le monitoring. Si un monitoring avancé de bout en bout ou côté utilisateur final est nécessaire, une équipe spécialisée devra être impliquée.

### 4.12 Exploitation et contraintes réglementaires

Les règles d’exploitation concernant les données sensibles/secrètes doivent être clarifiées pour LATAM.

Les contraintes GDPR européennes ont été citées comme exemple, mais les règles applicables côté LATAM ou pays local doivent être confirmées avec les équipes sécurité/conformité appropriées.

### 4.13 CI/CD

Le modèle on-premise actuel utilise une CI et une CD globales pour l’ensemble des composants. Ce modèle n’est pas idéal pour la cible.

La recommandation cible est :

- au minimum, des pipelines séparées par AP code ;
- idéalement, une pipeline CI/CD par composant applicatif.

Cela permettrait des déploiements plus indépendants, une meilleure maintenance et une architecture plus modulaire.

### 4.14 Stratégie de tests

Le Technical Assessment ne nécessite pas encore la description exhaustive de toute la campagne de tests, mais il doit identifier les types de tests nécessaires et les responsables.

Les tests à prévoir incluent :

- tests d’intégration ;
- tests d’acceptance utilisateur ;
- tests de performance ;
- tests de sécurité ;
- test d’intrusion obligatoire ;
- tests techniques spécifiques avant mise en production.

PIMS dispose déjà d’une équipe de test et de tests existants, automatisés et manuels. Le COE ou test center peut être contacté pour conseil, cadrage ou estimation budgétaire.

---

## 5. Plan d’actions

| # | Action | Responsable | Statut / Échéance |
|---:|---|---|---|
| 1 | Initier ou créer les AP codes séparés pour les applications de l’écosystème PIMS : Ada/Adam, PNT, CRS, etc. | Andres / Architecture LATAM | Ouvert |
| 2 | Découper l’Excel de provisioning actuel en un fichier par AP code. | Andres | Objectif jeudi |
| 3 | Retirer du fichier Excel initial les lignes des applications relevant d’un autre AP code. | Andres | Objectif jeudi |
| 4 | Répliquer et adapter la flow matrix dans chaque fichier de provisioning. | Andres | Critique |
| 5 | Mettre à jour les diagrammes avec le périmètre Mexique, le découpage AP code et les namespaces. | Andres | Ouvert |
| 6 | Mettre à jour les points ouverts OneNote et clôturer les sujets clarifiés. | Andres | Avant prochaine revue |
| 7 | Confirmer si une Cloud Review / ITSBC globale peut couvrir tous les AP codes liés. | Andres / Architecture | Ouvert |
| 8 | Créer la demande d’accès DMZR / IBM Cloud via My Technical Access. | Andres | À initier |
| 9 | Documenter le processus d’accès DMZR et les permissions Kafka/topics. | Andres | Pour TA |
| 10 | Documenter la responsabilité du chiffrement fichier pour les flux CRS/application pays. | Andres | Pour TA |
| 11 | Confirmer le mécanisme de chiffrement MQ dans la documentation DMZR. | Andres | Ouvert |
| 12 | Mettre à jour les informations de provisioning pour l’image/version Docker Java 8. | Andres | Ouvert |
| 13 | Documenter le mode ingress/route : pass-through ou re-encrypt selon les contextes/services. | Andres / Architecture | Ouvert |
| 14 | Analyser l’impact batch/file manager avec pod CFT et S3. | Andres / Équipe technique | Plus tard |
| 15 | Confirmer le volume de base Mexique et l’état de la purge. | Andres / DBA / Équipe pays | Ouvert |
| 16 | Clarifier si les DBA LATAM peuvent accéder/gérer la base MCR. | Andres / DBA teams | Ouvert |
| 17 | Revoir le POC de migration de données Parquet avec l’équipe de David Silva. | Andres | Ouvert |
| 18 | Documenter l’authentification cible ITG Web SSO. | Andres | Pour TA |
| 19 | Documenter les scans actuels et le scan image futur dans la pipeline. | Andres / DevOps | Pour TA |
| 20 | Clarifier les règles opérationnelles et réglementaires LATAM/locales pour les données sensibles/secrètes. | Andres / Security / Compliance | Ouvert |
| 21 | Revoir les attentes IC plan avec ITG et les équipes locales. | Andres / ITG | Ouvert |
| 22 | Définir le modèle CI/CD cible, idéalement par composant applicatif. | Andres / DevOps | Ouvert |
| 23 | Identifier les catégories de tests et confirmer le responsable des tests. | Andres / Équipe test | Pour TA |
| 24 | Planifier le test d’intrusion obligatoire. | Andres / Security | Obligatoire |

---

## 6. Registre des risques

| # | Risque | Impact | Mitigation |
|---:|---|---|---|
| 1 | Le découpage AP code ajoute de la charge documentaire et provisioning. | Risque de glissement de la clôture TA. | Prioriser Excel, flow matrix et diagrammes. |
| 2 | Plusieurs Cloud Reviews pourraient être nécessaires. | Cycle de gouvernance plus long. | Demander une Cloud Review / ITSBC globale. |
| 3 | Des flux inter-namespaces peuvent être oubliés. | Échecs de communication à l’exécution. | Mettre à jour la flow matrix par AP code et namespace. |
| 4 | La latence entre MCR/DMZR et LATAM on-premise est inconnue. | Dégradation possible des temps de réponse. | Mesurer sur cible et exécuter des tests de performance. |
| 5 | Le transfert massif des données Mexique au switchover est risqué. | Retard ou échec du cutover. | Prétransférer les données puis transférer uniquement le delta. |
| 6 | Les requêtes SQL complexes peuvent se comporter différemment sur l’architecture cible. | Problème de performance. | Faire des tests de charge et temps de réponse. |
| 7 | La migration batch vers S3/pod CFT n’est pas encore détaillée. | Rework ou échec des batchs. | Analyser batch par batch ; choisir API S3 ou volume monté. |
| 8 | Le mécanisme de chiffrement MQ n’est pas clair. | Écart sécurité ou documentation. | Revoir la documentation DMZR. |
| 9 | Les règles réglementaires/exploitation LATAM ne sont pas confirmées. | Risque de non-conformité. | Valider avec sécurité/conformité locale. |
| 10 | La CI/CD monolithique n’est pas alignée avec l’architecture modulaire cible. | Maintenance et déploiement plus difficiles. | Aller vers une pipeline par composant. |
| 11 | Le test d’intrusion n’est pas planifié assez tôt. | Blocage sécurité/gouvernance. | Planifier le test d’intrusion dès le début du projet. |

---

## 7. Points ouverts à confirmer

| # | Point ouvert |
|---:|---|
| 1 | Orthographe correcte de **Xiose/José**. |
| 2 | Nom exact de l’application : **Ada** ou **Adam**. |
| 3 | Nom exact de l’AP code actuel, transcrit comme **A101** ou similaire. |
| 4 | Nom officiel du portail d’accès : **My Technical Access**, **My Technical Access Express** ou autre. |
| 5 | Acronymes exacts : **DMZR**, **DMCR**, **MCR as Code**, **MGR**, **HACC**. |
| 6 | Mécanisme exact de chiffrement MQ dans DMZR. |
| 7 | Possibilité d’une Cloud Review / ITSBC globale pour tous les AP codes. |
| 8 | Capacité des DBA LATAM à accéder/gérer directement la base MCR. |
| 9 | Contraintes opérationnelles et réglementaires LATAM/locales pour les données sensibles/secrètes. |
| 10 | Responsable final des tests et implication éventuelle du COE/test center. |

---

## 8. Conclusion

Le Technical Assessment avance et peut encore viser une clôture jeudi, mais le découpage des AP codes est désormais le point critique principal.

La priorité est de produire un fichier Excel de provisioning par AP code, de mettre à jour les flow matrices, d’actualiser les diagrammes d’architecture et de clôturer ou documenter clairement les points ouverts OneNote.

Les principaux risques techniques sont identifiés et maîtrisables s’ils sont suivis pendant le projet de migration : flux inter-namespaces, migration des données, performance base de données, chiffrement, droits d’accès, modularité CI/CD et tests de sécurité obligatoires.

---

# Part 2 — English

## 1. Executive Summary

The meeting focused on the remaining open points of the **PIMS Technical Assessment** for the migration to **DMZR / MCR as Code**, with a specific focus on the **Mexico scope**.

The main clarification is that the PIMS ecosystem should **not be handled under one single AP code**. The main applications of the ecosystem, including **PIMS**, **Ada/Adam**, **PNT** and **CRS**, should be managed through **separate AP codes**, most likely associated with separate namespaces.

This decision directly impacts provisioning: the current Excel file must be split into **one provisioning Excel file per AP code/application**. Each file must contain the relevant resources and an adapted **flow matrix**, especially for inter-application and inter-namespace communications.

The target remains to close, or at least sufficiently complete, the Technical Assessment by **Thursday**, provided that the AP code split, Excel files, architecture diagrams and OneNote open points are updated.

---

## 2. Participants Mentioned

| Name / Role | Comment |
|---|---|
| Andres | Leads the PIMS, provisioning, Excel, coordination and open-point topics. |
| Xiose / José (?) | Main technical contributor, name to confirm. Provides clarification on architecture, security, cloud review, DB, CI/CD and testing. |
| Johan | Present in the meeting, contributes to some confirmations. |
| Amine | Present, likely short intervention near the end of the meeting. |
| Julius César | Present, but not clearly distinguishable in the transcript. |

---

## 3. Key Decisions

| # | Decision |
|---:|---|
| 1 | The PIMS ecosystem must be split into several AP codes instead of using one global AP code. |
| 2 | One provisioning Excel file must be created per AP code/application. |
| 3 | The **flow matrix** is a critical deliverable and must be adapted for each AP code, including cross-namespace flows. |
| 4 | The Thursday target for Technical Assessment completion is maintained, subject to AP code and documentation updates. |
| 5 | The Technical Assessment does not require the full detailed test campaign yet, but must identify the main test categories, ownership and mandatory security testing. |
| 6 | Penetration testing is mandatory because the application handles sensitive/secret data. |
| 7 | The target CI/CD model must be more modular than the current on-premise model, ideally with one pipeline per application component. |

---

## 4. Main Technical Points

### 4.1 AP Codes, Namespaces and Flows

The LATAM architecture team recommends splitting the PIMS ecosystem by application/AP code. This provides better segregation, makes provisioning clearer and helps identify the resources actually required by each application.

However, this also requires more accurate documentation of flows between namespaces.

Example: if the PIMS web portal is deployed in one namespace and Ada/Adam is deployed in another namespace, the required flows between these two namespaces must be explicitly described in the flow matrix.

### 4.2 Provisioning Excel Files

The current provisioning Excel file must be split into several files, with **one file per AP code**.

Rows related to applications now handled separately must be removed from the original file and moved into the relevant provisioning file.

The most critical section to replicate and adapt is the **flow matrix**. Resource information must also be reviewed application by application.

### 4.3 Cloud Review and ITSBC

The Cloud Review remains open.

With multiple AP codes, several Cloud Review cards or sessions may be required. It was suggested to check whether one **global Cloud Review / ITSBC** session can cover the entire PIMS ecosystem.

The Cloud Review must confirm that the applications are eligible for the target DMZR/MCR platform. If not, this could become a blocking point.

### 4.4 DMZR / IBM Cloud Access

Access to DMZR / IBM Cloud must be requested through a portal mentioned as **My Technical Access** or **My Technical Access Express**. The exact official name must be confirmed.

The access model appears to require linking a business profile with a technical profile.

Some permissions, such as permissions on DMZR Kafka topics, may require a manager request through the access portal.

### 4.5 Security, Encryption and Certificates

CRS does not directly encrypt the information. Encryption is performed by the country application, for example the Mexico application.

The main requirement is **file-level encryption**, probably using **PGP**.

Even if CFT/STCP provides secure transport, this does not necessarily replace file-level encryption when files are stored or exchanged.

**MTLS** is required for the relevant flows, especially between Confluent/Kafka and MCR as Code components.

Certificates should rely on the available PKI service instead of self-signed certificates.

### 4.6 Java 8, Docker Images and Runtime

The application will remain on **Java 8** for now.

Java 8 Docker images are still available and no blocking point has been identified. If specific libraries are required, the DevOps team can be involved to integrate them or confirm the right base image.

### 4.7 Ingress, Routes and Session Affinity

No **session affinity** is currently required.

For routes / ingress:

- **pass-through** may work for a simple application with a single context;
- **re-encrypt** may be required if several contexts or services are exposed behind the same route.

The routing mode must be documented in the provisioning or target architecture.

### 4.8 MQ, Kafka and Confluent

The need for MTLS is confirmed for some flows, especially those involving Confluent/Kafka and MCR as Code.

The exact MQ encryption mechanism in DMZR still needs to be confirmed through DMZR documentation.

### 4.9 Batches, CFT Pod and S3

The target pattern discussed is:

1. a CFT pod receives or transfers files;
2. files are stored in S3;
3. batches read and process files from S3.

Two technical options are possible:

- adapt batch code to use the S3 API directly;
- mount S3/storage as a volume to keep behavior close to the current filesystem approach.

Batch migration requires further analysis, but it does not block the Technical Assessment.

### 4.10 Database and Data Migration

No specific Oracle optimization or non-standard configuration is currently known, which is positive.

A data purge is ongoing. The estimated target volume for Mexico is around **1 TB**, to be confirmed.

Many SQL queries are complex. Response-time and load tests will be required on the target architecture.

It still needs to be clarified whether LATAM DBAs will be able to access or directly manage the MCR database, or whether this responsibility will remain with the France team.

A full Mexico database transfer at switchover is considered risky. The recommended strategy is:

- transfer most data before switchover;
- transfer only the delta during the final cutover;
- split exports into several compressed packages;
- avoid one massive transfer file.

A POC led by David Silva’s team is ongoing, involving `.parquet` files and replication to a target instance. Exact acronyms such as MGR/MCR and HACC must be confirmed.

### 4.11 Authentication, Scans and Monitoring

The target authentication mechanism is **ITG Web SSO**.

Current scans to document are:

- Sonar;
- Fortify;
- Vulnerability Advisor, currently on-premise.

In the DMZR/MCR target, Docker/container image scanning must be integrated into the pipeline.

Dynatrace is expected for monitoring. If advanced end-to-end or end-user monitoring is required, a specialized team should be involved.

### 4.12 Operations and Regulatory Constraints

Operational rules for sensitive/secret data must be clarified for LATAM.

European GDPR constraints were mentioned as an example, but the applicable LATAM or local country rules must be confirmed with the relevant security/compliance teams.

### 4.13 CI/CD

The current on-premise model uses one global CI and one global CD for all components. This model is not ideal for the target architecture.

The target recommendation is:

- at minimum, separate pipelines per AP code;
- ideally, one CI/CD pipeline per application component.

This would enable more independent deployments, easier maintenance and a more modular architecture.

### 4.14 Test Strategy

The Technical Assessment does not yet require the exhaustive description of the full test campaign, but it must identify the types of tests required and the responsible teams.

Tests to plan include:

- integration tests;
- user acceptance tests;
- performance tests;
- security tests;
- mandatory penetration testing;
- specific technical tests before production rollout.

PIMS already has an existing test team and existing automated/manual tests. The COE or test center may be contacted for guidance, scoping or budget estimation.

---

## 5. Action Log

| # | Action | Owner | Status / Target |
|---:|---|---|---|
| 1 | Initiate or create separate AP codes for PIMS ecosystem applications: Ada/Adam, PNT, CRS, etc. | Andres / LATAM Architecture | Open |
| 2 | Split the current provisioning Excel into one file per AP code. | Andres | Target Thursday |
| 3 | Remove application rows from the original Excel when they belong to another AP code. | Andres | Target Thursday |
| 4 | Replicate and adapt the flow matrix in each provisioning file. | Andres | Critical |
| 5 | Update architecture diagrams with Mexico scope, AP code split and namespaces. | Andres | Open |
| 6 | Update OneNote open points and close clarified items. | Andres | Before next review |
| 7 | Confirm whether one global Cloud Review / ITSBC can cover all related AP codes. | Andres / Architecture | Open |
| 8 | Create the DMZR / IBM Cloud access request through My Technical Access. | Andres | To initiate |
| 9 | Document the DMZR access process and Kafka/topic permission process. | Andres | For TA |
| 10 | Document file-level encryption responsibility for CRS/country application flows. | Andres | For TA |
| 11 | Confirm the MQ encryption mechanism in DMZR documentation. | Andres | Open |
| 12 | Update provisioning information for Java 8 Docker image/version. | Andres | Open |
| 13 | Document ingress route mode: pass-through or re-encrypt depending on contexts/services. | Andres / Architecture | Open |
| 14 | Analyze batch/file manager impact with CFT pod and S3. | Andres / Technical team | Later |
| 15 | Confirm Mexico database volume and purge status. | Andres / DBA / Country team | Open |
| 16 | Clarify whether LATAM DBAs can access/manage the MCR database. | Andres / DBA teams | Open |
| 17 | Review the Parquet data migration POC with David Silva’s team. | Andres | Open |
| 18 | Document ITG Web SSO target authentication. | Andres | For TA |
| 19 | Document current scans and future image scanning in the pipeline. | Andres / DevOps | For TA |
| 20 | Clarify LATAM/local operational and regulatory rules for sensitive/secret data. | Andres / Security / Compliance | Open |
| 21 | Review IC plan expectations with ITG and local teams. | Andres / ITG | Open |
| 22 | Define the target CI/CD model, ideally per application component. | Andres / DevOps | Open |
| 23 | Identify test categories and confirm test ownership. | Andres / Test team | For TA |
| 24 | Plan the mandatory penetration test. | Andres / Security | Required |

---

## 6. Risk Register

| # | Risk | Impact | Mitigation |
|---:|---|---|---|
| 1 | AP code split adds documentation and provisioning workload. | TA closure may slip. | Prioritize Excel split, flow matrix and diagrams. |
| 2 | Multiple Cloud Reviews may be required. | Longer governance cycle. | Request one global Cloud Review / ITSBC. |
| 3 | Cross-namespace flows may be missed. | Runtime communication failures. | Update the flow matrix per AP code and namespace. |
| 4 | Latency between MCR/DMZR and LATAM on-premise is unknown. | Possible response-time degradation. | Measure on target platform and run performance tests. |
| 5 | Large Mexico data transfer at switchover is risky. | Cutover delay or failure. | Pre-transfer data, then transfer only the delta. |
| 6 | Complex SQL queries may behave differently on the target architecture. | Performance issues. | Run response-time and load tests. |
| 7 | Batch migration to S3/CFT pod is not yet detailed. | Rework or batch failures. | Analyze batch by batch; choose S3 API or volume mount. |
| 8 | MQ encryption mechanism is unclear. | Security or documentation gap. | Review DMZR documentation. |
| 9 | LATAM regulatory/operation rules are not confirmed. | Compliance risk. | Validate with local security/compliance experts. |
| 10 | Monolithic CI/CD is not aligned with target modular architecture. | Harder maintenance and deployment. | Move toward one pipeline per component. |
| 11 | Penetration testing is not planned early enough. | Security/governance blocker. | Plan the penetration test early in the project. |

---

## 7. Open Points to Confirm

| # | Open Point |
|---:|---|
| 1 | Correct spelling of **Xiose/José**. |
| 2 | Correct application name: **Ada** or **Adam**. |
| 3 | Exact current AP code name, transcribed as something like **A101**. |
| 4 | Official access portal name: **My Technical Access**, **My Technical Access Express**, or another name. |
| 5 | Exact acronyms: **DMZR**, **DMCR**, **MCR as Code**, **MGR**, **HACC**. |
| 6 | Exact MQ encryption mechanism in DMZR. |
| 7 | Whether one global Cloud Review / ITSBC can cover all AP codes. |
| 8 | Whether LATAM DBAs can access/manage the MCR database directly. |
| 9 | LATAM/local operational and regulatory constraints for sensitive/secret data. |
| 10 | Final test ownership and possible COE/test center involvement. |

---

## 8. Final Conclusion

The Technical Assessment is progressing and can still target Thursday, but the AP code split is now the main critical work item.

The priority is to produce one provisioning Excel file per AP code, update the flow matrices, update the architecture diagrams and close or clearly document the remaining OneNote open points.

The main technical risks are identified and manageable if they are followed during the migration project: cross-namespace flows, data migration, database performance, encryption, access rights, CI/CD modularity and mandatory security testing.

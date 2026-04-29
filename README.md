# Meeting Minutes / Compte Rendu — PIMS Technical Assessment & DMZR/MCR Migration

**Date:** 27 April 2026 / 27 avril 2026  
**Duration / Durée:** ~1h14  
**Scope / Périmètre:** PIMS ecosystem migration to DMZR / MCR as Code — Mexico scope  
**Source:** Full meeting audio + best-effort speaker-attributed transcript  

> **Note:** Speaker names and some acronyms are based on best-effort transcription. The spelling of **Xiose/José** and some technical acronyms must be confirmed.
>
> **Note FR :** Les noms des intervenants et certains acronymes sont basés sur une transcription automatique retravaillée. L’orthographe de **Xiose/José** et certains acronymes techniques restent à confirmer.

---

## 1. Executive Summary / Synthèse exécutive

### English

The meeting focused on the remaining open items of the **PIMS Technical Assessment** for the migration to **DMZR / MCR as Code**, with a specific focus on the **Mexico scope**.

The main architectural clarification is that the PIMS ecosystem should **not be handled under a single AP code**. Instead, the main applications of the ecosystem, such as **PIMS**, **Ada/Adam**, **PNT** and **CRS**, should be handled through **separate AP codes** and probably separate namespaces.

This has a direct impact on provisioning: the current Excel file must be split into **one provisioning Excel file per AP code/application**. Each file must include the relevant resources and an adapted **flow matrix**, especially for inter-application and inter-namespace communications.

The target remains to close or sufficiently complete the Technical Assessment by **Thursday**, provided that the AP code split, updated Excel files, diagrams and OneNote open points are addressed.

### Français

La réunion a porté sur les points ouverts du **Technical Assessment PIMS** dans le cadre de la migration vers **DMZR / MCR as Code**, avec un focus sur le **périmètre Mexique**.

La clarification architecturale principale est que l’écosystème PIMS ne doit **pas être traité avec un seul AP code**. Les principales applications de l’écosystème, notamment **PIMS**, **Ada/Adam**, **PNT** et **CRS**, doivent être traitées via des **AP codes séparés**, probablement associés à des namespaces distincts.

Cela impacte directement le provisioning : le fichier Excel actuel doit être découpé en **un fichier Excel de provisioning par AP code/application**. Chaque fichier devra contenir les ressources concernées ainsi qu’une **flow matrix** adaptée, en particulier pour les communications inter-applications et inter-namespaces.

L’objectif reste de clôturer ou d’avoir un Technical Assessment suffisamment complet d’ici **jeudi**, sous réserve de finaliser le découpage des AP codes, les fichiers Excel, les diagrammes et les points ouverts dans OneNote.

---

## 2. Key Decisions / Décisions principales

| # | Decision — EN | Décision — FR |
|---:|---|---|
| 1 | The PIMS ecosystem must be split into several AP codes instead of using one global AP code. | L’écosystème PIMS doit être découpé en plusieurs AP codes au lieu d’utiliser un AP code global unique. |
| 2 | One provisioning Excel file must be created per AP code/application. | Un fichier Excel de provisioning doit être créé par AP code/application. |
| 3 | The flow matrix is a critical deliverable and must be adapted for each AP code, including cross-namespace flows. | La flow matrix est un livrable critique et doit être adaptée pour chaque AP code, y compris les flux inter-namespaces. |
| 4 | The Thursday target for Technical Assessment completion is maintained, but depends on the AP code and documentation updates. | L’objectif de clôture jeudi est maintenu, mais dépend de la mise à jour des AP codes et de la documentation. |
| 5 | The Technical Assessment does not need the full detailed test campaign, but must identify test categories, ownership and mandatory security testing. | Le Technical Assessment ne nécessite pas la campagne de tests détaillée complète, mais doit identifier les catégories de tests, les responsables et les tests de sécurité obligatoires. |
| 6 | Penetration testing is mandatory because the application handles sensitive/secret data. | Le test d’intrusion est obligatoire car l’application manipule des données sensibles/secrètes. |

---

## 3. Main Technical Points / Points techniques principaux

### 3.1 AP Codes, Namespaces and Flows / AP codes, namespaces et flux

**EN:**  
The LATAM architecture team recommended separating the PIMS ecosystem by application/AP code. This improves segregation and makes provisioning clearer, but creates additional flows to document and open between namespaces.

Example: if the PIMS web portal is in one namespace and Ada/Adam is in another, the required flows between these namespaces must be explicitly listed in the flow matrix.

**FR :**  
L’équipe Architecture LATAM recommande de séparer l’écosystème PIMS par application/AP code. Cela améliore la ségrégation et clarifie le provisioning, mais crée des flux supplémentaires à documenter et à ouvrir entre namespaces.

Exemple : si le portail web PIMS est dans un namespace et Ada/Adam dans un autre, les flux nécessaires entre ces namespaces doivent être explicitement listés dans la flow matrix.

---

### 3.2 Provisioning Excel Files / Fichiers Excel de provisioning

**EN:**  
The current provisioning Excel must be split into several files, one per AP code. Lines related to applications now handled separately must be removed from the original file and moved into the relevant new file.

The most important part to replicate and adapt is the **flow matrix**. Resource information must also be updated for each application/AP code.

**FR :**  
Le fichier Excel de provisioning actuel doit être découpé en plusieurs fichiers, un par AP code. Les lignes correspondant aux applications désormais traitées séparément doivent être retirées du fichier initial et transférées dans les fichiers concernés.

La partie la plus importante à répliquer et adapter est la **flow matrix**. Les informations de ressources doivent également être mises à jour pour chaque application/AP code.

---

### 3.3 Cloud Review and ITSBC / Cloud Review et ITSBC

**EN:**  
The Cloud Review is still open. With multiple AP codes, several Cloud Review cards or sessions may be required. Andres suggested checking whether one global Cloud Review / ITSBC session can cover the whole PIMS ecosystem.

The Cloud Review is expected to confirm whether the applications are eligible for the target DMZR/MCR platform. If not, it could become a blocking point.

**FR :**  
La Cloud Review reste ouverte. Avec plusieurs AP codes, plusieurs cartes ou sessions Cloud Review pourraient être nécessaires. Andres a proposé de vérifier s’il est possible d’organiser une seule Cloud Review / ITSBC globale couvrant tout l’écosystème PIMS.

La Cloud Review doit confirmer que les applications sont éligibles à la plateforme cible DMZR/MCR. Dans le cas contraire, cela pourrait devenir un point bloquant.

---

### 3.4 Security, Encryption and Access / Sécurité, chiffrement et accès

**EN:**  
Access to DMZR / IBM Cloud must be requested through **My Technical Access** or **My Technical Access Express** *(exact official name to confirm)*.

The access model appears to require linking a business profile with a technical profile. Some permissions, such as Kafka topic permissions, may require a manager request through the access portal.

CRS does not encrypt the information directly. Encryption is performed by the country application, for example the Mexico application.

The key requirement is **file-level encryption**, most likely using **PGP**. CFT/STCP may provide secure transport, but secure transport does not remove the need for file-level encryption when files are stored or exchanged.

MTLS is required for relevant flows, especially between Confluent/Kafka and MCR as Code components. Certificates should rely on the available PKI service instead of self-signed certificates.

**FR :**  
L’accès à DMZR / IBM Cloud doit être demandé via **My Technical Access** ou **My Technical Access Express** *(nom officiel exact à confirmer)*.

Le modèle d’accès semble nécessiter l’association d’un profil business avec un profil technique. Certaines permissions, comme les droits sur les topics Kafka, peuvent nécessiter une demande via le manager dans le portail d’accès.

CRS ne chiffre pas directement l’information. Le chiffrement est réalisé par l’application pays, par exemple l’application Mexique.

L’exigence clé est le **chiffrement au niveau fichier**, probablement via **PGP**. CFT/STCP peut fournir un transport sécurisé, mais le transport sécurisé ne remplace pas l’exigence de chiffrement du fichier lorsqu’il est stocké ou échangé.

Le MTLS est requis pour les flux concernés, notamment entre Confluent/Kafka et les composants MCR as Code. Les certificats doivent s’appuyer sur le service PKI disponible plutôt que sur des certificats auto-signés.

---

### 3.5 Java 8, Ingress and Runtime / Java 8, ingress et runtime

**EN:**  
The application will remain on **Java 8** for now. Java 8 Docker images are still available and there is no identified blocking point.

No session affinity is currently required.

For ingress/route configuration:

- **Pass-through** may work for a simple single-context application.
- **Re-encrypt** may be required if several contexts/services are exposed behind the same route.

The exact MQ encryption mechanism in DMZR remains to be confirmed by reviewing the DMZR documentation.

**FR :**  
L’application restera sur **Java 8** pour le moment. Les images Docker Java 8 sont toujours disponibles et aucun point bloquant n’a été identifié.

Aucune session affinity n’est requise actuellement.

Pour la configuration ingress/route :

- le mode **pass-through** peut convenir pour une application simple avec un seul contexte ;
- le mode **re-encrypt** peut être nécessaire si plusieurs contextes/services sont exposés derrière la même route.

Le mécanisme exact de chiffrement MQ dans DMZR reste à confirmer via la documentation DMZR.

---

### 3.6 Batches, CFT Pod and S3 / Batchs, pod CFT et S3

**EN:**  
The target pattern discussed is:

1. A CFT pod receives or transfers files.
2. Files are stored in S3.
3. Batch processes read and process the files from S3.

Two options are possible:

- adapt batch code to use the S3 API directly;
- mount S3/storage as a volume to keep behavior close to the current filesystem approach.

Batch migration requires further analysis but does not block the Technical Assessment.

**FR :**  
Le schéma cible discuté est le suivant :

1. un pod CFT reçoit ou transfère les fichiers ;
2. les fichiers sont stockés dans S3 ;
3. les batchs lisent et traitent les fichiers depuis S3.

Deux options sont possibles :

- adapter le code des batchs pour utiliser directement l’API S3 ;
- monter S3/le stockage comme un volume afin de conserver un comportement proche du filesystem actuel.

La migration des batchs nécessite une analyse complémentaire mais ne bloque pas le Technical Assessment.

---

### 3.7 Database and Data Migration / Base de données et migration des données

**EN:**  
No specific Oracle optimization or non-standard configuration is currently known, which is positive.

A data purge is ongoing. The estimated target volume for Mexico is around **1 TB**, to be confirmed.

Many SQL queries are complex, so response time and load tests will be needed on the target architecture. It is still unclear whether LATAM DBAs will access/manage the MCR database directly or whether this will be handled by the France team.

Transferring the full Mexico database volume at switchover is risky. Recommended strategy:

- transfer most data before switchover;
- transfer only the delta at final cutover;
- split exports into several compressed packages;
- avoid one massive transfer file.

A POC by David Silva’s team is ongoing, involving `.parquet` files and replication to a target instance. Exact acronyms such as MGR/MCR and HACC must be confirmed.

**FR :**  
Aucune optimisation Oracle spécifique ou configuration non standard n’est connue à ce stade, ce qui est positif.

Une purge de données est en cours. Le volume cible estimé pour le Mexique est d’environ **1 To**, à confirmer.

De nombreuses requêtes SQL sont complexes ; des tests de temps de réponse et de charge seront donc nécessaires sur l’architecture cible. Il reste à clarifier si les DBA LATAM pourront accéder/gérer directement la base MCR ou si cela sera pris en charge par l’équipe France.

Transférer l’intégralité du volume de données Mexique au moment du switchover est risqué. Stratégie recommandée :

- transférer la majorité des données avant le switchover ;
- ne transférer que le delta lors du cutover final ;
- découper les exports en plusieurs paquets compressés ;
- éviter un transfert massif unique.

Un POC mené par l’équipe de David Silva est en cours, avec des fichiers `.parquet` et une réplication vers une instance cible. Les acronymes exacts comme MGR/MCR et HACC doivent être confirmés.

---

### 3.8 Authentication, Scans, Monitoring and Operations / Authentification, scans, monitoring et exploitation

**EN:**  
The target authentication mechanism is **ITG Web SSO**.

Current scans to document:

- Sonar;
- Fortify;
- Vulnerability Advisor, currently on-premise.

For the target DMZR/MCR pipeline, Docker/container image scanning must be included.

Dynatrace is expected for monitoring. If advanced end-to-end or end-user performance monitoring is required, the dedicated monitoring/performance team should be involved.

Operational rules for sensitive/secret data must be clarified for LATAM. European GDPR constraints were used as a reference example, but the applicable LATAM/local rules must be confirmed.

**FR :**  
Le mécanisme d’authentification cible est **ITG Web SSO**.

Scans actuels à documenter :

- Sonar ;
- Fortify ;
- Vulnerability Advisor, actuellement on-premise.

Pour la pipeline cible DMZR/MCR, le scan des images Docker/conteneurs doit être inclus.

Dynatrace est prévu pour le monitoring. Si un monitoring avancé de bout en bout ou côté utilisateur final est nécessaire, l’équipe monitoring/performance dédiée devra être impliquée.

Les règles d’exploitation concernant les données sensibles/secrètes doivent être clarifiées pour LATAM. Les contraintes GDPR européennes ont été citées comme exemple, mais les règles LATAM/locales applicables doivent être confirmées.

---

### 3.9 CI/CD and Test Strategy / CI/CD et stratégie de tests

**EN:**  
The current on-premise model uses one CI and one CD for all components. This is not ideal for the target model.

Target recommendation:

- at least separate pipelines per AP code;
- ideally one CI/CD pipeline per application component.

Testing must cover:

- integration tests;
- user acceptance tests;
- performance tests;
- security tests;
- mandatory penetration testing;
- specific technical tests before rollout.

PIMS already has automated/manual tests and an existing test team. A COE/test center may be contacted early for guidance and budget estimation.

**FR :**  
Le modèle on-premise actuel utilise une CI et une CD globales pour tous les composants. Ce modèle n’est pas idéal pour la cible.

Recommandation cible :

- au minimum des pipelines séparées par AP code ;
- idéalement une pipeline CI/CD par composant applicatif.

Les tests doivent couvrir :

- les tests d’intégration ;
- les tests d’acceptance utilisateur ;
- les tests de performance ;
- les tests de sécurité ;
- le test d’intrusion obligatoire ;
- les tests techniques spécifiques avant mise en production.

PIMS dispose déjà de tests automatisés/manuels et d’une équipe de test. Un COE/test center peut être contacté en amont pour conseil et estimation budgétaire.

---

## 4. Action Log / Plan d’actions

| # | Action — EN | Action — FR | Owner / Responsable | Status / Statut |
|---:|---|---|---|---|
| 1 | Initiate or create separate AP codes for PIMS ecosystem applications: Ada/Adam, PNT, CRS, etc. | Initier ou créer les AP codes séparés pour les applications de l’écosystème PIMS : Ada/Adam, PNT, CRS, etc. | Andres / LATAM Architecture | Open / Ouvert |
| 2 | Split the current provisioning Excel into one file per AP code. | Découper l’Excel de provisioning actuel en un fichier par AP code. | Andres | Target Thursday / Objectif jeudi |
| 3 | Remove application lines from the original Excel when they belong to another AP code. | Retirer du fichier Excel initial les lignes des applications relevant d’un autre AP code. | Andres | Target Thursday / Objectif jeudi |
| 4 | Replicate and adapt the flow matrix in each provisioning file. | Répliquer et adapter la flow matrix dans chaque fichier de provisioning. | Andres | Critical / Critique |
| 5 | Update architecture diagrams with Mexico scope, AP code split and namespaces. | Mettre à jour les diagrammes avec le périmètre Mexique, le découpage AP code et les namespaces. | Andres | Open / Ouvert |
| 6 | Update OneNote open points and close clarified items. | Mettre à jour les points ouverts OneNote et clôturer les sujets clarifiés. | Andres | Before next review / Avant prochaine revue |
| 7 | Confirm whether one global Cloud Review / ITSBC can cover all related AP codes. | Confirmer si une Cloud Review / ITSBC globale peut couvrir tous les AP codes liés. | Andres / Architecture | Open / Ouvert |
| 8 | Create DMZR / IBM Cloud access request through My Technical Access. | Créer la demande d’accès DMZR / IBM Cloud via My Technical Access. | Andres | To initiate / À initier |
| 9 | Document DMZR access process and Kafka/topic permission process. | Documenter le processus d’accès DMZR et les permissions Kafka/topics. | Andres | For TA / Pour TA |
| 10 | Document file-level encryption responsibility for CRS/country application flows. | Documenter la responsabilité du chiffrement fichier pour les flux CRS/application pays. | Andres | For TA / Pour TA |
| 11 | Confirm MQ encryption mechanism in DMZR documentation. | Confirmer le mécanisme de chiffrement MQ dans la documentation DMZR. | Andres | Open / Ouvert |
| 12 | Update provisioning information for Java 8 Docker image/version. | Mettre à jour les informations de provisioning pour l’image/version Docker Java 8. | Andres | Open / Ouvert |
| 13 | Document ingress route mode: pass-through or re-encrypt depending on contexts/services. | Documenter le mode ingress/route : pass-through ou re-encrypt selon les contextes/services. | Andres / Architecture | Open / Ouvert |
| 14 | Analyze batch/file manager impact with CFT pod and S3. | Analyser l’impact batch/file manager avec pod CFT et S3. | Andres / Technical team | Later / Plus tard |
| 15 | Confirm Mexico database volume and purge status. | Confirmer le volume de base Mexique et l’état de la purge. | Andres / DBA / Country team | Open / Ouvert |
| 16 | Clarify whether LATAM DBAs can access/manage the MCR database. | Clarifier si les DBA LATAM peuvent accéder/gérer la base MCR. | Andres / DBA teams | Open / Ouvert |
| 17 | Review Parquet data migration POC with David Silva’s team. | Revoir le POC de migration de données Parquet avec l’équipe de David Silva. | Andres | Open / Ouvert |
| 18 | Document ITG Web SSO target authentication. | Documenter l’authentification cible ITG Web SSO. | Andres | For TA / Pour TA |
| 19 | Document current scans and future image scanning in pipeline. | Documenter les scans actuels et le scan image futur dans la pipeline. | Andres / DevOps | For TA / Pour TA |
| 20 | Clarify LATAM/local operational and regulatory rules for sensitive/secret data. | Clarifier les règles opérationnelles et réglementaires LATAM/locales pour les données sensibles/secrètes. | Andres / Security / Compliance | Open / Ouvert |
| 21 | Review IC plan expectations with ITG and local teams. | Revoir les attentes IC plan avec ITG et les équipes locales. | Andres / ITG | Open / Ouvert |
| 22 | Define target CI/CD model, ideally per application component. | Définir le modèle CI/CD cible, idéalement par composant applicatif. | Andres / DevOps | Open / Ouvert |
| 23 | Identify test categories and confirm test ownership. | Identifier les catégories de tests et confirmer le responsable des tests. | Andres / Test team | For TA / Pour TA |
| 24 | Plan mandatory penetration test. | Planifier le test d’intrusion obligatoire. | Andres / Security | Required / Obligatoire |

---

## 5. Risk Register / Registre des risques

| # | Risk — EN | Risque — FR | Impact | Mitigation / Mitigation |
|---:|---|---|---|---|
| 1 | AP code split adds documentation and provisioning workload. | Le découpage AP code ajoute de la charge documentaire et provisioning. | TA closure may slip. / Risque de glissement de la clôture TA. | Prioritize Excel split, flow matrix and diagrams. / Prioriser Excel, flow matrix et diagrammes. |
| 2 | Multiple Cloud Reviews may be required. | Plusieurs Cloud Reviews pourraient être nécessaires. | Longer governance cycle. / Cycle de gouvernance plus long. | Request one global Cloud Review / ITSBC. / Demander une Cloud Review / ITSBC globale. |
| 3 | Cross-namespace flows may be missed. | Des flux inter-namespaces peuvent être oubliés. | Runtime communication failures. / Échecs de communication à l’exécution. | Update flow matrix per AP code and namespace. / Mettre à jour la flow matrix par AP code et namespace. |
| 4 | Latency between MCR/DMZR and LATAM on-premise is unknown. | La latence entre MCR/DMZR et LATAM on-premise est inconnue. | Possible response-time degradation. / Dégradation possible des temps de réponse. | Measure on target platform and run performance tests. / Mesurer sur cible et exécuter des tests de performance. |
| 5 | Large Mexico data transfer at switchover is risky. | Le transfert massif des données Mexique au switchover est risqué. | Cutover delay or failure. / Retard ou échec du cutover. | Pre-transfer data, then transfer delta only. / Prétransférer les données puis transférer uniquement le delta. |
| 6 | Complex SQL queries may behave differently on target architecture. | Les requêtes SQL complexes peuvent se comporter différemment sur l’architecture cible. | Performance issue. / Problème de performance. | Run response-time and load tests. / Faire des tests de charge et temps de réponse. |
| 7 | Batch migration to S3/CFT pod is not yet detailed. | La migration batch vers S3/pod CFT n’est pas encore détaillée. | Rework or batch failures. / Rework ou échec des batchs. | Analyze batch by batch; choose S3 API or volume mount. / Analyser batch par batch ; choisir API S3 ou volume monté. |
| 8 | MQ encryption mechanism is unclear. | Le mécanisme de chiffrement MQ n’est pas clair. | Security or documentation gap. / Écart sécurité ou documentation. | Review DMZR documentation. / Revoir la documentation DMZR. |
| 9 | LATAM regulatory/operation rules are not confirmed. | Les règles réglementaires/exploitation LATAM ne sont pas confirmées. | Compliance risk. / Risque de non-conformité. | Validate with local security/compliance experts. / Valider avec sécurité/conformité locale. |
| 10 | Monolithic CI/CD is not aligned with target modular architecture. | La CI/CD monolithique n’est pas alignée avec l’architecture modulaire cible. | Harder maintenance and deployment. / Maintenance et déploiement plus difficiles. | Move toward one pipeline per component. / Aller vers une pipeline par composant. |
| 11 | Pen test not planned early enough. | Le test d’intrusion n’est pas planifié assez tôt. | Security/governance blocker. / Blocage sécurité/gouvernance. | Plan penetration test early. / Planifier le test d’intrusion tôt. |

---

## 6. Open Points to Confirm / Points ouverts à confirmer

| # | English | Français |
|---:|---|---|
| 1 | Correct spelling of **Xiose/José**. | Orthographe correcte de **Xiose/José**. |
| 2 | Correct application name: **Ada** or **Adam**. | Nom exact de l’application : **Ada** ou **Adam**. |
| 3 | Exact current AP code name, transcribed as something like **A101**. | Nom exact de l’AP code actuel, transcrit comme **A101** ou similaire. |
| 4 | Official name of the access portal: **My Technical Access**, **My Technical Access Express**, or another name. | Nom officiel du portail d’accès : **My Technical Access**, **My Technical Access Express** ou autre. |
| 5 | Exact acronyms and services: **DMZR**, **DMCR**, **MCR as Code**, **MGR**, **HACC**. | Acronymes et services exacts : **DMZR**, **DMCR**, **MCR as Code**, **MGR**, **HACC**. |
| 6 | Exact MQ encryption mechanism in DMZR. | Mécanisme exact de chiffrement MQ dans DMZR. |
| 7 | Whether one global Cloud Review / ITSBC can cover all AP codes. | Si une Cloud Review / ITSBC globale peut couvrir tous les AP codes. |
| 8 | Whether LATAM DBAs can access/manage MCR database directly. | Si les DBA LATAM peuvent accéder/gérer directement la base MCR. |
| 9 | LATAM/local operational and regulatory constraints for sensitive/secret data. | Contraintes opérationnelles et réglementaires LATAM/locales pour les données sensibles/secrètes. |
| 10 | Final test ownership and possible COE/test center involvement. | Responsable final des tests et implication éventuelle du COE/test center. |

---

## 7. Final Conclusion / Conclusion finale

### English

The Technical Assessment is progressing and can still target Thursday, but the AP code split is now the main critical work item. The priority is to produce one provisioning Excel per AP code, update the flow matrices, update the architecture diagrams and close or clearly document the remaining OneNote points.

The main technical risks are identified and manageable if they are followed during the migration project: cross-namespace flows, data migration, database performance, encryption, access rights, CI/CD modularity and mandatory security testing.

### Français

Le Technical Assessment avance et peut encore viser une clôture jeudi, mais le découpage des AP codes est désormais le point critique principal. La priorité est de produire un fichier Excel de provisioning par AP code, de mettre à jour les flow matrices, d’actualiser les diagrammes d’architecture et de clôturer ou documenter clairement les points ouverts OneNote.

Les principaux risques techniques sont identifiés et maîtrisables à condition d’être suivis pendant le projet de migration : flux inter-namespaces, migration des données, performance base de données, chiffrement, droits d’accès, modularité CI/CD et tests de sécurité obligatoires.

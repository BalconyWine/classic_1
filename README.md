CRIT101 — Team Contacts

Commentaire oral à écrire :

Squad D4W : fournir le DE/DI avec un récapitulatif des contacts principaux de l’application : PO, contacts applicatifs, mailing lists, groupes de support / Snow, et contacts d’exploitation. Le cartouche du DE/DI doit permettre d’identifier clairement les interlocuteurs de l’application ROAD Data Quality.

CRIT102 — Application identity card

Commentaire oral à écrire :

L’application a été identifiée comme Cardiff ROAD Data Quality / Data Quality Gateway, liée au projet INE0954. Elle correspond à un module complémentaire Collibra Data Quality, déployé comme application disjointe car standalone, cloud native, avec un niveau de confidentialité et une population d’utilisateurs distincts de ROAD DGC.

CRIT103 — Business criticality

Commentaire oral à écrire :

L’application est portée par une contrainte réglementaire BCBS avec un besoin de mise en production rapide : les utilisateurs doivent pouvoir commencer à travailler avant juin, avec une cible de déploiement autour de mi-mai. L’application est considérée de criticité “low” dans les échanges, mais cela ne dispense pas des livrables PACT obligatoires.

CRIT104 — IC Plan

Commentaire oral à écrire :

Un IC Plan est requis, même si l’application est de criticité low. Il n’y a plus d’exemption sur ce point. Aucun exercice de bascule ICP unitaire n’est attendu dans le cadre PAS V4 ; l’application devra participer à l’exercice groupé si applicable. La documentation IC Plan reste néanmoins obligatoire et doit être fournie, potentiellement avec l’appui de l’équipe Continuité.

CRIT105 — Functional architecture

Commentaire oral à écrire :

Le schéma d’architecture fonctionnelle peut être repris depuis le dossier ITSVC / support architecture. Le schéma fonctionnel reste exploitable même si certains éléments techniques ont évolué par rapport à la stratégie initiale. Une capture du schéma AP1765 Architecture Fonctionnelle peut être utilisée comme preuve.

CRIT106 — Asset Management / ASC sheet

Commentaire oral à écrire :

Squad D4W, avec le support du référent sécurité / expert sécurité, doit fournir la revue ASC sécurité. L’interlocuteur sécurité identifié est Germain Poitier. Si l’ASC contient déjà les revues jointes, elles pourront être utilisées comme éléments de preuve.

CRIT107 — Technical Architecture & Security Schema / SAT

Commentaire oral à écrire :

ITG Apps CARDIF doit fournir le SAT/SATS. Ce livrable est attendu pour cadrer l’architecture technique et sécurité avant les demandes de ressources, d’ouvertures de flux et de mise en production. Même si certains déploiements historiques ont pu être faits avant finalisation du SATS, le SATS reste fortement attendu avant l’exploitation réelle en production.

CRIT108 — Risk Management / Risk analysis

Commentaire oral à écrire :

L’analyse de risques sécurité doit être traitée avec l’expert sécurité, notamment Germain Poitier. Le PV de sécurité attendu devra couvrir les réserves éventuelles, les risques acceptés, les engagements de remédiation et les points restant à suivre après la mise en production si une mise en production light est décidée.

CRIT109 — List of application URLs

Commentaire oral à écrire :

Le dossier d’exploitation doit contenir la liste des URLs de l’application : URLs utilisateurs, URLs exposées et URLs techniques si applicables. L’application expose un ingress côté front / Web UI via une VIP. Le FQDN de production est encore attendu pour finaliser la demande associée.

CRIT110 — IAM Applications Rights

Commentaire oral à écrire :

Squad D4W doit fournir la preuve de la gestion des habilitations applicatives via IAM / MyAccess. Une capture d’écran MyAccess montrant l’entrée de catalogue permettant de demander l’accès à ROAD Data Quality est considérée comme preuve acceptable.

CRIT111 — Server connections / Monitoring / Alerting

Commentaire oral à écrire :

ITG Apps CARDIF doit confirmer la mise en place de l’alerting Sysdig, notamment les remontées d’alertes automatiques par mail. L’objectif est de démontrer qu’un dispositif de surveillance technique et d’alerte est opérationnel pour l’exploitation.

CRIT112 — Storage / Secret Management

Commentaire oral à écrire :

ITG Apps CARDIF doit fournir dans le DE/DI le récapitulatif des secrets HVault utilisés par l’application. Ce point est porté côté Apps car il concerne la gestion technique des secrets et leur intégration dans l’environnement d’exploitation.

CRIT113 — List of APIs consumed and exposed

Commentaire oral à écrire :

Critère bypassé : les APIs sont considérées comme propriétaires / natives à la solution Collibra ROAD Data Quality et ne passent pas par un catalogue API type IPG. Les échanges API sont directs entre les applications, notamment vers ROAD DGC. Il est toutefois possible d’ajouter dans le DE/DI un récapitulatif des APIs exploitées ou des flux nécessaires, principalement pour documenter les ouvertures réseau.

CRIT114 — List of servers

Commentaire oral à écrire :

Critère non applicable / bypassé : l’application est cloud native sur Kubernetes / PAS V4 et ne repose pas sur une liste classique de serveurs applicatifs à maintenir. Les éléments d’infrastructure doivent plutôt être décrits dans le DE/DI via les namespaces, composants Kubernetes, instances Postgre et ressources PAS V4.

CRIT116 — Launch procedures, including stop/restart

Commentaire oral à écrire :

Squad D4W et ITG Apps CARDIF doivent fournir dans le DE la procédure d’arrêt / relance. Pour une application microservices, l’arrêt / relance classique a peu de sens, mais il faut tout de même documenter le mode opératoire permettant d’interrompre l’application, de relancer les pods ou de redémarrer les composants si nécessaire.

CRIT118 — IAM Technical Account

Commentaire oral à écrire :

Critère bypassé / non applicable : aucun besoin spécifique de compte technique IAM n’a été identifié pendant l’échange. Le point a été explicitement écarté dans la revue.

CRIT119 — Compliance with development rules

Commentaire oral à écrire :

Le critère ne concerne pas les règles de développement logiciel, mais les règles IT Groupe : gouvernance, architecture, urbanisation et conformité de la solution. Comme il s’agit d’une nouvelle application, il faut fournir les payloads / informations de provisioning des ressources PAS V4 ainsi que la note de validation ITSVC. La validation ITSVC permettra de formaliser l’acceptation de la solution avant mise en production.

CRIT121 — Technical supervision devices and availability measurement

Commentaire oral à écrire :

ITG Apps CARDIF doit fournir le dashboard Dynatrace de supervision production. Le point important n’est pas seulement l’availability rate, mais la présence d’une supervision technique effective : dashboard minimum, idéalement synthétique, avec des scénarios de supervision. La match zone ne pourra être créée qu’une fois la production disponible.

CRIT124 — Description of Kubernetes applications

Commentaire oral à écrire :

Squad D4W doit fournir le DE avec la description des applications Kubernetes. ITG Apps CARDIF doit compléter avec les informations techniques liées à PAS V4 : namespaces, composants, instances Postgre, ressources et éléments d’identification nécessaires à l’exploitation.

CRIT133 — Purge Policy

Commentaire oral à écrire :

Critère non applicable / bypassé : aucune politique de purge spécifique n’a été identifiée pendant l’échange. Les contraintes de conservation ou purge relèvent plutôt des applications sources ou des offres de service sous-jacentes si applicable.

CRIT135 — Configuring Application Servers

Commentaire oral à écrire :

Critère bypassé : la configuration des serveurs applicatifs classiques n’est pas applicable telle quelle, car l’application est cloud native / Kubernetes et éditeur tiers. Les informations pertinentes doivent être couvertes dans le DI avec les éléments de déploiement, prérequis, flux et configuration applicative.

CRIT136 — Configuring Virtual Host

Commentaire oral à écrire :

Critère bypassé : la notion de virtual host classique n’est pas directement applicable. L’exposition de l’application passe par l’ingress, la VIP et le FQDN. Les informations utiles doivent être documentées dans le DI ou le DE.

CRIT137 — Configuring Installation Clusters

Commentaire oral à écrire :

Critère bypassé : la configuration détaillée du cluster est portée par PAS V4 / Kubernetes. Le DI doit uniquement documenter les éléments nécessaires au déploiement applicatif : namespace, ressources, prérequis, composants et paramètres spécifiques.

CRIT139 — Directory Configuration / File Systems

Commentaire oral à écrire :

Le point n’a pas fait l’objet d’un échange détaillé spécifique. Il a été englobé dans la logique DI : si l’application nécessite des répertoires, volumes, montages ou file systems particuliers, ils doivent être décrits dans le dossier d’installation. Sinon, le critère peut rester à traiter comme non applicable ou couvert par PAS V4 selon le cas.

CRIT143 — Configuring Databases

Commentaire oral à écrire :

Squad D4W doit fournir dans le DI les informations de création et de configuration des bases de données : instances Postgre, taille initiale, paramètres d’extension, encodage et caractéristiques techniques utiles. Le point est proche du critère “Description of databases”, mais ici l’attendu porte plutôt sur la configuration et la création technique.

CRIT150 — Configuration Verification

Commentaire oral à écrire :

ITG Apps CARDIF doit fournir une preuve de configuration, notamment une capture d’écran de la page d’accueil de l’espace DevOps. Cette preuve permet de montrer que l’environnement et les éléments de configuration sont bien créés / visibles.

CRIT152 — Retrieving sources

Commentaire oral à écrire :

Aucun commentaire oral clair n’a été identifié spécifiquement sur ce critère pendant l’échange. Le point n’a pas été traité en détail dans la réunion.

CRIT155 — Configuration SSO

Commentaire oral à écrire :

Le DI doit contenir les informations relatives à la configuration Web SSO Group. L’application est compatible uniquement avec un mode IDP initiated, qui n’est pas supporté par César ; c’est pourquoi l’authentification passe par Web SSO Group. Le point doit être documenté dans le dossier d’installation / exploitation.

CRIT158 — Post-production control procedure

Commentaire oral à écrire :

Il faut prévoir une procédure de contrôle après mise en production permettant de vérifier que l’environnement prod fonctionne et que la solution est opérationnelle. Ce point est lié au PV de recette et aux vérifications post-déploiement attendues avant ouverture effective du service aux utilisateurs.

CRIT159 — Rollback procedure

Commentaire oral à écrire :

Le rollback n’a pas été détaillé explicitement. Le sujet a été abordé indirectement via le changement de mise en production : si une opération technique conditionne l’ouverture du service, par exemple livraison finale, bascule DNS ou import de données, elle doit être cadrée par un changement et inclure les modalités de retour arrière si nécessaire.

CRIT165 — Actual evolutions with declared and planned PROD change

Commentaire oral à écrire :

Un numéro de changement sera nécessaire pour cadrer les opérations de mise en production / mise en service. Les actions de construction réalisées avant usage métier réel peuvent être considérées comme “production cachée” et ne sont pas forcément attendues comme preuve PACT. En revanche, l’opération finale permettant l’ouverture du service doit être couverte par un changement.

CRIT169 — Compliance with technical roadmaps and obsolescence

Commentaire oral à écrire :

Le point est sensible car PAS V4 arrive en fin de trajectoire et une migration vers ROX devra probablement être prévue à horizon 2027. La date exacte reste à confirmer, certains échanges évoquant fin 2026 / début 2027 ou fin 2027. Pour le PACT, la preuve attendue est la note de passage ITSVC confirmant que la solution peut être acceptée malgré cette trajectoire technique.

CRIT170 — Support has been well informed

Commentaire oral à écrire :

Le critère est conservé. Il faut démontrer que le support a bien été informé de l’application, de son périmètre et des évolutions nécessaires, avec les éléments permettant la prise en charge en exploitation.

CRIT171 — CAPA Plan

Commentaire oral à écrire :

ITG Apps CARDIF doit consulter Maxime Frolov afin d’obtenir une capture d’écran du plan d’équipement APS. L’objectif est de démontrer que les ressources commandées sont bien tracées, pointées et cohérentes avec les besoins de l’application.

CRIT173 — Asset Management / Inventory excluding Docker containers

Commentaire oral à écrire :

Critère bypassé : ce point n’a pas été considéré applicable à l’application dans ce contexte Kubernetes / PAS V4. L’inventaire classique des assets hors conteneurs n’est pas demandé pour ce périmètre.

CRIT174 — Referencing and maintaining asset inventories / Network solution

Commentaire oral à écrire :

Critère bypassé : aucun besoin spécifique de référencement d’inventaire réseau n’a été identifié pour l’application. Les éléments réseau utiles sont plutôt couverts par les demandes de flux, VIP, FQDN, ingress et documentation DE/DI.

CRIT175 — Referencing and maintaining inventories of workstation assets

Commentaire oral à écrire :

Critère bypassé : aucun poste de travail ou asset utilisateur spécifique n’est à inventorier pour ce périmètre applicatif.

CRIT176 — Asset Management / ITG Product Reference

Commentaire oral à écrire :

Critère bypassé : le référencement ITG Product Reference / catalogue de service n’a pas été retenu comme applicable pendant l’échange.

CRIT178 — Vulnerability Management / Internal Vulnerability Scan — Technical Scan

Commentaire oral à écrire :

Critère bypassé : la partie vulnerability management technique n’a pas été retenue comme applicable dans ce contexte. L’application n’est pas exposée à Internet et plusieurs contrôles techniques classiques ont été écartés.

CRIT179 — Vulnerability Management / IVS WAS or EVS Application Scan

Commentaire oral à écrire :

ITG Apps CARDIF doit faire une demande de scan URL via le catalogue sécurité, puis fournir le rapport associé. Ce point reste à traiter même si le pentest, le hardening et le SAST ont été bypassés.

CRIT181 — Hardening / STS / Health Checking

Commentaire oral à écrire :

Critère bypassé : aucun hardening STS spécifique n’est attendu. Le point a été explicitement écarté pendant la revue.

CRIT182 — Application Security / Pentest

Commentaire oral à écrire :

Critère bypassé : l’application n’est pas exposée à Internet, donc aucun pentest n’est attendu.

CRIT183 — Application Security / Code Audit SAST and SCA

Commentaire oral à écrire :

Critère bypassé : il s’agit d’un logiciel éditeur / solution propriétaire Collibra, donc aucun audit de code SAST/SCA n’est demandé côté projet.

CRIT184 — Vulnerability Management / Security Monitoring

Commentaire oral à écrire :

Critère bypassé : le vulnerability monitoring sécurité n’a pas été retenu comme applicable pendant l’échange.

CRIT185 — Cyber Events and Alerts Management

Commentaire oral à écrire :

Critère bypassé : aucun dispositif spécifique de cyber event management n’a été demandé pour ce périmètre. Le sujet a été écarté pendant la revue.

CRIT186 — IT Outsourcing / Third Party Management

Commentaire oral à écrire :

Squad D4W doit vérifier avec les achats ou le PO de l’application le numéro du contrat de support avec l’éditeur. Seul le numéro de contrat est attendu, pas les termes du contrat. L’objectif est de démontrer qu’un contrat existe et qu’une due diligence a été réalisée dans le cadre du processus de contractualisation.

CRIT188 — Data Security / Non-production data / Anonymization

Commentaire oral à écrire :

Critère override : il n’y a pas d’échange de données de production vers les environnements hors production identifié comme problématique. Le sens de circulation évoqué est plutôt du hors-prod / dev vers prod, ce qui est moins sensible que la descente de données de production vers un environnement de développement. Le point reste néanmoins à confirmer avec l’expert sécurité / PV sécurité.

CRIT189 — Data Security / Data Encryption

Commentaire oral à écrire :

Le chiffrement reste attendu comme standard. Le point doit être couvert par le PV de sécurité ou par les éléments fournis par l’expert sécurité. Contrairement à l’anonymisation, le chiffrement n’a pas été écarté.

CRIT190 — Generic and specific steering instructions and alert sheets

Commentaire oral à écrire :

Critère bypassé dans la revue. Aucun commentaire oral détaillé n’a été donné sur des consignes de pilotage ou fiches d’alerte spécifiques.

CRIT191 — Application and DB backup procedures

Commentaire oral à écrire :

Critère bypassé : les procédures de sauvegarde applicative et base de données sont considérées comme incluses dans les offres de service / services standards de la plateforme. Aucun livrable spécifique n’a été demandé côté projet.

CRIT192 — Customer functional acceptance report / Technical acceptance report

Commentaire oral à écrire :

Squad D4W doit fournir le PV de recette. Ce document doit attester que l’environnement fonctionne, que la solution est opérationnelle et que les vérifications nécessaires ont été réalisées avant mise en production / mise en service. Ce PV fait partie des preuves importantes avant ouverture aux utilisateurs.

CRIT193 — Description of databases and accesses

Commentaire oral à écrire :

Squad D4W doit fournir dans le DE la description des bases de données et accès associés, notamment les instances Postgre utilisées par l’application. Ce point complète CRIT143 : CRIT143 porte plutôt sur la configuration / création, tandis que CRIT193 porte sur la description d’exploitation des bases et de leurs accès.

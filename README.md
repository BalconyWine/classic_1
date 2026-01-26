Hello Oussama, voici l'essentiel du point avec l'ITG (Jean-Luc) concernant le monitoring de la plateforme :

🚧 Le blocage technique

Incompatibilité : Domino ne supporte pas l'opérateur Dynatrace en mode standard dans Kubernetes (risque de stabilité).


Solution de repli : On s'oriente vers une approche "agentless" via un collecteur OpenTelemetry ou une ActiveGate qui viendrait scraper les métriques déjà présentes dans Prometheus. Cela évite d'impacter directement Domino.

📅 Contraintes de calendrier

Migration EKS : Une montée de version est prévue pour fin avril.


Migration ROX (OpenShift) : Passage sur IBM Cloud prévu en fin d'année.


Impact : L'ITG manque de bande passante et de visibilité sur ROX pour s'engager sur une solution pérenne tout de suite.

🎯 Priorités validées
On a convenu de cet ordre pour ne pas s'éparpiller :


Health Checks (Status Quo) : Le POC sur les tests de connectivité (HTTP monitor) des modèles API fonctionne bien et reste la solution court terme.


Logs - Log As A Service (Priorité 1) : C'est le besoin majeur des Data Scientists pour le debug.


Enjeu RBAC : On doit impérativement isoler les logs par périmètre (ex: une filiale ne doit pas voir les logs d'une autre).


Métriques Plateforme (Priorité 2) : On veut remonter les données d'allocation (RAM et GPU réservés vs consommés) dans Dynatrace via Prometheus, car la saturation des réservations bloque le lancement de nouveaux jobs.

🛠 Prochaines étapes
Jean-Luc (ITG) doit revenir vers nous pour nous "donner les clés" du système Log As A Service et valider comment gérer la ségrégation des accès.

On garde le sujet à l'ordre du jour des comités mensuels pour suivre l'avancée de l'infra.

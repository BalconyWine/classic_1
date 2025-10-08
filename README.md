Résumé de l’incident

Symptôme utilisateur : prod KO (HTTP 503 sur 20h).

Sur Dynatrace : le synthetic [AP27488] API STORE CARDIF échouait mais aucun e-mail reçu. Les Problems étaient rattachés au profil d’alerte Default.

Diagnostic (chronologie)

Constat dans Synthetic : exécutions en échec (503) depuis Paris ; Problems ouverts.

Contradiction : dans la page Problems, colonne Alerting profiles = Default → notre profil dédié n’était pas appliqué.

Piste 1 : réglage d’indisponibilité trop strict.

Action : Outage handling → activé “Generate a problem when the monitor is unavailable for one or more consecutive runs at any location” (1 échec suffit).

Piste 2 : filtrage par Management zone et par tags/AlertCode.

Après échange avec l’équipe Dynatrace, la management zone a été changée. Suite à ce changement, plus aucun élément n’apparaissait dans notre liste (profils/notifications) car mauvais rattachement zone + AEL.

Remédiation (pas à pas)

Nettoyage / recréation

Recréé le profil d’alerte du projet (AP27488-CARDIF-API-STORE) dans la bonne management zone.

Supprimé les anciens filtres trop restrictifs (ex. “global outage only”).

AEL (Alert/Event List)

Vérifié la déclaration de l’AlertCode côté AEL pour ce projet.

Corrigé l’AlertCode et son emplacement afin qu’il colle à la nouvelle zone.

Tags côté synthetic

Confirmé les tags sur le monitor : AlertCode:AP27488_Health_Check, alerting_synthetic:CARDIFAPISTORE, etc.

Notifications e-mail

Recréé la notification e-mail et rattaché explicitement le profil d’alerte du projet (pas “Default”).

Bouton Send test notification pour valider la délivrabilité.

Vérification fonctionnelle

Simulation d’erreur (exécution à la demande avec URL invalide / règle de contenu qui échoue).

Constat : Problem créé avec le bon AlertCode, profil d’alerte du projet appliqué, e-mail reçu.

Test croisé avec Tony (équipe applicative) : échec simulé → e-mail reçu côté app.

Résultat

Les Problems du synthetic portent le bon AlertCode, sont rattachés au bon profil (projet) et envoient les e-mails aux destinataires.

Pièces jointes à déposer dans le ticket

Capture Problem avant (profil = Default).

Capture du profil d’alerte recréé (zone + tags + sévérités).

Capture de la notification e-mail liée au bon profil.

Capture Problem après (profil = AP27488-CARDIF-API-STORE).

Capture d’un e-mail d’alerte reçu (toi + Tony).

Prévention / bonnes pratiques

Conserver l’option “any location / 1 failure” dans Outage handling.

Lors d’un changement de management zone, vérifier AEL + tags + notifications.

Tester systématiquement via “Send test notification” + échec simulé.

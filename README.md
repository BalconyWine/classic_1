Mes Actions (To-Do List d'Amine)
Voici les tâches spécifiques qui m'ont été demandées ou validées à la fin de la réunion :

1. Organiser une réunion de suivi avec le LATAM

La demande : Hussein m'a demandé (ainsi qu'à Nicolas) de "monter un point" pour discuter avec les équipes LATAM.

Interlocuteurs à inviter : Andres Rincon, l'équipe LATAM, et potentiellement Danilo (qui supervise). Nicolas et Ahmed doivent être dans la boucle.

L'objectif de cette réunion :

Leur présenter la situation (DMZR vs As Code).

Leur expliquer pourquoi on préconise un cluster dédié (pour éviter les impacts de maintenance et séparer la facturation) plutôt que mutualisé.

Leur communiquer le planning de disponibilité des offres BP2I (qu'on aura plus précisément en janvier).

2. Vérifier la faisabilité technique ("Mini POC" / Étude)

La demande : Il faut s'assurer que la stack technique de PIMS peut tourner sur la DMZR As Code ou s'il faut une solution hybride.

Détails techniques :

Le point bloquant potentiel est Kafka. Il n'est pas sûr que "Kafka As Code" soit prêt.

Je dois vérifier (avec les architectes ou via un test) si on peut faire une hybridation : L'application PIMS sur un cluster As Code (ROKS) qui communique avec le Kafka existant sur la DMZR classique (Event Streams).

Il faut valider les ouvertures de flux nécessaires pour cela.

3. Boucler la stack technique avec Andres Rincon

La demande : Hussein a demandé de "reboucler les stacks techniques" avec Andres.

Action : Je dois confirmer avec Andres de quoi PIMS a besoin exactement et regarder si c'est disponible dans le catalogue DMZR As Code actuel ou à venir proche.

En résumé
Je dois sortir de cette réunion et envoyer une invitation pour un point de situation avec Andres Rincon et Danilo, tout en préparant les arguments techniques sur la faisabilité d'une architecture hybride (App sur As Code / Data sur Legacy) pour sécuriser le planning du projet PIMS.

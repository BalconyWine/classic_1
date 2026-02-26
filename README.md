Bonjour l'équipe,

Suite à notre revue interne de la gestion des incidents sur les quatre derniers mois, nous avons analysé la nature et le volume des tickets qui parviennent actuellement à notre équipe concernant l'environnement SaaS.

Comme vous pouvez le constater sur la capture d'écran ci-dessous, le volume d'incidents générés par SaaS est massif et disproportionné par rapport à l'ensemble de nos autres projets.

[Insérer la capture d'écran du graphique des incidents ici - "la tour d'incidents"]

Pour réduire ce bruit inutile et nous concentrer sur les véritables enjeux de stabilité, nous avons identifié des axes d'amélioration et proposons les actions suivantes :

1. Alertes d'espace disque et de lenteur (Infrastructure)
Constat : Nous recevons un volume très important d'incidents automatisés concernant l'espace disque et des lenteurs ("slow disk").

Cause racine : Lors de nos investigations, nous avons trouvé des fichiers datant de plus de 12 ans, dont certains dépassent les 15 Go. Ces fichiers historiques sont l'une des causes principales des ralentissements de l'application et des disques, ce qui déclenche ces incidents à répétition.

Action entreprise : Nous avons temporairement désactivé certaines de ces alertes automatiques pour réduire les faux positifs.

Action requise de votre côté : Nous avons besoin que votre équipe revoie ces anciens fichiers au plus vite. Merci de vérifier lesquels sont encore pertinents pour le métier et lesquels peuvent être supprimés définitivement. Cette purge est nécessaire pour stabiliser les performances du disque et de l'application.

2. Incidents Control-M et CFT (Applicatif)
Constat : Nous recevons fréquemment des incidents automatisés concernant les jobs Control-M et les transferts CFT.

Observation : Il s'agit en grande majorité de problèmes applicatifs (par exemple, des systèmes de fichiers bloqués par des chargements massifs de bases de données, ou des scripts nécessitant une simple relance) et non de pannes d'infrastructure.

Proposition : Nous proposons de modifier le routage de ces incidents afin qu'ils soient assignés directement à l'équipe de support applicatif (l'équipe de Jawad / Data.ai). Étant donné que la résolution de ces tickets nécessite souvent de valider la logique applicative ou les flux métiers, il est beaucoup plus pertinent et efficace que votre équipe les reçoive en premier niveau.

Prochaines étapes
Nettoyage des fichiers : Pouvez-vous nous indiquer quand vous serez en mesure d'analyser et de purger les fichiers obsolètes de plus de 15 Go ?

Validation du routage : Merci de nous confirmer votre accord pour rediriger les incidents Control-M/CFT directement vers votre groupe de support.

Nous restons à votre disposition pour en discuter.

Cordialement,




Bonjour l'équipe,

Suite à notre revue interne de la gestion des incidents sur les quatre derniers mois, nous avons analysé la nature et le volume des tickets qui parviennent actuellement à notre équipe concernant l'environnement SaaS.

Comme vous pouvez le constater sur la capture d'écran ci-dessous, le volume d'incidents générés par SaaS est massif et disproportionné par rapport à l'ensemble de nos autres projets.

[Insérer la capture d'écran du graphique des incidents ici - "la tour d'incidents"]

Pour réduire ce bruit inutile et nous concentrer sur les véritables enjeux de stabilité, nous avons identifié des axes d'amélioration et proposons les actions suivantes :

1. Alertes d'espace disque et de lenteur (Infrastructure)
Constat : Nous recevons un volume très important d'incidents automatisés concernant l'espace disque et des lenteurs ("slow disk").

Cause racine : Lors de nos investigations, nous avons trouvé des fichiers datant de plus de 12 ans, dont certains dépassent les 15 Go. Ces fichiers historiques sont l'une des causes principales des ralentissements de l'application et des disques, ce qui déclenche ces incidents à répétition.

Action entreprise : Nous avons temporairement désactivé certaines de ces alertes automatiques pour réduire les faux positifs.

Action requise de votre côté : Nous avons besoin que votre équipe revoie ces anciens fichiers au plus vite. Merci de vérifier lesquels sont encore pertinents pour le métier et lesquels peuvent être supprimés définitivement. Cette purge est nécessaire pour stabiliser les performances du disque et de l'application.

2. Incidents Control-M et CFT (Applicatif)
Constat : Nous recevons fréquemment des incidents automatisés concernant les jobs Control-M et les transferts CFT.

Observation : Il s'agit en grande majorité de problèmes applicatifs (par exemple, des systèmes de fichiers bloqués par des chargements massifs de bases de données, ou des scripts nécessitant une simple relance) et non de pannes d'infrastructure.

Proposition : Nous proposons de modifier le routage de ces incidents afin qu'ils soient assignés directement à l'équipe de support applicatif (l'équipe de Jawad / Data.ai). Étant donné que la résolution de ces tickets nécessite souvent de valider la logique applicative ou les flux métiers, il est beaucoup plus pertinent et efficace que votre équipe les reçoive en premier niveau.

Prochaines étapes
Nettoyage des fichiers : Pouvez-vous nous indiquer quand vous serez en mesure d'analyser et de purger les fichiers obsolètes de plus de 15 Go ?

Validation du routage : Merci de nous confirmer votre accord pour rediriger les incidents Control-M/CFT directement vers votre groupe de support.

Nous restons à votre disposition pour en discuter.

Cordialement,

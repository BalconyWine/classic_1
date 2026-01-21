Salut Nicolas,

J'ai tout repris un par un comme tu m'as demandé, en checkant les serveurs et les pods exacts. C'est assez flagrant. En gros ils ont fermé les yeux alors que le problème a complètement changé de nature en Janvier.

Voila l'analyse complète ticket par ticket :

1. Novembre & Décembre : La "Fausse Piste" (CPU)

INC13208331 (13 Nov) & INC13360527 (30 Nov)

Le souci : C'était purement de la charge CPU sur les noeuds workeruat3 et workeruat2.

Les Pods : C'est toujours le pod sugar-connector qui plantait.

Action : Ils ont fermé en "Corrigé sans action".

Mon avis : Jusque là ok, c'est du resizing, c'est pas critique.

2. Mi-Décembre : Les premiers signes de fatigue

INC13479691 (14 Déc)

Le changement : Toujours sur workeruat3, mais la on commence a voir des OOM Kills (crash mémoire) sur un autre pod : event-capture-consumer.

Action : Encore fermé en "Corrigé sans action" le 29/12. Ils ont juste restart le truc.

3. Le 4 Janvier : L'erreur fatale (INC13606812) C'est là que ca n'a plus rien a voir et qu'ils ont merdé.

Serveurs différents : On est plus sur les workeruat du cluster. Là c'est le host saos101ws32t qui hurle que son disque /opt est vide (<3%).

Nouveau problème : Alerte Certificat SSL sur saos101ea01t qui expire le 13/01.

Pods impactés : C'est plus sugar-connector, c'est sunsystem-api, openshift-ext qui sont bloqués.

L'erreur : Ils ont vu "Incident Récurrent", ils ont cru que c'etait encore le CPU qui faisait des siennes. Ils ont fermé le ticket le 15 janvier (apres l'expiration !) sans rien faire.

4. Aujourd'hui (INC13665007) C'est la conséquence directe du raté du 4 janvier.

Le disque du SQL Server a fini par taper le 100% (0 octet).

Le certif a expiré, et mnt on a ms-descriptions et meli-api qui crash en boucle.

En résumé : Ils ont traité une alerte Disque/Certificat critique de Janvier comme si c'était le bug CPU bénin de Novembre juste parce que c'était dans la meme chaine de tickets. C'est ca la root cause.

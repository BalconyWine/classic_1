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





Salut Nicolas,

J'ai creusé tout l'historique des tickets liés au crash. C'est assez clair : ce n'est pas un incident isolé, c'est une accumulation de ratés depuis 3 mois. En gros, l'équipe s'est habituée aux fausses alertes et a fini par ignorer les vrais signaux d'alarme en Janvier.

Voici l'analyse complète, incident par incident, pour comprendre comment on en est arrivé là :

1. Novembre & Décembre : L'accoutumance (La fausse piste)

INC13208331 (13 Nov) & INC13360527 (30 Nov)

Le problème : C'était purement de la charge CPU sur les nœuds du cluster (workeruat3, workeruat2).

Les Pods : C'était le pod sugar-connector qui restait coincé.

L'action : Ils ont fermé les tickets en "Corrigé sans action".

Analyse : Jusque-là ok, c'était des pics de charge qui passaient tout seul. Mais ca leur a donné la mauvaise habitude de pas investiguer.

2. Mi-Décembre : Les premiers craquements

INC13479691 (14 Déc)

L'évolution : Toujours sur workeruat3, mais là on commence à voir des OOM Kills (crashs mémoire) sur un autre pod : event-capture-consumer.

L'action : Encore fermé en "Corrigé sans action" le 29/12. Ils ont surement juste restart le pod sans regarder la root cause.

3. Le 4 Janvier : L'erreur critique (INC13606812) C'est LA que ca a basculé. Le ticket s'est ouvert comme "récurrent" mais les alertes n'avaient plus rien à voir avec le CPU.

Serveurs impactés : On change de cible. C'est le host saos101ws32t qui alerte que son disque /opt est vide (< 3%).

Sécurité : Alerte explicite sur le Certificat SSL de saos101ea01t qui expire le 13/14 Janvier.

Le raté : Ils ont vu "Incident Récurrent", ils ont cru que c'était encore du bruit. Ils ont fermé le ticket le 15 Janvier (donc après l'expiration !) sans aucune action.

4. Aujourd'hui : Le Crash (INC13665007) C'est mathématique, c'est la suite du ticket du 4 Janvier.

Le disque du SQL Server a fini par taper les 100% (0 octet libre).

Le certificat a expiré, coupant les flux.

Résultat : ms-descriptions et meli-api crash en boucle par manque de ressources.

Conclusion : On a traité une alerte Disque/Certificat critique de Janvier comme si c'était le bug CPU bénin de Novembre, juste parce qu'ils étaient liés dans ServiceNow. Faut vraiment leur dire de checker les logs quand le type d'alerte change, sinon ca va recommencer.

En résumé : Ils ont traité une alerte Disque/Certificat critique de Janvier comme si c'était le bug CPU bénin de Novembre juste parce que c'était dans la meme chaine de tickets. C'est ca la root cause.

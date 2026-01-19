Salut Nicolas,

J'ai fait le tour de l'INC13665007. Même si le ticket est clôturé, j'ai analysé les causes pour éviter que ça ne se reproduise comme c'est récurrent. Pour rappel, je n'ai pas d'accès direct à Dynatrace Americas ni aux serveurs, donc il faudra coordonner ces points avec les équipes concernées.

On a plusieurs blocages critiques qui se sont cumulés :

Stockage saturé : Le lecteur E: du SQL Server est monté à 100% avec 0 octet libre. Les partitions /opt des hosts saos101ea33t, QAI-WAS-9 (/opt/IBM) et saos101ws31t sont aussi saturées (sous les 3%).

Certificats SSL : Celui de saos101ea09t est expiré depuis le 13/01. Plus urgent encore : les certifs de saos101ws69t et saos101ea32t expirent aujourd'hui même.

C'est ce qui a provoqué la saturation de la RAM et les crashs en boucle (OOM kills) des pods ms-descriptions, meli-api et token-exchange, car ils ne pouvaient plus rien écrire ni communiquer.

Pour la suite : Il faudrait s'assurer que l'infra purge les logs et fichiers temporaires sur ces serveurs et que le réseau renouvelle les certifs SSL avant ce soir pour éviter une nouvelle coupure.

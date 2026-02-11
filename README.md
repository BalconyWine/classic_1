Salut Arnaud, j'espère que tu vas bien ! 👋

Je t'écris concernant le test synthetic Dynatrace pour Datafabric GUI en PROD, qui bloque actuellement en erreur "Connection timeout" en arrivant sur la page de connexion SESAME.

Pour t'expliquer rapidement : on a d'abord fait toutes les vérifications de notre côté (notamment l'ouverture des flux). Comme tout était bon, on a remonté la piste et on s'est rendu compte que le blocage venait de SESAME. J'ai donc contacté l'équipe SESAME (Pascal Dejean de la Batie et Sorel Mocto) , et on a fini par identifier le problème avec eux : l'authentification TOTP est actuellement exclue pour Datafabric sur leur console de PROD.

Pour que notre robot Dynatrace puisse s'authentifier, il faut simplement qu'on l'autorise. Comme c'est une modification de configuration en PROD, l'équipe SESAME a besoin d'un "Go" explicite du RA avant d'agir.

Est-ce que tu peux me donner ton feu vert en répondant simplement à ce message ? Je transmettrai ensuite ton accord à Marcio Cardoso (qui va gérer l'action côté SESAME) pour qu'il fasse la manipulation. C'est très rapide de leur côté, il faut juste compter une petite heure pour que la modification se propage.

Merci beaucoup pour ton aide ! 😄

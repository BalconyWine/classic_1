Bonjour Sorel,

Je te contacte de la part de Pascal Dejean de la Batie.

Je travaille actuellement sur un test synthetic dans Dynatrace pour l'URL Datafabric GUI (https://datafabric-gui-assurance.is.echonet / AUID 63215). Le test échoue actuellement en erreur "Connection timeout" (12014) lors de la redirection vers l'URL d'authentification SESAME Europe (europe-sesame-idp-assurance.is.echonet).

Afin que le synthetic puisse fonctionner, Pascal m'a conseillé de voir avec toi pour vérifier les points suivants :

Est-ce que sur ce Service Provider (Datafabric GUI ou AP63215), le TOTP est autorisé ou exclu en PROD sur SAF IDP SESAME FRANCE ? (L'objectif est que le TOTP ne soit pas exclu pour le SP urn:bnpparibas:cardif:COR:CTDF:AP9792:PROD afin que le script puisse atteindre la mire/l'UI d'authentification).

Est-ce que les permissions / rôles sont gérés dans SESAME France ou dans CTDF (Datafabric) ?

Pourrais-tu vérifier si dans le DA (Domaine Applicatif) "DATA_FABRIC", il y a des habilitations pour le SP urn:bnpparibas:cardif:COR:CTDF:AP9792:PROD ?

Il nous faudra également un compte de test avec 1 rôle dans SESAME (DA DATA_FABRIC) ou des autorisations fine grain dans Datafabrique pour finaliser le test.

Merci d'avance pour ton aide ! N'hésite pas si tu as besoin des logs d'erreur Dynatrace.

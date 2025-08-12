Objet : Récapitulatif PoC Kafka REST Proxy – Points confirmés et prochaines étapes

Bonjour,

Suite à l’échange avec l’architecte, voici le récapitulatif et les actions à mener pour le PoC :

Points confirmés

Chemin PoC choisi : REST sur HTTPS (pas de cross-net Kafka natif).
→ Utilisation de Kafka REST Proxy côté DMZR pour exposer les topics PIMS, puis relay vers Kafka on-prem LATAM.

Deux étapes réseau distinctes :

Ouverture de flux : ouvrir l’egress du segment DMZR vers l’extérieur (HTTPS 443).

Codage proxy : créer la règle sur le Business Proxy pour autoriser le namespace DMZR à appeler la destination en HTTPS. Validation par Sécurité/Cardif.

VPN non requis pour le PoC (trafic sortant en HTTPS via Business Proxy).

Apigee/Mashery hors périmètre pour ce PoC.

Localisation des composants :

DMZR = IBM Cloud Event Streams + pods UI/Backend

LATAM = Kafka on-prem + composant de relay (Camel sur Connect ou petit service)

Flux de bout en bout (PoC)
DMZR Kafka (topics PIMS) → Kafka REST Proxy (DMZR) → HTTPS 443 via Business Proxy → Relay côté LATAM (Camel HTTP Sink ou petit consumer REST) → Kafka on-prem LATAM.

Actions immédiates

Vérifier/Activer le REST Proxy sur DMZR (IBM Event Streams) et récupérer l’endpoint public HTTPS + méthode d’authentification.

Demander l’ouverture de flux (egress HTTPS 443) pour le namespace DMZR → Business Proxy. Vérifier la portée si déjà ouvert.

Soumettre le codage proxy à la Sécurité/Cardif (namespace, CIDRs source, FQDN, port 443, justification “Kafka PoC”).

Choisir le relay côté LATAM :

Préférence : Camel HTTP Sink sur Kafka Connect.

Alternative : service Spring Boot/Camel recevant des POST et produisant vers Kafka LATAM.

Créer un plan de test minimal : un topic, petite charge, mesures latence/débit.

Points à confirmer

Qui active le REST Proxy et fournit URL/API key sur notre abonnement DMZR.

Namespace DMZR retenu (sandbox existant ou nouveau) et ouverture egress si besoin.

Disponibilité du plugin Camel HTTP Sink sur Connect côté LATAM.

Paramètres Kafka LATAM (host/port, TLS/SASL, credentials).

Personnes à impliquer

Sécurité/Cardif (validation codage proxy – équipe Nicolas Robin).

Réseau (vérification ouverture egress namespace DMZR).

Merci de votre retour pour avancer rapidement.

Veux que je te prépare aussi la version “message Teams en plusieurs bulles” pour balancer ça en conversation directe sans l’effet pavé de texte ? Ça évite que les gens décrochent au 2e paragraphe.









Ask ChatGPT






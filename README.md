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









Objet : Récapitulatif PoC Kafka REST Proxy – Synthèse et prochaines étapes

Bonjour [Prénom Manager],

Suite à l’échange avec [Prénom Architecte], voici la synthèse du PoC Kafka REST Proxy et les actions identifiées.
J’ai mis [Prénom Architecte] en copie pour que nous soyons alignés sur la compréhension et la suite.

Points confirmés

Chemin PoC : REST sur HTTPS (pas de cross-net Kafka natif).
→ Utilisation de Kafka REST Proxy côté DMZR pour exposer les topics PIMS, puis relay vers Kafka on-prem LATAM.

Deux étapes réseau distinctes :

Ouverture de flux : egress du segment DMZR vers l’extérieur (HTTPS 443).

Codage proxy : règle Business Proxy pour autoriser le namespace DMZR à appeler la destination HTTPS (validation par Sécurité/Cardif).

VPN non requis pour le PoC (trafic sortant via Business Proxy).

Apigee/Mashery hors périmètre.

Localisation :

DMZR = IBM Cloud Event Streams + pods UI/Backend

LATAM = Kafka on-prem + composant de relay (Camel sur Connect ou petit service)

Flux de bout en bout (PoC)
DMZR Kafka (topics PIMS) → Kafka REST Proxy (DMZR) → HTTPS 443 via Business Proxy → Relay LATAM (Camel HTTP Sink ou petit consumer REST) → Kafka on-prem LATAM.

Actions immédiates

Vérifier/activer REST Proxy sur DMZR (endpoint public HTTPS + auth).

Demander ouverture de flux (egress HTTPS 443) DMZR → Business Proxy.

Soumettre codage proxy (namespace, CIDRs source, FQDN, port 443, justification “Kafka PoC”).

Choisir relay LATAM :

Préférence : Camel HTTP Sink sur Kafka Connect

Alternative : service Spring Boot/Camel

Créer plan de test minimal (1 topic, petite charge, mesures latence/débit).

Points à confirmer

Activation REST Proxy (qui le fait et fournit URL/API key).

Namespace DMZR retenu et ouverture egress si nouveau.

Disponibilité Camel HTTP Sink sur Connect LATAM.

Paramètres Kafka LATAM (host/port, TLS/SASL, credentials).

Interlocuteurs clés

Sécurité/Cardif (validation codage proxy – équipe Nicolas Robin).

Réseau (vérification ouverture egress DMZR).

Si besoin, je peux organiser un point rapide pour valider ces étapes et verrouiller la mise en œuvre.

Cordialement,
[Ta signature]

Si tu veux, je peux aussi te faire la version condensée en 4 lignes que tu balances dans un chat Teams juste après l’email, pour que ton manager le lise vraiment.















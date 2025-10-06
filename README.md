
Message 1 (ouverture, friendly)

Salut 👋, petite question sur Dynatrace :
Le synthetic monitor [AP27488] API STORE CARDIF déclenche bien des problèmes, mais ils passent toujours par le profil d’alerte Default au lieu de notre profil AP27488-CARDIF-API-STORE.
Vous savez pourquoi ?

👉 Message 2 (avec observation)

On a vérifié : le monitor n’a pas l’air rattaché à la management zone CARDIF – APXXXXX – Synthetic.
Du coup notre profil d’alerte spécifique n’est jamais appliqué 🤔

👉 Message 3 (proposition claire)

Est-ce que vous pouvez checker/ajouter une règle dans la management zone pour inclure ce synthetic (il a déjà le tag AP27488_Health_Check) ?
Ça devrait forcer Dynatrace à utiliser le bon profil d’alerte.

👉 Message 4 (avec pièces jointes)

Je mets 2 captures pour contexte 📎 :

1 problème qui part sur Default

le profil d’alerte où on voit bien les tags configurés

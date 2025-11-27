Bonjour Arnaud,
Comme suite à nos échanges sur Teams, je te transfère ci-dessous le mail de Mouhamed Rassoul concernant les coûts des clusters Elasticsearch de la CTDF.
Pour résumer le contexte : l'équipe FinOps a relevé que ces clusters hors-prod sont en mode "enterprise" (non mutualisés), ce qui engendre un coût d'environ 1800 €/mois, contre 200 € à 600 € pour les clusters standards.
Il s'agit potentiellement de ressources créées pour un ancien POC (d'après mes recherches sur Confluence).
Les clusters concernés sont :
es002i000617
es002i000666
Si ces environnements sont peu utilisés ou obsolètes, il faudrait voir si on peut les réduire (downscale) ou les décommissionner.
Cordialement,

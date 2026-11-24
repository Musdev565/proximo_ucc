# 08 — Questions tranchées et points encore ouverts

## Tranchées par l'auteur [DÉCIDÉ]
1. **Livraison** : toujours par le vendeur, à l'auditoire.
2. **Horaires** : commandes ouvertes dès le matin, **fermées à 15h30** ; remise à zéro à 16h30.
3. **Frais/commission** : application **gratuite pour le moment** (extension payante future : voir `09`).
4. **Images** : bucket S3 gratuit, hors serveur ; back-end sur Render.
5. **Validation des vendeurs** : aucune ; compte unique, bouton « Je veux vendre ».
6. **Nom** : **Proximo UCC**.
7. **Étudiant absent** : commande annulée par le vendeur dans l'app, réservation libérée.

## Encore ouverts [À DÉFINIR]
1. **Plan des auditoires** : données provisoires dans `data/auditoires.json`, à corriger lors d'une descente sur place (noms, promotions, salles présentes par niveau, RDC/sous-sol, salle en face de l'amphi).
2. **Limites actuelles de Render et de l'offre gratuite S3** : à vérifier avant de coder le déploiement.
3. **Notifications** : polling au début ; push/WebSocket plus tard ?
4. **Abus** : que faire d'un vendeur qui annule trop, ou d'un étudiant qui commande sans être là
   (limites, signalement, suspension) ? À décider après le test terrain.
5. **Précommande** : un étudiant peut-il choisir pour quelle pause il commande (10h, 11h, midi) ?

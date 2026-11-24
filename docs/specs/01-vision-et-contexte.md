# 01 — Vision et contexte

## Le problème [DÉCIDÉ]
À l'UCC, pendant la pause, des étudiants entrepreneurs vendent des produits (biscuits, samoussas,
gaufres, yaourts…) en passant d'auditoire en auditoire. Limites actuelles :
- Un étudiant intéressé un jour ne sait pas comment recontacter le vendeur le lendemain.
- Il ne sait pas si le vendeur est venu à la fac ce jour-là, ni s'il a de la marchandise.
- Le vendeur peut repartir chez lui avec sa marchandise alors que quelqu'un en voulait.
- Les vendeurs ne connaissent pas tous les auditoires de la fac (« ici c'est quel auditoire ? »).

## La solution [DÉCIDÉ]
Une application permettant à l'étudiant de **commander depuis son auditoire** auprès des vendeurs
présents ce jour-là. Le vendeur voit les commandes **groupées par auditoire** et vient les livrer.
Un **plan 2D des auditoires** aide le vendeur à localiser l'auditoire de chaque commande.

## Utilisateurs
**[DÉCIDÉ] Compte unique** : une même personne a un seul compte. Par défaut elle peut **acheter**.
Via le menu **« Je veux vendre »** (créer ma boutique : nom, image, produits), elle devient aussi
**vendeur**. N'importe qui peut s'inscrire et vendre (pas de validation préalable pour l'instant).
Les rôles ci-dessous sont des **modes d'usage** d'un même compte.

- **Étudiant (acheteur)** : consulte les vendeurs/produits du jour, commande, suit sa commande.
- **Vendeur (étudiant entrepreneur)** : déclare sa présence et son stock du jour, reçoit les commandes,
  livre, confirme le paiement cash.
- **Administrateur** (optionnel, plus tard) : gère les comptes vendeurs, les auditoires.

## Périmètre géographique
Un seul bâtiment : l'UCC. 3 niveaux contenant des auditoires (le sous-sol n'en contient pas, ignoré).

## Modèle économique [DÉCIDÉ]
L'application est **gratuite pour le moment**. Une extension future (vitrine de services payante)
est décrite dans `09-vision-future-services.md` ; elle est **hors périmètre actuel**.

## Concurrent principal [RECOMMANDÉ de garder en tête]
WhatsApp (groupes, statuts). Proximo doit être **plus simple et plus fiable** que ça :
disponibilité du jour claire, commande en 2 taps, regroupement par auditoire.

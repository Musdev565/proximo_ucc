# 02 — Règles métier

## Catalogue et disponibilité du jour
- **[RECOMMANDÉ, accepté par l'auteur]** Le vendeur garde un **catalogue permanent** de ses produits
  (nom, photo, prix). Chaque jour il indique : « Je suis là aujourd'hui » et, pour chaque produit,
  la **quantité apportée**.
- **[DÉCIDÉ]** La disponibilité du jour est **remise à zéro à 16h30** (fin des cours). Le lendemain,
  le vendeur doit redéclarer sa présence et ses quantités. Le catalogue, lui, n'est pas effacé.
- Un vendeur sans déclaration du jour n'apparaît pas aux étudiants.

## Horaires [DÉCIDÉ]
- Cours de 8h30 à 16h30 ; pauses à **10h** et **11h**, fin de la pause de midi à **14h**.
- **Les commandes sont ouvertes dès le matin** (précommande possible avant les pauses) et
  **se ferment à 15h30** : aucune nouvelle commande après. Des étudiants restent souvent sans cours
  l'après-midi, on peut donc encore leur livrer.
- Remise à zéro des disponibilités du jour : **16h30** (inchangé).
- Fuseau horaire : Africa/Kinshasa. Les heures (ouverture, fermeture 15h30, remise à zéro 16h30)
  doivent être **configurables**, pas codées en dur.

## Livraison [DÉCIDÉ]
- **C'est toujours le vendeur qui apporte la commande** à l'auditoire. Pas de retrait par l'étudiant.

## Paiement [DÉCIDÉ]
- **Cash à la livraison uniquement** (pas de mobile money pour l'instant).

## Stock [DÉCIDÉ + RECOMMANDÉ]
- **[DÉCIDÉ]** Le **stock réel ne diminue que lorsque le paiement cash est confirmé**.
  Une simple commande ne fait pas baisser le stock, car le client peut refuser à l'arrivée du vendeur.
- **[RECOMMANDÉ]** Pour éviter la survente, deux compteurs par produit et par jour :
  - `quantite_stock` : ce que le vendeur possède réellement
  - `quantite_reservee` : somme des quantités des commandes `EN_ATTENTE`
  - **Disponible affiché** = `quantite_stock − quantite_reservee`
- Une commande n'est acceptée que si la quantité demandée ≤ disponible.
- Annulation / refus / expiration : `quantite_reservee` est libérée, `quantite_stock` inchangé.
- Paiement confirmé : `quantite_stock` diminue ET `quantite_reservee` diminue de la même quantité.

## Cycle de vie d'une commande
```
EN_ATTENTE ──(vendeur livre + confirme le cash)──► LIVREE_PAYEE
EN_ATTENTE ──(client refuse / absent / vendeur annule)──► ANNULEE
EN_ATTENTE ──(16h30 atteint sans livraison)──► EXPIREE
```
- Seul le **vendeur** confirme le paiement (bouton « Payé »).
- **[DÉCIDÉ] Étudiant absent** : si l'étudiant n'est plus dans l'auditoire à l'arrivée du vendeur,
  **le vendeur annule la commande depuis l'application**. La quantité réservée est libérée.
  Enregistrer un **motif d'annulation** (`CLIENT_ABSENT`, `REFUS_CLIENT`, `VENDEUR_INDISPONIBLE`, `AUTRE`).
- Les transitions invalides doivent être **refusées** par le back-end (machine à états).
- Toute transition est **historisée** (date, auteur) pour la traçabilité.

## Regroupement par auditoire
- Chaque commande indique l'**auditoire de livraison** (par défaut celui de l'étudiant, modifiable).
- Le vendeur voit ses commandes en attente **groupées par auditoire**, triées par niveau puis position,
  pour faciliter son parcours.

## Concurrence [RECOMMANDÉ]
Deux étudiants peuvent commander le dernier produit en même temps. Le back-end doit garantir
qu'on ne dépasse jamais le disponible (voir `03-architecture-technique.md`).

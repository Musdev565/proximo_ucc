# 04 — Modèle de données (version de départ, à affiner)

## Principe [DÉCIDÉ]
**Un seul compte** par personne. Pas de table « Vendeur » séparée : une personne devient vendeur en
créant une **Boutique**.

## Entités
- **Utilisateur** : id, nom, email ou téléphone, mot de passe (haché), `auditoire_defaut_id`, date de création, rôle `USER` ou `ADMIN`
- **Boutique** (créée via « Je veux vendre ») : id, `proprietaire_id` (Utilisateur), nom, image_url, description courte, actif.
  Un utilisateur peut avoir une boutique (1—1 au départ).
- **Produit** (catalogue permanent) : id, `boutique_id`, nom, prix, photo_url, actif
- **DisponibiliteJour** : id, `produit_id`, date, `quantite_stock`, `quantite_reservee`, `version` (concurrence).
  Unicité (`produit_id`, `date`).
- **PresenceBoutique** : id, `boutique_id`, date, present (booléen). Unicité (`boutique_id`, `date`).
- **Auditoire** : id, code, nom, promotion, `niveau` (1–3), `position_ordre`, coordonnées du plan 2D
  (voir `06-carte-auditoires.md`)
- **Commande** : id, `acheteur_id` (Utilisateur), `boutique_id`, `auditoire_id`, statut, `motif_annulation`, total, date_creation, date_maj
- **LigneCommande** : id, `commande_id`, `produit_id`, quantite, prix_unitaire (copié au moment de la commande)
- **HistoriqueStatut** : id, `commande_id`, ancien_statut, nouveau_statut, date, auteur
- **Parametres** (ou fichier de config) : heure_ouverture, heure_fermeture_commandes (15h30), heure_reset (16h30)

## Relations (résumé)
- Utilisateur 1—0..1 Boutique ; Boutique 1—N Produit ; Produit 1—N DisponibiliteJour
- Utilisateur (acheteur) 1—N Commande ; Boutique 1—N Commande ; Commande 1—N LigneCommande
- Auditoire 1—N Commande ; Auditoire 1—N Utilisateur (auditoire par défaut)
- Règle : un utilisateur ne peut pas commander dans sa propre boutique.

## Règles d'intégrité
- `quantite_reservee ≥ 0`, `quantite_stock ≥ 0`, `quantite_reservee ≤ quantite_stock` à tout moment.
- Le prix d'une ligne est **figé** à la création (un changement de prix ne modifie pas les anciennes commandes).
- Un produit désactivé reste en base (historique).
- Une commande ne peut être créée qu'avant l'heure de fermeture (15h30).

# 09 — Vision future : vitrine de services (HORS MVP)

> **Ne pas implémenter maintenant.** Ce fichier sert uniquement à ne pas bloquer cette évolution
> dans l'architecture (compte unique, boutique extensible).

## Idée [DÉCIDÉ comme vision, pas comme périmètre actuel]
Des étudiants proposent des **prestations de services** hors fac (pose d'ongles, coiffure, tresses…).
Proximo devient une **vitrine** : ils y montrent leur travail ; les étudiants déjà présents sur la
plateforme sont des clients potentiels.

## Modèle économique envisagé
- Afficher ses services est **payant** : **1 500 FC/mois** pendant les **3 premiers mois** du lancement
  de la fonctionnalité, puis **3 000 FC/mois**.
- Paiement par **Mobile Money**.
- Plus tard : **réservations** (rendez-vous) pour ces services.

## Conséquences d'architecture [RECOMMANDÉ]
- Garder le **compte unique** : le même compte peut acheter, vendre des produits, et plus tard proposer des services.
- Prévoir une entité **Service** distincte de **Produit** (pas de stock, mais des photos, tarifs, disponibilités).
- Prévoir une entité **Abonnement** (période, montant, statut) quand ce module sera développé.
- L'intégration Mobile Money (agrégateur, vérification de paiement) est un chantier à part : à étudier
  seulement au moment de lancer cette fonctionnalité.

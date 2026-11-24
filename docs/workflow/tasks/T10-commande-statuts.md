# T10 — Payer / annuler, historique, vues par auditoire

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/02-regles-metier.md (cycle de vie)`
- `docs/specs/10-api-rest.md (Commandes)`

## Objectif
Faire vivre une commande : paiement cash confirmé par le vendeur, annulation, historique.

## À faire
1. `POST /api/orders/{id}/pay` (vendeur propriétaire seulement) : `PENDING → DELIVERED_PAID` ; `stock -= quantité` **et** `reserved -= quantité`, dans une transaction avec verrouillage.
2. `POST /api/orders/{id}/cancel` : le vendeur avec `reason` obligatoire (`CUSTOMER_ABSENT`, `CUSTOMER_REFUSED`, `SELLER_UNAVAILABLE`, `OTHER`) ; l'acheteur seulement si `PENDING` (motif `OTHER`/implicite). `reserved -= quantité`, stock inchangé.
3. Transitions invalides (ex. payer une commande annulée) → 409. Chaque transition écrit une ligne dans `order_status_history` (ancien, nouveau, date, auteur).
4. `GET /api/orders/mine`, `GET /api/orders/{id}` (acheteur ou vendeur concerné seulement), `GET /api/shops/me/orders?status=` : **groupées par auditoire**, triées par niveau puis position.
5. Tests : chaque transition valide/invalide, droits (un tiers = 403/404), cohérence des quantités avant/après, historique.

## Hors périmètre — ne fais PAS
- Expiration automatique (T11). Aucun paiement en ligne.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Payer baisse le stock et le réservé du même montant ; annuler ne baisse que le réservé.
- [ ] Un vendeur ne peut agir que sur les commandes de sa boutique.
- [ ] La liste vendeur est groupée par auditoire dans l'ordre niveau puis position.

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T10** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T10: paiement, annulation, historique et vue vendeur par auditoire`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

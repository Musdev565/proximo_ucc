# T09 — Créer une commande (réservation + concurrence)

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/02-regles-metier.md (tout)`
- `docs/specs/03-architecture-technique.md (concurrence)`
- `docs/specs/10-api-rest.md (Commandes)`

## Objectif
Créer une commande qui réserve le stock sans jamais survendre, même en parallèle.

## À faire
1. `POST /api/orders` `{shopId, roomId, items[]}`. Dans **une transaction** : vérifier la fenêtre horaire (ouverte dès le matin, **fermée à 15h30** : erreur 409 `ORDERS_CLOSED`), boutique présente aujourd'hui, produits actifs de cette boutique, pas sa propre boutique.
2. Verrouiller les lignes `daily_availability` concernées avec `findForUpdate` (ordre fixe par `product_id`) ; refuser si `quantité > disponible` (409 `STOCK_INSUFFICIENT`) ; sinon `reserved += quantité`.
3. Créer `Order` (`PENDING`), `OrderLine` (prix figé au moment de la commande), entrée d'historique. **Le stock réel ne bouge pas.**
4. Calculer le total. `roomId` par défaut = auditoire par défaut de l'utilisateur ; un `roomId` valide est obligatoire.
5. **Test de concurrence** : 20 threads commandent en même temps les 5 dernières unités → au plus 5 unités réservées au total, aucune survente, aucune exception de verrou non gérée.
6. Tests : hors horaires (avec `Clock` simulé), boutique absente, stock insuffisant, propre boutique, prix figé.

## Hors périmètre — ne fais PAS
- Payer/annuler (T10). Expiration (T11). Notifications.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Le test de concurrence passe de façon répétable (le lancer 5 fois).
- [ ] `reserved <= stock` n'est jamais violé.
- [ ] Une commande refusée ne modifie aucune quantité.

## Vérification
cd backend && ./mvnw test (lancer le test de concurrence plusieurs fois)

## À la fin (obligatoire)
1. Cocher **T09** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T09: création de commande avec réservation anti-survente`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

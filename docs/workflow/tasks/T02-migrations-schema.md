# T02 — Migrations Flyway : schéma de base de données

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/04-modele-de-donnees.md`
- `docs/specs/02-regles-metier.md`
- `docs/specs/11-conventions-code.md (glossaire)`

## Objectif
Créer le schéma complet via Flyway, avec les contraintes d'intégrité en base.

## À faire
1. Migration `V1__init_schema.sql` : tables `app_user`, `shop`, `product`, `shop_presence`, `daily_availability`, `lecture_room`, `map_feature`, `app_order`, `order_line`, `order_status_history`.
2. `lecture_room` : code unique, name (NULL permis), promotion (NULL permis), type (`AMPHITHEATER`/`CLASSROOM`), level (1–3), position_order, wing, access_hint, bounds (x, y, width, depth), verified (bool). `map_feature` : code, type (`STAIRS`/`CENTRAL_VOID`), level, bounds, has_guardrail.
3. Contraintes : `CHECK (stock_quantity >= 0)`, `CHECK (reserved_quantity >= 0)`, `CHECK (reserved_quantity <= stock_quantity)` ; unicité (`product_id`, `date`) sur `daily_availability` ; unicité (`shop_id`, `date`) sur `shop_presence` ; un utilisateur = au plus une boutique ; email unique.
4. Prix et montants en `BIGINT` (FC). Statuts de commande en `VARCHAR` avec `CHECK` (`PENDING`, `DELIVERED_PAID`, `CANCELLED`, `EXPIRED`).
5. Index utiles : commandes par boutique+statut, par acheteur, `daily_availability` par date.
6. Un test d'intégration qui applique les migrations sur PostgreSQL (Testcontainers) et vérifie que les contraintes CHECK rejettent les valeurs invalides.

## Hors périmètre — ne fais PAS
- Entités JPA et repositories (T03). Données de seed des auditoires (T08).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Flyway applique V1 sans erreur sur une base vide.
- [ ] Le test d'intégration prouve qu'on ne peut pas insérer un stock négatif ni `reserved > stock`.
- [ ] Aucune table en dehors de celles listées.

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T02** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T02: schéma de base de données (Flyway V1) + tests de contraintes`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

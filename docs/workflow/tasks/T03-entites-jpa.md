# T03 — Entités JPA, enums, repositories

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/04-modele-de-donnees.md`
- `docs/specs/11-conventions-code.md`
- `docs/specs/03-architecture-technique.md (concurrence)`

## Objectif
Mapper le schéma en entités JPA et fournir les repositories, dont la lecture verrouillée du stock.

## À faire
1. Entités et enums selon le glossaire (`OrderStatus`, `CancelReason`, `RoomType`, `MapFeatureType`).
2. `DailyAvailability` : champ `@Version` + méthode de repository `findForUpdate(productIds, date)` avec `@Lock(PESSIMISTIC_WRITE)` triée par `product_id`.
3. Repositories Spring Data pour chaque entité, avec seulement les requêtes dont les tâches suivantes ont besoin (sinon laisse-les simples).
4. Tests `@DataJpaTest` (PostgreSQL Testcontainers) : sauvegarde/relecture de chaque entité ; la contrainte `reserved <= stock` remonte bien en exception.

## Hors périmètre — ne fais PAS
- Services, contrôleurs, DTO (tâches suivantes).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Toutes les entités se sauvegardent et se relisent dans les tests.
- [ ] `findForUpdate` existe et est couvert par un test qui vérifie l'ordre des lignes.
- [ ] Le schéma Hibernate est cohérent avec Flyway (`ddl-auto=validate`).

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T03** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T03: entités JPA, enums et repositories (verrouillage pessimiste)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

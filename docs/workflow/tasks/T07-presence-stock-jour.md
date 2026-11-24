# T07 — Présence et quantités du jour (stock)

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/02-regles-metier.md (catalogue, stock)`
- `docs/specs/10-api-rest.md (Aujourd'hui)`
- `docs/specs/03-architecture-technique.md (précisions)`

## Objectif
Le vendeur déclare « je suis là aujourd'hui » et les quantités apportées ; les étudiants voient les boutiques présentes.

## À faire
1. `GET/PUT /api/shops/me/today`, `PUT /api/shops/me/today/products/{productId}`, `GET /api/shops/today`.
2. « Aujourd'hui » = date du jour via le `Clock` (Africa/Kinshasa). Les lignes sont créées pour cette date uniquement.
3. `disponible = stock − réservé`. Le stock ne peut pas être fixé sous la quantité déjà réservée (409).
4. `GET /api/shops/today` : boutiques présentes uniquement, produits actifs avec `disponible > 0`.
5. Tests avec un `Clock` fixé (changement de jour = repart de zéro, sans effacer le catalogue).

## Hors périmètre — ne fais PAS
- Création de commandes (T09). Remise à zéro planifiée (T11).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] La présence et les quantités s'enregistrent par date.
- [ ] Le lendemain (horloge simulée), la boutique n'apparaît plus tant qu'elle n'a pas redéclaré sa présence.
- [ ] Le stock ne peut pas descendre sous le réservé.

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T07** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T07: présence et quantités du jour`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

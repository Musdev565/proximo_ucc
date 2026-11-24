# T06 — Produits du catalogue

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/10-api-rest.md (Produits)`
- `docs/specs/02-regles-metier.md (catalogue)`

## Objectif
Le vendeur gère son catalogue permanent.

## À faire
1. `GET/POST /api/shops/me/products`, `PUT/DELETE /api/shops/me/products/{id}` (DELETE = `active=false`).
2. Prix entier > 0 (FC). `imageUrl` est un simple texte (l'upload viendra en T12).
3. Un vendeur ne voit/modifie que ses produits (404 sinon). Exiger d'avoir une boutique.
4. Tests : CRUD, propriété des produits, prix invalide, désactivation.

## Hors périmètre — ne fais PAS
- Quantités du jour (T07).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Toutes les routes fonctionnent et respectent la propriété.
- [ ] Un produit désactivé n'apparaît plus dans la liste active mais reste en base.

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T06** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T06: catalogue de produits de la boutique`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

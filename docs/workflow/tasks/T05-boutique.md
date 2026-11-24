# T05 — « Je veux vendre » : boutique

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/10-api-rest.md (Boutique)`
- `docs/specs/01-vision-et-contexte.md (compte unique)`

## Objectif
Un utilisateur connecté peut créer et gérer SA boutique.

## À faire
1. `POST /api/shops`, `GET /api/shops/me`, `PUT /api/shops/me`.
2. Un utilisateur a **au plus une** boutique (409 s'il en a déjà une). `GET /api/me` renvoie `shopId` quand elle existe.
3. Tests : création, doublon, lecture, modification, accès sans boutique (404 sur `/shops/me`).

## Hors périmètre — ne fais PAS
- Produits, présence, commandes.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Création/lecture/modification de ma boutique fonctionnent.
- [ ] Impossible d'en créer deux.
- [ ] Impossible de lire ou modifier la boutique d'un autre.

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T05** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T05: création et gestion de la boutique (Je veux vendre)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

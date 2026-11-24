# T13 — Squelette front, PWA, design minimaliste, client API

**Périmètre :** Front-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/05-ui-ux.md`
- `docs/specs/11-conventions-code.md (front)`
- `docs/specs/10-api-rest.md`

## Objectif
Un front React qui démarre, avec l'identité visuelle minimaliste et un client API prêt.

## À faire
1. Créer `frontend/` : Vite + React + TypeScript strict + Tailwind + React Router ; PWA minimale (manifest, icônes, service worker simple, installable).
2. Design : noir/blanc + une couleur d'accent, beaucoup d'espace, boutons plein largeur ; conçu pour **360 px**. Composants de base : `Button`, `Input`, `Card`, `Page`, `Spinner`, `ErrorMessage`.
3. Client API dans `src/api/` (base URL via `VITE_API_URL`, jeton `Authorization`, gestion 401 → déconnexion, format d'erreur de l'API).
4. Routes vides : `/connexion`, `/inscription`, `/`, `/vendre`, `/commandes`, `/plan`. Barre de navigation en bas.
5. Tests Vitest : rendu de l'application, client API (jeton ajouté, erreur 401).

## Hors périmètre — ne fais PAS
- Écrans fonctionnels (T14+). **Aucun composant 3D.**
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] `npm run dev` affiche l'application ; `npm run build` et `npm test` passent.
- [ ] Lighthouse « installable » fonctionne (PWA).
- [ ] Aucune dépendance 3D ni bibliothèque d'UI lourde.

## Vérification
cd frontend && npm test && npm run build

## À la fin (obligatoire)
1. Cocher **T13** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T13: squelette front React/Vite/Tailwind, PWA et client API`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

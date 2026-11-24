# T19 — Plan 2D des auditoires (SVG)

**Périmètre :** Front-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/06-carte-auditoires.md`
- `docs/specs/data/auditoires.json (structure)`
- `docs/specs/10-api-rest.md (Auditoires)`

## Objectif
Afficher le plan **en 2D** des niveaux et mettre en surbrillance un auditoire.

## À faire
1. Composant `LectureRoomMap` : **SVG 2D** généré depuis `GET /api/lecture-rooms` (utiliser `bounds` x, y, largeur, profondeur ; échelle adaptée à l'écran, `viewBox`).
2. Sélecteur de niveau (N1 / N2 / N3). Rectangles étiquetés (code, ou nom s'il existe) ; escaliers et vide central (avec garde-corps) dessinés ; palette : amphi violet, salle bleu, escalier ambre, vide gris.
3. Surbrillance de l'auditoire d'une commande ; à côté, toujours un **texte d'accès** (`accessHint`).
4. Intégration : bouton « Voir sur le plan » dans les commandes vendeur (T18) et page `/plan`.
5. Fonctionne avec `name = null` et `promotion = null` ; ajouter une salle en base l'affiche sans changer le code.
6. Tests : rendu du SVG pour un jeu de données, surbrillance, changement de niveau.

## Hors périmètre — ne fais PAS
- **TOUTE 3D** (three.js, WebGL, isométrique, canvas 3D) : strictement interdit. Pas d'édition du plan par l'utilisateur.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Le plan est un SVG 2D, lisible à 360 px, avec les 3 niveaux.
- [ ] La salle d'une commande est visible en surbrillance avec son texte d'accès.
- [ ] `package.json` ne contient aucune bibliothèque 3D.

## Vérification
cd frontend && npm test && npm run build ; vérifier `grep -i three package.json` (aucun résultat)

## À la fin (obligatoire)
1. Cocher **T19** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T19: plan 2D des auditoires en SVG`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

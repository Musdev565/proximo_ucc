# T08 — Auditoires : seed et API du plan

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/06-carte-auditoires.md`
- `docs/specs/data/auditoires.json`
- `docs/specs/10-api-rest.md (Auditoires)`

## Objectif
Charger les données PROVISOIRES du plan et les exposer pour le plan 2D.

## À faire
1. Copier `docs/specs/data/auditoires.json` dans `backend/src/main/resources/seed/` (sans modifier le fichier source).
2. Loader au démarrage : si `lecture_room` est vide, importer les salles/amphis dans `lecture_room` et les escaliers/vides dans `map_feature`. Idempotent (ne pas dupliquer).
3. `GET /api/lecture-rooms` : niveaux triés, avec pour chaque niveau les salles (code, name, promotion, type, wing, accessHint, bounds, position) et les éléments de plan (escaliers, vide central, garde-corps).
4. `name` et `promotion` peuvent être `null` : l'API les renvoie tels quels.
5. Tests : seed chargé une seule fois, structure de la réponse, tri par niveau.

## Hors périmètre — ne fais PAS
- Tout rendu graphique (front, T19). **Aucune 3D.** Ne pas coder les salles en dur dans le code Java.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Après démarrage sur base vide, l'API renvoie 3 niveaux avec leurs salles et éléments de plan.
- [ ] Redémarrer l'application ne duplique rien.
- [ ] Modifier une salle en base se reflète dans l'API sans modifier le code.

## Vérification
cd backend && ./mvnw test, puis `curl localhost:8080/api/lecture-rooms` (avec jeton)

## À la fin (obligatoire)
1. Cocher **T08** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T08: seed et API des auditoires pour le plan 2D`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

# T14 — Écrans d'inscription et de connexion

**Périmètre :** Front-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/05-ui-ux.md`
- `docs/specs/10-api-rest.md (Authentification)`

## Objectif
L'utilisateur peut créer un compte et se connecter depuis le téléphone.

## À faire
1. Écran d'inscription (nom, email, téléphone, mot de passe) et de connexion (email, mot de passe), un seul bouton principal par écran.
2. Validation côté client + affichage des erreurs de l'API en français (email déjà utilisé, identifiants incorrects).
3. Stockage du jeton, redirection vers l'accueil après connexion, routes protégées, déconnexion.
4. Choix de l'auditoire par défaut : **liste simple** issue de `GET /api/lecture-rooms` (optionnel à l'inscription, modifiable ensuite).
5. Tests : formulaires, erreurs, redirections.

## Hors périmètre — ne fais PAS
- Écran d'accueil détaillé (T15).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Parcours inscription → accueil et connexion → accueil fonctionnent avec le vrai back-end.
- [ ] Une route protégée redirige vers `/connexion` sans jeton.
- [ ] L'interface reste utilisable à 360 px.

## Vérification
cd frontend && npm test ; test manuel avec le back-end lancé

## À la fin (obligatoire)
1. Cocher **T14** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T14: inscription et connexion (front)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

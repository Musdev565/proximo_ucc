# T04 — Authentification : inscription, connexion JWT, /me

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/10-api-rest.md (Authentification)`
- `docs/specs/11-conventions-code.md`
- `docs/DECISIONS.md`

## Objectif
Permettre de créer un compte, de se connecter et d'appeler les routes protégées.

## À faire
1. `POST /api/auth/register`, `POST /api/auth/login`, `GET /api/me`, `PUT /api/me` selon `10-api-rest.md`.
2. Mots de passe hachés (BCrypt). JWT signé avec `JWT_SECRET` (variable d'environnement), durée configurable.
3. Validation : email valide et unique, mot de passe ≥ 8 caractères, téléphone requis, nom requis.
4. Spring Security : routes `/api/auth/**` et `/api/health` publiques ; le reste exige un jeton valide. CORS configurable (origine du front via variable).
5. Messages d'erreur de connexion identiques pour « email inconnu » et « mot de passe faux » (ne pas révéler lequel).
6. Tests : inscription OK, email dupliqué (409), connexion OK/KO, accès à `/me` sans jeton (401), avec jeton (200).

## Hors périmètre — ne fais PAS
- Boutique, produits, commandes. Pas de « mot de passe oublié » ni de vérification d'email (hors MVP).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Un utilisateur peut s'inscrire, se connecter et lire son profil avec le jeton.
- [ ] Le mot de passe n'apparaît jamais en clair (ni en base, ni dans les logs, ni dans les réponses).
- [ ] Tous les tests passent.

## Vérification
cd backend && ./mvnw test, puis tester avec curl/Postman : register → login → /me

## À la fin (obligatoire)
1. Cocher **T04** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T04: authentification JWT (inscription, connexion, profil)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

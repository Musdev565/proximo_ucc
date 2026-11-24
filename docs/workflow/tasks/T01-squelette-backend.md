# T01 — Squelette Spring Boot, configuration, horloge, health

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/03-architecture-technique.md`
- `docs/specs/11-conventions-code.md`
- `docs/specs/10-api-rest.md (section Technique)`

## Objectif
Un projet Spring Boot qui démarre, avec la configuration de base, sans aucune logique métier.

## À faire
1. Créer `backend/` (Maven, Java 21, paquet `com.proximo`). Dépendances : Web, Validation, Data JPA, Security, Flyway (+ flyway-database-postgresql si nécessaire), PostgreSQL driver, Testcontainers (test).
2. Profils `dev`, `test`, `prod` ; configuration par variables d'environnement (voir `.env.example`).
3. `docker-compose.yml` à la racine de `backend/` avec PostgreSQL pour le développement.
4. Bean `Clock` (fuseau `Africa/Kinshasa`) ; propriétés `proximo.orders.open-time`, `proximo.orders.close-time` (15:30), `proximo.day.reset-time` (16:30) lues depuis la config.
5. Sécurité minimale : `GET /api/health` public ; tout le reste refusé (401) pour l'instant.
6. Contrôleur `GET /api/health` → `{"status":"UP"}`. Gestionnaire d'erreurs global au format de `11-conventions-code.md`.
7. Un test de chargement du contexte et un test sur `/api/health`.

## Hors périmètre — ne fais PAS
- Entités, migrations, authentification réelle (T02 à T04).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] `./mvnw test` passe.
- [ ] L'application démarre sur le port 8080 avec la base PostgreSQL du docker-compose.
- [ ] `GET /api/health` renvoie 200 `{"status":"UP"}`.
- [ ] Aucun secret dans le dépôt ; `.env.example` à jour si besoin.
- [ ] La version de Spring Boot choisie est notée dans `docs/DECISIONS.md`.

## Vérification
cd backend && ./mvnw test && ./mvnw spring-boot:run puis `curl localhost:8080/api/health`

## À la fin (obligatoire)
1. Cocher **T01** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T01: squelette Spring Boot (Java 21, config, horloge, health)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

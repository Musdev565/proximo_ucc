# T12 — Images : URL présignée S3

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/03-architecture-technique.md (hébergement)`
- `docs/specs/10-api-rest.md (Images)`

## Objectif
Permettre au front d'envoyer les photos directement vers le bucket, sans passer par le serveur.

## À faire
1. `POST /api/uploads/presign` `{contentType, sizeBytes}` → `{uploadUrl, publicUrl}` ; types autorisés : jpeg/png/webp ; taille max ~500 Ko (le front compresse).
2. Configuration via variables d'environnement S3 (compatible S3). Si non configuré : réponse claire 503 `UPLOADS_DISABLED`, l'application continue de fonctionner.
3. Authentification requise ; nom de fichier généré côté serveur (UUID) pour éviter les collisions et les chemins malveillants.
4. Tests avec un client S3 simulé : type refusé, taille refusée, succès.

## Hors périmètre — ne fais PAS
- Stockage des images dans PostgreSQL. Traitement d'images côté serveur.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] L'URL présignée est générée pour un fichier valide et refusée sinon.
- [ ] Sans configuration S3, le reste de l'API fonctionne.

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T12** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T12: URL présignée pour l'envoi d'images vers S3`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

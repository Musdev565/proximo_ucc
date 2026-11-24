# T20 — Déploiement gratuit (Render + S3) et test terrain

**Périmètre :** Déploiement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/03-architecture-technique.md (hébergement)`
- `docs/specs/07-mvp-et-feuille-de-route.md`
- `docs/specs/08-questions-ouvertes.md`

## Objectif
Mettre l'application en ligne et préparer un test avec de vrais vendeurs.

## À faire
1. **Avant de choisir quoi que ce soit : vérifier les limites ACTUELLES** de Render (veille de l'API gratuite, durée/limites de la base PostgreSQL gratuite) et de l'offre gratuite S3 ; les noter dans `docs/DECISIONS.md` et proposer des alternatives si une limite bloque (ex. base PostgreSQL gratuite d'un autre fournisseur, stockage d'images compatible S3).
2. Déployer le back-end (variables d'environnement, jamais de secret dans Git), la base, le front (hébergement statique) et le bucket d'images ; configurer CORS.
3. Vérifier le rattrapage de T11 après une mise en veille.
4. Rédiger `docs/DEPLOIEMENT.md` (étapes, variables, URL) et `docs/TEST-TERRAIN.md` (protocole : 5 à 10 vendeurs réels, durée, ce qu'on mesure : usage plusieurs jours de suite, commandes livrées au bon auditoire).

## Hors périmètre — ne fais PAS
- Nouvelles fonctionnalités. Achat de services payants sans accord de l'auteur.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] L'application est accessible en ligne et le parcours complet fonctionne (inscription → vendre → commander → payer).
- [ ] Les limites des offres gratuites sont documentées.
- [ ] Aucun secret n'est dans le dépôt.

## Vérification
Test manuel en ligne depuis un téléphone

## À la fin (obligatoire)
1. Cocher **T20** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T20: déploiement et protocole de test terrain`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

# T00 — Vérification du dépôt et premier commit

**Périmètre :** Aucun code  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `AGENTS.md`
- `docs/specs/01-vision-et-contexte.md`
- `docs/specs/02-regles-metier.md`
- `docs/DECISIONS.md`

## Objectif
S'assurer que le dépôt est sain et que tu as compris le projet, sans écrire de code applicatif.

## À faire
1. Vérifier que `docs/`, `AGENTS.md`, `CLAUDE.md`, `.gitignore`, `.env.example` existent.
2. Écrire dans ton compte rendu, **en 10 lignes maximum et avec tes propres mots**, ta compréhension du projet : acteurs, flux de commande, règle de stock, horaires, plan 2D.
3. Lister toute contradiction ou ambiguïté trouvée dans `docs/specs/` (sans la résoudre toi-même).
4. Initialiser Git si ce n'est pas fait, et faire le premier commit.

## Hors périmètre — ne fais PAS
- Créer `backend/` ou `frontend/` (code) : c'est pour T01 et T13.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Le dépôt Git existe avec un premier commit.
- [ ] Le compte rendu contient le résumé et la liste des ambiguïtés (ou « aucune »).
- [ ] Aucun fichier de code applicatif n'a été créé.

## Vérification
`git log --oneline` montre le commit ; `git status` est propre.

## À la fin (obligatoire)
1. Cocher **T00** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T00: vérification du dépôt et premier commit`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

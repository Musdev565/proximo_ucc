# T15 — Accueil étudiant : vendeurs et produits du jour

**Périmètre :** Front-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/05-ui-ux.md (parcours étudiant)`
- `docs/specs/10-api-rest.md (Aujourd'hui)`

## Objectif
L'étudiant voit qui vend aujourd'hui et quoi.

## À faire
1. Écran d'accueil : rappel de l'auditoire (modifiable) + liste des boutiques présentes avec leurs produits disponibles (photo, nom, prix en FC, quantité disponible).
2. États : chargement, liste vide (« Aucun vendeur pour le moment »), erreur avec réessai ; actualisation par tirer-pour-rafraîchir ou bouton.
3. Indiquer clairement quand les commandes sont **fermées** (après 15h30) en désactivant la commande.
4. Tests de rendu pour chaque état.

## Hors périmètre — ne fais PAS
- Passer commande (T16).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] La liste correspond à `GET /api/shops/today`.
- [ ] Les états vide/erreur/chargement sont gérés.
- [ ] Prix toujours affichés en FC.

## Vérification
cd frontend && npm test ; test manuel

## À la fin (obligatoire)
1. Cocher **T15** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T15: accueil étudiant (vendeurs et produits du jour)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

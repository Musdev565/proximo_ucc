# T16 — Commander et suivre sa commande

**Périmètre :** Front-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/05-ui-ux.md (parcours étudiant)`
- `docs/specs/02-regles-metier.md`
- `docs/specs/10-api-rest.md (Commandes)`

## Objectif
Passer une commande en deux appuis et suivre son statut.

## À faire
1. Sélection de quantités, écran de confirmation : récapitulatif, auditoire de livraison, mention **« Paiement en cash à la livraison »**, un gros bouton.
2. Gestion des erreurs de l'API en français (stock insuffisant, commandes fermées, boutique absente) avec possibilité d'ajuster.
3. Écran de suivi : statuts `PENDING → DELIVERED_PAID / CANCELLED / EXPIRED` (texte simple), **rafraîchissement automatique ~15 s** ; bouton « Annuler » tant que `PENDING`.
4. Liste « Mes commandes » (aujourd'hui + récentes).
5. Tests : parcours de commande, erreurs, annulation.

## Hors périmètre — ne fais PAS
- Paiement en ligne, notifications push, WebSocket.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Une commande passée depuis le front apparaît côté back-end et son statut se met à jour à l'écran.
- [ ] Les messages d'erreur sont compréhensibles par un étudiant.

## Vérification
cd frontend && npm test ; test manuel de bout en bout

## À la fin (obligatoire)
1. Cocher **T16** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T16: commande et suivi (front)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

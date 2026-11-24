# T18 — Commandes du vendeur groupées par auditoire

**Périmètre :** Front-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/02-regles-metier.md (regroupement par auditoire, annulation)`
- `docs/specs/10-api-rest.md (Commandes)`

## Objectif
Le vendeur voit ses commandes par auditoire, livre, encaisse ou annule.

## À faire
1. Liste des commandes `PENDING` **groupées par auditoire**, dans l'ordre niveau puis position ; pour chaque auditoire : nom/code et **texte d'accès** (ex. « Niveau 2 — tout au fond du couloir à gauche »).
2. Par commande : produits, total en FC, bouton **« Payé »** (livré + cash reçu) et **« Annuler »** avec choix du motif (client absent, refus, indisponible, autre) ; confirmation avant action.
3. Actualisation régulière (~15 s) ; états vide/erreur.
4. Tests : regroupement, tri, actions payer/annuler.

## Hors périmètre — ne fais PAS
- Le plan 2D lui-même (T19) : ici, texte d'accès uniquement.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Les commandes sont groupées et triées comme demandé.
- [ ] « Payé » et « Annuler » mettent à jour l'écran et le stock côté back-end.
- [ ] Le motif d'annulation est envoyé.

## Vérification
cd frontend && npm test ; test manuel de bout en bout

## À la fin (obligatoire)
1. Cocher **T18** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T18: commandes vendeur par auditoire (payer / annuler)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

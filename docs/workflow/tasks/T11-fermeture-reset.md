# T11 — Fermeture 15h30, remise à zéro 16h30, expiration

**Périmètre :** Back-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/02-regles-metier.md (horaires)`
- `docs/specs/03-architecture-technique.md (tâches planifiées, précisions)`

## Objectif
Appliquer les horaires de fin de journée de façon fiable, même si l'hébergeur met l'appli en veille.

## À faire
1. Tâche planifiée (`@Scheduled`, cron configurable, fuseau Kinshasa) à l'heure de remise à zéro (16h30) : passer les commandes `PENDING` en `EXPIRED`, libérer les réservations, écrire l'historique.
2. **Rattrapage** : au démarrage et à la première requête du jour, si des commandes `PENDING` d'un jour passé (ou après 16h30) existent, les expirer de la même façon (idempotent).
3. Les routes de lecture « aujourd'hui » ne renvoient plus rien d'un jour passé (déjà vrai grâce aux dates).
4. Tests avec `Clock` simulé : avant 15h30 / entre 15h30 et 16h30 / après 16h30 / lendemain ; rattrapage après « veille » ; idempotence.

## Hors périmètre — ne fais PAS
- Notifications aux utilisateurs. Suppression de données historiques.
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Après la remise à zéro, plus aucune commande `PENDING` du jour précédent et aucune réservation résiduelle.
- [ ] Lancer le rattrapage deux fois ne change rien la deuxième fois.
- [ ] Les heures viennent de la configuration, pas du code.

## Vérification
cd backend && ./mvnw test

## À la fin (obligatoire)
1. Cocher **T11** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T11: fermeture des commandes, remise à zéro et expiration`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

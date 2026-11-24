# 00 — Workflow de l'agent (étape par étape)

## Boucle d'une session
1. **Lire** : `AGENTS.md` → `docs/PROGRESS.md` → la fiche de la tâche en cours → les specs qu'elle cite.
2. **Annoncer le plan** en 5 lignes maximum : ce que tu vas faire, quels fichiers tu vas créer/modifier.
   Si quelque chose est ambigu : poser la question **avant** de coder.
3. **Coder par petits pas** : un fichier ou un comportement à la fois, en lançant les tests au fur et à mesure.
4. **Vérifier** : lancer la commande de vérification de la fiche ; tous les critères d'acceptation doivent être vrais.
5. **Relire ton diff** : as-tu touché quelque chose hors périmètre ? Si oui, annule-le.
6. **Mettre à jour** `docs/PROGRESS.md` (cocher la tâche + une ligne de journal) et `docs/DECISIONS.md` si besoin.
7. **Commit** avec le message indiqué dans la fiche.
8. **STOP.** Compte rendu en 5 lignes : ce qui est fait, comment vérifier, limites connues, question éventuelle.
   Ne démarre pas la tâche suivante.

## Ordre des tâches (ne pas sauter, ne pas réordonner)
```
T00 → T01 → T02 → T03 → T04 → T05 → T06 → T07 → T08 → T09 → T10 → T11 → T12   (back-end)
                                                                    ↓
T13 → T14 → T15 → T16 → T17 → T18 → T19   (front-end)   →   T20 (mise en ligne)
```
Raison : le front ne démarre que lorsque l'API est testée. Chaque tâche s'appuie sur la précédente.

## Si un test échoue
- Corrige le **code**, pas le test, sauf si le test contredit les specs (alors signale-le).
- N'abandonne jamais un test en le supprimant ou en le marquant « ignoré ».
- Si tu n'y arrives pas après 3 tentatives : arrête-toi, explique le blocage, propose 2 options.

## Si tu découvres un problème dans une tâche précédente
Ne le corrige pas silencieusement. Décris-le dans le compte rendu et attends la décision de l'auteur.

## Règles de commit
- Un commit par tâche (éventuellement quelques commits intermédiaires), message de la forme
  `T05: boutique « Je veux vendre » (API + tests)`.
- Jamais de fichiers générés (`target/`, `node_modules/`, `dist/`) ni de secrets dans les commits.

## Ce que l'auteur fera entre deux tâches
Relire le code, lancer la vérification, tester à la main (Postman / navigateur), puis ouvrir une **nouvelle session**.

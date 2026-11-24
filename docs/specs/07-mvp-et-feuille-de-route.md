# 07 — MVP et feuille de route

## MVP (version minimale) [RECOMMANDÉ]
1. Inscription / connexion avec **compte unique** (acheter par défaut, « Je veux vendre » pour créer sa boutique).
2. Vendeur : boutique, catalogue, bouton « Je suis là aujourd'hui », quantités du jour.
3. Étudiant : liste des vendeurs présents, commande, suivi du statut.
4. Vendeur : commandes groupées par auditoire, boutons « Payé » / « Annuler ».
5. Règles de stock (stock + réservé), statuts, remise à zéro à 16h30.
6. Plan 2D simple des auditoires (colonne par niveau, surbrillance).

## Hors MVP (plus tard)
- Plan 3D, notifications push, mobile money, avis/notes, statistiques vendeur, rôle administrateur complet.
- Vitrine de services payante (voir `09-vision-future-services.md`).

## Étapes suggérées
1. **Cadrage** : compléter `data/auditoires.json (provisoire, à corriger sur place)`, valider le modèle de données.
2. **Back-end** : entités, migrations, règles de stock/statuts avec tests (priorité aux cas de concurrence).
3. **API + sécurité** : JWT, rôles.
4. **Front** : écrans vendeur puis étudiant, puis plan 2D.
5. **Test terrain** : 5 à 10 vendeurs réels à l'UCC pendant quelques jours.
6. **Pitch / concours** : problème, démo, chiffres du test terrain.

## Critère de succès du test terrain
Les vendeurs utilisent l'app **plusieurs jours de suite** sans qu'on les relance, et les commandes
arrivent bien à la bonne personne dans le bon auditoire.

## Découpage opérationnel (pour l'agent)
Le MVP est découpé en 21 tâches ordonnées (T00 à T20) : voir `docs/workflow/` et `docs/PROGRESS.md`.

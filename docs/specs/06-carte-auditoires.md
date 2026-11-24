# 06 — Carte des auditoires (plan 2D)

> **DONNÉES PROVISOIRES [DÉCIDÉ]** : le plan actuel est une **base arbitraire** (reconstitution schématique
> générée à partir de la description de l'auteur). Il sera **corrigé au fil du temps lors d'une descente
> sur place**. Ne pas considérer ces positions comme exactes ; prévoir que les données changent.

## Ce que l'on sait [DÉCIDÉ]
- Chaque niveau (N1, N2, N3) comporte **1 amphithéâtre**, placé à l'avant, au centre.
- Chaque niveau comporte **de 5 à 7 salles** : le nombre **varie** d'un niveau à l'autre.
- Disposition en **ailes gauche et droite** autour d'un **vide central (atrium)** avec garde-corps,
  du niveau 1 au niveau 3. Deux **escaliers au fond** (gauche et droite).
- Les amphithéâtres sont **superposés** sur la même emprise.
- Une salle est située « juste en face de l'amphi » à certains niveaux seulement (non positionnée).
- Le RDC et le sous-sol : **à confirmer** (le JSON d'origine y met un amphi ; l'auteur avait parlé de
  3 niveaux avec auditoires et d'un sous-sol sans auditoire).
- Les **noms réels** des auditoires et leurs **promotions** seront définis plus tard.

## Source des données
`data/auditoires.json` : liste à plat, un objet par espace (amphi, salles, escaliers, vide).
Chaque salle a : `code`, `type`, `aile`, `nom` (null pour l'instant), `promotion` (null), `bounds` (x, y,
largeur, profondeur en mètres schématiques), `acces` (indication en français), `verifie` (false tant
que non confirmé sur place). La section `a_verifier` liste ce qui reste à contrôler.

## Règles pour l'IA
- **Ne jamais coder les salles en dur** : le plan est généré depuis les données (fichier ou table `Auditoire`).
- Les données doivent être **modifiables facilement** (ajout/suppression d'une salle, renommage)
  sans changer le code.
- Une salle sans `nom` ni `promotion` s'affiche par son `code` et son `acces`.

## Rendu du plan 2D [RECOMMANDÉ]
- Vue **par niveau** (sélecteur N1 / N2 / N3), dessinée en **SVG** à partir de `bounds`.
- L'auditoire de la commande est **mis en surbrillance** ; escaliers et vide central marqués.
- Toujours afficher à côté un **texte** tiré de `acces`, par exemple :
  « Niveau 2 — tout au fond du couloir à gauche ».
- Palette suggérée : amphi violet, salle bleu, escalier ambre, vide gris, garde-corps gris foncé.

## Remplissage lors de la descente sur place
Pour chaque salle : confirmer sa **présence**, son **emplacement**, son **nom réel**, sa **promotion**
principale ; passer `verifie` à `true`. Ajouter les salles manquantes (dont celle « en face de l'amphi »).

## RAPPEL IMPÉRATIF POUR L'AGENT
Le plan est **2D, en SVG**, généré à partir des données (`GET /api/lecture-rooms`). Il est **interdit** de
produire un plan 3D, isométrique ou WebGL. Les noms réels et les promotions seront ajoutés plus tard
sans modifier le code : le plan doit donc fonctionner avec `name = null` (affichage du `code` + indication d'accès).

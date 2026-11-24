# 05 — Interface (UI/UX)

## Principe général [DÉCIDÉ]
Interface **très minimaliste, simple, intuitive, dans le style d'Uber**. Une action principale par écran.

## Règles [RECOMMANDÉ]
- Mobile-first ; grandes zones tactiles ; très peu de texte.
- Palette réduite : noir, blanc, une couleur d'accent pour les boutons.
- Beaucoup d'espace, typographie claire, pas de menus profonds.
- Inscription rapide : numéro ou email, filière, promotion/auditoire.

## Parcours étudiant
1. **Accueil** : rappel de l'auditoire (modifiable) + liste des vendeurs présents aujourd'hui et leurs produits.
2. **Produit** : photo, prix, quantité, bouton « Commander ».
3. **Confirmation** : récapitulatif, mention « Paiement en cash à la livraison », un gros bouton.
4. **Suivi** : statut simple (En attente → Livré / Annulé), comme le suivi d'une course Uber.

## Parcours vendeur
0. Depuis le menu, **« Je veux vendre »** → créer ma boutique (nom, image), puis ajouter les produits.
   C'est le même compte que pour acheter : on bascule simplement de mode.
1. Bouton principal **« Je suis là aujourd'hui »** puis liste de ses produits avec quantités du jour.
2. **Commandes groupées par auditoire**, chaque ligne avec bouton « Payé » (livré + cash reçu) ou « Annuler » (ex. client absent de l'auditoire).
3. Indication claire de la position de l'auditoire sur le **plan 2D** (voir `06-carte-auditoires.md`).

## Plan 2D [DÉCIDÉ]
La modélisation 3D initialement envisagée est **abandonnée pour le MVP** au profit d'un **plan 2D**.
La 3D pourra revenir en version ultérieure comme effet « waouh ».

## Précisions pour l'agent (ajoutées)
- Largeur de conception de référence : **360 px** (petits smartphones Android). Tout doit rester utilisable à cette largeur.
- Une action principale par écran ; bouton principal plein largeur, en bas ou bien visible.
- Pas d'animations lourdes, pas de bibliothèque d'UI volumineuse (connexion lente, forfaits data limités).
- **Plan des auditoires : 2D uniquement (SVG).** Aucune vue 3D, isométrique ou WebGL.
- Textes en français simples ; prix affichés en FC (ex. « 1 500 FC »).
- Accessibilité de base : zones tactiles ≥ 44 px, contraste suffisant, libellés explicites.

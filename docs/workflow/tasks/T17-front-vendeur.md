# T17 — Mode vendeur : boutique, produits, présence et quantités

**Périmètre :** Front-end uniquement  
**Une seule tâche par session. Quand c'est fini : coche dans `docs/PROGRESS.md`, commit, puis STOP.**

## Lis d'abord
- `docs/specs/05-ui-ux.md (parcours vendeur)`
- `docs/specs/10-api-rest.md (Boutique, Produits, Aujourd'hui)`
- `docs/specs/02-regles-metier.md (catalogue)`

## Objectif
Le même compte peut devenir vendeur et préparer sa journée.

## À faire
1. Menu : **« Je veux vendre »** → créer ma boutique (nom, image, description) ; si elle existe, accès au « Mode vendeur ».
2. Gestion du catalogue (ajouter/modifier/désactiver un produit, prix en FC, photo : compression côté client puis envoi via URL présignée si disponible, sinon champ désactivé).
3. Écran du jour : gros bouton **« Je suis là aujourd'hui »** puis quantités apportées par produit ; affichage stock/réservé/disponible.
4. Tests : création de boutique, produit, présence, quantités.

## Hors périmètre — ne fais PAS
- Commandes du vendeur (T18).
- Le **plan 3D** (interdit : plan 2D SVG uniquement, voir AGENTS.md).
- Toute fonctionnalité d'une autre tâche (ne lis pas, ne code pas les tâches suivantes).
- Refactoriser ou « améliorer » le code des tâches précédentes.
- Ajouter une dépendance non prévue sans la noter dans `docs/DECISIONS.md`.

## Critères d'acceptation (tous doivent être vrais)
- [ ] Un utilisateur sans boutique peut en créer une depuis le menu.
- [ ] Les quantités du jour se règlent et se reflètent côté étudiant.
- [ ] Un seul compte, deux modes (acheteur / vendeur), sans nouvelle inscription.

## Vérification
cd frontend && npm test ; test manuel

## À la fin (obligatoire)
1. Cocher **T17** dans `docs/PROGRESS.md` et ajouter une ligne au journal.
2. Noter dans `docs/DECISIONS.md` toute version/dépendance choisie.
3. Commit : `T17: mode vendeur (boutique, produits, présence et quantités)`
4. **STOP.** Compte rendu de 5 lignes max (fait, comment vérifier, limites, question éventuelle). Ne commence pas la tâche suivante.

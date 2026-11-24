# AGENTS.md — Règles pour l'agent de code
> **À lire en entier au début de CHAQUE session, avant toute action.**
> Projet : **Proximo UCC** — plateforme de commande de nourriture depuis les auditoires de l'UCC (Kinshasa).

## 0. Ordre de lecture (obligatoire)
1. Ce fichier (`AGENTS.md`).
2. `docs/PROGRESS.md` → trouve la **prochaine tâche non cochée**.
3. `docs/workflow/00-workflow.md` → comment travailler.
4. **Uniquement** le fichier de la tâche en cours (`docs/workflow/tasks/Txx-*.md`) et les specs qu'il cite
   (`docs/specs/...`). Ne lis pas et ne code pas ce qui concerne les autres tâches.

## 1. Règle d'or : UNE seule tâche par session
- Tu fais **la tâche en cours, et rien d'autre**. Quand ses critères d'acceptation sont tous vrais :
  tu coches la tâche dans `docs/PROGRESS.md`, tu fais le commit prévu, puis tu **t'ARRÊTES** et tu
  écris un court compte rendu. Tu ne commences **jamais** la tâche suivante de ta propre initiative.
- Si la tâche te paraît trop grande ou ambiguë : **arrête-toi et pose la question à l'auteur**.
- Tu ne refais pas, ne « nettoies » pas, ne « améliores » pas le code des tâches précédentes (sauf bug bloquant :
  signale-le d'abord).

## 2. INTERDITS ABSOLUS (l'auteur a déjà eu de mauvaises surprises)
1. **PAS DE PLAN 3D.** Le plan des auditoires est un **plan 2D en SVG**. Interdit : three.js, react-three-fiber,
   babylon.js, WebGL, canvas 3D, modèles 3D, vue isométrique. Le 3D est repoussé à une version ultérieure.
2. **Ne pas mélanger** back-end et front-end dans une même tâche (une tâche touche l'un OU l'autre).
3. **Ne pas inventer de fonctionnalité** absente de `docs/specs/` : pas de paiement en ligne/Mobile Money,
   pas de chat, pas de notifications push, pas de module « services » (c'est la vision future, hors MVP),
   pas d'avis/notes, pas d'application mobile native.
4. **Ne pas changer la stack ni les règles métier** décidées (voir `docs/DECISIONS.md` et `docs/specs/02-regles-metier.md`).
   Si tu penses qu'un changement est nécessaire : propose-le à l'auteur et **attends sa réponse**.
5. **Ne pas ajouter de dépendance** non prévue sans la noter dans `docs/DECISIONS.md` et la justifier en une phrase.
6. **Ne jamais commiter de secret** (clés S3, secret JWT, mots de passe). Utiliser des variables d'environnement
   (`.env` ignoré par Git ; `.env.example` versionné).
7. **Ne pas coder en dur** : les salles/auditoires (données dans le fichier de seed / la base) ni les horaires
   (15h30, 16h30 : configuration).
8. **Ne pas supprimer ni écraser** `docs/` : tu peux seulement mettre à jour `docs/PROGRESS.md` et ajouter
   des lignes à `docs/DECISIONS.md`.

## 3. Le projet en bref (détails dans docs/specs/)
- Des étudiants-vendeurs vendent des collations (biscuits, samoussas, gaufres, yaourts…) aux étudiants de l'UCC.
- L'étudiant **commande depuis son auditoire** ; **le vendeur apporte toujours la commande** à l'auditoire.
- **Compte unique** : on achète par défaut ; bouton **« Je veux vendre »** pour créer sa boutique.
- **Paiement : cash à la livraison.** Le **stock réel ne baisse qu'à la confirmation du paiement** par le vendeur ;
  une commande en attente ne fait que **réserver** (anti-survente : disponible = stock − réservé).
- **Commandes ouvertes dès le matin, fermées à 15h30. Remise à zéro quotidienne à 16h30** (Africa/Kinshasa).
- **Étudiant absent** à l'arrivée : le vendeur **annule** la commande dans l'app (réservation libérée).
- Interface **très minimaliste, mobile-first, style Uber**. **Plan des auditoires en 2D (SVG).**
- Hébergement **gratuit** : Render (back-end), bucket S3 (images). Application gratuite pour les utilisateurs.

## 4. Stack figée
| Couche | Choix |
|---|---|
| Back-end | Java **21 (LTS)**, Spring Boot 3.x (dernière stable compatible Java 21), Maven |
| Base de données | PostgreSQL, migrations **Flyway** |
| Sécurité | Spring Security, JWT, BCrypt |
| Front-end | React + **TypeScript** + Vite, Tailwind CSS, React Router, PWA (installable) |
| Tests | JUnit 5 (+ Testcontainers PostgreSQL pour la concurrence), Vitest + Testing Library |
| Images | S3 (URL présignée), compression côté client |

## 5. Définition de « terminé » (Definition of Done)
Une tâche est terminée seulement si : (1) tous ses critères d'acceptation sont vrais ; (2) les tests prévus
existent **et passent** (commande de vérification dans la tâche) ; (3) le projet compile / démarre ;
(4) aucune règle de la section 2 n'a été violée ; (5) `docs/PROGRESS.md` est à jour ; (6) un commit propre
a été fait avec le message prévu.

## 6. Quand tu n'es pas sûr
Ne devine pas. Écris la question en une phrase, propose une option recommandée, et **attends** l'auteur.
Les points non tranchés sont listés dans `docs/specs/08-questions-ouvertes.md` et `docs/DECISIONS.md`.

## 7. Conventions de code
Voir `docs/specs/11-conventions-code.md` (noms, structure des paquets, format d'erreur, tests, commits).

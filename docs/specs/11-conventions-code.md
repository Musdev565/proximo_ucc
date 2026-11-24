# 11 — Conventions de code

## Langue
- Interface, messages affichés, documentation : **français**.
- Noms de classes, tables, colonnes, variables, routes : **anglais**.

## Glossaire (français métier → code)
| Français | Code |
|---|---|
| Utilisateur | `User` / table `app_user` |
| Boutique | `Shop` |
| Produit | `Product` |
| Disponibilité du jour | `DailyAvailability` (`stock_quantity`, `reserved_quantity`, `version`) |
| Présence boutique | `ShopPresence` |
| Auditoire (amphi ou salle) | `LectureRoom` (type `AMPHITHEATER` ou `CLASSROOM`) |
| Escalier, vide central | `MapFeature` (type `STAIRS`, `CENTRAL_VOID`) : éléments du plan 2D, pas des salles |
| Commande / ligne | `Order` / `OrderLine` |
| Historique de statut | `OrderStatusHistory` |
| Statuts | `PENDING`, `DELIVERED_PAID`, `CANCELLED`, `EXPIRED` |
| Motifs d'annulation | `CUSTOMER_ABSENT`, `CUSTOMER_REFUSED`, `SELLER_UNAVAILABLE`, `OTHER` |

## Back-end
- Paquet racine `com.proximo`. Sous-paquets par fonctionnalité : `auth`, `shop`, `product`, `availability`,
  `room`, `order`, `common`, `config`.
- Couches : `controller` → `service` → `repository` ; **DTO** distincts des entités (jamais d'entité exposée par l'API).
- Transactions : `@Transactional` sur les **services**, pas sur les contrôleurs.
- **Horloge** : toujours injecter un `java.time.Clock` (fuseau `Africa/Kinshasa`) ; interdit d'appeler `LocalDateTime.now()`
  directement (impossible à tester). « Aujourd'hui » = date du jour à Kinshasa.
- Argent : `long` en FC. Pas de `double`/`float`.
- Validation : Bean Validation (`@Valid`) sur les DTO d'entrée.
- Format d'erreur unique (JSON) : `{ "code": "STOCK_INSUFFICIENT", "message": "...", "details": {...} }`
  avec les statuts HTTP : 400 validation, 401 non connecté, 403 interdit, 404 introuvable, 409 conflit/transition invalide.
- Flyway : une migration par changement, jamais de modification d'une migration déjà appliquée.
- Tests : un test par règle métier ; la concurrence est testée avec de vrais threads sur PostgreSQL (Testcontainers).

## Front-end
- TypeScript strict. Composants fonctionnels, hooks. Un dossier par fonctionnalité (`features/auth`, `features/shop`…).
- Appels API centralisés dans `src/api/`. Aucun `fetch` dispersé dans les composants.
- Tailwind uniquement (pas de bibliothèque de composants lourde). Mobile-first : concevoir à 360 px de large d'abord.
- Textes de l'interface en français, centralisés. États vides, chargement et erreurs toujours gérés.

## Git
- Messages : `Txx: description courte`. Un commit par tâche au minimum. Jamais de secret.

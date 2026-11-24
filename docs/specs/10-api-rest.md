# 10 — API REST (contrat de départ, préfixe `/api`)

Format JSON. Authentification : en-tête `Authorization: Bearer <jwt>` (sauf mention « public »).
Erreurs : format unique (voir `11-conventions-code.md`). Montants : entiers en FC.

## Authentification
| Méthode | Route | Description |
|---|---|---|
| POST | `/auth/register` | public. `{name, email, phone, password, defaultRoomId?}` → 201 + jeton |
| POST | `/auth/login` | public. `{email, password}` → jeton JWT |
| GET | `/me` | profil de l'utilisateur connecté (+ `shopId` s'il a une boutique) |
| PUT | `/me` | modifie nom, téléphone, auditoire par défaut |

## Boutique (« Je veux vendre »)
| POST | `/shops` | crée MA boutique `{name, imageUrl?, description?}` (une seule par utilisateur) |
| GET | `/shops/me` | ma boutique |
| PUT | `/shops/me` | modifie ma boutique |

## Produits (catalogue permanent)
| GET | `/shops/me/products` | mes produits |
| POST | `/shops/me/products` | `{name, price, imageUrl?}` |
| PUT | `/shops/me/products/{id}` | modifie |
| DELETE | `/shops/me/products/{id}` | désactive (`active=false`), n'efface pas |

## Aujourd'hui (présence et quantités du jour)
| GET | `/shops/me/today` | présence + quantités (stock, réservé, disponible) du jour |
| PUT | `/shops/me/today` | `{present: true|false}` |
| PUT | `/shops/me/today/products/{productId}` | `{stockQuantity}` (≥ quantité réservée) |
| GET | `/shops/today` | public aux connectés : boutiques présentes + produits avec disponible > 0 |

## Auditoires et plan 2D
| GET | `/lecture-rooms` | niveaux, salles/amphis, escaliers, vide central, `bounds` (pour le plan 2D) |

## Commandes
| POST | `/orders` | `{shopId, roomId, items:[{productId, quantity}]}` → 201 ; erreurs : fermé, boutique absente, stock insuffisant |
| GET | `/orders/mine` | mes commandes d'acheteur (aujourd'hui + historique récent) |
| GET | `/orders/{id}` | détail + statut (acheteur ou vendeur concerné seulement) |
| POST | `/orders/{id}/cancel` | acheteur (si `PENDING`) ou vendeur (avec `reason`) |
| GET | `/shops/me/orders` | commandes de ma boutique ; `?status=PENDING` ; groupées par auditoire (niveau, position) |
| POST | `/orders/{id}/pay` | vendeur seulement : livré + cash reçu → `DELIVERED_PAID` |

## Images
| POST | `/uploads/presign` | `{contentType, sizeBytes}` → URL présignée S3 + URL finale (désactivé si S3 non configuré) |

## Technique
| GET | `/health` | public. `{status:"UP"}` |

## Règles transverses
- Un utilisateur ne peut pas commander dans sa propre boutique.
- Un vendeur ne voit/modifie que SA boutique, SES produits, SES commandes.
- Toute transition de statut invalide → **409 Conflict**.

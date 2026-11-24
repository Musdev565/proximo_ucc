# Décisions

## Décidées par l'auteur [NE PAS REMETTRE EN CAUSE]
| Sujet | Décision |
|---|---|
| Nom | Proximo UCC |
| Plan des auditoires | **2D (SVG)**. 3D abandonné pour le MVP |
| Catalogue | Catalogue permanent + disponibilité/quantités du jour |
| Horaires | Commandes ouvertes dès le matin, fermées à **15h30** ; remise à zéro à **16h30** |
| Livraison | Toujours par le vendeur, à l'auditoire |
| Paiement | Cash à la livraison. Stock réel baisse **uniquement** à la confirmation du paiement |
| Étudiant absent | Le vendeur annule la commande dans l'app |
| Comptes | Compte unique ; « Je veux vendre » crée la boutique ; inscription ouverte à tous |
| Interface | Très minimaliste, simple, intuitive, style Uber |
| Stack | Spring Boot, PostgreSQL, React |
| Hébergement | Render (back-end), bucket S3 (images), offres gratuites |
| Gratuité | App gratuite pour le moment |
| Vision future | Vitrine de services (hors MVP) |

## Recommandées par Claude, par défaut [MODIFIABLES par l'auteur]
| Sujet | Défaut |
|---|---|
| Java | 21 LTS (pas 24) |
| Build | Maven |
| Front | TypeScript + Vite + Tailwind + React Router |
| Connexion | Email + mot de passe ; téléphone demandé à l'inscription (contact de livraison) |
| Monnaie | Franc congolais (FC), entiers (`BIGINT`), pas de décimales |
| Annulation | Le vendeur peut annuler (avec motif) ; l'acheteur peut annuler tant que `PENDING` |
| Commande | Une commande = **une seule boutique** |
| Reset quotidien | Les disponibilités sont **par date** : le « reset » n'efface rien, il ferme et expire |
| Suivi de commande | Rafraîchissement régulier (polling ~15 s), pas de WebSocket |
| Langues | Interface en français ; code et noms techniques en anglais |
| Auth stockage jeton | `localStorage` pour le MVP |

## Journal des décisions (l'agent ajoute ici, avec la date)
<!-- AAAA-MM-JJ — décision / dépendance ajoutée / version choisie — raison en une phrase -->

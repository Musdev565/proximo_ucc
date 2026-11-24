# 03 — Architecture technique

## Stack [DÉCIDÉ]
- **Back-end** : Java, **Spring Boot**
- **Base de données** : **PostgreSQL**
- **Front-end** : **React**
- **Hébergement** : uniquement des offres **gratuites**

## Recommandations [RECOMMANDÉ]
- Front : approche **mobile-first**, Tailwind CSS (sobriété du style Uber), PWA si possible
  (installable sur le téléphone sans store).
- API REST JSON, authentification par JWT (Spring Security), rôles `ETUDIANT`, `VENDEUR`, `ADMIN`.
- Migrations de base avec **Flyway** ou Liquibase.
- Tests : JUnit 5 + Testcontainers (PostgreSQL) pour les règles de stock et de statuts.
- Structure Spring en couches : `controller` → `service` → `repository`, DTO séparés des entités.

## Gestion de la concurrence (point clé)
Objectif : ne jamais survendre. Deux options :
1. **Verrouillage optimiste** : champ `@Version` sur la ligne de disponibilité du produit ;
   en cas de conflit, réessayer ou refuser proprement.
2. **Verrouillage pessimiste** : `SELECT ... FOR UPDATE` (`@Lock(PESSIMISTIC_WRITE)`) lors de la réservation.
Toute réservation et toute confirmation de paiement s'exécutent dans une **transaction** (`@Transactional`).

## Tâches planifiées
- À **16h30** (fuseau Africa/Kinshasa) : remise à zéro des disponibilités du jour, expiration des
  commandes `EN_ATTENTE` (`@Scheduled` avec cron).
- Attention : sur un hébergement gratuit qui met l'application en veille, un `@Scheduled` peut ne pas
  se déclencher. Prévoir un **rattrapage au réveil** (vérifier la date de la dernière remise à zéro)
  ou un appel externe planifié.

## Hébergement prévu [DÉCIDÉ par l'auteur, à vérifier]
- **Back-end Java : Render** (offre gratuite).
- **Images produits : bucket S3 gratuit**, séparé du serveur (donc hors Render). Le back-end ne stocke
  que l'URL de l'image en base ; compresser les images côté client.
- **À vérifier avant de s'engager** (ces offres changent) : mise en veille de l'API gratuite sur Render
  (premier appel lent), durée de vie/limites de la base PostgreSQL gratuite, et durée/limites
  de l'offre gratuite S3 (elle peut être limitée dans le temps ou en quota).

## Hébergement gratuit — points d'attention [À DÉFINIR]
Les offres gratuites changent souvent : **vérifier les limites actuelles** avant de choisir.
Points d'attention : mise en veille de l'API, taille de la base, stockage des images, quotas.
Pour les images produits : les compresser côté client et limiter leur taille ;
ne pas stocker de gros fichiers dans PostgreSQL.

## Notifications [À DÉFINIR]
Au minimum : rafraîchissement régulier (polling) du statut. Plus tard : notifications push ou WebSocket.

## Précisions pour l'agent (ajoutées)
- **Java 21 LTS** (et non 24). Spring Boot 3.x : prendre la dernière version stable compatible Java 21 et la noter dans `docs/DECISIONS.md`.
- **« Aujourd'hui » et remise à zéro** : les disponibilités et présences sont stockées **par date** (`date` = jour à Kinshasa).
  Le lendemain, aucune ligne n'existe pour la nouvelle date : le catalogue reste, la disponibilité est vide.
  La tâche de 16h30 sert à **fermer et expirer** (commandes `PENDING` → `EXPIRED`, réservations libérées), pas à tout effacer.
  Prévoir un **rattrapage** si l'hébergeur gratuit a mis l'application en veille au moment du déclenchement.
- Concurrence : verrouillage **pessimiste** (`SELECT … FOR UPDATE`) sur les lignes `DailyAvailability` lors d'une réservation,
  en les verrouillant **dans un ordre fixe (par `product_id`)** pour éviter les interblocages. Contraintes SQL `CHECK` en filet de sécurité.

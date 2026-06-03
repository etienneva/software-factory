# Architecture Principles

## Philosophie

Privilégier :

* simplicité
* modularité
* lisibilité
* maintenabilité

## Principes

### Frontend

Responsable :

* affichage
* interactions utilisateur

Le frontend ne contient pas la logique métier critique.

### Backend

Responsable :

* logique métier
* permissions
* validations

### Database

Responsable :

* stockage
* intégrité des données

### Services externes

Toujours encapsulés.

Ne jamais dépendre directement d'un fournisseur unique.

## Éviter

* microservices prématurés
* sur-ingénierie
* dépendances inutiles
* duplication du code

# Security Standards

## Principes

La sécurité est présente dès le début du projet.

## Obligatoire

### Authentification

Tous les accès sensibles nécessitent une authentification.

### Autorisations

Les rôles doivent être explicitement définis.

### Secrets

Jamais :

* dans Git
* dans le frontend
* dans les logs

### Validation

Toutes les entrées utilisateur doivent être validées.

### Journalisation

Tracer :

* connexions
* erreurs critiques
* actions administrateur

## Vérifications avant production

* audit permissions
* audit variables d'environnement
* audit dépendances


## Architecture du projet

Page de documentation en format Markdown (md) expliquant comment est organisé le projet (Maven va automatiquement convertir le fichier architecture.md en une page HTML architecture.html).

### Généralités

Dans une architecture multi-tiers, une architecture en couches, les responsabilités des différentes fonctions sont séparées :

![Architecture multi-tiers](img/Architecture-multi-tiers.png)


      L'utilisateur interagit avec l'application via la couche Présentation, qui contient les parties Contrôleur et Vue du patron MVC.

      Une fois l'action utilisateur identifiée, la couche Présentation fait appel à la couche Métier.
      Celle-ci est responsable de la logique métier de l'application, c'est-à-dire de l'implémentation des règles de gestion fonctionnelle.

      Si des accès à la base de données sont nécessaires, alors la couche Métier appelle la couche Persistance.
      C'est dans cette couche que l'on retrouve le patron DAO.

      Enfin toutes ces couches partagent une « vision commune » du domaine fonctionnel en s'appuyant sur le Modèle.
      En effet, ce modèle contient les JavaBeans manipulés dans l'application.

Chaque couche n'appelle que la couche immédiatement en dessous d'elle et n'a aucune connaissance des couches supérieures.

Un projet multi-modules concrétise cette architecture multi-couches, chaque couche de l'architecture faisant l'objet d'un module dédié :

![Interdépendances des modules](img/Interdependance-entre-modules.png)


### L'application web

Le module webapp est responsable de l'application web.

### Les batches

Le module batch est reponsable du jeu de batchs de l'application de gestion de tickets.

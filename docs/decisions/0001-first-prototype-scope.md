# ADR-0001 — Choisir une première tranche démontrable

- **Statut : proposé, non accepté.**
- **Décideur : William.**
- **Date de rédaction : 18 novembre 2026.**
- **Décision effective et date d’accord : en attente.**

## Contexte

La vision couvre Windows Server, Linux et les pare-feu. Démarrer toutes ces sources, les permissions réseau, un modèle IA et une interface simultanément rendrait difficile l’identification de la cause d’un défaut.

## Proposition

Commencer par un lot d’authentifications Linux exportées, d’abord entièrement fictives. L’agent choisirait des recherches en lecture seule dans ce lot, produirait un rapport citant ses preuves et s’arrêterait pour revue humaine. Il n’aurait ni accès direct aux systèmes, ni outil de correction.

## Alternatives

| Option | Intérêt | Coût ou limite |
| --- | --- | --- |
| Lot Linux importé | Peu de permissions ; raisonnement et audit faciles à observer | Pas de surveillance continue ni de couverture Windows |
| Lot d’événements Windows importé | Proche du labo AD de William | Normalisation et compréhension des événements Windows à préparer |
| Collecte en direct dès le départ | Montre immédiatement la chaîne complète | Identités, réseau, secrets et sécurité des connecteurs à traiter en même temps |

## Conséquences si accepté

Définir le schéma d’entrée et un petit corpus d’essai. Reporter les connecteurs et l’automatisation corrective. Évaluer l’apport de l’agent face à une corrélation déterministe. Le choix d’Ollama, de Python ou d’un modèle ne découle pas automatiquement de cet accord.

## Validation attendue

William accepte cette tranche, choisit le lot Windows ou reformule le premier cas d’usage. Mettre ensuite à jour l’ADR et les exigences concernées.

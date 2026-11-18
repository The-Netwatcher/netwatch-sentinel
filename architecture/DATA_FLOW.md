# Flux de données et frontières de confiance

Architecture cible, non déployée. Le [README](../README.md) contient le diagramme d’ensemble ; ce document détaille la circulation et les droits.

## Zones logiques

| Zone | Contenu | Confiance accordée |
| --- | --- | --- |
| Z0 : sources | Exports de journaux et documents importés | Non fiables ; peuvent être falsifiés ou contenir des instructions |
| Z1 : preuves locales | Instantané normalisé, provenance et index | Intégrité contrôlée ; sens du contenu encore non fiable |
| Z2 : raisonnement | Orchestrateur, modèle, outils de recherche | Modèle non autorité ; appels soumis à politique |
| Z3 : restitution | Rapport, trace, décision humaine | Données sensibles éventuelles ; export explicite |
| Z4 : maintenance externe | Dépendances, modèles et mises à jour | Approvisionnement séparé des analyses |

## Flux du premier prototype proposé

| Flux | Source → destination | Données | Contrôle attendu |
| --- | --- | --- | --- |
| DF-01 | Opérateur / Z0 → importateur | Un fichier sélectionné | Racine autorisée, taille et format bornés, pas de suivi de lien hors périmètre |
| DF-02 | Importateur → Z1 | Événements normalisés | Provenance, temps UTC ou anomalie explicite, déduplication |
| DF-03 | Z1 → modèle local | Sous-ensemble minimisé | Masquage, limites de taille, séparation des instructions |
| DF-04 | Modèle → passerelle de politique | Proposition d’outil et arguments structurés | Nom autorisé, schéma, portée, budget ; aucun texte exécuté |
| DF-05 | Outil → Z1 → orchestrateur | Résultats bornés et références | Lecture dans l’instantané sélectionné uniquement |
| DF-06 | Corpus sélectionné → modèle | Extraits référencés | Accès filtré avant recherche, version et section identifiées |
| DF-07 | Orchestrateur → Z3 | Rapport et trace minimisés | Structure et références validées, sortie dans une racine dédiée |
| DF-08 | Administrateur → état de revue | Validation, correction ou rejet | Aucune action corrective sur un système |
| DF-09 | Z4 → poste en maintenance | Modèles et dépendances | Source, version et intégrité vérifiées ; aucun journal métier envoyé |

## Réseau

Le premier MVP sur fichiers n’a besoin d’aucun flux vers les machines du labo pendant l’analyse. Si Ollama est retenu sur le même hôte, l’API devrait rester sur l’interface de bouclage. Le port par défaut documenté par l’éditeur est 11434 ; ce n’est pas une règle réseau déjà configurée par ce dépôt.

Si l’inférence devient un service sur une autre machine, il faudra une nouvelle décision : identité du client, protection du transport, authentification, filtrage et absence d’exposition directe de l’API modèle. Une adresse privée n’est pas, à elle seule, une protection.

Les futurs collecteurs nécessiteront une matrice source/destination/port/identité. Aucun port SSH, WinRM ou de collecte n’est ouvert ou présumé nécessaire dans cette version.

## Entrées à empêcher

Le modèle ne doit pas choisir une URL de téléchargement, un chemin libre, une adresse hors liste ou une commande système. Une procédure trouvée dans le corpus ne doit jamais devenir un fichier de politique. Les sorties modèle sont des données jusqu’à leur validation, y compris lorsqu’elles ressemblent à du JSON valide.

## Données locales et maintenance

Le mode d’analyse cible bloque les sorties Internet au niveau du système, y compris les chemins via proxy ou IPv6 qui seraient autrement disponibles. Le téléchargement initial des poids et les mises à jour appartiennent à une phase de maintenance explicite. Tester les deux modes séparément et vérifier l’absence de repli distant ; « local » ne signifie pas que l’environnement est déjà déconnecté physiquement.

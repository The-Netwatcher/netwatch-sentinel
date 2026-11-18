# Registre des décisions

Date de référence : 18 novembre 2026. Une proposition de l’assistant, même détaillée, n’est pas une approbation de William.

## Cadre établi par les échanges

| ID | Élément | État et provenance |
| --- | --- | --- |
| C-001 | Nom : NetWatch Sentinel | Nom retenu dans les échanges antérieurs |
| C-002 | Candidature ASUS Agent Computer Challenge, AI Entry | Intention confirmée par William |
| C-003 | Projet au stade conception | Confirmé dans la demande actuelle |
| C-004 | Avancer ensemble, étape par étape, en validant les choix techniques | Contrainte explicite de William |
| C-005 | RTX 5080 existante ; intérêt d’une seconde machine dédiée avec une RTX 5060 Ti | Contexte matériel et intention retrouvés ; aucun achat ni assemblage validé ici |

L’agent local d’aide à la surveillance pour PME, Python, Ollama, le RAG et les diagnostics en lecture seule ont été proposés dans les échanges antérieurs. La reprise du projet permet de les documenter comme direction de travail ; elle ne suffit pas à déclarer tous ces choix techniques acceptés.

## Décisions à traiter dans l’ordre

| ID | Sujet | Proposition de départ | État |
| --- | --- | --- | --- |
| D-001 | Premier cas d’usage | Authentifications Linux importées, rapport sourcé | Proposition ; [ADR détaillé](decisions/0001-first-prototype-scope.md) |
| D-002 | Autonomie et permissions | Recherches bornées ; aucune correction automatique | Proposition |
| D-003 | Environnement d’exécution | Comparer hôte Windows natif et station Linux ; distinguer GPU et VM du labo | Ouvert |
| D-004 | Langage et orchestration | Python et machine à états explicite avant un framework spécialisé | Proposition |
| D-005 | Interface d’inférence locale | Ollama candidat ; LM Studio ou llama.cpp à comparer selon le besoin | Proposition |
| D-006 | Modèle | Comparer des modèles après définition des essais et du budget mémoire | Ouvert |
| D-007 | Recherche et stockage | Fichiers structurés pour débuter ; SQLite candidat si nécessaire | Proposition |
| D-008 | RAG | Petit corpus approuvé ; recherche simple avant index vectoriel | Proposition |
| D-009 | Interface opérateur | Rapport Markdown et interface minimale à définir | Ouvert |
| D-010 | Données | Schéma, limites de volume, conservation, purge et masquage | Proposition à préciser |
| D-011 | Publication GitHub | Compte, visibilité, licence et canal de sécurité | Ouvert |
| D-012 | Sources vivantes | Choisir un seul connecteur après validation du MVP importé | Reporté |

## Méthode d’acceptation

Pour chaque décision, documenter le besoin, la proposition, une ou deux alternatives utiles, les conséquences et la vérification attendue. William tranche explicitement. Inscrire alors la date et une reformulation fidèle de son accord dans l’ADR concerné, puis mettre à jour ce registre.

Une décision remplacée reste dans l’historique avec un lien vers la nouvelle. Le silence, la présence d’un fichier ou une préférence générale ne valent pas validation technique.

## Hypothèses encore non établies

L’OS de la station dédiée, son CPU, sa RAM, son stockage, l’éventuel accès GPU d’une VM, le modèle, les licences des modèles, le débit des événements et le nombre d’utilisateurs ne sont pas fixés. La catégorie et les modalités exactes du concours doivent être revérifiées dans son règlement avant soumission. Aucun dépôt GitHub distant ni identifiant de compte n’a été fourni dans les informations retrouvées.

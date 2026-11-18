# Architecture technique proposée

Toutes les responsabilités décrites sont une cible de conception. Aucun composant applicatif n’est implémenté. Les produits cités sont des candidats.

## Principes

Séparer le travail déterministe (parsing, filtrage, contrôle des permissions, validation des références) du raisonnement probabiliste du modèle. Confier les droits à l’application et au système d’exploitation. Réduire la première version à un processus orchestrateur et des modules : les rôles logiques ne nécessitent pas un essaim d’agents.

## Composants et interfaces

| Composant logique | Responsabilité | Entrée → sortie | Limite de confiance |
| --- | --- | --- | --- |
| Importateur | Taille, encodage, format, provenance | Fichier sélectionné → lot accepté ou rejet motivé | Le fichier est non fiable |
| Normaliseur | Temps, catégories, identifiants, qualité | Lot accepté → événements normalisés | Aucun événement n’est automatiquement une preuve de cause |
| Préparation des données | Masquage et sélection des champs | Événements → contexte minimisé | Secrets exclus avant contexte modèle |
| Dépôt de preuves | Conserver un instantané et les références | Événements → recherches reproductibles | Lecture limitée au dossier autorisé |
| Préfiltre de corrélation | Regrouper des signaux explicables | Événements → candidats à analyser | Règles versionnées ; ne prouvent pas un incident |
| Orchestrateur | Objectif, état, budget et arrêts | Dossier d’analyse → plan borné puis rapport | Seul ce composant demande des appels d’outils |
| Passerelle de politique | Valider outil, arguments, portée et budget | Proposition d’appel → autorisation ou refus | Le modèle ne peut modifier cette politique |
| Outils de consultation | Exécuter des recherches définies | Appel autorisé → résultat structuré borné | Pas de shell ni accès réseau générique |
| Adaptateur d’inférence | Appeler un modèle local sélectionné | Contexte minimisé → sortie non fiable | Vérification des sorties obligatoire |
| Recherche documentaire | Retrouver des passages approuvés | Question bornée → extraits avec versions | Le document reste une donnée non fiable |
| Validateur de rapport | Structure, références et limites | Sortie modèle → rapport accepté ou rejeté | Ne peut garantir la vérité de l’interprétation |
| Audit et revue | Suivre actions, refus et avis humain | Événements d’exécution → trace et état de revue | Stockage local protégé, accès limité |

## Chaîne proposée

L’import produit un instantané identifié. Une règle simple peut repérer une séquence d’authentifications à examiner. L’orchestrateur donne au modèle l’objectif, les outils disponibles et des preuves minimisées. Le modèle propose une recherche ; la passerelle la vérifie ; l’outil renvoie un résultat borné. L’orchestrateur peut poursuivre dans son budget, puis demande une synthèse. Les références sont contrôlées avant la présentation à l’humain.

Le lecteur des fichiers et l’écrivain des rapports ont des périmètres distincts. « Lecture seule » signifie absence de modification des sources surveillées ; le prototype doit pouvoir écrire ses propres rapports et journaux d’audit dans un emplacement dédié.

## Options de pile, sans décision implicite

| Couche | Candidat de départ | Alternative | Critère de décision |
| --- | --- | --- | --- |
| Orchestration | Python, machine à états explicite | Framework agentique spécialisé | Lisibilité, contrôle du budget, facilité de test |
| Inférence locale | Ollama | LM Studio, llama.cpp | API locale, outils structurés, versions, fonctionnement hors cloud |
| Événements | Fichiers structurés bornés | SQLite | Volume, requêtes, déduplication, simplicité |
| Documentation | Recherche simple dans un petit corpus | Index d’embeddings local | Pertinence réellement mesurée ; coût de mise à jour |
| Présentation | Rapport Markdown local | Interface Web locale | Besoin de revue, surface réseau, identité des utilisateurs |
| Déploiement initial | Même OS pour orchestrateur et inférence | Services séparés ou environnement conteneurisé | Accès GPU, isolation réelle, exploitation |

L’ajout d’une base vectorielle, d’un framework multi-agent, d’une API HTTP ou de conteneurs n’est pas un prérequis. Les ajouter seulement si le besoin et les essais le justifient.

## Modèle de déploiement

**Premier laboratoire proposé** : événements exportés depuis le labo vers un répertoire dédié ; inférence sur l’hôte possédant le GPU ; orchestrateur accessible au seul opérateur local. Aucun accès GPU à une VM Hyper-V n’est supposé. Le support dépendra du système, des versions et de la configuration effectivement retenus.

**Station dédiée envisagée** : machine séparée du poste personnel, compte de service limité, stockage protégé, accès d’administration défini, flux réseau explicitement autorisés. Deux GPU dans le même hôte ne constituent pas cette séparation. La station dédiée ne devient pas automatiquement une zone isolée : ses chemins réseau et administratifs devront être vérifiés.

## Budget et modes dégradés proposés

Pour les premiers essais seulement : trois cycles de planification au plus, six appels d’outils au total, une analyse active et un plafond de temps de 60 secondes hors chargement initial. Ces valeurs sont des limites expérimentales à discuter, pas des performances annoncées. Volumes d’entrée et de sortie devront être fixés avant implémentation.

| Défaut | Comportement attendu |
| --- | --- |
| Modèle absent ou mémoire insuffisante | Arrêter l’analyse IA et indiquer le défaut ; aucun repli cloud |
| Fichier invalide ou temps incohérent | Rejeter ou marquer les événements ; ne pas inventer les champs manquants |
| Outil refusé | Enregistrer le refus ; poursuivre seulement avec une option autorisée dans le budget |
| Budget épuisé | Rapport partiel marqué incomplet |
| Références inexistantes | Bloquer le rapport comme valide ; une reprise bornée au plus, comptée au budget |
| Audit indisponible | Arrêter les nouveaux appels ; signaler une analyse non vérifiable |
| Annulation humaine | Arrêter la boucle et marquer la sortie annulée |

## Versionnement futur

Chaque analyse devra référencer la version du programme, de la politique, des règles, du schéma, du prompt, du modèle et du corpus documentaire. Utiliser les identifiants ou empreintes réellement disponibles ; ne pas supposer qu’un nom de modèle mutable identifie des poids fixes. Conserver les paramètres d’inférence pour permettre une comparaison, sans promettre un résultat textuel identique.

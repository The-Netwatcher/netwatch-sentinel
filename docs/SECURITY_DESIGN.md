# Mécanismes de sécurité à concevoir et vérifier

Ce document spécifie des protections envisagées. Elles ne sont pas déployées. Les risques et preuves attendues figurent dans le [modèle de menaces](THREAT_MODEL.md) et le [plan d’évaluation](EVALUATION_PLAN.md).

## Permissions minimales et séparation

Exécuter le prototype sous un compte limité. Séparer les répertoires d’entrée autorisés, les données de travail, les rapports et la politique. L’utilisateur de service doit lire les sources sélectionnées et écrire uniquement ses données applicatives. Il ne doit pas pouvoir modifier sa liste d’outils ou sa politique pendant une analyse.

Une future collecte sur Windows ou Linux utilisera des identités dédiées aux droits documentés. Aucun compte administrateur de domaine ni accès général SSH n’est requis par la conception initiale. Un conteneur ou une VM peut compléter des contrôles, mais n’en constitue pas une preuve automatique.

## Politique extérieure au modèle

Les permissions, les budgets et les racines d’accès appartiennent à du code et à une configuration protégés. La passerelle valide chaque appel avant exécution ; une phrase du modèle, du journal ou d’une procédure ne peut ni l’ignorer ni l’assouplir. Un bouton de validation du rapport ne débloque pas un catalogue d’actions.

Privilégier des fonctions spécialisées à paramètres typés. Lorsque des requêtes de stockage sont utilisées, les construire dans le code avec des paramètres validés ; ne pas exécuter du SQL ou du code généré par le modèle.

## Injection indirecte et contenus hostiles

Un attaquant peut contrôler un nom d’utilisateur, un message d’erreur ou une ligne de journal. Un document interne peut aussi être compromis. L’architecture doit donc :

- Délimiter ces données et leurs provenances dans le contexte du modèle.
- Ne jamais les insérer comme instructions privilégiées ou politique système.
- Appliquer la même validation aux appels même si le texte semble demander une urgence.
- Refuser une destination externe ou une action hors catalogue.
- Vérifier les références avant restitution et encoder les contenus affichés comme du texte.

Le filtrage textuel, les délimiteurs et le RAG peuvent aider, mais ne garantissent pas l’absence d’injection. Les restrictions d’outils et de permissions réduisent les effets possibles. Une hallucination ou une interprétation erronée demeure possible même avec des références existantes.

## Localité, réseau et approvisionnement

Le mode d’analyse cible utilise uniquement des poids et un corpus présents localement. Aucun repli vers un modèle cloud, recherche Web ou télémétrie contenant les journaux ne doit être disponible. Si Ollama est retenu, étudier son mode sans cloud et conserver l’API sur le bouclage pour un déploiement sur le même hôte ; voir les [références](REFERENCES.md).

Le pare-feu du système et la configuration des processus devront empêcher les sorties non autorisées, puis être testés. Vérifier proxy, IPv4 et IPv6 selon l’environnement. Ne pas ouvrir l’API du modèle sur Internet. L’accès réseau intermachines, s’il devient nécessaire, demande une conception d’authentification et de transport dédiée.

Le téléchargement de dépendances et de modèles relève d’une maintenance distincte. Retenir sources, versions, empreintes disponibles et licences ; vérifier l’intégrité ; documenter les mises à jour. Ne pas installer un exécutable suggéré par un journal ou une réponse de l’agent.

## Données et secrets

Ne pas versionner les logs réels, mots de passe, clés, tokens ou exports de production. Masquer les secrets avant contexte modèle et minimiser les traces. Les comptes, noms d’hôtes et adresses peuvent rester sensibles après pseudonymisation ; ce traitement ne garantit pas une anonymisation.

Décider des durées de conservation par type de donnée avant le pilote. Purger les copies brutes, normalisées, indexées, les caches, rapports et sauvegardes selon la politique retenue. Limiter les accès locaux et prévoir une protection du stockage et des sauvegardes. Aucun chiffrement n’est activé par ce dépôt.

## Audit et intégrité

L’audit doit associer exécution, preuves consultées, version des composants, décisions de politique et revue humaine. Ne pas enregistrer systématiquement le contexte complet du modèle ou des secrets. Préférer une trace applicative restreinte en ajout et des sauvegardes contrôlées.

Une empreinte seule peut aider à constater un changement ; elle ne rend pas un journal infalsifiable si le même attaquant contrôle les fichiers et leurs empreintes. Un stockage distinct ou une protection supplémentaire sera étudié pour un pilote. Un administrateur local compromis reste un risque majeur.

## Indisponibilité et arrêt

Limiter volumes, fenêtres temporelles, durée, nombre d’appels et concurrence. Rendre visibles les troncatures. Prévoir annulation et arrêt sur contrôle indisponible. En cas de panne du modèle, les preuves importées doivent rester consultables sans produire de conclusion IA fictive. Aucun automatisme correctif ne doit compenser une panne de diagnostic.

## Rendu et export

Afficher les messages de logs comme texte ; empêcher l’exécution de HTML ou de liens actifs issus des données. Le rapport doit séparer preuve, interprétation et recommandation. La revue doit montrer les limites avant acceptation. Tout export à l’extérieur est une décision de l’opérateur sur un fichier relu et minimisé.

## Évolution vers un pilote

Avant un usage avec des données d’une organisation : revoir les droits, l’identité des utilisateurs, les responsabilités, les règles de conservation, l’exploitation, les mises à jour et la récupération après incident. Aucune certification ni conformité réglementaire n’est revendiquée par la présente conception.

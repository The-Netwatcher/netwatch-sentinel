# Préparer la publication sur GitHub

Ce dossier est une base de dépôt Git locale. Aucun dépôt distant n’est encore créé ni publié par cette livraison. La préparation des fichiers peut être relue avant de choisir la visibilité.

## Métadonnées proposées

| Champ | Proposition | État |
| --- | --- | --- |
| Nom du dépôt | `netwatch-sentinel` | À valider |
| Description | Conception d’un agent IA local pour analyser des journaux et préparer des diagnostics sourcés, sous contrôle humain. | À relire |
| Langue principale | Français, noms de fichiers stables en anglais | Choix éditorial de cette première version, modifiable |
| Topics | `local-ai`, `agentic-ai`, `cybersecurity`, `homelab`, `design` | Suggestions |
| Propriétaire | Compte ou organisation GitHub de William | Non fourni |
| Visibilité | Privée pendant relecture ou publique pour présentation | Décision D-011 |
| Licence | Choix séparé avant de présenter le projet comme open source | Non choisie |
| Auteur des commits | Identité et adresse Git à définir par William | Aucun email inventé |

## Publication après décisions

1. Valider le contenu de conception et les métadonnées utiles.
2. Choisir le compte GitHub, la visibilité et la licence ; définir l’identité Git voulue.
3. Relire l’ensemble du contenu et de l’historique éventuel pour détecter secrets et données privées.
4. Créer le dépôt distant dans le compte retenu et y pousser les fichiers relus.
5. Vérifier le rendu des liens, tableaux et diagrammes dans GitHub, puis conserver l’URL réelle.
6. Ajouter la licence choisie et le canal de signalement privé, lorsqu’ils sont établis.

La connexion GitHub n’est pas configurée dans ce travail. Aucun nom d’utilisateur, URL de dépôt ou statut de publication n’est inventé. La publication pourra être effectuée une fois ces décisions prises.

## Licence et contributions

La visibilité publique et la licence sont deux sujets distincts. Ce dépôt ne contient pas de fichier LICENSE et ne se déclare pas open source. Les droits sur les dépendances, modèles et documents importés devront aussi être examinés lorsqu’ils seront choisis. La [documentation GitHub](REFERENCES.md) fournit le point d’entrée pour décider.

Les modèles d’issue et de pull request facilitent la revue des choix sans donner accès à une infrastructure. Aucun CODEOWNERS ne doit être rempli avec un compte supposé.

## Automatisation du dépôt

Aucun workflow GitHub Actions n’est activé dans cette version documentaire. Un contrôle de liens ou de format pourra être ajouté après choix de ses outils, versions et permissions. Ne jamais transmettre des journaux de production à une CI publique. Ne pas afficher un badge de build ou de sécurité sans résultat réel associé.

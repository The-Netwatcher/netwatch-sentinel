# Données, preuves et recherche documentaire

Schémas et traitements proposés ; aucune base ni index n’est créé par cette documentation.

## Événements

Les exports Linux, les événements Windows et les pare-feu ont des formats distincts. La première source retenue déterminera le premier parseur. Ne pas prétendre qu’un format normalisé suffit à interpréter correctement tous les systèmes.

| Champ logique proposé | Sens | Règle envisagée |
| --- | --- | --- |
| `event_id` | Référence locale stable | Unique dans le lot, attribuée ou vérifiée par l’application |
| `occurred_at` | Temps déclaré par la source | UTC si conversion justifiée ; inconnue ou ambiguïté signalée |
| `ingested_at` | Temps d’import | Distinct du temps de l’événement |
| `source` | Type et provenance de la source | Origine déclarée et format conservés |
| `host_id` | Hôte concerné | Identifiant pseudonymisé si nécessaire |
| `category`, `event_type`, `outcome` | Classe de l’événement | Vocabulaire défini ; valeur inconnue possible |
| `principal_ref` | Compte concerné | Référence minimisée, jamais un mot de passe |
| `source_address` | Origine observée | Champ facultatif ; ne prouve pas l’identité d’une personne |
| `message` | Extrait utile | Non fiable, borné et minimisé |
| `synthetic` | Donnée entièrement fabriquée | Obligatoire et vrai pour les exemples publics de ce dépôt |

La clé de déduplication réelle sera définie par source. Un hash du message seul peut confondre des événements distincts ; il ne suffit pas. Conserver l’identifiant source et la position d’origine quand disponibles. Toute référence de preuve doit retrouver un événement dans l’instantané utilisé.

## Faits et interprétations

Les comptages et tris doivent être calculés par les outils, pas estimés par le modèle. Le modèle peut proposer une explication, mais doit l’identifier comme hypothèse. La restitution présente aussi le périmètre temporel, les sources absentes, les erreurs et les troncatures.

Éviter les pourcentages de confiance non calibrés. Décrire le niveau de preuve : faits observés, éléments concordants, informations manquantes. Une référence existante ne garantit pas que la phrase la décrit correctement ; cela doit être évalué et revu.

## RAG : rôle et progression

La génération augmentée par recherche consiste ici à fournir au modèle des passages retrouvés dans un corpus local sélectionné. Elle ne constitue pas un réentraînement. Un premier corpus de quelques procédures peut être parcouru par recherche simple avant de justifier un index vectoriel.

Chaîne envisagée : sélectionner et autoriser les documents, identifier versions et provenance, découper en sections stables, indexer si nécessaire, filtrer les droits avant recherche, retourner des extraits référencés, puis contrôler les références de la synthèse.

| Métadonnée documentaire | Utilité |
| --- | --- |
| Identifiant et version | Relier une recommandation à une procédure précise |
| Origine et date de révision | Évaluer la pertinence et la fraîcheur |
| Section et emplacement | Retrouver le passage utilisé |
| Statut d’approbation et périmètre d’accès | Éviter d’interroger des documents non autorisés |
| Empreinte disponible | Détecter un changement de la copie de référence |

Si des embeddings sont utilisés, choisir un modèle local et sa licence, puis mesurer qualité, coût mémoire et mise à jour. L’index est une copie dérivée potentiellement sensible. La suppression d’un document doit entraîner la suppression de ses passages, embeddings et caches associés.

Un document approuvé comme source n’est pas autorisé à modifier la politique de l’agent. Les données récupérées restent non fiables vis-à-vis des instructions et des outils.

## Conservation et publication

Distinguer données brutes, normalisées, index, contexte temporaire, audit, rapports et sauvegardes. Les durées et destinations restent à fixer dans D-010. La pseudonymisation conserve parfois des possibilités de rapprochement ; elle ne justifie pas la publication de journaux réels.

Le dépôt public prévu doit contenir uniquement documentation et données fabriquées. Les exemples d’adresses utilisent la plage documentaire `192.0.2.0/24`. Aucun nom de machine, compte ou événement réel du labo n’est nécessaire pour présenter le concept.

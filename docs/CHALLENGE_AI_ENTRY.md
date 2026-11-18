# Dossier de conception pour la catégorie AI Entry

Document de travail, pas un formulaire envoyé ni une confirmation d’éligibilité. L’intention de candidature est établie ; le détail du règlement doit être vérifié avant soumission.

## Présentation proposée

NetWatch Sentinel est un projet d’agent IA local pour aider un administrateur de petite structure à analyser des journaux système et de sécurité. Il vise à rapprocher les événements, consulter des procédures locales sélectionnées et produire un diagnostic sourcé avec ses limites. L’humain garde la décision et effectue les interventions nécessaires.

Le projet est au stade conception. La première tranche proposée porte sur des authentifications Linux exportées : l’agent choisirait des recherches autorisées dans un lot local, réévaluerait ses hypothèses puis produirait une chronologie et des recommandations. La collecte continue et la prise en charge de Windows Server et des pare-feu constituent des extensions à étudier après ce premier prototype.

## Pourquoi un agent local

La boucle envisagée adapte ses recherches aux preuves disponibles. Elle utilise des outils à périmètre limité plutôt qu’un terminal libre. Le traitement local viserait à éviter l’envoi de journaux ou de procédures à un service cloud pendant l’analyse. La maîtrise des permissions et des flux serait vérifiée par des essais, sans se limiter aux consignes du prompt.

## Cohérence matérielle

Le poste actuel avec RTX 5080 16 Go permettrait de démarrer les expérimentations. Une éventuelle RTX 5060 Ti 16 Go aiderait à construire une seconde machine dédiée à l’analyse, séparée des usages personnels et disponible indépendamment de ceux-ci. La configuration complète, l’isolation et les performances restent à établir. Aucun gain ne doit être présenté comme acquis.

## Éléments montrables aujourd’hui

| Élément | Preuve dans le dépôt | Ce que cela ne démontre pas |
| --- | --- | --- |
| Besoin et limites | [Vision](VISION_AND_SCOPE.md) | Adoption ou efficacité en entreprise |
| Architecture | [Composants](../architecture/TECHNICAL_DESIGN.md), [flux](../architecture/DATA_FLOW.md) | Système déjà intégré |
| Caractère agentique prévu | [Workflows](AGENT_WORKFLOWS.md), [contrats](TOOL_CONTRACTS.md) | Appels d’outils déjà exécutés |
| Attention portée à la sécurité | [Menaces](THREAT_MODEL.md), [sécurité](SECURITY_DESIGN.md) | Protection déjà éprouvée |
| Cas concret | [Exemple fictif](../examples/incident-review/SCENARIO.md) | Incident réel ou résultat d’un prototype |
| Faisabilité à vérifier | [Matériel](HARDWARE.md), [évaluation](EVALUATION_PLAN.md) | Benchmark ou disponibilité permanente |
| Progression | [Feuille de route](../ROADMAP.md), [décisions](DECISIONS.md) | Choix techniques tous validés |

## Contrôle avant soumission

- Relire le règlement et le formulaire correspondant exactement au challenge français.
- Vérifier catégorie AI Entry, dates, territoire, conditions d’éligibilité, pièces et liens acceptés.
- Vérifier les éventuelles exigences matérielles, logicielles et droits de présentation.
- Confirmer la place facultative ou obligatoire d’un dépôt GitHub à partir des consignes actuelles.
- Décrire fidèlement l’état de conception et les choix encore ouverts.
- Relire les fichiers pour éviter données privées, secrets et promesses non étayées.

## Références du concours

La [page officielle ASUS France](https://www.asus.com/microsite/agent-computer/fr/) contient une section « Agent Computer Challenge » et renvoie vers [le formulaire du challenge](https://gleam.io/SMomy/asus-agent-computer-challenge). Le 18 novembre 2026, ce renvoi a été retrouvé, mais le texte détaillé du formulaire et du règlement n’a pas été vérifié dans ce travail.

Les échanges antérieurs décrivaient GitHub comme non obligatoire pour AI Entry et mentionnaient une RTX 5060 Ti 16 Go et une PRIME B860-PLUS WIFI. Ces informations de contexte ne sont pas certifiées ici comme clauses actuelles du règlement. Aucune date limite, pondération du jury ou promesse de lot n’est présentée comme officiellement vérifiée dans ce dépôt.

# Exigences proposées et critères d’acceptation

Ces exigences définissent une cible à valider. Aucun critère n’a été exécuté sur une application NetWatch Sentinel.

| ID | Exigence proposée | Preuve attendue au prototype |
| --- | --- | --- |
| F-01 | Importer un lot d’événements dans un format défini | Import d’un lot valide ; rejet explicite d’un format invalide |
| F-02 | Conserver source, identifiant, temps et qualité de chaque événement | Chaque fait du rapport retrouve son événement d’origine |
| F-03 | Dédupliquer sans confondre deux événements distincts | Réimport du même lot sans doubler les résultats |
| F-04 | Proposer et exécuter des recherches autorisées selon les résultats | Trace d’au moins deux chemins différents selon les données |
| F-05 | Produire une chronologie et séparer faits et hypothèses | Rapport révisable avec références de preuves |
| F-06 | Présenter les informations manquantes et la fraîcheur des sources | Cas incomplet rendu comme incomplet |
| F-07 | Consulter une procédure locale identifiée, si intégrée | Référence à la version et à la section exactes ; aucun document inventé |
| F-08 | Permettre la revue humaine du rapport | Validation, rejet ou correction enregistré sans exécution corrective |
| S-01 | Ne disposer d’aucun outil de modification des systèmes dans le premier MVP | Appel de modification refusé par le moteur de politique |
| S-02 | Restreindre chaque outil à des données et arguments autorisés | Rejet d’un chemin, hôte ou filtre hors périmètre |
| S-03 | Traiter les journaux et documents comme des données non fiables | Scénario d’injection ne déclenchant ni privilège ni outil interdit |
| S-04 | Éviter l’envoi de données à un service cloud | Inférence et recherches fonctionnelles en runtime sans sortie Internet |
| S-05 | Limiter temps, appels, volumes et concurrence | Dépassement arrêté avec rapport partiel et motif |
| S-06 | Minimiser les données et protéger les stockages | Accès non autorisé refusé ; purge et restauration testées |
| S-07 | Journaliser les appels, refus et décisions de l’opérateur | Audit corrélé à un identifiant d’exécution |
| Q-01 | Fonctionner de manière explicite en cas d’indisponibilité du modèle | Aucune conclusion générée présentée comme réalisée |
| Q-02 | Vérifier la structure des sorties et l’existence des références | Rapport invalide ou référence inexistante bloqué avant export |
| Q-03 | Définir une expérience reproductible | Versions, modèle, configuration et lot d’essai enregistrés |

## Definition of done documentaire

- Le statut de conception est visible dès l’accueil.
- Les choix non validés sont marqués « proposés » ou « ouverts ».
- Chaque domaine demandé a un document et des liens locaux utilisables.
- Les références techniques pointent vers les éditeurs ou organismes sources.
- Les exemples sont entièrement fictifs et ne contiennent pas de secrets.
- Aucune performance ou protection non mesurée n’est présentée comme acquise.

## Definition of done du futur MVP

Après validation du périmètre : démonstration locale reproductible de F-01 à F-06 et F-08, des exigences S-01 à S-07 et Q-01 à Q-03 ; F-07 seulement si la phase documentaire est incluse. Les résultats réels, écarts et risques résiduels devront figurer dans un rapport d’évaluation. Aucun simple passage des exemples de cette version documentaire ne suffit à déclarer le MVP prêt.

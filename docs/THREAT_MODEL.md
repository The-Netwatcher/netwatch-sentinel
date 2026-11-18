# Modèle de menaces initial

Analyse de conception, sans validation pratique à ce stade. Périmètre initial : un opérateur local, un lot importé, des outils de consultation bornés et une inférence locale.

## Actifs et adversaires

Actifs : journaux, identités et adresses, procédures internes, intégrité des preuves et rapports, politique d’outils, secrets futurs des connecteurs et disponibilité de la station.

Adversaires ou causes de défaut : auteur d’un message de journal hostile, document empoisonné, utilisateur local non autorisé, dépendance compromise, erreur de configuration, modèle trompé ou incorrect. Une machine source compromise peut produire des journaux incomplets ou falsifiés.

## Risques et réponses proposées

| ID | Menace et chemin | Effet possible | Contrôle proposé | Vérification prévue |
| --- | --- | --- | --- | --- |
| T-01 | Instruction dans une ligne de log ou un document | Appel hors périmètre ou synthèse détournée | Données délimitées ; politique hors modèle ; catalogue fermé | EV-03 |
| T-02 | Chemin, identifiant ou filtre manipulé dans un appel | Lecture d’un autre dossier ou de données privées | Racines, types et identifiants autorisés ; refus des liens sortants | EV-04 |
| T-03 | Demande de commande ou remédiation | Modification d’un compte ou d’un service | Aucun outil de correction, aucune commande libre, compte limité | EV-05 |
| T-04 | Repli cloud, télémétrie ou sortie réseau inattendue | Exfiltration de journaux et documents | Runtime local, blocage réseau et vérification des sorties | EV-06 |
| T-05 | Faux liens de preuves ou interprétation sans support | Diagnostic trompeur | Existence des références, séparation des hypothèses, revue humaine | EV-02, EV-10 |
| T-06 | Lot immense, boucles, document surdimensionné | Déni de service, mémoire épuisée | Bornes d’entrée, résultats, appels, temps et concurrence | EV-07 |
| T-07 | Journaux ou audit modifiés après analyse | Perte de traçabilité | Instantané identifié, accès restreints, empreintes et sauvegardes à étudier | EV-09 |
| T-08 | Secrets conservés dans Git, index ou audit | Fuite persistante | Données fictives publiques, minimisation, exclusion et revue avant publication | EV-08 |
| T-09 | Modèle ou dépendance altéré lors de la maintenance | Exécution ou comportement compromis | Sources maîtrisées, versions et intégrité vérifiées | EV-11 |
| T-10 | Horloges, doublons ou collecte incomplète | Chronologie et comptages incorrects | Qualité des temps, provenance, déduplication, absence signalée | EV-01, EV-10 |
| T-11 | API locale exposée ou service trop privilégié | Accès non autorisé à l’analyse | Bouclage, compte limité ; identité et transport avant accès distant | EV-04, EV-06 |
| T-12 | Contenu HTML ou lien hostile dans le rapport | Action involontaire ou fuite au rendu | Échappement, rendu texte, aucun suivi automatique de liens | EV-03, EV-08 |

## Risques résiduels

Un modèle peut interpréter incorrectement des preuves réelles. Une injection peut altérer le texte sans obtenir d’appel interdit. Un opérateur peut accorder trop de confiance à la restitution. Une source compromise peut mentir de façon cohérente. Un administrateur de la station peut contourner des protections locales ou modifier un audit insuffisamment séparé.

Les contrôles doivent donc être évalués sur leurs effets observables, sans annoncer un système « inviolable » ou une détection exhaustive. Conserver la possibilité d’abstention, présenter la couverture et soumettre les conclusions à la revue humaine.

## Hors périmètre et révision

La gestion de plusieurs organisations, l’authentification distante, la collecte de production, l’exécution corrective et la haute disponibilité ne sont pas couvertes par ce premier périmètre. Réviser ce modèle à chaque ajout d’un connecteur, d’un outil, d’une interface exposée, d’un corpus ou d’un niveau d’autonomie.

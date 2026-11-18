# Vision et périmètre

## Besoin utilisateur

L’utilisateur cible serait un administrateur ou technicien d’une petite structure, confronté à des journaux fragmentés et disposant de peu de temps pour les analyser. NetWatch Sentinel l’aiderait à répondre à trois questions : que montrent réellement les données, quelles explications restent plausibles et quelle vérification effectuer ensuite ?

La valeur attendue tient à la mise en relation des preuves et à la préparation d’un diagnostic. Elle devra être mesurée face à une lecture manuelle et à une simple règle de corrélation. Aucun gain n’est encore démontré.

## Vision à terme

Un assistant local pourrait rapprocher des événements Windows Server, Linux et pare-feu, retrouver une procédure interne, effectuer des diagnostics autorisés en lecture seule et produire une restitution exploitable. Le traitement local viserait à garder les journaux et procédures dans l’environnement de l’organisation.

Cette cible ne constitue pas une promesse de prise en charge complète de ces environnements. Chaque connecteur nécessitera des permissions, des tests et une décision distincts.

## Première tranche proposée : analyse d’un lot d’authentifications Linux

Entrée : fichier d’événements synthétiques ou anonymisés, importé manuellement. Objectif : examiner une série d’échecs suivie ou non d’une connexion réussie. Sortie : chronologie, faits cités, hypothèses, contexte manquant et recommandations de vérification.

Cette tranche évite de commencer simultanément par la collecte réseau, les comptes privilégiés et l’inférence. Elle permet d’évaluer le raisonnement et la traçabilité avant d’accorder un accès à un système vivant. Elle reste à valider dans D-001.

| Inclus dans la proposition initiale | Reporté ou exclu |
| --- | --- |
| Import manuel d’un petit lot borné | Collecte continue, volumétrie de production |
| Normalisation et qualité des horodatages | Correction automatique des horloges des machines |
| Recherche dans les données importées | Exploration du réseau ou scan d’actifs |
| Choix borné d’outils de consultation | Terminal arbitraire, SSH libre, exécution de code généré |
| Rapport et validation humaine | Blocage d’adresse, désactivation de compte, modification du pare-feu |
| Procédure locale sélectionnée si utile | Téléchargement automatique de documents depuis le Web |
| Données fictives publiques | Journaux réels dans le dépôt ou dans GitHub Actions |

## Trois usages à distinguer

1. **Prototype de laboratoire** : lot importé, un utilisateur, outils sur un instantané local.
2. **Pilote de surveillance** : collecte et diagnostics sur des actifs explicitement autorisés ; nouveau modèle de menace requis.
3. **Service pour une PME** : disponibilité, identité des utilisateurs, sauvegarde, exploitation et vérification des obligations applicables ; validation supplémentaire requise.

## Limites

Le projet ne remplace pas les contrôles de sécurité existants, un antivirus, un EDR, un SIEM ou une équipe de réponse à incident. Il ne peut conclure à une compromission sur la seule présence d’échecs suivis d’un succès. Une absence d’événement n’est pas une preuve d’absence d’incident.

Un résultat utile doit pouvoir dire « données insuffisantes » et expliquer ce qui manque. La couverture est limitée aux sources effectivement fournies, à leur fiabilité et à leur fraîcheur.

## Première validation attendue

Accepter, modifier ou refuser D-001 : commencer par les authentifications Linux exportées, avec rapport sourcé et aucune action de correction exécutée par l’agent. Le langage, le moteur IA et le modèle seront examinés ensuite.

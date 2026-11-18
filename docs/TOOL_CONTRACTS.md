# Contrats proposés pour les outils

Ces interfaces décrivent des outils à développer, pas des API existantes. Leur nom et leur schéma seront validés avec le langage choisi.

## Enveloppe commune

L’application associe chaque appel à un `run_id`, au lot autorisé, à la politique et au budget. Ces valeurs viennent de l’état serveur ou du processus ; elles ne sont pas acceptées comme une extension de permission fournie par le modèle.

L’appel proposé contient un nom dans une liste fermée et un objet d’arguments strict. Rejeter les champs inconnus, types incorrects, dates hors fenêtre, volumes excessifs et identifiants absents. Le validateur ne transforme jamais une chaîne en commande.

Le retour contient un statut, des résultats bornés, les identifiants de preuves, les limites ou troncatures et la fraîcheur. Une liste vide et un échec d’outil sont deux états différents.

## Catalogue du premier prototype proposé

| Outil | Arguments logiques | Accès | Sortie et contrôle |
| --- | --- | --- | --- |
| `query_events` | Fenêtre, hôte autorisé, type, compte, origine, limite | Lecture de l’instantané sélectionné | Événements et identifiants ; pagination/troncature explicites |
| `summarize_auth_window` | Fenêtre et dimensions dans une liste fermée | Agrégats sur le même instantané | Comptes d’échecs/succès calculés par le code, preuves associées |
| `search_runbooks` | Requête courte et nombre de résultats borné | Corpus autorisé uniquement | Identifiants, versions et passages ; aucun accès Web |
| `read_runbook_section` | Identifiant de document et section existants | Document déjà autorisé | Passage exact et provenance ; aucun chemin libre |

Les deux outils documentaires sont optionnels selon D-008. L’export d’un rapport est une fonction applicative avec destination fixée par l’opérateur, pas un outil d’écriture libre accordé au modèle.

## Politique de refus

| Demande | Réponse cible |
| --- | --- |
| Outil inconnu ou appel de shell | Refus `TOOL_NOT_ALLOWED` |
| Identifiant de lot ou hôte hors périmètre | Refus `OUT_OF_SCOPE` |
| Chemin arbitraire, traversée de répertoires, lien sortant | Refus `PATH_NOT_ALLOWED` |
| URL ou destination réseau fournie dans une donnée | Refus : aucun outil réseau générique dans le premier MVP |
| Modification d’utilisateur, service ou pare-feu | Refus `WRITE_OPERATION_FORBIDDEN` |
| Argument invalide | Refus `INVALID_ARGUMENTS`, sans correction permissive automatique |
| Dépassement du budget | Refus `BUDGET_EXCEEDED`, sortie partielle |
| Contrôle ou audit en défaut | Arrêt `CONTROL_UNAVAILABLE` |

Ne pas exposer `exec`, `eval`, un terminal, un navigateur libre, un client HTTP libre, une requête SQL libre, un chemin d’écriture libre ou une commande distante au modèle. Les futurs outils vivants auront des paramètres fermés et des permissions spécifiques, à examiner séparément.

## Répétabilité et limites

Les lectures d’un même instantané doivent donner les mêmes résultats structurés pour les mêmes filtres. Le texte du modèle peut varier. Une recherche plus large reste soumise au périmètre initial ; elle ne peut pas « découvrir » une autorisation.

Le compte de lecture ne possède aucun secret d’administration des systèmes. Pour une extension réseau, les références de secrets seraient résolues côté outil ; leur valeur ne serait jamais transmise au modèle ni écrite dans le rapport.

# Rapport fictif attendu — DEMO-001

**Rédigé pour illustrer la conception. Aucun agent ne l’a généré.**

| Champ | Valeur fictive |
| --- | --- |
| Périmètre | `lab-linux-01`, 1er novembre 2026, 08:00–08:03 UTC |
| Source | events.jsonl, sept événements fabriqués |
| Couverture | Six événements d’authentification, un message applicatif ; aucune autre preuve |
| État | Revue humaine attendue ; aucune intervention exécutée |

## Faits observables

Cinq échecs d’authentification concernent `demo-user` depuis `192.0.2.44`, entre 08:00:00 et 08:01:20 UTC : [evt-001 à evt-005](events.jsonl). Un événement de succès pour le même compte et la même origine apparaît à 08:02:00 UTC : [evt-006](events.jsonl).

Un message applicatif contient une demande de commande administrateur : [evt-007](events.jsonl). Cette demande fait partie des données non fiables ; elle ne constitue pas une consigne autorisée.

## Hypothèses et limites

La séquence justifie une vérification. Elle pourrait correspondre à des erreurs de saisie suivies d’une connexion légitime, ou à une tentative non autorisée ayant abouti. Ce lot ne permet pas de départager ces hypothèses ni d’attribuer l’action à une personne.

Nous ne disposons pas d’inventaire des origines attendues, de confirmation de l’utilisateur, de données de session ou d’alertes complémentaires. Les journaux fournis sont synthétiques ; ils ne témoignent d’aucun incident réel.

## Vérifications recommandées à l’administrateur

Confirmer si l’accès était attendu, comparer les autres preuves disponibles sur le même compte et la même fenêtre et documenter les sources manquantes. Ces pistes correspondent à [RB-AUTH-001, version 0.1, section Vérifications](RUNBOOK.md#vérifications), procédure pédagogique de ce scénario.

Aucun blocage, changement de compte ou commande n’est proposé à l’exécution automatique. La validation éventuelle porte sur le rapport et son interprétation.

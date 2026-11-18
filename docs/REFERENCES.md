# Sources et provenance

Références consultées le 18 novembre 2026. Elles étayent l’étude des options ; elles ne valident ni l’implémentation ni les performances de NetWatch Sentinel.

## Références primaires

| Source | Usage dans le projet | Limite |
| --- | --- | --- |
| [ASUS Agent Computer France](https://www.asus.com/microsite/agent-computer/fr/) | Orientation IA locale et renvoi vers le challenge | Le contenu promotionnel n’est pas le règlement détaillé |
| [Formulaire ASUS Agent Computer Challenge](https://gleam.io/SMomy/asus-agent-computer-challenge) | Destination officielle liée par ASUS | Lien identifié ; contenu détaillé non vérifié dans ce travail |
| [Ollama — FAQ locale](https://docs.ollama.com/faq) | Option de désactivation cloud, liaison locale de l’API, configuration | Réglages à valider sur la version effectivement retenue ; pas une preuve de blocage réseau |
| [Ollama — Tool calling](https://docs.ollama.com/capabilities/tool-calling) | Étude des appels d’outils | La permission d’exécuter un outil reste contrôlée par l’application |
| [Ollama — Structured outputs](https://docs.ollama.com/capabilities/structured-outputs) | Étude d’une structure de sortie contrainte | Un format valide ne prouve pas l’exactitude des faits |
| [Ollama — Hardware support](https://docs.ollama.com/gpu) | Présence des familles de GPU envisagées dans la documentation | Compatibilité et performances du montage réel à mesurer |
| [OWASP — LLM01 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) | Injection via contenu externe et limites du RAG comme protection | Référence de risques ; aucune certification du projet |
| [GitHub — Licensing a repository](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository) | Séparation visibilité et choix d’une licence | Licence du projet encore ouverte |
| [IETF — RFC 5737](https://www.rfc-editor.org/rfc/rfc5737.html) | Plages IPv4 réservées aux exemples | L’adresse des exemples ne vise aucun actif réel |

## Provenance des choix

Les échanges précédents ont fourni le nom retenu, l’intention AI Entry, le stade de conception et l’objectif d’une station dédiée. Ils ont aussi fourni des propositions antérieures de l’assistant : agent local pour PME, journaux Windows/Linux/pare-feu, Python, Ollama, RAG et diagnostics en lecture seule. Ces propositions restent ouvertes dans le [registre](DECISIONS.md).

Le premier cas Linux importé, les contrats d’outils, les budgets et le découpage des jalons sont de nouvelles propositions de conception de cette version. Les fichiers d’exemple ont été fabriqués pour illustrer cette proposition. Aucun contenu d’ECF, capture privée ou journal réel n’a été intégré.

## Informations restant à vérifier

Règlement complet du concours ; identité et visibilité GitHub ; licences du dépôt et des futurs modèles ; configuration matérielle exacte de la station ; OS et accès GPU ; performances ; durées de conservation. Toute décision doit préciser les versions et conditions réellement testées.

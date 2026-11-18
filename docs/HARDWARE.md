# Faisabilité et rôle du matériel

Étude de conception. Aucun benchmark NetWatch Sentinel n’a été exécuté et aucune configuration complète de station dédiée n’a été validée.

## Contexte et intention

| Élément | Situation | Rôle envisagé |
| --- | --- | --- |
| RTX 5080 16 Go existante | Matériel disponible indiqué par William | Développement et premières mesures sur le poste actuel |
| RTX 5060 Ti 16 Go éventuelle | Matériel associé à la candidature selon les échanges ; attribution non acquise | Inférence sur une seconde machine dédiée, si assemblage réalisable |
| Plateforme de la seconde machine | CPU, RAM, SSD, alimentation et OS non arrêtés | Dimensionnement après mesure et vérification des compatibilités |
| Machines du laboratoire | Environnements Windows Server/Linux déjà pratiqués | Sources d’exports pour la validation, puis éventuels connecteurs autorisés |

L’inventaire du PC portable ne doit pas être transposé au PC fixe. Le CPU, la RAM et les disques de la future station ne sont pas déduits des caractéristiques d’une autre machine.

## Pourquoi une seconde station

L’objectif serait de séparer le poste personnel et de création du service d’analyse, avec une configuration plus stable et une disponibilité indépendante des sessions de jeu. L’isolation exige une configuration des comptes, stockages, réseaux et accès d’administration. Une carte supplémentaire dans le poste existant ne suffit pas à la créer.

Le projet doit pouvoir commencer avec la RTX 5080 actuelle. L’éventuel gain matériel faciliterait une évolution vers une station dédiée ; il n’est pas présenté comme indispensable à la conception ni comme une augmentation de VRAM par rapport aux 16 Go déjà disponibles.

## Budget mémoire

L’occupation dépend des poids du modèle, de la quantification, du contexte, du cache d’inférence, de la concurrence et des autres processus GPU. La VRAM nominale ne garantit pas qu’un modèle, ses outils et une longue fenêtre de contexte tiennent entièrement en mémoire.

Les modèles de génération et d’embeddings pourraient être exécutés séquentiellement. Aucun entraînement, fine-tuning, modèle de taille imposée ou multi-GPU n’est requis par la proposition initiale.

La documentation d’Ollama répertorie les RTX 5060 Ti et RTX 5080 parmi les cartes prises en charge. Cela ne démontre pas les performances du projet ni la compatibilité de toute configuration de virtualisation. Vérifier les versions du pilote, du moteur et du système sur la machine retenue avant essai ; voir les [sources](REFERENCES.md).

## Mesures à obtenir avant choix d’un modèle

| Mesure | Méthode envisagée | Résultat disponible |
| --- | --- | --- |
| VRAM et RAM maximales | Observer au chargement et pendant le scénario borné | Aucun |
| Temps de chargement et de rapport | Distinguer démarrage à froid et analyse à chaud | Aucun |
| Respect du format et des appels | Même corpus, mêmes outils, plusieurs exécutions | Aucun |
| Qualité des faits et des références | Comparaison avec une vérité terrain annotée | Aucun |
| Débit et concurrence | Commencer avec une seule analyse ; augmenter seulement si utile | Aucun |
| Stabilité prolongée | Essais répétés avec journalisation des erreurs | Aucun |
| Consommation et bruit, si pertinents | Mesure à la prise et conditions documentées | Aucun |

Définir ensuite une configuration cible réaliste. Aucune promesse de fonctionnement permanent, de coût inférieur, de latence ou d’économie d’énergie ne doit remplacer ces mesures.

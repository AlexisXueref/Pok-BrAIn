
📸 Pokémon Card Detector
=========================

Ce projet utilise une webcam et un modèle TorchScript pour reconnaître en temps réel des cartes Pokémon placées devant l'objectif.

Structure du projet :
---------------------
pokemon-card-director/
│
├── model/
│   └── model_traced.pt         # Modèle TorchScript entraîné
│
├── data/
│   └── labels.txt              # Liste des noms de classes (une par ligne)
│
├── predi_camera.py             # Script principal de détection
└── README.txt                  # Ce fichier

Prérequis :
-----------
Installe les dépendances nécessaires avec :

    pip install torch torchvision opencv-python Pillow

Lancement :
-----------
Assure-toi d’avoir une webcam connectée, puis exécute :

    python predi_camera.py

- Appuie sur [q] pour quitter l'application.
- Une boîte verte s’affichera au centre de la webcam : place la carte dans cette zone pour qu’elle soit analysée.

Modèle :
--------
- Le fichier `model/model_traced.pt` est un modèle TorchScript optimisé pour l’inférence.
- Il prend en entrée des images redimensionnées à 224×224 et prétraitées avec la normalisation standard d’ImageNet.
- Le fichier `data/labels.txt` contient les noms des classes, une par ligne.

Fonctionnement :
----------------
1. Capture de l’image via la webcam.
2. Extraction d’une zone centrale (300×420) contenant la carte.
3. Conversion et prétraitement de l’image.
4. Prédiction via le modèle.
5. Affichage en direct de l’étiquette prédite et du pourcentage de confiance.

Exemple de sortie :
-------------------
    🔍 Carte détectée : Pikachu (92.4%)

Améliorations possibles :
-------------------------
- Ajout de la sauvegarde automatique de l’image et de la prédiction.
- Intégration dans un inventaire local.
- Support du traitement en lot (dossiers d’images).

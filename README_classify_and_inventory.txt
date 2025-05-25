📦 classify_and_inventory.py

Ce script Python permet de classifier automatiquement des cartes Pokémon à partir d’images, puis de générer un inventaire chiffré (quantité, valeur unitaire, valeur totale) en s'appuyant sur un modèle de Deep Learning et des métadonnées issues d'une base de données JSON.

--------------------------------------------------
🚀 Fonctionnement

1. Chargement du modèle de classification TorchScript (`model_traced.pt`).
2. Parcours de tous les fichiers `.jpg`, `.jpeg` ou `.png` du répertoire courant.
3. Classification de chaque image → obtention d’un label de type `Nom_set-id`.
4. Recherche de la valeur estimée (prix moyen) dans le fichier `metadata.json`.
5. Création d’un inventaire local avec le nombre d’exemplaires détectés par carte.
6. Sauvegarde automatique de l'inventaire dans `outputs/inventaire.csv`.

--------------------------------------------------
📁 Structure requise

project/
│
├── classify_and_inventory.py       <- Script principal
├── model/
│   └── model_traced.pt             <- Modèle entraîné (TorchScript)
├── data/
│   ├── labels.txt                  <- Liste des classes (une par ligne)
│   └── metadata.json               <- Métadonnées contenant les prix
└── outputs/
    └── inventaire.csv              <- Fichier généré automatiquement

--------------------------------------------------
📷 Exemple d'exécution

✅ Fichier metadata chargé.
📷 Image 'charizard.jpg' classifiée comme : Charizard_cel25c-4_A
🧾 Carte: Charizard_cel25c-4_A | Valeur: 110.0 € | Total: 1
📷 Image 'tepig.jpg' classifiée comme : Tepig_bw1-15
🧾 Carte: Tepig_bw1-15 | Valeur: 0.74 € | Total: 1

=== 🗃️ Inventaire final ===
Charizard_cel25c-4_A : 1 exemplaire(s), valeur unitaire : 110.0 €
Tepig_bw1-15 : 1 exemplaire(s), valeur unitaire : 0.74 €
💾 Inventaire sauvegardé dans 'outputs/inventaire.csv'

--------------------------------------------------
📄 Format du fichier CSV

Le fichier `outputs/inventaire.csv` contient :

Nom de carte             | Quantité | Valeur unitaire (€) | Valeur totale (€)
------------------------|----------|----------------------|-------------------
Charizard_cel25c-4_A     | 1        | 110.0                | 110.0
Tepig_bw1-15             | 1        | 0.74                 | 0.74

--------------------------------------------------
✅ Pré-requis

- Python 3.8+
- PyTorch
- torchvision
- PIL (Pillow)

Installez les dépendances avec :
pip install torch torchvision pillow

--------------------------------------------------
📌 Remarques

- Les images doivent être placées dans le même dossier que le script.
- Le script ignore les images déjà classées dans un inventaire.
- Le fichier `metadata.json` doit contenir les identifiants et prix des cartes.

--------------------------------------------------
🛠️ À venir

- Export JSON de l'inventaire
- Interface graphique simplifiée
- Intégration directe à une base SQLite ou NoSQL
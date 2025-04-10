# Projet-Clustering-d-images-
🧠 Image Clustering avec SIFT, Autoencodeur et Histogramme de Couleur
🔍 Objectif du projet
Ce projet a pour objectif de regrouper automatiquement des images similaires (clustering non supervisé) en combinant plusieurs descripteurs d’images :

SIFT pour les caractéristiques locales,

Histogrammes de couleur pour l'information chromatique,

Autoencodeur convolutionnel pour une représentation globale profonde.

📸 Présentation générale
À partir d'un dossier contenant des images classées par dossier (classe réelle), le pipeline extrait les features de chaque image, les combine, applique une réduction de dimension (UMAP), puis effectue le clustering avec différentes méthodes (KMeans, Agglomerative, DBSCAN).

🧱 Descripteurs utilisés
Descripteur	Rôle
🧩 SIFT	Détecte les points clés (formes, motifs locaux)
🎨 Histogramme	Capture la distribution des couleurs (HSV)
🧠 Autoencodeur	Apprend une compression intelligente de l'image
Ces descripteurs sont concatenés pour créer une signature riche et robuste pour chaque image.

🧪 Techniques utilisées
Clustering non supervisé : KMeans, Agglomerative Clustering, DBSCAN
Détection des outliers : Isolation Forest
Réduction de dimension : UMAP
Autoencodeur convolutionnel : TensorFlow / Keras

📊 Métriques d’évaluation
Chaque méthode de clustering est évaluée avec les scores suivants :
Adjusted Rand Index (ARI)
Jaccard Index
Homogeneity, Completeness, V-Measure
Adjusted Mutual Information
Silhouette Score (si applicable)

Les résultats sont enregistrés automatiquement dans un fichier CSV (results.csv) pour faciliter la visualisation.

💻 Fonctionnement du pipeline
bash
Copier
Modifier
python pipeline.py

Ce script :
Charge toutes les images depuis le dossier static/images/test
Extrait les features avec SIFT, AE et histogramme
Supprime les outliers
Réduit les dimensions avec UMAP
Applique plusieurs modèles de clustering
Évalue les performances
Sauvegarde les résultats

📁 Structure du projet
Clustering_Project/
│
├── static/images/test/        # Dossier contenant les sous-dossiers d’images (par classe)
├── pipeline.py                # Pipeline principal
├── dashboard.py               # (Optionnel) Visualisation Streamlit
├── results.csv                # Résultats sauvegardés
├── reduced_features.npy       # Données UMAP compressées
├── labels.npy                 # Labels de clustering

✅ Résultats observés
La combinaison des descripteurs améliore nettement les résultats par rapport à l’utilisation d’un seul descripteur.
L’agglomerative clustering donne de bons scores de V-Measure et d’homogeneity.
L’autoencodeur permet d’extraire des représentations profondes et utiles même sur de petites images.

🚀 Améliorations possibles
Ajouter d’autres descripteurs (HOG, LBP, CLIP)
Optimisation automatique des hyperparamètres (k, eps, etc.)
Visualisation interactive des clusters en 3D
Support pour images non classées (réelles données non supervisées)

🛠️ Technos utilisées
Python
OpenCV (SIFT)
Scikit-learn (clustering, évaluation)
UMAP-learn
TensorFlow / Keras (autoencodeur)
Pandas / NumPy
(optionnel) Streamlit pour le dashboard

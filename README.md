# Prédiction des catastrophes naturelles et analyse des risques

## 1. Présentation du projet

Ce projet applique des techniques de **Data Mining** à l’analyse des catastrophes naturelles. Il vise à explorer les caractéristiques des événements, à regrouper les catastrophes similaires et à construire des modèles de classification capables de distinguer les événements sévères des événements moins sévères.

Le projet est réalisé en Python dans un notebook Jupyter.

## 2. Objectifs

- Nettoyer et préparer les données.
- Réaliser une analyse exploratoire des données (EDA).
- Étudier les distributions et les valeurs extrêmes.
- Regrouper les catastrophes à l’aide de l’algorithme **K-Means**.
- Comparer plusieurs modèles de classification supervisée.
- Évaluer les modèles avec des métriques adaptées à la classification.

## 3. Méthodes et outils

### Prétraitement des données
- Traitement des valeurs manquantes.
- Suppression des doublons.
- Correction des types de données.
- Traitement des valeurs extrêmes par *capping*.
- Création de variables dérivées et transformation logarithmique des dommages économiques.
- Encodage des variables catégorielles.

### Clustering
L’algorithme **K-Means** est utilisé pour regrouper les catastrophes présentant des caractéristiques similaires. Le nombre de clusters est étudié à l’aide de la méthode du coude (*Elbow Method*) et du score de silhouette.

### Classification
Les modèles suivants sont comparés :
- Régression logistique (*Logistic Regression*)
- Arbre de décision (*Decision Tree*)
- Forêt aléatoire (*Random Forest*)
- Gradient Boosting

La variable cible `Severe` vaut `1` lorsque le nombre de décès est supérieur à 100, et `0` dans le cas contraire. Ce seuil constitue une règle définie pour ce projet ; il ne représente pas une définition universelle de la gravité d’une catastrophe.

Les performances de validation sont comparées à l’aide de l’Accuracy, de la Precision, du Recall et du F1-score. Le jeu de test final est réservé à l’évaluation du modèle sélectionné.

## 4. Technologies utilisées

- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- scikit-learn

## 5. Structure du dépôt

```text
projet-data-mining-catastrophes/
├── notebooks/projet_data_mining_catastrophes_naturelles.ipynb
├── data/natural_disasters.csv
├── requirements.txt
└── README.md
```

Le fichier `natural_disasters.csv` contient les données nécessaires à l’exécution du notebook. Il n’est pas inclus automatiquement dans ce dépôt : ajoutez-le uniquement si sa licence et ses conditions de partage l’autorisent. Sinon, indiquez dans cette section la source officielle et les instructions pour obtenir les données.

## 6. Données attendues

Le notebook lit le fichier `natural_disasters.csv` situé dans le même dossier que le notebook.

Les colonnes attendues comprennent notamment :
- `Year` : année de l’événement ;
- `Disaster_Type` : type de catastrophe ;
- `Total_Deaths` : nombre total de décès ;
- `Total_Damages_000_US$` : dommages économiques, selon l’unité indiquée dans le nom de la colonne de la source.

Vérifiez les noms et les unités des colonnes dans le fichier d’origine avant l’exécution. Le notebook renomme la colonne des dommages en `Damage_Thousands_USD` pour rendre l’unité plus explicite.

## 7. Installation

Python 3.10 ou une version plus récente est recommandé.

### Étape 1 — Cloner ou télécharger le dépôt

Si le projet est hébergé sur GitHub :

```bash
git clone URL_DU_DEPOT
cd NOM_DU_DEPOT
```

Remplacez `URL_DU_DEPOT` et `NOM_DU_DEPOT` par les informations réelles du dépôt.

### Étape 2 — Créer un environnement virtuel (recommandé)

Sous Windows :

```bash
python -m venv .venv
.venv\Scripts\activate
```

Sous macOS ou Linux :

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Étape 3 — Installer les dépendances

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Étape 4 — Ajouter les données

Placez `natural_disasters.csv` dans le même dossier que le notebook, en respectant ce nom de fichier, ou adaptez le chemin dans le notebook.

### Étape 5 — Exécuter le notebook

Ouvrez le notebook dans Jupyter Notebook ou Visual Studio Code, puis exécutez les cellules dans l’ordre.

Pour lancer Jupyter Notebook si nécessaire :

```bash
pip install notebook
jupyter notebook
```

`notebook` est nécessaire uniquement si vous souhaitez utiliser l’interface Jupyter classique ; Visual Studio Code peut aussi exécuter le notebook avec son extension Python/Jupyter.

## 8. Évaluation

Les modèles de classification sont comparés à partir des métriques suivantes :
- **Accuracy** : proportion de prédictions correctes ;
- **Precision** : proportion de prédictions positives qui sont correctes ;
- **Recall** : proportion des événements sévères correctement détectés ;
- **F1-score** : moyenne harmonique de la précision et du rappel.

Les résultats numériques et le modèle le plus performant doivent être générés en exécutant le notebook avec le jeu de données utilisé. Ils ne sont pas indiqués ici afin de ne pas annoncer de résultats non vérifiés.

## 9. Limites et pistes d’amélioration

- Le seuil de 100 décès utilisé pour définir `Severe` est une règle propre au projet.
- Le remplacement des dommages manquants par zéro doit être justifié par la source des données ; une valeur manquante ne signifie pas nécessairement zéro dommage.
- Les variables disponibles peuvent limiter la capacité à identifier la sévérité d’un événement.
- Les résultats dépendent de la qualité, de la couverture et de la représentativité du jeu de données.
- Le modèle classe la sévérité à partir des variables disponibles ; il ne prédit pas directement la date ou l’occurrence future des catastrophes.

Pistes d’amélioration :
- enrichir le jeu de données avec des variables géographiques, climatiques et socio-économiques ;
- comparer d’autres modèles et stratégies de validation ;
- examiner l’importance des variables ;
- étudier les erreurs de classification et le compromis entre faux positifs et faux négatifs.

## 10. Auteure

**Sarra Askri**

Projet académique de Data Mining — année universitaire 2025–2026.

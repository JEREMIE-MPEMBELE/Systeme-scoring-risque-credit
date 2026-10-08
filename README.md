
```markdown
# 🏦 Système de Scoring de Risque de Crédit (Credit Scoring)

Pipeline de Machine Learning de niveau professionnel conçu pour prédire le risque de défaut de paiement sur un jeu de données bancaire de 150 000 lignes. Ce projet se concentre sur une méthodologie rigoureuse de traitement du déséquilibre des classes, l'optimisation des hyperparamètres et l'analyse critique des compromis entre métriques financières.

---

## 🚀 Aperçu du Projet

En milieu bancaire, l'évaluation du risque de crédit est un enjeu critique. Ce projet implémente un pipeline d'analyse complet dans un environnement Jupyter Notebook, priorisant la robustesse méthodologique et l'auditabilité plutôt qu'une mise en production logicielle complexe.

### 📊 Caractéristiques du Dataset & Défis
* **Volume :** ~150 000 lignes de données financières.
* **Déséquilibre extrême :** Taux de défaut de paiement d'environ **6.7%** (classe minoritaire).
* **Qualité des données :** Traitement des valeurs aberrantes (ex: âges à 0), imputation par la médiane pour les revenus, et gestion d'une forte multicolinéarité entre les variables de retard de paiement.

---

## 🛠️ Stack Technique & Méthodologie

* **Langage :** Python
* **Manipulation & Analyse :** Pandas, NumPy
* **Machine Learning :** Scikit-Learn, Imbalanced-Learn (`imblearn`)
* **Modélisation :** Random Forest Classifier couplé à **SMOTE** pour le sur-échantillonnage de la classe minoritaire.
* **Sécurité Anti-Leakage :** Utilisation stricte de `Pipeline` pour intégrer SMOTE directement au sein de la validation croisée et éviter toute fuite de données (*data leakage*).
* **Optimisation :** `RandomizedSearchCV` pour le réglage des hyperparamètres (Score **ROC-AUC : 0.8416**).
* **Sérialisation :** Sauvegarde du modèle via `joblib` pour l'analyse de portefeuille et l'audit à la demande.

---

## 📈 Résultats et Analyse Métier

L'évaluation du modèle met en lumière la réalité du terrain en milieu bancaire (le compromis Précision vs Rappel) :
* **Capacité discriminante globale :** Un solide score **ROC-AUC de 0.8416**.
* **Matrice de Confusion & Compromis :** 
  * Un bon **rappel (~69%)** permettant de capturer un maximum de défauts réels (1 378 vrais défauts détectés).
  * Un volume de **4 837 faux positifs** (clients sains étiquetés à tort comme risqués), illustrant l'arbitrage difficile entre la minimisation des impayés et la préservation de la relation client/chiffre d'affaires.

---

## 📂 Structure du Projet

```text
Systeme_scoring_risque_credit/
│
├── backend/
│   └── models/
│       └── credit_scoring_model.pkl  # Modèle final sérialisé
│
├── notebooks/                        # Notebooks d'EDA et de modélisation
├── credit_env/                       # Environnement virtuel Python (ignoré par Git)
├── .gitignore
└── README.md

```

---

## ⚙️ Installation et Utilisation

1. **Cloner le dépôt :**
```bash
git clone [https://github.com/ton-nom-utilisateur/Systeme_scoring_risque_credit.git](https://github.com/ton-nom-utilisateur/Systeme_scoring_risque_credit.git)
cd Systeme_scoring_risque_credit

```


2. **Créer et activer l'environnement virtuel :**
```bash
python -m venv credit_env
# Sur Windows :
credit_env\Scripts\activate
# Sur Mac/Linux :
source credit_env/bin/activate

```


3. **Installer les dépendances :**
```bash
pip install pandas numpy scikit-learn imbalanced-learn matplotlib joblib jupyter

```


4. **Lancer Jupyter Notebook :**
```bash
jupyter notebook

```

-

```

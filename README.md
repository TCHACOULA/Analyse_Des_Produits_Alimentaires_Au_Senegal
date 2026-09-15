# Analyse_Des_Produits_Alimentaires_Au_Senegal

## 📌 Présentation du projet

La sécurité alimentaire au Sénégal dépend fortement de la **stabilité et de l'accessibilité des prix des produits alimentaires de base**.

Les chocs climatiques, les difficultés logistiques, l'inflation des matières premières et les perturbations des chaînes d'approvisionnement peuvent entraîner des variations importantes des prix et affecter directement le pouvoir d'achat des ménages.

Ce projet propose une **analyse exploratoire, statistique, temporelle et géographique des prix alimentaires au Sénégal**, à partir des données du **World Food Programme (WFP)**.

L'objectif est d'identifier :

* les produits les plus chers ;
* les produits présentant la plus forte volatilité ;
* les régions et départements les plus exposés ;
* les marchés présentant les niveaux de prix extrêmes ;
* l'évolution des prix dans le temps ;
* les changements intervenus avant et après 2020 ;
* les différences entre catégories de produits ;
* les indicateurs pouvant être intégrés dans un **dashboard Power BI d'aide à la décision**.

---

# 🎯 Objectifs de l'analyse

L'étude répond à plusieurs questions métier.

### 1. Analyse des prix

* Quels sont les produits les plus chers ?
* Quels marchés présentent les prix maximums ?
* Quelles régions affichent les prix moyens les plus élevés ?

### 2. Analyse de la volatilité

* Quels produits sont les plus volatils ?
* Quels départements présentent les plus fortes fluctuations ?
* La volatilité est-elle concentrée dans certaines zones ?

### 3. Analyse temporelle

* Comment les prix ont-ils évolué depuis 2000 ?
* Existe-t-il des ruptures ou périodes de forte inflation ?
* Quels produits ont le plus augmenté après 2020 ?

### 4. Analyse géographique

* Quelles sont les zones structurellement les plus chères ?
* Quels marchés présentent les niveaux de prix les plus faibles ?
* Existe-t-il des écarts importants entre marchés ?

### 5. Aide à la décision

L'analyse vise également à produire des indicateurs exploitables par :

* les autorités publiques ;
* les ONG ;
* les programmes de sécurité alimentaire ;
* les acteurs du suivi des marchés ;
* les décideurs et responsables de programmes.

---

# 📊 Données

Le projet utilise le fichier :

```text
wfp_food_prices_sen.csv
```

Les données proviennent du **World Food Programme (WFP)** et correspondent au suivi des prix de détail des produits alimentaires sur les marchés sénégalais.

## Principales caractéristiques

| Indicateur              |                       Valeur |
| ----------------------- | ---------------------------: |
| Nombre d'observations   |                   **50 060** |
| Période                 | **Janvier 2000 – Mars 2026** |
| Régions (`admin1`)      |                       **14** |
| Départements (`admin2`) |                       **34** |
| Marchés suivis          |                       **64** |
| Catégories de produits  |                        **2** |
| Produits suivis         |                       **12** |
| Type de prix            |                   **Retail** |
| Unité                   |                       **KG** |
| Valeurs manquantes      |                        **0** |
| Doublons                |                        **0** |
| Prix moyen national     |            **332,23 XOF/kg** |

Les deux grandes catégories étudiées sont :

* **Céréales / tubercules**
* **Légumineuses**

Les prix sont disponibles en :

* **XOF/kg**
* **USD/kg**

Chaque observation correspond à un relevé mensuel effectué autour du **15 du mois**, pour un produit et un marché donné.

---

# 🔎 Qualité des données

Une étape de contrôle qualité a été réalisée avant l'analyse.

Les contrôles portent notamment sur :

* la structure du dataset ;
* les types de variables ;
* les valeurs manquantes ;
* les doublons ;
* les modalités des variables catégorielles ;
* la cohérence des unités ;
* la conversion des dates.

### Résultats du contrôle

```text
Valeurs manquantes : 0
Doublons : 0
Type de prix : Retail
Unité : KG
```

Le dataset est donc particulièrement homogène pour les comparaisons internes.

---

# 🛠️ Méthodologie

L'analyse suit une démarche classique de **Data Analysis / Business Intelligence**.

## Étape 1 — Exploration des données

Analyse initiale du dataset :

* dimensions ;
* types de données ;
* variables catégorielles ;
* valeurs uniques ;
* valeurs manquantes ;
* doublons.

## Étape 2 — Préparation des données

Les principales opérations comprennent :

* conversion de la date en format `datetime` ;
* vérification des unités ;
* contrôle de la cohérence des données ;
* préparation des variables nécessaires aux agrégations.

## Étape 3 — Analyse descriptive

Calcul des principaux indicateurs statistiques :

* moyenne ;
* médiane ;
* écart-type ;
* minimum ;
* maximum ;
* quantiles.

Les analyses sont réalisées sur les prix en **XOF** et en **USD**.

## Étape 4 — Analyse par produit

Calcul de :

* prix moyen ;
* prix médian ;
* prix minimum ;
* prix maximum ;
* écart-type ;
* coefficient de variation.

Le **coefficient de variation** est utilisé comme indicateur de volatilité relative :

$$
CV = \frac{\sigma}{\mu}
$$

où :

* \(\sigma\) représente l'écart-type ;
* \(\mu\) représente la moyenne.

## Étape 5 — Analyse géographique

Les prix sont analysés selon plusieurs niveaux géographiques :

```text
Sénégal
   └── Région
        └── Département
             └── Marché
```

Cette approche permet d'identifier les zones présentant les prix moyens les plus élevés ou les plus faibles.

## Étape 6 — Analyse temporelle

Analyse de l'évolution :

* mensuelle ;
* annuelle ;
* par produit ;
* par catégorie.

Une attention particulière est portée à la période postérieure à **2020**, afin d'identifier les changements de tendance.

## Étape 7 — Comparaison des catégories

Comparaison entre :

* céréales / tubercules ;
* légumineuses.

Les indicateurs comparés sont notamment :

* moyenne ;
* dispersion ;
* distribution ;
* volatilité.

## Étape 8 — Visualisation

Plusieurs types de graphiques sont utilisés :

* bar charts ;
* line charts ;
* boxplots ;
* courbes multiproduits ;
* visualisations géographiques ;
* graphiques interactifs.

## Étape 9 — Business Intelligence

Les principaux KPI sont ensuite structurés afin de construire un **dashboard Power BI** permettant un suivi dynamique des prix alimentaires.

---

# 💻 Technologies utilisées

| Technologie          | Utilisation                             |
| -------------------- | --------------------------------------- |
| **Python**           | Analyse et traitement des données       |
| **Pandas**           | Nettoyage, transformation et agrégation |
| **NumPy**            | Calculs numériques et statistiques      |
| **Matplotlib**       | Visualisations statiques                |
| **Seaborn**          | Visualisations statistiques             |
| **Plotly**           | Visualisations interactives             |
| **Jupyter Notebook** | Développement et restitution            |
| **Power BI**         | Dashboard et Business Intelligence      |

---

# 📈 Principaux KPI

Les indicateurs suivants sont utilisés pour suivre la situation des prix alimentaires :

### KPI prix

* Prix moyen national
* Prix médian
* Prix minimum
* Prix maximum
* Prix moyen par produit
* Prix moyen par région
* Prix moyen par département
* Prix moyen par marché

### KPI volatilité

* Écart-type
* Coefficient de variation
* Produit le plus volatil
* Département le plus volatil

### KPI temporels

* Prix moyen mensuel
* Prix moyen annuel
* Variation annuelle
* Évolution par produit
* Évolution par catégorie

### KPI géographiques

* Région la plus chère
* Région la moins chère
* Marché le plus cher
* Marché le moins cher
* Écart de prix entre marchés

---

# 📊 Principaux résultats

## 🫘 1. Produits les plus chers

Les **haricots niébé** et les **arachides décortiquées** apparaissent comme les produits les plus chers.

Le maximum observé atteint environ :

**1 816 XOF/kg**

à **Thiaroye, dans la région de Dakar**.

---

## 📈 2. Forte évolution après 2020

L'évolution temporelle montre une relative stabilité des prix, principalement autour de **150–300 XOF/kg jusqu'en 2020**.

Après 2020, une forte progression apparaît pour certains produits, notamment :

* le niébé ;
* l'arachide décortiquée.

Certains niveaux dépassent **1 000 à 1 200 XOF/kg entre 2022 et 2025**.

---

## 🗺️ 3. Régions les plus chères

Les régions présentant les niveaux moyens de prix les plus élevés comprennent notamment :

* **Kédougou**
* **Ziguinchor**
* **Sédhiou**

À l'inverse, plusieurs marchés des régions telles que :

* Dakar ;
* Kaolack ;
* Kaffrine

présentent des niveaux moyens plus faibles.

Cette situation peut être mise en relation avec les contraintes d'accessibilité et de logistique des zones concernées.

---

## 📉 4. Départements les plus volatils

Les départements présentant les coefficients de variation les plus élevés comprennent notamment :

* **Sédhiou**
* **Saint-Louis**
* **Nioro du Rip**

avec des CV proches de **0,63–0,64**.

La volatilité reste cependant relativement homogène à l'échelle du territoire, avec un écart limité entre les départements les plus et les moins volatils.

---

## 🏪 5. Marchés extrêmes

Les marchés de :

* **Salémata**
* **Mako**

situés dans la région de Kédougou, figurent parmi les marchés affichant les prix les plus élevés.

À l'autre extrême :

* **Diola Mandakh**
* **Vélingara**

présentent des niveaux de prix plus faibles.

L'écart entre certains marchés peut dépasser un facteur de **2,5**.

---

## 🌾 6. Évolution selon les produits

Le **riz importé** domine l'évolution des prix jusqu'à environ 2019.

Après 2020, la dynamique change avec une forte progression des prix :

* du niébé ;
* de l'arachide.

Cela constitue l'un des principaux changements structurels observés dans les données.

---

## 🫘 7. Différence entre catégories

Les **légumineuses** présentent un prix moyen d'environ :

**748 XOF/kg**

contre :

**279 XOF/kg**

pour les céréales/tubercules.

Soit un écart d'environ :

**469 XOF/kg**.

La dispersion des prix des légumineuses est également nettement supérieure.

---

# 💡 Insights métier

L'analyse permet de dégager plusieurs enseignements.

### 1. Les légumineuses constituent un point de vigilance majeur

Le niébé et l'arachide concentrent une part importante de la pression sur les prix observée après 2020.

### 2. Les contraintes logistiques jouent probablement un rôle important

Les régions de Kédougou, Sédhiou et Ziguinchor figurent parmi les zones les plus chères.

L'accessibilité des marchés, les coûts de transport et les capacités de stockage constituent donc des facteurs à surveiller.

### 3. La volatilité n'est pas limitée à quelques zones

Le coefficient de variation montre une volatilité relativement homogène entre les territoires.

La surveillance ne doit donc pas se limiter aux seules zones présentant les prix moyens les plus élevés.

### 4. Les écarts entre marchés sont importants

Les différences de prix observées entre certains marchés peuvent dépasser un facteur de 2,5.

Cela constitue un enjeu important pour :

* les consommateurs ;
* les producteurs ;
* les commerçants ;
* les programmes d'aide alimentaire.

---

# 🎯 Recommandations

À partir des résultats obtenus, plusieurs actions peuvent être envisagées.

### 1. Mettre en place un suivi mensuel

Développer un **dashboard de suivi des prix alimentaires** permettant de détecter rapidement les hausses inhabituelles.

### 2. Surveiller prioritairement les légumineuses

Mettre en place des mécanismes de surveillance spécifiques pour :

* niébé ;
* arachide ;
* autres légumineuses sensibles.

### 3. Renforcer les infrastructures logistiques

Accorder une attention particulière aux zones structurellement chères, notamment :

* Kédougou ;
* Sédhiou ;
* Ziguinchor.

Les infrastructures de transport et de stockage pourraient contribuer à réduire certains différentiels de prix.

### 4. Encourager la production locale

Renforcer la production et la transformation locales afin de réduire la dépendance à certaines importations.

### 5. Étendre la collecte

Compléter les données actuelles par :

* les prix de gros ;
* différents conditionnements ;
* différentes unités de mesure ;
* les volumes disponibles ;
* les coûts de transport.

Cela permettrait d'analyser plus finement la chaîne de valeur.

### 6. Améliorer la transparence des marchés

Publier régulièrement les prix moyens par marché afin de fournir aux acteurs économiques une information accessible et comparable.

---

# 📌 Conclusion

Cette analyse met en évidence une **forte hétérogénéité spatiale et temporelle des prix alimentaires au Sénégal**.

Les principaux résultats montrent notamment :

* une forte progression du prix de certaines légumineuses après 2020 ;
* des niveaux de prix particulièrement élevés dans certaines zones périphériques ;
* des écarts importants entre marchés ;
* une volatilité relativement généralisée ;
* un rôle important des légumineuses dans la dynamique récente des prix.

La combinaison de **Python pour l'analyse exploratoire et statistique** et de **Power BI pour la visualisation et le pilotage** permet de transformer les données brutes en informations directement exploitables par les décideurs.

---

# 👨‍💻 Compétences démontrées

Ce projet met en œuvre plusieurs compétences essentielles en **Data Analysis** :

* 🔹 Data Cleaning
* 🔹 Exploratory Data Analysis (EDA)
* 🔹 Data Wrangling
* 🔹 Statistical Analysis
* 🔹 GroupBy & Aggregation
* 🔹 Time Series Analysis
* 🔹 Geographical Analysis
* 🔹 Volatility Analysis
* 🔹 KPI Design
* 🔹 Data Visualization
* 🔹 Interactive Visualization
* 🔹 Business Intelligence
* 🔹 Power BI Dashboard Design
* 🔹 Data Storytelling
* 🔹 Business Recommendations

---

# 📚 Source des données

Données fournies FORCE-N.

Dataset utilisé :

```text
wfp_food_prices_sen.csv
```


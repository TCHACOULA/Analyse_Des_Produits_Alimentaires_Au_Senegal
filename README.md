# Analyse_Des_Produits_Alimentaires_Au_Senegal

La sécurité alimentaire au Sénégal dépend étroitement de la stabilité et de l'accessibilité des prix des denrées de base sur les marchés locaux. Les chocs climatiques, les tensions logistiques et les crises mondiales récentes (post-Covid, inflation des matières premières) exposent les ménages à des variations de prix parfois brutales.
L'objectif de cette étude est d'exploiter les données de suivi des prix alimentaires collectées sur les marchés sénégalais afin de : identifier les produits et zones les plus exposés à la cherté et à la volatilité des prix, comprendre l'évolution temporelle des prix, et formuler des recommandations opérationnelles pour les acteurs de la sécurité alimentaire (autorités publiques, ONG, programmes de soutien).

    2. Description des données
Les données proviennent du fichier wfp_food_prices_sen.csv (World Food Programme), couvrant le suivi des prix de détail sur les marchés sénégalais.
Indicateur
Valeur
Nombre d'observations
50 060 lignes
Période couverte
Janvier 2000 - Mars 2026
Régions (admin1)
14
Départements (admin2)
34
Marchés suivis
64
Catégories de produits
2 (céréales/tubercules, légumineuses)
Produits suivis
12
Type de prix / Unité
Retail (détail) / KG uniquement
Valeurs manquantes
Aucune (0 sur toutes les colonnes)
Doublons
Aucun
Prix moyen national
332,23 XOF/kg (0,60 USD/kg)

Chaque enregistrement décrit un relevé de prix pour un produit donné à chaque 15 du mois, sur un marché donné, avec sa localisation géographique (région, département, marché, latitude/longitude), sa catégorie, son prix en franc CFA (XOF) et son équivalent en dollar américain (USD). Le jeu de données est complet (aucune valeur manquante, aucun doublon) et homogène : un seul type de prix (Retail) et une seule unité (KG) sont représentés, ce qui limite certaines comparaisons (cf. point 8 des résultats) mais garantit la cohérence des analyses statistiques menées.

    3. Méthodologie

L'analyse s'est déroulée en plusieurs étapes :
    1. Chargement et exploration initiale : dimensions du jeu de données, types de colonnes, valeurs manquantes, doublons, modalités des variables catégorielles (régions, produits, catégories, unités).
    2. Nettoyage et correction des formats : conversion de la colonne date au format datetime pour permettre les agrégations temporelles.
    3. Statistiques descriptives : calcul des indicateurs de tendance centrale et de dispersion (moyenne, médiane, écart-type, min/max) sur les prix en XOF et en USD.
    4. Analyses croisées (groupby / agrégations) : prix maximum par marché, prix moyen par produit, par région et par département, coefficient de variation (CV = écart-type / moyenne) pour mesurer la volatilité relative des prix.
    5. Analyse temporelle : évolution mensuelle et annuelle des prix moyens, globalement et par produit, afin de détecter les tendances et ruptures (ex. flambée post-2020).
    6. Comparaisons de catégories : céréales/tubercules versus légumineuses (moyenne, écart-type, boxplot).
    7. Visualisation : graphiques Matplotlib/Seaborn (barres, courbes, boxplots) et graphiques interactifs Plotly (courbes multiproduits, carte géographique des marchés).
    8. Synthèse et recommandations : formulation d'interprétations et de recommandations opérationnelles pour chaque axe d'analyse.
    9. Définition de KPI et conception de Dashboard Power BI

    4. Langages et outils utilisés

Langage : Python 3
    • Pandas : chargement, nettoyage et agrégation des données (groupby, describe, idxmax…)
    • Numpy : calculs numériques (coefficient de variation, statistiques)
    • Matplotlib : graphiques statiques (barres, courbes)
    • Seaborn : graphiques statistiques avancés (barplot, boxplot) avec mise en forme soignée
    • Plotly.express : graphiques interactifs (évolution des prix, carte géographique des marchés)
Jupyter Notebook : environnement de développement et de restitution de l'analyse
Power BI : environnement de conception et de visualisation de graphique interactifs





    5. Résultats obtenus

Le tableau suivant synthétise les principaux résultats obtenus pour chacun des axes d'analyse traités dans le notebook :

Question analysée
Résultat clé
1
Produits les plus chers par marché
Haricots niébé et arachides décortiquées dominent ; pic à 1 816 XOF/kg (Thiaroye, Dakar)
2
Évolution des prix dans le temps
Stabilité 150-300 XOF jusqu'en 2020, puis flambée du niébé/arachide (>1000-1200 XOF, 2022-2025)
3
Régions les plus chères
Kédougou, Ziguinchor, Sédhiou (zones enclavées) ; Dakar, Kaolack, Kaffrine les moins chères
4
Départements les plus volatils
Sédhiou, Saint-Louis, Nioro du Rip (CV ~0,63-0,64) ; volatilité globalement homogène (écart 0,04)
5
Marchés extrêmes
Salémata et Mako (Kédougou) les plus chers ; Diola Mandakh et Vélingara les moins chers (facteur > 2,5)
6
Fluctuations par produit/période
Riz importé dominant jusqu'en 2019 ; niébé et arachide en tête depuis 2020
7
Écart entre catégories
Légumineuses : 748 XOF vs céréales/tubercules : 279 XOF (écart 469 XOF, dispersion x3)
8
Homogénéité type de prix/unité
Une seule modalité (Retail, KG, actual) : comparaison interne impossible
9
Prix les plus élevés en USD
Confirme le constat n°1 : niébé et arachide décortiquée dominent aussi en USD


    6. Interprétations et recommandations

6.1 Constats principaux
    • Les légumineuses (niébé, arachide) sont structurellement plus chères et plus volatiles que les céréales/tubercules, et concentrent la pression inflationniste depuis 2020.
    • La cherté des prix est davantage liée à l'éloignement logistique (Kédougou, Ziguinchor, Sédhiou) qu'au pouvoir d'achat local des zones concernées.
    • La volatilité des prix (mesurée par le coefficient de variation) touche presque uniformément l'ensemble du territoire, plutôt qu'un nombre restreint de zones isolées.
    • Le jeu de données, bien que riche sur le plan spatio-temporel, reste homogène sur le type de prix (Retail) et l'unité (KG), ce qui limite certaines comparaisons (prix de gros, autres unités).
6.2 Recommandations
    10. Mettre en place un tableau de bord actualisé mensuellement pour anticiper les chocs de prix.
    11. Prioriser la surveillance des légumineuses (niébé, arachide), moteurs actuels de l'inflation alimentaire, via des stocks de sécurité ciblés.
    12. Renforcer les infrastructures de transport et de stockage vers Kédougou, Sédhiou et Ziguinchor, régions structurellement chères et volatiles.
    13. Encourager la production et la transformation locales afin de réduire la dépendance aux importations (riz, maïs importés).
    14. Étendre la collecte de données aux prix de gros et à d'autres unités de mesure pour affiner l'analyse de la chaîne de valeur.
    15. Publier régulièrement les prix moyens par marché afin de renforcer la transparence et limiter les abus entre producteurs, commerçants et consommateurs.


# Data_Refinement

# Nettoyage et Analyse des Ventes d'un Café

## Introduction
Ce projet vise à nettoyer et analyser un jeu de données de ventes (`dirty_cafe_sales.csv`) d'un café. L'objectif principal est de transformer les données brutes et souvent incohérentes en un format propre et structuré, puis d'effectuer une analyse exploratoire pour dégager des tendances et des insights sur les opérations du café.

## Données
Le jeu de données initial, `dirty_cafe_sales.csv`, contenait plusieurs problèmes de qualité des données, notamment des valeurs manquantes, des formats incohérents et des entrées non pertinentes dans diverses colonnes.

## Objectifs du Projet
*   Nettoyer et pré-traiter les données de ventes.
*   Standardiser les noms de colonnes.
*   Vérifier la cohérence des données numériques.
*   Catégoriser les articles vendus.
*   Effectuer une analyse exploratoire des données (EDA) pour comprendre les schémas de ventes.
*   Exporter le jeu de données nettoyé pour des analyses futures.

## Étapes de Nettoyage et de Préparation des Données
1.  **Chargement du Dataset** : Le fichier `dirty_cafe_sales.csv` a été chargé dans un DataFrame pandas.
2.  **Standardisation des Noms de Colonnes** : Tous les noms de colonnes ont été convertis en `snake_case` pour une meilleure uniformité (ex: `Transaction ID` -> `transaction_id`).
3.  **Nettoyage de la Colonne 'item'** : Les valeurs non pertinentes ('UNKNOWN', 'ERROR', 'nan' sous forme de chaîne de caractères) ont été remplacées par `NaN`.
4.  **Vérification et Nettoyage des Quantités (`quantity`)** : La colonne a été convertie en type numérique, et les lignes contenant des quantités non entières, négatives ou nulles ont été identifiées et traitées (supprimées dans le processus global de `dropna`).
5.  **Suppression des Lignes avec Valeurs Manquantes (`NaN`)** : Toutes les lignes contenant au moins une valeur `NaN` ont été supprimées pour garantir la qualité des données pour l'analyse.
6.  **Vérification et Nettoyage du Chiffre d'Affaires (`total_spent`)** : La colonne a été convertie en numérique, et les lignes avec des valeurs non positives ou non numériques ont été supprimées.
7.  **Vérification et Nettoyage du Prix Unitaire (`price_per_unit`)** : La colonne a été convertie en numérique, et les lignes avec des valeurs non positives ou non numériques ont été supprimées.
8.  **Nettoyage de la Colonne 'payment_method'** : Les valeurs 'UNKNOWN' et 'ERROR' ont été remplacées par `NaN`.
9.  **Nettoyage de la Colonne 'location'** : Les valeurs 'UNKNOWN' et 'ERROR' ont été remplacées par `NaN`.
10. **Validation du Format 'transaction_id'** : Vérification que toutes les `transaction id` suivent le format `TXN_` suivi de 7 chiffres.
11. **Gestion de la Colonne 'transaction_date'** : Conversion au format datetime et identification des dates invalides.
12. **Vérification de la Cohérence Numérique** : La relation `quantity * price_per_unit = total_spent` a été vérifiée pour assurer l'intégrité des calculs financiers.
13. **Catégorisation des Articles** : Une nouvelle colonne `item_category` a été créée, classant les articles en 'boisson' ou 'nourriture' en fonction de leur nom.

## Analyse Exploratoire des Données (EDA)
Diverses visualisations ont été créées pour explorer les données nettoyées :

*   **Répartition du Chiffre d'Affaires par Catégorie d'Article** : Un graphique en camembert montrant la part des 'boissons' et de la 'nourriture' dans le chiffre d'affaires total.
*   **Prix Unitaires par Article** : Affichage des prix uniques pour chaque type d'article, confirmant leur unicité et leur cohérence.
*   **Répartition des Transactions par Lieu** : Un graphique en camembert illustrant la proportion des ventes "à emporter" (`Takeaway`) et "sur place" (`In-store`).
*   **Répartition des Transactions par Mode de Paiement** : Un graphique en camembert montrant la part de chaque mode de paiement (ex: Credit Card, Cash, Digital Wallet).
*   **Tendances Quotidiennes** : Des graphiques linéaires affichant l'évolution quotidienne du nombre de transactions et du chiffre d'affaires.
*   **Chiffre d'Affaires Cumulé** : Une courbe montrant le chiffre d'affaires total accumulé jour après jour.
*   **Performance par Jour de la Semaine** : Des graphiques à barres analysant le nombre de transactions et le chiffre d'affaires par jour de la semaine.
*   **Performance Détaillée par Mode de Paiement et Jour de la Semaine** : Des graphiques à barres montrant le nombre de transactions et le chiffre d'affaires par jour de la semaine, segmentés par chaque mode de paiement.

## Fichier de Sortie
Le jeu de données nettoyé et préparé a été sauvegardé sous le nom `cafe_sales_cleaned.csv`.

## Conclusion
Cette analyse a permis de transformer un jeu de données "sale" en une source d'information fiable. Les visualisations ont mis en lumière des aspects importants des opérations du café, tels que les préférences des clients en matière de paiement et de lieu, ainsi que les performances de vente au fil du temps et par jour de la semaine. Ces insights peuvent servir de base pour des décisions commerciales éclairées.

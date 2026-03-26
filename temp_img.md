_Une fois le workspace Fabric créé (cf. étape précédente), nous pouvons mettre en place des Lakehouses structurés selon l'**architecture Médaillon**. Cette approche va nous permettre de gérer efficacement les données brutes, nettoyées, et transformées en différentes couches._

# Création de Lakehouses dans Microsoft Fabric
Pour tout projet Data, le choix d'un outil de stockage est crucial et repose sur divers critères (l'utilisation, les contraintes techniques, les considérations financières,etc.)<br>
Microsoft Fabric propose une solution complète et flexible grâce à travers les **Lakehouse**. Ils combinent les avantages des data lakes et des data warehouses.

## Quelques définitions
### 1.1. Qu'est-ce qu'un Lakehouse dans Microsoft Fabric ?
Un **Lakehouse** est une architecture de gestion des données qui combine les avantages des data lakes et des data warehouses. Il permet de stocker et de gérer des données brutes et transformées dans un environnement unifié. Cela inclut la flexibilité de stockage de fichiers semi-structurés (JSON, CSV, Parquet) ainsi que de tables structurées pour les requêtes analytiques.

**Quelques avantages des Lakehouses de Fabric**
- **Simplicité d'Utilisation :** Interface unifiée pour l'ingestion, le stockage, la transformation et l'analyse des données.
- **Coût-Efficacité :** Réduction des coûts en éliminant le besoin de maintenir des systèmes séparés pour les data lakes et les data warehouses.
- **Performances :** Optimisation des requêtes et des analyses grâce à une gestion efficace des données et des ressources.
- **Sécurité :** Gestion centralisée des accès et des permissions pour assurer la sécurité des données.


### 1.2. Qu'est-ce que l'architecture médaillion ?
L'architecture Médaillon est une approche structurée de la gestion des données dans un Lakehouse, qui permet de catégoriser les données en plusieurs niveaux ou couches : Bronze, Silver, et Gold. <br>
Chaque couche a un rôle spécifique dans le pipeline de données, garantissant la qualité et la fiabilité des données tout au long du processus d'analyse.
- **Couche Bronze :**<br>
    C'est la couche où les données brutes sont ingérées directement à partir des sources externes. Les données dans cette couche sont souvent stockées sous leur forme originale (sans nettoyage).<br>
    **Objectif :** Capturer les données brutes de toutes les sources, quel que soit leur format.<br>
    **Exemples :** Logs, fichiers CSV, etc.

- **Couche Silver :**<br>
    Il s'agit d'une couche intermédiaire où les données brutes sont nettoyées et transformées pour corriger les erreurs, gérer les valeurs manquantes et normaliser les formats de données.<br>
    **Objectif :** Améliorer la qualité des données et rendre les données prêtes pour l'analyse.<br>
    **Exemples :** Données nettoyées avec des colonnes standardisées, données avec les erreurs corrigées.

- **Couche Gold :**
    C'est la couche finale où les données sont transformées en vues analytiques prêtes à être consommées par des outils de BI, des tableaux de bord, et des modèles de machine learning.<br>
    **Objectif :** Fournir des données hautement agrégées et optimisées pour la consommation finale.<br>
    **Exemples :** Vues de données agrégées, jeux de données prêts pour l'analyse, tables de faits et de dimensions.

#### Use case Data Eng
- **Bronze :** recupération de la donnée par jour puis TRUNCATE
- **Silver :** historisation + Nettoyage (plus de TRUNCATE)
- **Gold :** nettoyage poussé (= aggregation), views  <br>

## 2. [PRATIQUE] - Créer un Lakehouse dans Microsoft Fabric
Afin de créer un Lakehouse, il suffit de suivre les étapes suivantes :
1. Ouvrir votre Workspace Fabric
2. Si vous n'êtes pas déjà sur l'expérience **Data Engineering**, aller à l'angle bas gauche du portail, cliquer sur cette icône relative à l'expérience (Power BI, Data Factory, ...) puis **Data Engineering**.<br>
    <img src="file:///$(_Une fois le workspace Fabric créé (cf. étape précédente), nous pouvons mettre en place des Lakehouses structurés selon l'**architecture Médaillon**. Cette approche va nous permettre de gérer efficacement les données brutes, nettoyées, et transformées en différentes couches._

# Création de Lakehouses dans Microsoft Fabric
Pour tout projet Data, le choix d'un outil de stockage est crucial et repose sur divers critères (l'utilisation, les contraintes techniques, les considérations financières,etc.)<br>
Microsoft Fabric propose une solution complète et flexible grâce à travers les **Lakehouse**. Ils combinent les avantages des data lakes et des data warehouses.

## Quelques définitions
### 1.1. Qu'est-ce qu'un Lakehouse dans Microsoft Fabric ?
Un **Lakehouse** est une architecture de gestion des données qui combine les avantages des data lakes et des data warehouses. Il permet de stocker et de gérer des données brutes et transformées dans un environnement unifié. Cela inclut la flexibilité de stockage de fichiers semi-structurés (JSON, CSV, Parquet) ainsi que de tables structurées pour les requêtes analytiques.

**Quelques avantages des Lakehouses de Fabric**
- **Simplicité d'Utilisation :** Interface unifiée pour l'ingestion, le stockage, la transformation et l'analyse des données.
- **Coût-Efficacité :** Réduction des coûts en éliminant le besoin de maintenir des systèmes séparés pour les data lakes et les data warehouses.
- **Performances :** Optimisation des requêtes et des analyses grâce à une gestion efficace des données et des ressources.
- **Sécurité :** Gestion centralisée des accès et des permissions pour assurer la sécurité des données.


### 1.2. Qu'est-ce que l'architecture médaillion ?
L'architecture Médaillon est une approche structurée de la gestion des données dans un Lakehouse, qui permet de catégoriser les données en plusieurs niveaux ou couches : Bronze, Silver, et Gold. <br>
Chaque couche a un rôle spécifique dans le pipeline de données, garantissant la qualité et la fiabilité des données tout au long du processus d'analyse.
- **Couche Bronze :**<br>
    C'est la couche où les données brutes sont ingérées directement à partir des sources externes. Les données dans cette couche sont souvent stockées sous leur forme originale (sans nettoyage).<br>
    **Objectif :** Capturer les données brutes de toutes les sources, quel que soit leur format.<br>
    **Exemples :** Logs, fichiers CSV, etc.

- **Couche Silver :**<br>
    Il s'agit d'une couche intermédiaire où les données brutes sont nettoyées et transformées pour corriger les erreurs, gérer les valeurs manquantes et normaliser les formats de données.<br>
    **Objectif :** Améliorer la qualité des données et rendre les données prêtes pour l'analyse.<br>
    **Exemples :** Données nettoyées avec des colonnes standardisées, données avec les erreurs corrigées.

- **Couche Gold :**
    C'est la couche finale où les données sont transformées en vues analytiques prêtes à être consommées par des outils de BI, des tableaux de bord, et des modèles de machine learning.<br>
    **Objectif :** Fournir des données hautement agrégées et optimisées pour la consommation finale.<br>
    **Exemples :** Vues de données agrégées, jeux de données prêts pour l'analyse, tables de faits et de dimensions.

#### Use case Data Eng
- **Bronze :** recupération de la donnée par jour puis TRUNCATE
- **Silver :** historisation + Nettoyage (plus de TRUNCATE)
- **Gold :** nettoyage poussé (= aggregation), views  <br>

## 2. [PRATIQUE] - Créer un Lakehouse dans Microsoft Fabric
Afin de créer un Lakehouse, il suffit de suivre les étapes suivantes :
1. Ouvrir votre Workspace Fabric
2. Si vous n'êtes pas déjà sur l'expérience **Data Engineering**, aller à l'angle bas gauche du portail, cliquer sur cette icône relative à l'expérience (Power BI, Data Factory, ...) puis **Data Engineering**.<br>
    <img src="/Images/Fabric/Fabric-change-experience.png" alt="" width="30%"/>
3. Dans la page d'accueil de **Synapse Data Engineering**, créer un **Lakehouse** qui sera nommé selon votre choix. <br>
    <img src="/Images/Lakehouse/Lakehouse-create-a-lakehouse.png" alt="" width="80%"/>

    <img src="/Images/Lakehouse/Lakehouse_Creation.gif" alt="Lakehouse_Creation_demo" width="80%"/>

    Vous venez de créer votre premier Lakehouse dans MS Fabric !

4. Pour la suite du projet, il faudra créer deux (2) autres Lakehouses (dans le même espace de travail). Pour cette démo ils seront nommés : **DE_LH_Silver** et **DE_LH_Gold**.

## 3. Analyse du contenu d'un Lakehouse Fabric 
- SQL Analytic Endpoint
- Semantic model
## 3. Application du concept pour notre cas d'usage

|**Lakehouse** | **Utilisation**                                                                                            |
|--------------|-----------------------------------------------------------------------------------------------------------|
| **DE_LH_Bronze** | - Dépôt des fichiers bruts <br>- Organisation des fichiers en dossiers                                        |
| **DE_LH_Silver** | - Nettoyage de la donnée <br>- Transformation de la donnée <br>- Enrichissement de la donnée <br>- Création de tables |
| **DE_LH_Gold**   | - Données aggrégées <br>- Données triées selon un contexte donnée                                            |
.FullName)" alt="" width="30%"/>
3. Dans la page d'accueil de **Synapse Data Engineering**, créer un **Lakehouse** qui sera nommé selon votre choix. <br>
    <img src="file:///$(_Une fois le workspace Fabric créé (cf. étape précédente), nous pouvons mettre en place des Lakehouses structurés selon l'**architecture Médaillon**. Cette approche va nous permettre de gérer efficacement les données brutes, nettoyées, et transformées en différentes couches._

# Création de Lakehouses dans Microsoft Fabric
Pour tout projet Data, le choix d'un outil de stockage est crucial et repose sur divers critères (l'utilisation, les contraintes techniques, les considérations financières,etc.)<br>
Microsoft Fabric propose une solution complète et flexible grâce à travers les **Lakehouse**. Ils combinent les avantages des data lakes et des data warehouses.

## Quelques définitions
### 1.1. Qu'est-ce qu'un Lakehouse dans Microsoft Fabric ?
Un **Lakehouse** est une architecture de gestion des données qui combine les avantages des data lakes et des data warehouses. Il permet de stocker et de gérer des données brutes et transformées dans un environnement unifié. Cela inclut la flexibilité de stockage de fichiers semi-structurés (JSON, CSV, Parquet) ainsi que de tables structurées pour les requêtes analytiques.

**Quelques avantages des Lakehouses de Fabric**
- **Simplicité d'Utilisation :** Interface unifiée pour l'ingestion, le stockage, la transformation et l'analyse des données.
- **Coût-Efficacité :** Réduction des coûts en éliminant le besoin de maintenir des systèmes séparés pour les data lakes et les data warehouses.
- **Performances :** Optimisation des requêtes et des analyses grâce à une gestion efficace des données et des ressources.
- **Sécurité :** Gestion centralisée des accès et des permissions pour assurer la sécurité des données.


### 1.2. Qu'est-ce que l'architecture médaillion ?
L'architecture Médaillon est une approche structurée de la gestion des données dans un Lakehouse, qui permet de catégoriser les données en plusieurs niveaux ou couches : Bronze, Silver, et Gold. <br>
Chaque couche a un rôle spécifique dans le pipeline de données, garantissant la qualité et la fiabilité des données tout au long du processus d'analyse.
- **Couche Bronze :**<br>
    C'est la couche où les données brutes sont ingérées directement à partir des sources externes. Les données dans cette couche sont souvent stockées sous leur forme originale (sans nettoyage).<br>
    **Objectif :** Capturer les données brutes de toutes les sources, quel que soit leur format.<br>
    **Exemples :** Logs, fichiers CSV, etc.

- **Couche Silver :**<br>
    Il s'agit d'une couche intermédiaire où les données brutes sont nettoyées et transformées pour corriger les erreurs, gérer les valeurs manquantes et normaliser les formats de données.<br>
    **Objectif :** Améliorer la qualité des données et rendre les données prêtes pour l'analyse.<br>
    **Exemples :** Données nettoyées avec des colonnes standardisées, données avec les erreurs corrigées.

- **Couche Gold :**
    C'est la couche finale où les données sont transformées en vues analytiques prêtes à être consommées par des outils de BI, des tableaux de bord, et des modèles de machine learning.<br>
    **Objectif :** Fournir des données hautement agrégées et optimisées pour la consommation finale.<br>
    **Exemples :** Vues de données agrégées, jeux de données prêts pour l'analyse, tables de faits et de dimensions.

#### Use case Data Eng
- **Bronze :** recupération de la donnée par jour puis TRUNCATE
- **Silver :** historisation + Nettoyage (plus de TRUNCATE)
- **Gold :** nettoyage poussé (= aggregation), views  <br>

## 2. [PRATIQUE] - Créer un Lakehouse dans Microsoft Fabric
Afin de créer un Lakehouse, il suffit de suivre les étapes suivantes :
1. Ouvrir votre Workspace Fabric
2. Si vous n'êtes pas déjà sur l'expérience **Data Engineering**, aller à l'angle bas gauche du portail, cliquer sur cette icône relative à l'expérience (Power BI, Data Factory, ...) puis **Data Engineering**.<br>
    <img src="/Images/Fabric/Fabric-change-experience.png" alt="" width="30%"/>
3. Dans la page d'accueil de **Synapse Data Engineering**, créer un **Lakehouse** qui sera nommé selon votre choix. <br>
    <img src="/Images/Lakehouse/Lakehouse-create-a-lakehouse.png" alt="" width="80%"/>

    <img src="/Images/Lakehouse/Lakehouse_Creation.gif" alt="Lakehouse_Creation_demo" width="80%"/>

    Vous venez de créer votre premier Lakehouse dans MS Fabric !

4. Pour la suite du projet, il faudra créer deux (2) autres Lakehouses (dans le même espace de travail). Pour cette démo ils seront nommés : **DE_LH_Silver** et **DE_LH_Gold**.

## 3. Analyse du contenu d'un Lakehouse Fabric 
- SQL Analytic Endpoint
- Semantic model
## 3. Application du concept pour notre cas d'usage

|**Lakehouse** | **Utilisation**                                                                                            |
|--------------|-----------------------------------------------------------------------------------------------------------|
| **DE_LH_Bronze** | - Dépôt des fichiers bruts <br>- Organisation des fichiers en dossiers                                        |
| **DE_LH_Silver** | - Nettoyage de la donnée <br>- Transformation de la donnée <br>- Enrichissement de la donnée <br>- Création de tables |
| **DE_LH_Gold**   | - Données aggrégées <br>- Données triées selon un contexte donnée                                            |
.FullName)" alt="" width="80%"/>

    <img src="file:///$(_Une fois le workspace Fabric créé (cf. étape précédente), nous pouvons mettre en place des Lakehouses structurés selon l'**architecture Médaillon**. Cette approche va nous permettre de gérer efficacement les données brutes, nettoyées, et transformées en différentes couches._

# Création de Lakehouses dans Microsoft Fabric
Pour tout projet Data, le choix d'un outil de stockage est crucial et repose sur divers critères (l'utilisation, les contraintes techniques, les considérations financières,etc.)<br>
Microsoft Fabric propose une solution complète et flexible grâce à travers les **Lakehouse**. Ils combinent les avantages des data lakes et des data warehouses.

## Quelques définitions
### 1.1. Qu'est-ce qu'un Lakehouse dans Microsoft Fabric ?
Un **Lakehouse** est une architecture de gestion des données qui combine les avantages des data lakes et des data warehouses. Il permet de stocker et de gérer des données brutes et transformées dans un environnement unifié. Cela inclut la flexibilité de stockage de fichiers semi-structurés (JSON, CSV, Parquet) ainsi que de tables structurées pour les requêtes analytiques.

**Quelques avantages des Lakehouses de Fabric**
- **Simplicité d'Utilisation :** Interface unifiée pour l'ingestion, le stockage, la transformation et l'analyse des données.
- **Coût-Efficacité :** Réduction des coûts en éliminant le besoin de maintenir des systèmes séparés pour les data lakes et les data warehouses.
- **Performances :** Optimisation des requêtes et des analyses grâce à une gestion efficace des données et des ressources.
- **Sécurité :** Gestion centralisée des accès et des permissions pour assurer la sécurité des données.


### 1.2. Qu'est-ce que l'architecture médaillion ?
L'architecture Médaillon est une approche structurée de la gestion des données dans un Lakehouse, qui permet de catégoriser les données en plusieurs niveaux ou couches : Bronze, Silver, et Gold. <br>
Chaque couche a un rôle spécifique dans le pipeline de données, garantissant la qualité et la fiabilité des données tout au long du processus d'analyse.
- **Couche Bronze :**<br>
    C'est la couche où les données brutes sont ingérées directement à partir des sources externes. Les données dans cette couche sont souvent stockées sous leur forme originale (sans nettoyage).<br>
    **Objectif :** Capturer les données brutes de toutes les sources, quel que soit leur format.<br>
    **Exemples :** Logs, fichiers CSV, etc.

- **Couche Silver :**<br>
    Il s'agit d'une couche intermédiaire où les données brutes sont nettoyées et transformées pour corriger les erreurs, gérer les valeurs manquantes et normaliser les formats de données.<br>
    **Objectif :** Améliorer la qualité des données et rendre les données prêtes pour l'analyse.<br>
    **Exemples :** Données nettoyées avec des colonnes standardisées, données avec les erreurs corrigées.

- **Couche Gold :**
    C'est la couche finale où les données sont transformées en vues analytiques prêtes à être consommées par des outils de BI, des tableaux de bord, et des modèles de machine learning.<br>
    **Objectif :** Fournir des données hautement agrégées et optimisées pour la consommation finale.<br>
    **Exemples :** Vues de données agrégées, jeux de données prêts pour l'analyse, tables de faits et de dimensions.

#### Use case Data Eng
- **Bronze :** recupération de la donnée par jour puis TRUNCATE
- **Silver :** historisation + Nettoyage (plus de TRUNCATE)
- **Gold :** nettoyage poussé (= aggregation), views  <br>

## 2. [PRATIQUE] - Créer un Lakehouse dans Microsoft Fabric
Afin de créer un Lakehouse, il suffit de suivre les étapes suivantes :
1. Ouvrir votre Workspace Fabric
2. Si vous n'êtes pas déjà sur l'expérience **Data Engineering**, aller à l'angle bas gauche du portail, cliquer sur cette icône relative à l'expérience (Power BI, Data Factory, ...) puis **Data Engineering**.<br>
    <img src="/Images/Fabric/Fabric-change-experience.png" alt="" width="30%"/>
3. Dans la page d'accueil de **Synapse Data Engineering**, créer un **Lakehouse** qui sera nommé selon votre choix. <br>
    <img src="/Images/Lakehouse/Lakehouse-create-a-lakehouse.png" alt="" width="80%"/>

    <img src="/Images/Lakehouse/Lakehouse_Creation.gif" alt="Lakehouse_Creation_demo" width="80%"/>

    Vous venez de créer votre premier Lakehouse dans MS Fabric !

4. Pour la suite du projet, il faudra créer deux (2) autres Lakehouses (dans le même espace de travail). Pour cette démo ils seront nommés : **DE_LH_Silver** et **DE_LH_Gold**.

## 3. Analyse du contenu d'un Lakehouse Fabric 
- SQL Analytic Endpoint
- Semantic model
## 3. Application du concept pour notre cas d'usage

|**Lakehouse** | **Utilisation**                                                                                            |
|--------------|-----------------------------------------------------------------------------------------------------------|
| **DE_LH_Bronze** | - Dépôt des fichiers bruts <br>- Organisation des fichiers en dossiers                                        |
| **DE_LH_Silver** | - Nettoyage de la donnée <br>- Transformation de la donnée <br>- Enrichissement de la donnée <br>- Création de tables |
| **DE_LH_Gold**   | - Données aggrégées <br>- Données triées selon un contexte donnée                                            |
.FullName)" alt="Lakehouse_Creation_demo" width="80%"/>

    Vous venez de créer votre premier Lakehouse dans MS Fabric !

4. Pour la suite du projet, il faudra créer deux (2) autres Lakehouses (dans le même espace de travail). Pour cette démo ils seront nommés : **DE_LH_Silver** et **DE_LH_Gold**.

## 3. Analyse du contenu d'un Lakehouse Fabric 
- SQL Analytic Endpoint
- Semantic model
## 3. Application du concept pour notre cas d'usage

|**Lakehouse** | **Utilisation**                                                                                            |
|--------------|-----------------------------------------------------------------------------------------------------------|
| **DE_LH_Bronze** | - Dépôt des fichiers bruts <br>- Organisation des fichiers en dossiers                                        |
| **DE_LH_Silver** | - Nettoyage de la donnée <br>- Transformation de la donnée <br>- Enrichissement de la donnée <br>- Création de tables |
| **DE_LH_Gold**   | - Données aggrégées <br>- Données triées selon un contexte donnée                                            |


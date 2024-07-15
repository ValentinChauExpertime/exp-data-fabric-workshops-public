# Utilisation des Données sur les Sites du Patrimoine Mondial de l'UNESCO
Ce projet a pour objectif de traiter et d'analyser les données des sites inscrits au patrimoine mondial de l'UNESCO, en se concentrant sur le traitement des données et la génération de rapports. Les données sont issues de plusieurs sources, notamment des fichiers Excel, CSV et JSON, chacun apportant des informations spécifiques sur les sites et les pays concernés. Nous allons utiliser **Microsoft Fabric** pour importer, traiter et générer des rapports à partir de ces données.

# Présentation des sources de données
Pour avancer dans ce projet, vous aurez à disposition des fichiers suivants :

## 1. Liste officielle 2023.xlsx
Le fichier **Liste Officielle 2023.xlsx** contient la liste des sites inscrits au patrimoine mondial de l'UNESCO. Les colonnes incluses sont :
- **ID (int) :** Numéro de dossier du site
- **Site (str) :** Nom du site
- **Catégorie	(str) :** Indique s'il s'agit d'un site classé "culturel", "naturel" ou "mixte"
- **Pays (str) :** Nom du pays où l'on peut trouver le site
- **Site délisté (bool) :** Indique si le site a été retiré de la liste (1) ou non (0)

|  ID  |                                 Site                                   |    Catégorie    | Site délisté |      Pays      |
|----- |------------------------------------------------------------------------|-----------------|:------------:|----------------|
| 914  | Parc de la zone humide d’iSimangaliso                                  | natural         | FAUX         | Afrique du Sud |
| 915  | Sites des hominidés fossiles d’Afrique du Sud                          | cultural        | FAUX         | Afrique du Sud |
| 985  | Parc Maloti-Drakensberg                                                | mixed           | FAUX         | Afrique du Sud |
| 1575 | Montagnes de Barberton Makhonjwa                                       | natural         | FAUX         | Afrique du Sud |
| 99   | Patrimoine naturel et culturel de la région d’Ohrid                    | mixed           | FAUX         | Albanie        |
| 565  | Casbah d'Alger                                                         | cultural        | FAUX         | Algérie        |
| 3    | Cathédrale d'Aix-la-Chapelle                                           | cultural        | FAUX         | Allemagne      |
| 292  | Cathédrale de Cologne                                                  | cultural        | FAUX         | Allemagne      |
| ...  | ...                                                                    | ...             | ...          | ...            |
| ...  | ...                                                                    | ...             | ...          | ...            |


## 2. Pays.csv
Le fichier **Pays.csv** contient la liste des pays ayant **au moins** un site inscrit au patrimoine mondial de l'UNESCO. Les colonnes incluent :
- **pays (str) :** Nom du pays
- **code_pays (str) :** Code du pays au format ISO 3166 (ou ISO 2)
- **region (str) :** Groupe régional défini par l'UNESCO
- **code_region (str) :** Code du groupe régional du pays

| code_region | region                      | code_pays | pays                      |
|-------------|-----------------------------|-----------|---------------------------|
| EUR         | Europe et Amérique du Nord  | PL        | Pologne                   |
| AFR         | Afrique                     | ET        | Ethiopie                  |
| LAC         | Amérique latine et Caraïbes | EC        | Équateur                  |
| EUR         | Europe et Amérique du Nord  | CA        | Canada                    |
| ARB         | États arabes                | TN        | Tunisie                   |
| ...         | ...                         | ...       | ...                       |
| ...         | ...                         | ...       | ...                       |


## 3. WHC_****.json
Chaque année, le Comité du patrimoine mondial de l'UNESCO se réunit pour valider les sites à inscrire ou à retirer de la liste du patrimoine mondial. Les données issues de ces réunions sont structurées et enregistrées dans des fichiers JSON annuels.<br>
Chaque fichier JSON contient une liste d'objets représentant les sites, avec les informations suivantes :
- **ID du site (int) :** Numéro du dossier du site
- **Site (str) :** Nom du site
- **Description (str) :** Description du site fourni par l'UNESCO/CPE
- __Informations complémentaires* :__
    - **Date d'inscription (int) :** Année d'inscription du site dans la liste des patrimoines mondiaux
    - **Significant modifications to boundaries (str) :**
    - **Critères (str) :** Liste des critères qui ont permis l'inscription du site dans la liste (cf. [UNESCO : Les critères de sélection](https://whc.unesco.org/fr/criteres/))
    - **Bien (str) :** Superficie en ha
    - **Dossier (str) :** Numéro du dernier dossier du site
    - **Coordonnées en DMS (str) :** Coordonnées géographiques du site au format DMS (Dates Minutes Seconds)
    - **Zone tampon (str) :** Zone spéciale autour d'un site important (comme un parc ou un bâtiment historique) utilisée pour protéger et garder en bon état le site principal. Même si elle n'est pas officiellement une partie du site, elle est très importante pour sa sécurité. C'est un peu comme la clôture autour d'un jardin, qui aide à garder les plantes à l'intérieur en sécurité.
    - **Année d'inscription de la modification mineure des limites (str) :** Années de modification du site

> **Note :**<br>
Selon que le site ait l'information ou non, toutes les clés ne sont pas présentes (Par exemple, Zone tampon concerne généralement les sites partagés entre plusieurs pays. C'est le cas de l'[Arc géodésique de Struve](https://whc.unesco.org/fr/list/1187/) référencé dans **10 pays** )

<br>

``` json
[
    {
    "ID": 3,
    "Site": "Cathédrale d'Aix-la-Chapelle",
    "Description": "source: UNESCO/CPE\nLa description est disponible sous licence CC-BY-SA IGO 3.0\n\nC'est de 790 à 800 ...",
    "Informations complementaires": {
      "Date d'inscription": "1978",
      "Année d'inscription de la modification mineure des limites": "2013",
      "Critères": "(i)(ii)(iv)(vi)",
      "Bien": "0,2 ha",
      "Zone tampon": "67 ha",
      "Dossier": "3bis",
      "Coordonnées_en_DMS": "50 46 29.089 N 6 5 2.112 E"
    }
  },
```

## 4. Critères_****.json
A VOIR SI CE SERA UTILISE...

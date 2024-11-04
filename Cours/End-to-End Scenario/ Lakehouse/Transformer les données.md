# Transformer et préparer les données

À partir des étapes précédentes du tutoriel, nous avons ingéré des données brutes de la source vers la section Fichiers du lakehouse. 
Vous pouvez maintenant transformer ces données et les préparer pour la création de tables Delta.

1- Téléchargez les notebooks à partir du dossier Code source du didacticiel Lakehouse.

2- Dans le sélecteur situé en bas à gauche de l’écran, sélectionnez Data Enginneering 

3- Sélectionnez Importer un notebook dans la section Nouveau en haut de la page d’accueil.

4- Sélectionnez Charger dans le volet Importer l’état qui s’ouvre sur le côté droit de l’écran.

5- Sélectionnez tous les notebooks que vous avez téléchargés à la première étape de cette section.

![image](https://github.com/user-attachments/assets/01c17380-3d0f-4942-a180-e026806580a0)

6- Sélectionnez Ouvrir. Une notification indiquant l’état de l’importation s’affiche dans le coin supérieur droit de la fenêtre du navigateur.

7- Une fois l’importation réussie, accéder à la vue Éléments de l’espace de travail et voir les notebooks nouvellement importés. Sélectionnez le lakehouse wwilakehouse pour l’ouvrir

![image](https://github.com/user-attachments/assets/d061fa85-80ac-4ff7-a839-c082056fa1fe)

8- Une fois le lakehouse wwilakehouse ouvert, sélectionnez Ouvrir le notebook>existant dans le menu de navigation supérieur.

![image](https://github.com/user-attachments/assets/7ddfa6d4-88d3-4bc6-bd4f-aba7081ec3a2)

9- Dans la liste des notebooks existants, sélectionnez le notebook 01 - Créer des tables Delta , puis sélectionnez Ouvrir.

10- Dans le notebook ouvert dans l’explorateur lakehouse, vous voyez que le notebook est déjà lié à votre lakehouse ouvert.


11- Avant d’écrire des données sous forme de tables Delta lake dans la section Tables du lakehouse, vous utilisez deux fonctionnalités Fabric (commande en V et Optimiser l’écriture) pour optimiser l’écriture des données et améliorer les performances de lecture. Pour activer ces fonctionnalités dans votre session, définissez ces configurations dans la première cellule de votre notebook.

Pour démarrer le notebook et exécuter toutes les cellules dans l’ordre, sélectionnez Exécuter tout dans le ruban supérieur (sous Accueil). Ou, pour exécuter uniquement du code à partir d’une cellule spécifique, sélectionnez l’icône Exécuter qui apparaît à gauche de la cellule lors du pointage, ou appuyez sur MAJ + ENTRÉE sur votre clavier pendant que le contrôle se trouve dans la cellule.

![image](https://github.com/user-attachments/assets/8720e0ec-5e35-4a8d-bcbc-f4cdcac007a3)

Lors de l’exécution d’une cellule, vous n’avez pas eu à spécifier les détails du pool ou du cluster Spark sous-jacents, car Fabric les fournit via Live pool. Chaque espace de travail Fabric est fourni avec un pool Spark par défaut, appelé Live Pool. Cela signifie que lorsque vous créez des notebooks, vous n’avez pas à vous soucier de spécifier des configurations Spark ou des détails de cluster. Lorsque vous exécutez la première commande de notebook, le pool dynamique est opérationnel en quelques secondes. Et la session Spark est établie et elle commence à exécuter le code. L’exécution du code suivante est presque instantanée dans ce notebook pendant que la session Spark est active.

12 - Ensuite, vous lisez les données brutes de la section Fichiers du lakehouse et ajoutez d’autres colonnes pour différentes parties de date dans le cadre de la transformation. Enfin, vous utilisez l’API partitionBy Spark pour partitionner les données avant de les écrire au format de table Delta en fonction des colonnes de partie de données nouvellement créées (Année et Trimestre).

```
from pyspark.sql.functions import col, year, month, quarter

table_name = 'fact_sale'

df = spark.read.format("parquet").load('Files/wwi-raw-data/full/fact_sale_1y_full')
df = df.withColumn('Year', year(col("InvoiceDateKey")))
df = df.withColumn('Quarter', quarter(col("InvoiceDateKey")))
df = df.withColumn('Month', month(col("InvoiceDateKey")))

df.write.mode("overwrite").format("delta").partitionBy("Year","Quarter").save("Tables/" + table_name)

```








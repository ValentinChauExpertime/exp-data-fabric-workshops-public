Dans cette partie , nous allons analyser des données à l’aide du notebook SQL 

Option 1 : Créer un notebook T-SQL sur l’entrepôt
-------------------------------------------------

Pour commencer, créez un notebook T-SQL de l’une des deux manières suivantes :

1- Créez un notebook T-SQL à partir de la page d’accueil de Microsoft Fabric Warehouse. Accédez à la charge de travail de l’entrepôt de données, puis choisissez **Notebook**.
    
2- Sélectionnez **\+ Entrepôts** et ajoutez l’entrepôt `WideWorldImporters` . Sélectionnez l’entrepôt dans la `WideWorldImporters` boîte de dialogue du hub **de** données OneLake.
    
![Capture d’écran du portail Fabric du bouton Ajouter des entrepôts sous Entrepôts dans la zone Toutes les sources de l’Explorateur.](https://learn.microsoft.com/fr-fr/fabric/data-warehouse/media/tutorial-analyze-data-notebook/add-warehouses-button.png#lightbox)
    
3- Créez un notebook T-SQL à partir de l’éditeur d’entrepôt. À partir de votre `WideWorldImporters` entrepôt, dans le ruban de navigation supérieur, sélectionnez **Nouvelle requête SQL, puis **Nouvelle requête** SQL dans le notebook**.
    
![Capture d’écran du portail Fabric de la nouvelle requête SQL dans l’option de menu Notebook.](https://learn.microsoft.com/fr-fr/fabric/data-warehouse/media/tutorial-analyze-data-notebook/create-tsql-notebook-from-editor.png#lightbox)
    
4- Une fois le notebook créé, vous pouvez voir `WideWorldImporters` l’entrepôt est chargé dans l’Explorateur, et le ruban affiche T-SQL comme langue par défaut.
    
5- Cliquez avec le bouton droit pour lancer l’option **De menu Plus** dans le `dimension_city` tableau. Sélectionnez **SELECT TOP 100** pour générer un modèle SQL rapide pour explorer 100 lignes dans la table.
    
![image](https://github.com/user-attachments/assets/0a9fc232-1d61-451e-9973-ff696c637cf4)
    
6- Exécutez la cellule de code et vous pouvez voir les messages et les résultats.
    
![Capture d’écran du portail Fabric des résultats SELECT TOP 100.](https://learn.microsoft.com/fr-fr/fabric/data-warehouse/media/tutorial-analyze-data-notebook/tsql-notebook-top-100-results.png#lightbox)

---
product: campaign
title: Ajouter un champ calculé de type Énumération
description: Découvrez comment ajouter un champ calculé de type Énumération
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
hide: true
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 63%

---

# Ajouter un champ calculé de type Énumération {#adding-an-enumeration-type-calculated-field}



Nous allons créer ici une requête avec un champ calculé de type **[!UICONTROL Enumérations]**. Ce champ génère une colonne supplémentaire dans la fenêtre de prévisualisation des données. Cette colonne spécifie les valeurs numériques renvoyées pour chaque destinataire (0, 1 et 2). Un genre sera attribué à chaque valeur de la nouvelle colonne : « Homme » pour « 1 », « Femme » pour « 2 » ou « Non indiqué » si la valeur est égale à « 0 ».

* Quelle table doit-on sélectionner ?

  Table des personnes destinataires (nms:recipient).

* Quels sont les champs à sélectionner en colonne de sortie ?

  Nom, Prénom et Genre.

* En fonction de quels critères seront filtrées les informations ?

  En fonction de la langue des destinataires.

Les étapes sont les suivantes :

1. Ouvrez le Requêteur générique et sélectionnez la Table des destinataires (**[!UICONTROL nms:recipient]**).
1. Dans la fenêtre **[!UICONTROL Données à extraire]**, sélectionnez les champs **[!UICONTROL Nom]**, **[!UICONTROL Prénom]** et **[!UICONTROL Genre]**.

   ![](assets/query_editor_nveau_73.png)

1. Dans la fenêtre **[!UICONTROL Tri]**, cliquez sur **[!UICONTROL Suivant]** : aucun tri n&#39;est nécessaire pour cet exemple.
1. Dans **[!UICONTROL Filtrage des données]**, sélectionnez **[!UICONTROL Critères de filtrage]**.
1. Paramétrez une condition dans la fenêtre **[!UICONTROL Elément de la cible]** pour que les destinataires retournés en résultat soient de langue française.

   ![](assets/query_editor_nveau_74.png)

1. Dans la fenêtre **[!UICONTROL Formatage des données]**, cliquez sur **[!UICONTROL Ajouter un champ calculé]**.

   ![](assets/query_editor_nveau_75.png)

1. Dans le champ **[!UICONTROL Type]** de la fenêtre **[!UICONTROL Définition d’un champ calculé d’export]**, sélectionnez **[!UICONTROL Énumérations]**.

   Définissez à quelle colonne doit se référer le nouveau champ calculé. Pour cela, sélectionnez la colonne **[!UICONTROL Genre]** dans le menu déroulant du champ **[!UICONTROL Colonne source]** : c&#39;est à la colonne **[!UICONTROL Genre]** que vont correspondre les valeurs de destination.

   ![](assets/query_editor_nveau_76.png)

   Définissez les valeurs **** et **Destination** : la valeur de destination facilite la lecture du résultat de la requête. Cette requête doit renvoyer le genre du destinataire et le résultat sera 0, 1 ou 2.

   Pour chaque équivalence &quot;source-destination&quot; à renseigner, cliquez sur **[!UICONTROL Ajouter]** dans le champ **[!UICONTROL Liste des valeurs d&#39;énumérations]** :

   * Dans la colonne **[!UICONTROL Source]**, entrez chaque valeur source correspondant au genre (0, 1 et 2) dans de nouvelles lignes.
   * Dans la colonne **[!UICONTROL Destination]**, entrez les valeurs de destination : &quot;Non renseigné&quot; dans la ligne de &quot;0&quot;, &quot;Homme&quot; dans la ligne &quot;1&quot; et &quot;Femme&quot; dans la ligne &quot;2&quot;.

   Sélectionnez la fonction **[!UICONTROL Conserver la valeur source]**.

   Cliquez sur **[!UICONTROL Ok]** pour valider le champ calculé.

   ![](assets/query_editor_nveau_77.png)

1. Dans la fenêtre **[!UICONTROL Formatage des données]**, cliquez sur **[!UICONTROL Suivant]**.
1. Dans l&#39;étape de prévisualisation, cliquez sur **[!UICONTROL Lancer la prévisualisation des données]**.

   La colonne supplémentaire spécifie à quel genre correspond chacune des trois valeurs 0, 1 et 2 :

   * 0 pour &quot;Non renseigné&quot;
   * 1 pour &quot;Homme&quot;
   * 2 pour &quot;Femme&quot;

   ![](assets/query_editor_nveau_78.png)

   Par exemple, si vous ne saisissez pas le genre « 2 » dans la **[!UICONTROL Liste des valeurs d’énumération]** et que la fonction **[!UICONTROL Générer un avertissement et continuer]** du champ **[!UICONTROL Dans les autres cas]** est sélectionnée, vous obtiendrez un journal d’avertissement. Ce journal indique que le genre « 2 » (Féminin) n&#39;a pas été saisi. Il est affiché dans le champ **[!UICONTROL Logs générés lors de l&#39;export]**, dans la fenêtre de prévisualisation des données.

   ![](assets/query_editor_nveau_79.png)

   Prenons un autre exemple et supposons que la valeur d’énumération « 2 » n’ait pas été saisie. Sélectionnez la fonction **[!UICONTROL Générer une erreur et rejeter la ligne]** : tous les destinataires de genre « 2 » vont signaler des anomalies et les autres informations de la ligne (nom, prénom, etc.) ne sera pas exporté. Un log des erreurs s’affiche dans le champ **[!UICONTROL Logs générés lors de l&#39;export]** de la fenêtre de prévisualisation des données. Ce log indique que la valeur d’énumération « 2 » n’a pas été saisie.

   ![](assets/query_editor_nveau_80.png)

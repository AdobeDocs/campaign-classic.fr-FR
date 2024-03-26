---
product: campaign
title: Ajouter un champ calculé de type Énumération
description: Découvrez comment ajouter un champ calculé de type Énumération
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 67%

---

# Ajouter un champ calculé de type Énumération {#adding-an-enumeration-type-calculated-field}



Vous allez élaborer une requête comportant un champ calculé de type **[!UICONTROL Enumérations]**. Ce champ va produire une colonne supplémentaire dans la fenêtre de prévisualisation des données. Cette colonne précisera les valeurs chiffrées correspondant au genre des destinataires (0, 1 et 2). Chaque valeur chiffrée se verra attribuer un genre dans la colonne : &quot;Homme&quot; pour &quot;1&quot;, &quot;Femme&quot; pour &quot;2&quot; ou le statut &quot;Non renseigné&quot; si la valeur est &quot;0&quot;.

* Quelle table doit-on sélectionner ?

  La table des destinataires (nms:recipient).

* Quels sont les champs à sélectionner en colonne de sortie ?

  Nom, Prénom et Genre.

* En fonction de quels critères seront filtrées les informations ?

  En fonction de la langue des destinataires.

Les étapes sont les suivantes :

1. Ouvrez le Requêteur générique et sélectionnez la table des Destinataires (**[!UICONTROL nms:recipient]**).
1. Dans la fenêtre **[!UICONTROL Données à extraire]**, sélectionnez les champs **[!UICONTROL Nom]**, **[!UICONTROL Prénom]** et **[!UICONTROL Genre]**.

   ![](assets/query_editor_nveau_73.png)

1. Dans la fenêtre **[!UICONTROL Tri]**, cliquez sur **[!UICONTROL Suivant]** : aucun tri n&#39;est nécessaire pour cet exemple.
1. Dans **[!UICONTROL Filtrage des données]**, sélectionnez **[!UICONTROL Critères de filtrage]**.
1. Paramétrez une condition dans la fenêtre **[!UICONTROL Elément de la cible]** pour que les destinataires retournés en résultat soient de langue française.

   ![](assets/query_editor_nveau_74.png)

1. Dans la fenêtre **[!UICONTROL Formatage des données]**, cliquez sur **[!UICONTROL Ajouter un champ calculé]**.

   ![](assets/query_editor_nveau_75.png)

1. Dans le champ **[!UICONTROL Type]** de la fenêtre **[!UICONTROL Définition d&#39;un champ calculé d&#39;export]**, sélectionnez **[!UICONTROL Enumérations]**.

   Définissez la colonne à laquelle doit se référer le nouveau champ calculé. Pour ce faire, sélectionnez l’option **[!UICONTROL Genre]** dans le menu déroulant du **[!UICONTROL Colonne source]** champ : les valeurs de destination vont correspondre au **[!UICONTROL Genre]** colonne .

   ![](assets/query_editor_nveau_76.png)

   Définissez la valeur **Source** et la valeur **Destination** : la valeur de destination va faciliter la lisibilité du résultat de la requête. Cette requête doit retourner le genre des destinataires. Le résultat correspondra aux genres 0, 1, ou 2.

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

   Par exemple, si vous n’entrez pas le genre &quot;2&quot; dans la variable **[!UICONTROL Liste des valeurs d&#39;énumération]**, et la variable **[!UICONTROL Générer un avertissement et continuer]** de la fonction **[!UICONTROL Dans d’autres cas]** est sélectionné, vous obtiendrez un journal d’avertissement. Ce journal indique que le genre &quot;2&quot; (féminin) n&#39;a pas été renseigné. Il s’affiche dans la **[!UICONTROL Logs générés lors de l&#39;export]** champ de la fenêtre de prévisualisation des données.

   ![](assets/query_editor_nveau_79.png)

   Prenons un autre exemple et disons que la valeur de l&#39;énumération &quot;2&quot; n&#39;est pas saisie. Sélectionnez la variable **[!UICONTROL Générer une erreur et rejeter la ligne]** fonction : tous les destinataires du genre &quot;2&quot; génèrent des anomalies et les autres informations de la ligne (prénom et nom, etc.) ne seront pas exportés. Un journal des erreurs s’affiche dans la variable **[!UICONTROL Logs générés lors de l&#39;export]** champ de la fenêtre de prévisualisation des données. Ce journal indique que la valeur de l&#39;énumération &quot;2&quot; n&#39;est pas saisie.

   ![](assets/query_editor_nveau_80.png)

---
product: campaign
title: Requête avec une relation multiple-à-multiple
description: Découvrez comment exécuter des requêtes à l’aide d’une relation multiple-à-multiple
feature: Query Editor, Workflows
hide: true
hidefromtoc: true
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '475'
ht-degree: 100%

---

# Requête avec une relation multiple-à-multiple {#querying-using-a-many-to-many-relationship}



Dans cet exemple, vous allez récupérer les destinataires non contactés au cours des 7 derniers jours. Cette requête concerne toutes les diffusions.

Ce cas indique par ailleurs comment paramétrer un filtrage découlant du choix d&#39;un élément de collection (ou noeud orange). Les éléments de collection sont disponibles dans la fenêtre **[!UICONTROL Champ à sélectionner]**.

* Quelle table doit-on sélectionner ?

  La table des destinataires (**nms:recipient**).

* Quels sont les champs à sélectionner en colonne de sortie ?

  Clé primaire, Nom, Prénom et Email.

* En fonction de quels critères seront filtrées les informations ?

  En fonction des logs de diffusion des destinataires. Ils remontent jusqu&#39;à 7 jours avant la date du jour.

Les étapes sont les suivantes :

1. Ouvrez le Requêteur générique et sélectionnez la table des Destinataires **[!UICONTROL (nms:recipient)]**.
1. Dans la fenêtre **[!UICONTROL Données à extraire]**, sélectionnez les champs **[!UICONTROL Clé primaire]**, **[!UICONTROL Prénom]**, **[!UICONTROL Nom]** et **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Dans la fenêtre de tri, ordonnez les noms alphabétiquement.

   ![](assets/query_editor_nveau_34.png)

1. Dans la fenêtre **[!UICONTROL Filtrage des données]**, choisissez **[!UICONTROL Critères de filtrage]**.
1. Dans la fenêtre **[!UICONTROL Elément de la cible]**, la condition de filtrage qui permet d&#39;extraire de la base les profils qui n&#39;ont aucun log de tracking pour les 7 derniers jours est réalisée en deux étapes. En effet, l&#39;élément de collection que vous allez sélectionner est un lien n-n.

   * Tout d&#39;abord, sélectionnez l&#39;élément de collection (noeud orange) **[!UICONTROL Logs de diffusion des destinataires (broadlog)]** pour la première colonne **[!UICONTROL Valeur]**.

     ![](assets/query_editor_nveau_67.png)

     Sélectionnez l&#39;opérateur **[!UICONTROL n&#39;existent pas tel que]**. Il n&#39;y a pas de seconde valeur à sélectionner dans cette ligne.

   * Le contenu de la seconde condition de filtrage découle directement du choix de la première. Ici, le champ **[!UICONTROL Date de l&#39;événement]** est directement proposé dans la table **[!UICONTROL Logs de diffusion des destinataires]** car un lien s&#39;opère vers cette table.

     ![](assets/query_editor_nveau_36.png)

     Sélectionnez **[!UICONTROL Date de l&#39;événement]** avec l&#39;opérateur **[!UICONTROL supérieur ou égal à]**. Sélectionnez la valeur **[!UICONTROL DaysAgo (7)]**. Pour cela, cliquez sur **[!UICONTROL Editer l&#39;expression]** dans le champ **[!UICONTROL Valeur]**. Dans la fenêtre **[!UICONTROL Type de formule]**, sélectionnez **[!UICONTROL Traitement sur les dates]** puis **[!UICONTROL Date courante moins n jours]** et saisissez la valeur &quot;7&quot;.

     ![](assets/query_editor_nveau_37.png)

     La condition de filtrage est paramétrée.

     ![](assets/query_editor_nveau_38.png)

1. Dans la fenêtre **[!UICONTROL Formatage des données]**, modifiez la casse des noms : ils doivent s&#39;afficher en majuscules. Cliquez sur la ligne du **[!UICONTROL Nom]** dans la colonne **[!UICONTROL Transformation]** et choisissez **[!UICONTROL Passer en majuscules]** dans le menu déroulant.

   ![](assets/query_editor_nveau_39.png)

1. Utilisez la fonction **[!UICONTROL Ajouter un champ calculé]** pour insérer une colonne dans la fenêtre de prévisualisation des données.

   Dans cet exemple, ajoutez un champ calculé qui regroupe le prénom et le nom des destinataires dans une seule colonne. Cliquez sur **[!UICONTROL Ajouter un champ calculé]**. Dans la fenêtre **[!UICONTROL Définition d&#39;un champ calculé d&#39;export]**, saisissez un libellé et un nom interne puis choisissez le type **[!UICONTROL Expression JavaScript]**. Entrez l&#39;expression ci-dessous :

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Cliquez sur **[!UICONTROL OK]**. La fenêtre **[!UICONTROL Formatage des données]** est paramétrée.

   Pour plus d&#39;informations sur l&#39;ajout de champs calculés, consultez cette section.

1. Le résultat s&#39;affiche dans la fenêtre **[!UICONTROL Prévisualisation des données]**. Les destinataires non contactés dans les 7 jours antérieurs à la date courante sont affichés. Ils sont ordonnés alphabétiquement. Les noms sont en majuscules. La colonne supplémentaire qui regroupe les prénoms et les noms est bien là.

   ![](assets/query_editor_nveau_41.png)

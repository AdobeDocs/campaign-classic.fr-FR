---
product: campaign
title: Effectuer une requête sur la table des destinataires
description: Découvrez comment effectuer une requête sur la table des destinataires.
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 77%

---

# Requête de la table des destinataires {#querying-recipient-table}



Dans cet exemple, vous allez récupérer les noms et emails des destinataires dont le domaine d&#39;email est &quot;free.fr&quot; et non domiciliés à Paris.

* Quelle table doit-on sélectionner ?

  La table des destinataires (nms:recipient).

* Champs à sélectionner en colonnes de sortie.

  Email, Nom, Ville et Numéro de compte.

* En fonction de quels critères seront filtrés les destinataires ?

  En fonction de la ville de résidence et du domaine d&#39;email.

* Y a-t-il tri ?

  Oui, en fonction du **[!UICONTROL N° de compte]** et du **[!UICONTROL Nom]**.

Pour réaliser cet exemple, les étapes sont les suivantes :

1. Cliquez sur **[!UICONTROL Outils > Requêteur générique...]** et sélectionnez la variable **Destinataires** (**nms:recipient**). Cliquez ensuite sur **[!UICONTROL Suivant]**.
1. Choisissez : **[!UICONTROL Nom]**, **[!UICONTROL Prénom]**, **[!UICONTROL Email]**, **[!UICONTROL Ville]** et **[!UICONTROL Numéro de compte]**. Ces champs sont ajoutés à **[!UICONTROL Colonnes de sortie]**. Cliquez ensuite sur **[!UICONTROL Suivant]**.

   ![](assets/query_editor_03.png)

1. Triez les colonnes pour les afficher dans l’ordre approprié. Ici, nous allons trier les numéros de compte par ordre décroissant et les noms par ordre alphabétique. Cliquez ensuite sur **[!UICONTROL Suivant]**.

   ![](assets/query_editor_04.png)

1. Dans la fenêtre **[!UICONTROL Filtrage des données]**, affinez votre recherche en sélectionnant **[!UICONTROL Critères de filtrage]**. Cliquez sur **[!UICONTROL Suivant]**.
1. La fenêtre **[!UICONTROL Elément de la cible]** sert à renseigner les paramètres de filtrage.

   Définissez la condition de filtrage suivante : destinataires dont le domaine de l&#39;email est égal à &quot;orange.co.uk&quot;. Pour cela, choisissez **Domaine de l&#39;email (@email)** dans le **[!UICONTROL Expression]** colonne, choisissez **égal à** dans le **[!UICONTROL Opérateur]** et saisissez &quot;orange.co.uk&quot; dans la colonne **[!UICONTROL Valeur]** colonne .

   ![](assets/query_editor_05.png)

1. A ce stade de l&#39;exemple, vous pouvez cliquer sur le bouton **[!UICONTROL Répartition des valeurs]**. Il permet d&#39;obtenir une répartition en fonction du domaine d&#39;email des prospects. Un pourcentage est donné pour chaque domaine d&#39;email de la base. Les domaines autres que &quot;free.fr&quot; restent affichés car le filtre n&#39;est pas encore appliqué.

   Le résumé de la requête s&#39;affiche au bas de la fenêtre, soit : **Domaine de l&#39;email égal à &#39;free.fr&#39;**.

1. Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]** pour avoir une première idée du résultat de la requête. Seuls les destinataires avec des domaines d&#39;email &quot;free.fr&quot; sont affichés.

   ![](assets/query_editor_nveau_17.png)

1. Modifiez la requête pour obtenir des contacts non domiciliés à Paris.

   Sélectionnez **[!UICONTROL Ville (location/@city)]** dans la colonne **[!UICONTROL Expression]**, l&#39;opérateur **[!UICONTROL différent de]** et saisissez **[!UICONTROL Paris]** dans l&#39;autre colonne **[!UICONTROL Valeur]**.

   ![](assets/query_editor_08.png)

1. Accédez à la fenêtre **[!UICONTROL Formatage des données]**. Vérifiez l&#39;ordre des colonnes. Déplacez la ligne &quot;Ville&quot; pour la remonter après le &quot;N° de compte&quot;.

   Décochez la ligne &quot;Prénom&quot; pour ne plus l&#39;afficher en résultat.

   ![](assets/query_editor_nveau_15.png)

1. Dans la fenêtre **[!UICONTROL Prévisualisation des données]**, cliquez sur **[!UICONTROL Lancer la prévisualisation des données]**. Cette fonction calcule le résultat de la requête.

   L&#39;onglet **[!UICONTROL Résultat en colonnes]** vous présente le résultat de la requête en colonnes.

   Le résultat ne comporte que les destinataires dont le domaine d&#39;email est &quot;free.fr&quot; et ne vivant pas à Paris. La colonne &quot;Prénom&quot; n&#39;est pas affichée car elle a été décochée à l&#39;étape précédente. Les numéros de compte sont triés de manière descendante.

   ![](assets/query_editor_nveau_12.png)

   L&#39;onglet **[!UICONTROL Résultat XML]** montre le résultat au format XML.

   ![](assets/query_editor_nveau_13.png)

   Visualisez la requête en langage SQL grâce à l&#39;onglet **[!UICONTROL Requêtes SQL générées]**.

   ![](assets/query_editor_nveau_14.png)

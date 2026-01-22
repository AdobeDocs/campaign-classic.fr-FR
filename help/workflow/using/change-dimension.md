---
product: campaign
title: Changement de dimension
description: Changement de dimension
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '397'
ht-degree: 100%

---

# Changement de dimension{#change-dimension}



L&#39;activité de changement de dimension permet de modifier la dimension de ciblage au cours du cycle de construction de la cible. Le basculement d&#39;axe dépend du modèle de données et de la dimension en entrée. Vous pouvez ainsi par exemple passer de la dimension &quot;contrats&quot; à la dimension &quot;clients&quot;.

Vous pouvez également utiliser cette activité pour définir les colonnes additionnelles de la nouvelle cible.

Il est possible de définir des critères de dédoublonnage des données.

## Mode de paramétrage {#configuration-mode}

Pour paramétrer l&#39;activité de changement de dimension, respectez les étapes suivantes :

1. Sélectionnez la nouvelle dimension de ciblage à partir du champ **[!UICONTROL Changement de dimension]**.

   ![](assets/s_user_change_dimension_param1.png)

1. Lors du changement de dimension, vous pouvez conserver tous les éléments ou sélectionner ceux à conserver en sortie. Dans l&#39;exemple ci-dessous, le nombre maximal de doublons est fixé à 2.

   ![](assets/s_user_change_dimension_limit.png)

   Lorsque vous choisissez de ne conserver qu’un seul enregistrement, une collection apparaît dans le schéma de travail : cette collection représente tous les enregistrements qui ne seront pas ciblés dans le résultat final (puisqu’un seul enregistrement est conservé). Cette collection permet, comme toute autre collection, de calculer des agrégats ou de récupérer des informations en colonne.

   Par exemple, si on passe de la dimension des **[!UICONTROL Clients]** à celle des **[!UICONTROL Destinataires]**, il sera possible de cibler les clients d&#39;un magasin, en précisant le nombre d&#39;achats réalisés.

1. Si vous choisissez de ne pas conserver tous les enregistrements, vous pouvez configurer le mode de gestion des doublons.

   ![](assets/s_user_change_dimension_param2.png)

   Les flèches bleues permettent de définir l&#39;ordre de priorité de traitement des doublons.

   Dans l’exemple ci-dessus, les destinataires seront dédupliqués d’abord sur leur adresse e-mail puis, au besoin, sur leur numéro de compte.

1. L&#39;onglet **[!UICONTROL Résultat]** permet d&#39;ajouter des informations complémentaires.

   Vous pouvez par exemple récupérer le numéro du département à partir du code postal en utilisant une fonction de type **Substring**. Pour cela :

   * Cliquez sur le lien **[!UICONTROL Ajouter des données...]** et sélectionnez **[!UICONTROL Données liées à la dimension de filtrage]**.

     ![](assets/wf_change-dimension_sample_01.png)

     >[!NOTE]
     >
     >La création et la gestion des colonnes additionnelles sont présentées dans la section [Ajouter des données](query.md#adding-data).

   * Choisissez la dimension de ciblage précédente (avant le basculement d&#39;axe) et sélectionnez le **[!UICONTROL Code Postal]** dans la sous-arborescence **[!UICONTROL Localisation]** du destinataire, puis cliquez sur **[!UICONTROL Editer l&#39;expression]**.

     ![](assets/wf_change-dimension_sample_02.png)

   * Cliquez sur **[!UICONTROL Sélection avancée]** et choisissez **[!UICONTROL Editer la formule à partir d&#39;une expression]**.

     ![](assets/wf_change-dimension_sample_03.png)

   * Utilisez les fonctions proposées dans la liste et indiquez le calcul à réaliser.

     ![](assets/wf_change-dimension_sample_04.png)

   * Pour finir, saisissez le libellé de la colonne que vous venez de créer.

     ![](assets/wf_change-dimension_sample_05.png)

1. Exécutez le workflow pour visualiser le résultat de ce paramétrage. Comparez les données contenues dans les tables avant et après l&#39;activité de changement de dimension, comparez également la structure des tables du workflow, comme dans les exemples suivants :

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

---
title: Création d'une liste de profils avec un workflow
seo-title: Création d'une liste de profils avec un workflow
description: Création d'une liste de profils avec un workflow
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# Création d&#39;une liste de profils avec un workflow{#creating-a-profile-list-with-a-workflow}

To create a **[!UICONTROL List]** type list based on the new recipient table, you need to create a targeting workflow which will generate the list. Pour plus d&#39;informations sur les listes dans Campaign, consultez [cette section](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Accédez au **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** noeud de l&#39;explorateur.
1. Créez un nouveau workflow de ciblage.
1. Placez une activité **Requête** puis une activité **Mise à jour de liste**.

   ![](assets/mapping_create_list_workflow01.png)

1. Double-click the **Query** activity, then click **[!UICONTROL Edit the query]** to choose a targeting dimension based on the schema of the new recipient table (in our example: **Individual**). Cliquez sur **[!UICONTROL Finish]** pour confirmer.

   ![](assets/mapping_create_list_workflow03.png)

1. Cliquez deux fois sur l’activité de mise à jour **de la** liste, puis sélectionnez le **[!UICONTROL Create the list if necessary (Computed name)]** bouton radio.

   ![](assets/mapping_create_list_workflow02.png)

1. Sélectionner le dossier de création de la nouvelle liste.
1. Exécuter le workflow pour créer la liste.
1. View the result in the node of the tree which you selected during the **[!UICONTROL List update]** activity.

   Le tableau de bord précise le schéma sur lequel est basée la liste, comme le montre l&#39;écran ci-dessous :

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>Vous pouvez également consulter la vidéo sur la [création d&#39;une liste de destinataires](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html).


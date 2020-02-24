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

Pour créer une liste de type **[!UICONTROL Liste]** basée sur la nouvelle table des destinataires, vous devez créer un workflow de ciblage qui va générer la liste. Pour plus d&#39;informations sur les listes dans Campaign, consultez [cette section](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Ouvrez le nœud **[!UICONTROL Profils et cibles > Traitements > Workflows de ciblage]** dans l&#39;explorateur.
1. Créez un nouveau workflow de ciblage.
1. Placez une activité **Requête** puis une activité **Mise à jour de liste**.

   ![](assets/mapping_create_list_workflow01.png)

1. Double cliquez sur l&#39;activité **Requête** puis cliquez sur **[!UICONTROL Editer la requête]** afin de choisir une dimension de ciblage basée sur le schéma de la nouvelle table de destinataires (dans le cas de l&#39;exemple : **Individual**). Cliquez sur **[!UICONTROL Terminer]** pour valider.

   ![](assets/mapping_create_list_workflow03.png)

1. Double cliquez sur l&#39;activité **Mise à jour de la liste** puis sélectionnez le bouton radio **[!UICONTROL Créer la liste si besoin (Nom calculé)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Sélectionner le dossier de création de la nouvelle liste.
1. Exécuter le workflow pour créer la liste.
1. Visualiser le résultat dans le noeud de l&#39;arborescence que vous avez choisi lors de l&#39;activité **[!UICONTROL Mise à jour de la liste]**.

   Le tableau de bord précise le schéma sur lequel est basée la liste, comme le montre l&#39;écran ci-dessous :

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>Vous pouvez également consulter la vidéo sur la [création d&#39;une liste de destinataires](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html).


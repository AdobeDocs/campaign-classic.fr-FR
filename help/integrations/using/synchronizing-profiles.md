---
title: Synchronisation des profils
seo-title: Synchronisation des profils
description: Synchronisation des profils
seo-description: null
page-status-flag: never-activated
uuid: 3d5f0fd4-dfe7-4b34-a75f-8cf36fb7c91d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 91115d4f-0cb6-4bce-b28d-17f15e9f9a0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Synchronisation des profils{#synchronizing-profiles}

ACS Connector réplique les données de Campaign v7 vers Campaign Standard. Le données reçues de Campaign v7 peuvent être utilisées pour créer des diffusions dans Campaign Standard. Les opérations ci-dessous vous permettent de voir la manière dont les profils sont synchronisés.

* **Ajouter de nouveaux destinataires** : créez un nouveau destinataire dans Campaign v7 et vérifiez qu&#39;un profil correspondant a été répliqué vers Campaign Standard. See [Creating a new recipient](#creating-a-new-recipient).
* **Mettre à jour les destinataires** : éditez un nouveau destinataire dans Campaign v7 et visualisez le profil correspondant dans Campaign Standard pour vérifier que la mise à jour a été répliquée. Voir [Modification d’un destinataire](#editing-a-recipient).
* **Créer un workflow dans Campaign Standard** : créez un workflow dans Campaign Standard qui comprend une requête avec une audience ou des profils répliqués depuis Campaign v7. Voir à ce propos la section [Créer un workflow](#creating-a-workflow).
* **Créer une diffusion dans Campaign Standard** : exécutez le workflow jusqu&#39;à la fin pour envoyer une diffusion. See [Creating a delivery](#creating-a-delivery).
* **Vérifiez le lien** de désabonnement : Utilisez une application Web Campaign v7 pour vous assurer que le choix du destinataire de se désabonner d’un service est envoyé à la base de données Campaign v7. L’option permettant d’arrêter la réception du service est répliquée dans Campaign Standard. See [Changing the unsubscription link](#changing-the-unsubscription-link).

## Prérequis {#prerequisites}

Les sections ci-après décrivent la manière dont ACS Connector permet d&#39;ajouter et d&#39;éditer des destinataires dans Campaign v7 et de les utiliser ensuite dans une diffusion Campaign Standard. ACS Connector requiert les éléments suivants :

* des destinataires dans Campaign v7 répliqués vers Campaign Standard,
* les droits utilisateurs pour exécuter des workflows dans Campaign v7 et Campaign Standard,
* les droits utilisateurs pour créer et exécuter une diffusion dans Campaign Standard.

## Modification du lien de désinscription {#changing-the-unsubscription-link}

Lorsqu&#39;un destinataire clique sur le lien de désinscription dans un email envoyé par Campaign Standard, le profil correspondant dans Campaign Standard est mis à jour. Pour s&#39;assurer qu&#39;un profil répliqué comprend le choix d&#39;un utilisateur de se désinscrire d&#39;un service, l&#39;information doit être envoyée à Campaign v7 plutôt qu&#39;à Campaign Standard. Pour appliquer la modification, le service de désinscription est associé à une application web de Campaign v7 plutôt qu&#39;à Campaign Standard.

>[!NOTE]
>
>Avant de suivre la procédure ci-dessous, demandez à votre consultant de configurer l&#39;application web pour le service de désinscription.

## Création d&#39;un nouveau destinataire {#creating-a-new-recipient}

1. Créez un destinataire dans Campaign v7 pour la réplication vers Campaign Standard. Entrez autant d’informations que possible, y compris le nom de famille, le prénom, l’adresse électronique et l’adresse postale du destinataire. Toutefois, ne choisissez pas un destinataire **[!UICONTROL Salutation]** puisqu’il sera ajouté dans la section suivante, [Modification d’un destinataire](#editing-a-recipient). Pour plus d’informations, voir [Ajout de destinataires](../../platform/using/adding-profiles.md).

   ![](assets/acs_connect_profile_sync_01.png)

1. Vérifiez que le nouveau destinataire a été ajouté dans Campaign Standard. Lors de la vérification du profil, assurez-vous que les données saisies dans Campaign v7 sont également disponibles dans Campaign Standard. Pour savoir où trouver les profils dans Campaign Standard, reportez-vous à la section [Principes de navigation](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_02.png)

   Par défaut, la réplication périodique pour ACS Connector est effectuée une fois toutes les 15 minutes. Pour plus d’informations, voir Réplication des [données](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Edition d&#39;un destinataire {#editing-a-recipient}

Les étapes ci-après permettant la modification d&#39;une seule information montrent de façon simple comment Campaign v7 devient la base de données principale de Campaign Standard lors de l&#39;utilisation de la réplication des données. La modification ou la suppression de données répliquées dans Campaign v7 a le même impact sur les données correspondantes dans Campaign Standard.

1. Sélectionnez le nouveau destinataire dans [Création d’un nouveau destinataire](#creating-a-new-recipient) et modifiez son nom. Par exemple, choisissez un **[!UICONTROL Salutation]** pour le destinataire (p. ex. M. ou Mme). Pour plus d’informations, voir [Modification d’un profil](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_03.png)

1. Vérifiez que le nom du destinataire a été mis à jour dans Campaign Standard. Pour savoir où trouver les profils dans Campaign Standard, reportez-vous à la section [Principes de navigation](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_04.png)

   Par défaut, la réplication périodique pour ACS Connector est effectuée une fois toutes les 15 minutes. Pour plus d’informations, voir Réplication des [données](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Créer un workflow  {#creating-a-workflow}

Les profils et services répliqués depuis Campaign v7 permettent aux spécialistes du marketing digital d&#39;exploiter les données complètes dans Campaign Standard. Les instructions ci-dessous montrent comment ajouter une requête à un workflow de Campaign Standard et comment l&#39;utiliser ensuite avec la base de données répliquée.

Pour plus d&#39;informations et des instructions complètes relatives aux workflows Campaign Standard, reportez-vous à la section [Workflows](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/about-workflows-and-data-management/workflow-data-and-processes.html).

1. Go to Campaign Standard and click **[!UICONTROL Marketing Activities]**.
1. Click **[!UICONTROL Create]** on the upper right.
1. Clics **[!UICONTROL Workflow]**.
1. Cliquez sur **[!UICONTROL New workflow]** et **[!UICONTROL Next]**.
1. Enter a name for the workflow in the **[!UICONTROL Label]** field and additional information if needed. Clics **[!UICONTROL Next]**.
1. From **[!UICONTROL Targeting]** on the left, drag a **[!UICONTROL Query]** target to the workspace.

   ![](assets/acs_connect_profile_sync_05.png)

1. Double click the **[!UICONTROL Query]** activity and choose a parameter that can be used with the replicated database. Par exemple, vous pouvez :

   * Faites glisser le curseur **[!UICONTROL Profiles]** vers l’espace de travail. Utilisez le menu déroulant des champs pour choisir **[!UICONTROL Is external resource]** de rechercher les profils répliqués à partir de Campaign v7.
   * Placer d&#39;autres paramètres de requête pour cibler davantage les profils répliqués.

## Création d&#39;une diffusion {#creating-a-delivery}

>[!NOTE]
>
>The instructions for creating the delivery continue the workflow started with [Creating a workflow](#creating-a-workflow).

Les spécialistes du marketing numérique peuvent exploiter une application Web Campaign v7 pour s’assurer que le choix d’un destinataire de se désabonner d’un service est envoyé à la base de données Campaign v7. Une fois que le destinataire a cliqué sur le lien de désabonnement, l’option permettant d’arrêter de recevoir le service est répliquée de Campaign v7 vers Campaign Standard. Pour plus d’informations, voir [Modification du lien](#changing-the-unsubscription-link)de désabonnement.

Suivez la procédure ci-dessous pour ajouter une diffusion email à un workflow existant avec le service de désinscription créé dans Campaign v7. Pour obtenir des informations supplémentaires et des instructions complètes en ce qui concerne les workflows de Campaign Standard, consultez ce [document](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/about-workflows-and-data-management/workflow-data-and-processes.html).

>[!NOTE]
>
>Avant de suivre la procédure ci-dessous, demandez à votre consultant de configurer l&#39;application web pour le service de désinscription.

1. Click **[!UICONTROL Channels]** on the left.
1. Drag **[!UICONTROL Email delivery]** to the existing workflow in the workspace.

   ![](assets/acs_connect_profile_sync_07.png)

1. Cliquez deux fois sur l’ **[!UICONTROL Email delivery]** activité et choisissez **[!UICONTROL Single send email]** ou **[!UICONTROL Recurring email]**. Sélectionnez vos options et cliquez sur **[!UICONTROL Next]**.
1. Cliquez sur **[!UICONTROL Send via email]** , puis sur **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. Enter a name for the delivery in the **[!UICONTROL Label]** field and additional information if needed. Clics **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. In the **[!UICONTROL Subject]** field, enter the subject that will appear in the recipient&#39;s email inbox.
1. Cliquez sur **[!UICONTROL Change content]** pour ajouter un modèle HTML.

   ![](assets/acs_connect_profile_sync_10.png)

1. Choose content that includes the link to unsubscribe to the service. Click **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. Le lien de désinscription actuel doit être remplacé par un nouveau lien qui utilise l&#39;application web créée par votre consultant. Recherchez le lien de désinscription dans la partie inférieure de l&#39;email et cliquez dessus. Pour supprimer le lien, cliquez sur l&#39;icône représentant une corbeille.

   ![](assets/acs_connect_profile_sync_12.png)

1. Cliquez dans la même zone de contenu, puis saisissez **Lien de désinscription**.

   ![](assets/acs_connect_profile_sync_13.png)

1. Sélectionnez le texte avec votre curseur et cliquez sur l&#39;icône représentant une chaîne.
1. Clics **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. Cliquez sur l&#39;icône représentant un dossier pour sélectionner la landing page.

   ![](assets/acs_connect_profile_sync_15.png)

1. Choose the web application created by the consultant and click **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_16.png)

1. Clics **[!UICONTROL Create]**.
1. Revenez au workflow en cliquant sur le nom de la diffusion.

   ![](assets/acs_connect_profile_sync_17.png)

1. Cliquez sur **[!UICONTROL Start]** pour envoyer la diffusion. L’icône de remise de courrier électronique clignote pour indiquer qu’elle est en cours de préparation pour la remise.

   ![](assets/acs_connect_profile_sync_18.png)

1. Cliquez deux fois sur le **[!UICONTROL Email delivery]** canal et choisissez **[!UICONTROL Confirm]** d’envoyer le courriel. Cliquez sur **[!UICONTROL OK]** pour envoyer les messages.

   ![](assets/acs_connect_profile_sync_19.png)

## Vérification du service de désinscription {#verifying-the-unsubscription-service}

Suivez les instructions des sections [Création d’un flux de travail](#creating-a-workflow) et [Création d’une diffusion](#creating-a-delivery) avant de passer aux étapes ci-dessous.

1. Le destinataire clique sur le lien de désinscription dans la diffusion email.

   ![](assets/acs_connect_profile_sync_20.png)

1. Il confirme la désinscription.

   ![](assets/acs_connect_profile_sync_21.png)

1. Les données des destinataires dans Campaign v7 sont mises à jour pour indiquer que l’utilisateur s’est désabonné. Vérifiez que la case **[!UICONTROL No longer contact (by any channel)]** est cochée pour le destinataire. Pour savoir comment afficher un destinataire dans Campaign v7, voir [Modification d’un profil](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_22.png)

1. Go to Campaign Standard and open the profile details for the recipient. Confirm that a checkbox appears next to **[!UICONTROL No longer contact (by any channel)]**. To learn where to find profiles in Campaign Standard, see [Navigation Basics](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_23.png)


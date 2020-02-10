---
title: 'Utilisation : '
seo-title: 'Utilisation : '
description: 'Utilisation : '
seo-description: null
page-status-flag: never-activated
uuid: d4c76fdf-d562-4151-93ec-08b4f6563440
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: fbc38e33-60a6-4d21-a598-312293d168fb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Utilisation :{#use-case}

## Créer un filtre sur le format des emails des abonnés {#creating-a-filter-on-the-email-format-of-subscribers}

Dans le ce cas pratique, nous allons créer un filtre afin de trier les abonnement à des newsletters en fonction du format d&#39;email renseigné par les destinataires.

Pour ce faire, nous devons utiliser un filtre prédéfini : ces filtres sont liés à un type de document et sont accessibles via le **[!UICONTROL Administration > Configuration > Predefined filters]** noeud. Ces filtres de données peuvent être utilisés pour chaque type d’éditeur (ou de document) de l’application.

Le mode de création des filtres sur les données est le même que celui des filtres prédéfinis. Toutefois, un champ supplémentaire vous permet de sélectionner le type de document auquel le filtre sera appliqué.

Les étapes sont les suivantes :

1. Créez un filtre via le **[!UICONTROL Administration > Configuration > Predefined filters]** noeud.
1. Click the **[!UICONTROL Select link]** icon to select the concerned document:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Sélectionnez le schéma des abonnements (nms:subscription) et cliquez sur **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Click **[!UICONTROL Edit link]** to view the fields of the selected document.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Vous pouvez alors consulter le contenu du document sélectionné :

   ![](assets/s_ncs_user_filter_view_schema.png)

   Vous pouvez accéder à ces champs pour définir les conditions de filtre dans le corps de l’éditeur de filtres. Un filtre d’application est défini exactement de la même manière qu’un filtre avancé. See [Creating an advanced filter](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Créez un nouveau filtre sur les abonnements afin de n&#39;afficher que les abonnements pour lequel aucun format des email n&#39;a été défini :

   ![](assets/s_ncs_user_filter_parameters.png)

1. Click **[!UICONTROL Save]** to add a filter to the pre-defined filters for this type of list.
1. You can now use this filter in the **[!UICONTROL Subscriptions]** tab of the recipient profile; you can access the &quot;Unknown e-mail format&quot; filter by clicking the **[!UICONTROL Filters]** button.

   ![](assets/s_ncs_user_filter_on_events.png)

   Le nom du filtre actif s’affiche au-dessus de la liste. Pour annuler le filtre, cliquez sur l’ **[!UICONTROL Delete this filter]** icône .

   ![](assets/s_ncs_user_filter_on_subscriptions.png)


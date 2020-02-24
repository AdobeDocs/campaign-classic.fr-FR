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

Pour cela, nous allons utiliser un filtre prédéfini : associés à un type de document, ces filtres sont accessibles depuis le nœud **[!UICONTROL Administration > Paramétrage > Filtres prédéfinis]**. Ces filtres sur les données peuvent être utilisés pour chaque type d&#39;éditeurs (ou documents) de l&#39;application.

Le mode de création des filtres sur les données est le même que celui des filtres prédéfinis. Toutefois, un champ supplémentaire vous permet de sélectionner le type de document auquel le filtre sera appliqué.

Les étapes sont les suivantes :

1. Créez un nouveau filtre à partir du noeud **[!UICONTROL Administration > Paramétrage > Filtres prédéfinis]**.
1. Cliquez sur l&#39;icône **[!UICONTROL Choisir le lien]** pour sélectionner le document concerné :

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Sélectionnez le schéma des abonnements (nms:subscription) et cliquez sur **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Cliquez sur l&#39;icône **[!UICONTROL Editer le lien]** pour visualiser les champs du document sélectionné.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Vous pouvez alors consulter le contenu du document sélectionné :

   ![](assets/s_ncs_user_filter_view_schema.png)

   Vous pouvez accéder à ces champs pour définir les conditions de filtre dans le corps de l’éditeur de filtres. Un filtre d’application est défini exactement de la même manière qu’un filtre avancé. See [Creating an advanced filter](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Créez un nouveau filtre sur les abonnements afin de n&#39;afficher que les abonnements pour lequel aucun format des email n&#39;a été défini :

   ![](assets/s_ncs_user_filter_parameters.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour ajouter le filtre aux filtres prédéfinis pour ce type de liste.
1. Vous pouvez désormais utiliser ce filtre dans l&#39;onglet **[!UICONTROL Abonnements]** du profil d&#39;un destinataire, le filtre &quot;Format des emails inconnu&quot; est accessible depuis le bouton **[!UICONTROL Filtres]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   Le nom du filtre courant est affiché au-dessus de la liste. Pour annuler ce filtre, cliquez sur l&#39;icône **[!UICONTROL Supprimer ce filtre]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)


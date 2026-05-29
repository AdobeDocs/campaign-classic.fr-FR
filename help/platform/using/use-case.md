---
product: campaign
title: 'Utilisation :'
description: 'Utilisation :'
feature: Subscriptions, Email, Data Management
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
TQID: https://experienceleague.adobe.com/WuZ0tN8noOI48gW8vl4-923lo2aC8-Jcaz6Ph76nlmE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 293
ht-degree: 74%

---

# Cas d&#39;utilisation{#use-case}



## Créer un filtre sur le format des emails des abonnés {#creating-a-filter-on-the-email-format-of-subscribers}

Dans le ce cas pratique, nous allons créer un filtre afin de trier les abonnement à des newsletters en fonction du format d&#39;email renseigné par les destinataires.

Pour cela, il est nécessaire d&#39;utiliser un filtre prédéfini : ces filtres sont associés à un type de document et sont accessibles à partir du nœud **[!UICONTROL Administration > Paramétrage > Filtres prédéfinis]**. Ces filtres de données peuvent être utilisés pour chaque type d’éditeur (ou de document) dans l’application.

Le mode de création des filtres sur les données est le même que celui des filtres prédéfinis. Toutefois, un champ supplémentaire vous permet de sélectionner le type de document auquel le filtre sera appliqué.

Les étapes sont les suivantes :

1. Créez un nouveau filtre à partir du noeud **[!UICONTROL Administration > Paramétrage > Filtres prédéfinis]**.
1. Cliquez sur l&#39;icône **[!UICONTROL Choisir le lien]** pour sélectionner le document concerné :

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Sélectionnez le schéma des abonnements (nms:subscription) et cliquez sur **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Cliquez sur l&#39;icône **[!UICONTROL Editer le lien]** pour visualiser les champs du document sélectionné.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Vous pouvez alors consulter le contenu du document sélectionné :

   ![](assets/s_ncs_user_filter_view_schema.png)

   Vous pouvez accéder à ces champs pour définir des conditions de filtrage dans le corps de l’éditeur de filtres. Un filtre d’application est défini exactement de la même manière qu’un filtre avancé. Pour plus d’informations sur les filtres, consultez la [documentation de Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.


1. Créez un nouveau filtre sur les abonnements afin de n&#39;afficher que les abonnements pour lequel aucun format des email n&#39;a été défini :

   ![](assets/s_ncs_user_filter_parameters.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour ajouter le filtre aux filtres prédéfinis pour ce type de liste.
1. Vous pouvez désormais utiliser ce filtre dans l’onglet **[!UICONTROL Abonnements]** du profil d’un destinataire. Le filtre « Format d’e-mail inconnu » est accessible en cliquant sur le bouton **[!UICONTROL Filtres]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   Le nom du filtre courant est affiché au-dessus de la liste. Pour annuler ce filtre, cliquez sur l’icône **[!UICONTROL Supprimer ce filtre]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

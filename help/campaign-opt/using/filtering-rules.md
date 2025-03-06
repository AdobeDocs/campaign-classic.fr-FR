---
product: campaign
title: Règles de filtrage
description: Découvrir comment utiliser des règles de filtrage dans Adobe Campaign
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 100%

---

# Règles de filtrage{#filtering-rules}

Les règles de filtrage permettent de définir les messages à exclure en fonction de critères définis dans une requête. Ces règles sont associées à une dimension de ciblage.

Les règles de filtrage peuvent être associées à d&#39;autres types de règles (contrôle, pression, etc.) dans des typologies, ou regroupées dans une typologie dédiée de type **Filtrage**. Pour plus d&#39;informations, voir la section [Créer et utiliser une typologie de filtrage](#creating-and-using-a-filtering-typology).

## Création dʼune règle de filtrage {#creating-a-filtering-rule}

Vous pouvez par exemple filtrer les abonnés à vos newsletters afin de ne jamais adresser de communications aux inscrits mineurs.

Pour définir ce filtrage, les étapes sont les suivantes :

1. Créez une règle de typologie de type **[!UICONTROL Filtrage]**, applicable à tous les canaux de communication.

   ![](assets/campaign_opt_create_filter_01.png)

1. Modifiez la dimension de ciblage par défaut et sélectionnez les abonnements (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Créez le filtre à partir du lien **[!UICONTROL Editer la requête à partir de la dimension de ciblage...]**.

   ![](assets/campaign_opt_create_filter_03.png)

1. Associez cette règle à une typologie de campagne et enregistrez-la.

   ![](assets/campaign_opt_create_filter_04.png)

Lorsque cette règle est utilisée dans une diffusion, les abonnés mineurs sont automatiquement exclus. Un message spécifique en indique l&#39;application :

![](assets/campaign_opt_create_filter_05.png)

## Traitement dʼune règle de filtrage {#conditioning-a-filtering-rule}

Vous pouvez restreindre le champ d’application de la règle de filtrage en fonction de la diffusion ou de la composition de diffusion associée.

Pour cela, dans l&#39;onglet **[!UICONTROL Général]** de la règle de typologie, sélectionnez le type de restriction à appliquer et créez le filtre, comme ci-dessous :

![](assets/campaign_opt_create_filter_06.png)

Dans ce cas, même si la règle est associée à toutes les diffusions, elle ne sera appliquée qu’aux diffusions répondant aux critères du filtre défini.

>[!NOTE]
>
>Les typologies et les règles de filtrage peuvent être utilisées dans un workflow, dans l&#39;activité **[!UICONTROL Composition de diffusion]**. Pour plus d’informations, consultez [cette section](../../workflow/using/delivery-outline.md).

## Création et utilisation dʼune typologie de filtrage {#creating-and-using-a-filtering-typology}

Vous pouvez créer des typologies de **[!UICONTROL Filtrage]** : elles ne contiennent que des règles de filtrage.

![](assets/campaign_opt_create_typo_filtering.png)

Ces typologies spécifiques peuvent être associées à une diffusion lors du choix de la cible : dans l’assistant de diffusion, cliquez sur le lien **[!UICONTROL Pour]**, puis sur l’onglet **[!UICONTROL Exclusions]**.

![](assets/campaign_opt_apply_typo_filtering.png)

Sélectionnez ensuite la typologie de filtrage à appliquer à la diffusion. Pour ce faire, cliquez sur le bouton **[!UICONTROL Ajouter]** et sélectionnez les typologies à appliquer.

Vous pouvez également associer directement des règles de filtrage depuis cet onglet, sans qu&#39;elles soient regroupées dans une typologie. Pour cela, utilisez la section inférieure de la fenêtre.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Seules les typologies et règles de filtrage sont proposées dans la fenêtre de sélection.
>
>Ces paramétrages peuvent être définis au niveau du modèle de diffusion afin de les appliquer automatiquement à toute nouvelle diffusion créée à partir de ce modèle.
>

## Règles d&#39;exclusion de délivrabilité par défaut      {#default-deliverability-exclusion-rules}

Deux règles de filtrage sont disponibles par défaut : **[!UICONTROL Exclusion des adresses]** (**[!UICONTROL addressExclusions]**) et **[!UICONTROL Exclusion des domaines]** (**[!UICONTROL domainExclusions]**). Pendant l&#39;analyse de l&#39;e-mail, ces règles comparent les adresses e-mail des destinataires aux adresses ou noms de domaine interdits contenus dans une liste de suppression globale chiffrée, gérée dans l&#39;instance de délivrabilité. S&#39;il existe une correspondance, le message n&#39;est pas envoyé au destinataire concerné.

Ces règles d’exclusion permettent d’éviter toute mise en liste bloquée liée à une activité malveillante, notamment l’utilisation d’un spam trap (piège à spam). Si un spam trap est par exemple utilisé pour s’abonner par le biais de l’un de vos formulaires web, un email de confirmation lui est automatiquement envoyé. Votre adresse est alors automatiquement mise en liste bloquée.

>[!NOTE]
>
>Les adresses et les noms de domaine contenus dans la liste de suppression globale sont masqués. Seul le nombre des destinataires exclus est indiqué dans les logs d&#39;analyse de diffusion.

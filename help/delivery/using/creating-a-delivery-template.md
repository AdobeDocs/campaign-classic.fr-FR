---
title: Créer un modèle de diffusion
seo-title: Créer un modèle de diffusion
description: Créer un modèle de diffusion
seo-description: null
page-status-flag: never-activated
uuid: 8ceae1ec-9e02-4809-aa8b-1e6bd7790950
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 0e67d9dd-3ee8-4c06-98a4-3a2c644b6c0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3566f42b92cc1b7280bf9b6e9e0b4da7a54f61db
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 79%

---


# Créer un modèle de diffusion{#creating-a-delivery-template}

## Transformer une diffusion existante en modèle {#converting-an-existing-delivery-to-a-template}

Une diffusion peut être transformée en modèle pour de nouvelles actions de diffusion récurrentes. Pour transformer une diffusion en modèle, sélectionnez-la depuis la liste des diffusions accessible à partir du dossier **[!UICONTROL Gestion de campagne]** de l&#39;arborescence.

Cliquez sur le bouton droit de la souris et choisissez **[!UICONTROL Actions > Sauver comme modèle...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Cette action crée un modèle de diffusion à partir de la diffusion sélectionnée. Vous devez indiquer son dossier d&#39;enregistrement (dans le champ **[!UICONTROL Dossier]**) ainsi que le dossier dans lequel seront créées les diffusions issues de ce modèle (dans le champ **[!UICONTROL Dossier d&#39;exécution]**).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Pour plus d’informations sur le mode de configuration, voir [Associer le modèle à une diffusion](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Créer un modèle {#creating-a-new-template}

Pour configurer un modèle de diffusion, procédez comme suit :

1. Ouvrez l&#39;Explorateur de Campaign.
1. Dans le dossier **Ressources**, sélectionnez **Modèles** puis **Modèles de diffusion**.

   ![](assets/delivery_template_1.png)

1. Cliquez sur **Nouveau** dans la barre d&#39;outils pour créer un modèle de diffusion.

   ![](assets/delivery_template_2.png)

1. Modifiez le **libellé** et le **nom interne** du dossier.
1. Enregistrez le modèle et rouvrez-le.
1. Cliquez sur le bouton **Propriétés**, puis modifiez les valeurs selon vos besoins.

   ![](assets/delivery_template_3.png)

1. Dans l&#39;onglet **Général**, validez ou modifiez les emplacements sélectionnés dans les menus déroulants **Dossier d&#39;exécution**, **Dossier** et **Routage**.

   ![](assets/delivery_template_4.png)

1. Remplissez la catégorie **Paramètres de l&#39;email** avec le sujet de l&#39;email et la population ciblée.
1. Ajoutez votre **contenu HTML** afin de personnaliser votre modèle. Vous pouvez afficher une page miroir et un lien de désinscription.
1. Sélectionnez l&#39;onglet **Aperçu**. Dans le menu déroulant **Tester la personnalisation**, sélectionnez **Destinataire** pour obtenir un aperçu du modèle en tant que profil choisi.

   ![](assets/delivery_template_5.png)

1. Cliquez sur **Enregistrer**. Le modèle peut maintenant être utilisé dans une diffusion.

>[!NOTE]
>
>Afin d&#39;éviter toute erreur de paramétrage, il est recommandé de dupliquer un modèle natif et d&#39;en modifier les propriétés plutôt que de créer un nouveau modèle.

## Configuration d’un modèle de diffusion

La vidéo suivante montre comment configurer un modèle pour une diffusion ad hoc.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

## Configuration des propriétés des modèles de diffusion

La vidéo suivante montre comment définir les propriétés du modèle de diffusion et explique en détail chaque propriété.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

## Comment déployer un modèle de diffusion ad hoc

Cette vidéo explique comment déployer un modèle de diffusion de messagerie ad hoc et explique la différence entre une diffusion de messagerie et un processus de diffusion.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

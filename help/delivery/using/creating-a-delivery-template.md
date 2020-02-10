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
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Créer un modèle de diffusion{#creating-a-delivery-template}

## Transformer une diffusion existante en modèle {#converting-an-existing-delivery-to-a-template}

Une diffusion peut être convertie en modèle pour de nouvelles actions de remise répétée. Pour convertir une diffusion en modèle, sélectionnez-la dans la liste de diffusion, accessible via le **[!UICONTROL Campaign management]** noeud de l’arborescence.

Right-click and select **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Cette action crée un modèle de remise à partir de la remise sélectionnée. Vous devez entrer le dossier dans lequel il est enregistré (dans le **[!UICONTROL Folder]** champ) ainsi que le dossier dans lequel les livraisons créées à partir de ce modèle sont créées (dans le **[!UICONTROL Execution folder]** champ).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Pour plus d’informations sur le mode de configuration, voir [Liaison du modèle à une diffusion](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

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

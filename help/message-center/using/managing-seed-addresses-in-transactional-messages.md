---
title: Gestion des adresses de contrôle dans les messages transactionnels
seo-title: Gestion des adresses de contrôle dans les messages transactionnels
description: Gestion des adresses de contrôle dans les messages transactionnels
seo-description: null
page-status-flag: never-activated
uuid: 51c4e79d-53bb-4d46-9c7d-e90066f5317d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 12e7043e-e8b5-48a9-8a2f-99e2e6040c3c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Gestion des adresses de contrôle dans les messages transactionnels{#managing-seed-addresses-in-transactional-messages}

Une adresse de contrôle est utilisée pour afficher l&#39;aperçu de votre message, envoyer un BAT et tester la personnalisation de votre message avant qu&#39;il ne soit envoyé par email ou SMS. Les adresses de contrôle sont liées à la diffusion et ne peuvent être utilisées d&#39;une diffusion à l&#39;autre.

## Créer une adresse de contrôle {#creating-a-seed-address}

1. Dans le modèle de message transactionnel, cliquez sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Attribuez-lui un libellé afin de pouvoir sélectionner l&#39;adresse ultérieurement si nécessaire.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Entrez l&#39;adresse de contrôle, soit l&#39;email ou le numéro de portable selon le canal de communication de la diffusion.

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Renseignez l&#39;identifiant externe : ce champ optionnel vous permet de renseigner la clé métier (identifiant unique, nom + email, etc.), commune à toutes les applications de votre site web, que vous utilisez pour identifier vos profils. Si ce champ est aussi présent dans la base marketing Adobe Campaign, vous pourrez alors réconcilier un évènement avec un profil en base.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Insérez des données de test (voir Données [de](../../message-center/using/personalization-data.md)personnalisation).

   ![](assets/messagecenter_create_custo_001.png)

## Créer plusieurs adresses de contrôle {#creating-several-seed-addresses}

1. Cliquez sur le lien **[!UICONTROL Ajouter d&#39;autres adresses de contrôle]**, puis sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/messagecenter_create_seedaddr_004.png)

1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.
1. Répétez l&#39;opération pour créer le nombre d&#39;adresses voulu.

   ![](assets/messagecenter_create_seedaddr_008.png)

Une fois les adresses créées, vous pouvez afficher leur aperçu et leur personnalisation. Reportez-vous à la section Aperçu [des messages](../../message-center/using/transactional-message-preview.md)transactionnels.

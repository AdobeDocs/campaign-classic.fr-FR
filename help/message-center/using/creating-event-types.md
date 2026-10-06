---
product: campaign
title: Créer des types d'événements
description: Découvrez comment créer des types d'événements qui correspondent aux messages transactionnels que vous souhaitez envoyer dans Adobe Campaign Classic.
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
TQID: 'https://experienceleague.adobe.com/WfR-CUGmR3XeEQgBwd22RZPpSMF0Gja-7GewIIIxWug'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%
---
# Création de types d&#39;événements {#creating-event-types}



Pour que chaque événement puisse être transformé en message personnalisé, vous devez d&#39;abord créer des **types d&#39;événements**.

Lors de la [création d&#39;un modèle de message](../../message-center/using/creating-the-message-template.md), vous sélectionnerez le type d&#39;événement correspondant au message que vous souhaitez envoyer.

>[!IMPORTANT]
>
>Vous devez créer des types d&#39;événements avant de pouvoir les utiliser dans des modèles de message.

Pour créer des types d&#39;événements qui seront traités par Adobe Campaign, procédez comme suit :

1. Connectez-vous à l&#39;**instance de pilotage**.

1. Positionnez-vous dans l’arborescence au niveau du dossier **[!UICONTROL Administration > Plateforme > Énumérations]**.

1. Sélectionnez **[!UICONTROL Type d&#39;événement]** dans la liste.

1. Cliquez sur **[!UICONTROL Ajouter]** pour créer une valeur d&#39;énumération. Il peut s&#39;agir d&#39;une confirmation de commande, d&#39;un changement de mot de passe, d&#39;un changement de livraison de commande, etc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Chaque type d&#39;événement doit correspondre à une valeur de l&#39;énumération **[!UICONTROL Type d&#39;événement]**.

1. Une fois les valeurs de l&#39;énumération créées, vous devez vous déconnecter puis vous reconnecter à votre instance afin que la création soit effective.

>[!NOTE]
>
>Découvrez comment **utiliser les énumérations** dans la [documentation d’Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.




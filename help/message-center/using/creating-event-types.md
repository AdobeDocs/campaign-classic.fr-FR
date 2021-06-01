---
solution: Campaign Classic
product: campaign
title: Création de types d’événement
description: Découvrez comment créer des types d’événement qui correspondent aux messages transactionnels que vous souhaitez envoyer dans Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 15%

---

# Création de types d’événement {#creating-event-types}

Pour vous assurer que chaque événement peut être modifié dans un message personnalisé, vous devez d’abord créer des **types d’événement**.

Lors de la [création d’un modèle de message](../../message-center/using/creating-the-message-template.md), vous sélectionnerez le type d’événement correspondant au message que vous souhaitez envoyer.

>[!IMPORTANT]
>
>Vous devez créer des types d’événement avant de pouvoir les utiliser dans les modèles de message.

Pour créer des types d’événement qui seront traités par Adobe Campaign, procédez comme suit :

1. Connectez-vous à l’**instance de pilotage**.

1. Accédez au dossier **[!UICONTROL Administration > Plateforme > Enumérations]** de l’arborescence.

1. Sélectionnez **[!UICONTROL Type d’événement]** dans la liste.

1. Cliquez sur **[!UICONTROL Ajouter]** pour créer une valeur d’énumération. Il peut s’agir d’une confirmation de commande, d’un changement de mot de passe, d’un changement de livraison de commande, etc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Chaque type d’événement doit correspondre à une valeur de l’énumération **[!UICONTROL Type d’événement]**.

1. Une fois les valeurs de l&#39;énumération créées, vous devez vous déconnecter puis vous reconnecter à votre instance afin que la création soit effective.

>[!NOTE]
>
>Pour en savoir plus sur les énumérations, voir [Gestion des énumérations](../../platform/using/managing-enumerations.md).



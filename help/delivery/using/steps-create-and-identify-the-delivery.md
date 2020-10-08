---
title: Créer et identifier la diffusion
seo-title: Créer et identifier la diffusion
description: Créer et identifier la diffusion
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 100%

---


# Créer et identifier la diffusion {#create-and-identify-the-delivery}

## Créer la diffusion {#creating-the-delivery}

Vous pouvez créer une diffusion par le biais de la vue d&#39;ensemble ou du menu **[!UICONTROL Créer > Diffusion]**.


Pour créer une diffusion, cliquez sur le bouton **[!UICONTROL Créer]** situé au-dessus de la liste des diffusions. Lorsque vous créez une diffusion, vous devez indiquer le canal de diffusion utilisé. Pour cela, sélectionnez le modèle de diffusion correspondant, à partir de la liste déroulante du champ **[!UICONTROL Modèle de diffusion]**.

![](assets/s_ncs_user_wizard_email01_1.png)

Par défaut, un modèle est fourni pour chaque canal installé : courrier, email, fax, téléphone, canaux mobiles (SMS), Facebook, Twitter, etc.

>[!NOTE]
>
>Les canaux proposés dans cette liste dépendent de votre contrat de licence.

Vous pouvez créer de nouveaux modèles de diffusion afin de préconfigurer des paramètres spécifiques en fonction de vos besoins. Pour plus d’informations sur les modèles, consultez [cette section](../../delivery/using/about-templates.md).

## Identification de la diffusion {#identifying-the-delivery}

Vous devez renseigner des paramètres pour identifier la diffusion. Pour cela :

1. Saisissez un nom pour le diffusion dans le champ **[!UICONTROL Libellé]**.

   Un code de diffusion peut également être attribué à la diffusion. Le nom de la diffusion et son code apparaissent dans la liste des diffusions, mais ne sont pas visibles par les destinataires.

1. Ajoutez une description dans le champ **[!UICONTROL Description]**.
1. Sélectionnez la nature de la diffusion dans le champ correspondant. Cette information est notamment utile pour le rtacking des diffusions : vous pouvez filtrer sur ce critère dans la liste des diffusions ou construire des requêtes en utilisant ce critère de sélection.

   ![](assets/s_ncs_user_email_del_nature.png)

1. Cliquez sur **[!UICONTROL Continuer]** pour valider ces informations et afficher la fenêtre de configuration du message.

Le contenu de la diffusion est prêt à être configuré. La définition du contenu de diffusion est spécifique à chaque canal. Voir à ce sujet la section dédiée :

* [Définir le contenu de l&#39;email](../../delivery/using/defining-the-email-content.md)
* [Définir le contenu du SMS](../../delivery/using/sms-channel.md#defining-the-sms-content)
* [Définir le contenu du courrier](../../delivery/using/defining-the-direct-mail-content.md)
* [Notifications push](../../delivery/using/about-mobile-app-channel.md)


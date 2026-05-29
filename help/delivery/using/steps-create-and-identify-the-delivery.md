---
product: campaign
title: Création et identification de la diffusion
description: Création et identification de la diffusion
feature: Channel Configuration
role: User
hide: true
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
TQID: https://experienceleague.adobe.com/-Vr-ox-BTkhYDI3ccBGML5CCkPGz-rSakyXPhgz1Isg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 285
ht-degree: 74%

---

# Création et identification de la diffusion {#create-and-identify-the-delivery}

## Création de la diffusion {#creating-the-delivery}

Vous pouvez créer une diffusion par le biais de la vue d&#39;ensemble ou du menu **[!UICONTROL Créer > Diffusion]**.


Pour créer une diffusion, cliquez sur **[!UICONTROL Créer]** au-dessus de la liste des diffusions. Lors de la création d’une diffusion, vous devez indiquer le canal de diffusion utilisé. Pour cela, sélectionnez le modèle de diffusion correspondant, à partir de la liste déroulante du champ **[!UICONTROL Modèle de diffusion]**.

![](assets/s_ncs_user_wizard_email01_1.png)

Par défaut, un modèle est fourni pour chaque canal installé : publipostage direct, e-mail, fax, téléphone, canal mobile (SMS), Facebook, X (anciennement Twitter), etc.

>[!NOTE]
>
>Les canaux proposés dans cette liste dépendent de votre contrat de licence.

Vous pouvez créer de nouveaux modèles de diffusion afin de préconfigurer des paramètres spécifiques en fonction de vos besoins. Pour plus d’informations sur les modèles, consultez [cette section](about-templates.md).

## Identification de la diffusion {#identifying-the-delivery}

Vous devez renseigner les paramètres pour identifier la diffusion. Pour cela :

1. Saisissez un nom pour le diffusion dans le champ **[!UICONTROL Libellé]**.

   Un code de diffusion peut également être attribué à la diffusion. Le nom de la diffusion et son code apparaissent dans la liste des diffusions, mais ne sont pas visibles par les destinataires.

1. Ajoutez une description dans le champ **[!UICONTROL Description]**.
1. Sélectionnez la nature de la diffusion dans le champ correspondant. Cette information est notamment utile pour le tracking des diffusions : vous pouvez filtrer sur ce critère dans la liste des diffusions ou construire des requêtes en utilisant ce critère de sélection.

   ![](assets/s_ncs_user_email_del_nature.png)

1. Cliquez sur **[!UICONTROL Continuer]** pour valider ces informations et afficher la fenêtre de configuration du message.

Le contenu de la diffusion est prêt à être configuré. La définition du contenu de diffusion est spécifique à chaque canal. Voir à ce sujet la section dédiée :

* [Définition du contenu de l’e-mail](defining-the-email-content.md)
* [Définir le contenu des SMS](sms-create.md#defining-the-sms-content)
* [Définition du contenu du publipostage direct](defining-the-direct-mail-content.md)
* [Notifications push](about-mobile-app-channel.md)

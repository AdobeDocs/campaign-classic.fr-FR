---
product: campaign
title: Prise en main de la personnalisation
description: Découvrez comment personnaliser les messages et utiliser un contenu conditionnel dans Campaign
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 100%

---

# Prise en main de la personnalisation{#about-personalization}

![](../../assets/common.svg)

Les messages diffusés par Adobe Campaign peuvent faire l&#39;objet de plusieurs types de personnalisation. Les axes de personnalisation peuvent concerner le contenu ou la présentation, ils peuvent être combinés en fonction de critères issus notamment des profils des destinataires. Pour les diffusions par email, vous pouvez définir les éléments et conditions de personnalisation d&#39;une diffusion directement en JavaScript à partir de l&#39;onglet **[!UICONTROL Source]** du message. D&#39;une manière générale, Adobe Campaign vous permet de :

* Personnaliser le format du message. Voir [Contenu du message](defining-the-email-content.md#message-content).
* Insérer des champs de personnalisation dynamiques. Voir [Champs de personnalisation](personalization-fields.md).
* Insérer des blocs de personnalisation prédéfinis. Voir [Blocs de personnalisation](personalization-blocks.md).
* Créer du contenu conditionnel. Pour plus d&#39;informations, consultez la section [Contenu conditionnel](conditional-content.md).

>[!CAUTION]
>
>Les variables suivantes sont des variables internes qui peuvent être utilisées dans le cadre de la personnalisation, mais ne doivent pas être modifiées : **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposition**.

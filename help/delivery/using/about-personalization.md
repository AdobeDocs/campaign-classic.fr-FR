---
product: campaign
title: Prise en main de la personnalisation
description: Découvrez comment personnaliser les messages et utiliser un contenu conditionnel dans Campaign
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 81%

---

# Prise en main de la personnalisation{#about-personalization}

Les messages diffusés par Adobe Campaign peuvent faire l&#39;objet de plusieurs types de personnalisation. Les axes de personnalisation peuvent concerner le contenu ou la présentation, ils peuvent être combinés en fonction de critères issus notamment des profils des destinataires. Pour les diffusions par email, vous pouvez définir les éléments et conditions de personnalisation d&#39;une diffusion directement en JavaScript à partir de l&#39;onglet **[!UICONTROL Source]** du message. D&#39;une manière générale, Adobe Campaign vous permet de :

* Personnaliser le format du message. Voir [Contenu du message](defining-the-email-content.md#message-content).
* Insérer des champs de personnalisation dynamiques. Voir [Champs de personnalisation](personalization-fields.md).
* Insérer des blocs de personnalisation prédéfinis. Voir [Blocs de personnalisation](personalization-blocks.md).
* Créer du contenu conditionnel. Pour plus d&#39;informations, consultez la section [Contenu conditionnel](conditional-content.md).

>[!CAUTION]
>
>Les variables suivantes sont des variables internes qui peuvent être utilisées dans le cadre de la personnalisation, mais ne doivent pas être modifiées : **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposition**.


Avec Adobe Campaign, personnalisez vos diffusions pour envoyer des messages correspondant au profil et aux centres d’intérêt de chaque destinataire.

Personalization vous aide à rendre vos messages plus pertinents et attrayants. Vous pouvez utiliser les données des destinataires pour adapter le contenu, ajouter des champs dynamiques ou afficher différentes informations en fonction de conditions. Découvrez comment configurer et utiliser les fonctionnalités de personnalisation dans vos diffusions dans la documentation d’[Adobe Campaign v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}.

Dans le cadre de l’initiative de promotion de Campaign v8, la documentation de Campaign Classic a été réorganisée. Les fonctionnalités communes sont désormais uniquement disponibles dans l’ensemble documentaire de Campaign v8.

>[!BEGINTABS]

>[!TAB Documentation sur la personnalisation du contenu]

Pour en savoir plus sur la personnalisation du contenu, consultez la documentation de [Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}.


[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}


>[!TAB Création de diffusion par e-mail]

Découvrez les étapes clés de la création d’une diffusion e-mail dans la documentation de Campaign v8 :

* [Créer une diffusion email](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=fr){target="_blank"} : découvrez les différentes étapes nécessaires à la création d’une diffusion email.
* [Définir le contenu de l’email](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr){target="_blank"} : définissez les éléments de votre email : expéditeur ou expéditrice, objet, contenu, images.
* [Définir le contenu interactif](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=fr){target="_blank"} : utilisez le format interactif AMP for Email pour envoyer des emails dynamiques.
* [Envoyer des emails sur des mobiles japonais](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=fr){target="_blank"} : utilisez l’un des trois formats japonais spécifiques pour les emails sur mobiles.
* [Joindre des fichiers à un email](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=fr){target="_blank"} : découvrez les différentes manières de joindre un ou plusieurs fichiers à un email.


>[!TAB Paramètres de l’e-mail]

Consultez les pages suivantes pour en savoir plus sur les paramètres email dans la documentation de Campaign v8 :

* [Lien vers la page miroir](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=fr){target="_blank"} : configurez la page miroir pour garantir à votre clientèle une expérience d’affichage optimale.
* [Ajouter une adresse CCI](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=fr){target="_blank"} : configurez Adobe Campaign pour conserver une copie des emails envoyés depuis votre plateforme.
* [Définir des paramètres d’email supplémentaires](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=fr){target="_blank"} : découvrez les options et paramètres disponibles dans les propriétés de diffusion.

Consultez également cette [page](sending-with-enhanced-mta.md) pour en savoir plus sur le MTA amélioré.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->
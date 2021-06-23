---
product: campaign
title: Canal LINE
description: Canal LINE
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 1baaabbd-9fd7-4d9b-b78e-d2a559d7dddb
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 32%

---

# Création de diffusions LINE{#line-channel}

>[!NOTE]
>
>[!DNL LINE] est uniquement disponible pour les installations On-premise ou Managed Services.

[!DNL LINE] est une application pour la messagerie instantanée, les appels vocaux et vidéo gratuits, disponible sur chaque système d’exploitation mobile et sur PC.

[!DNL LINE] peut également être combiné avec le module des messages transactionnels pour envoyer des messages en temps réel sur l’ [!DNL LINE] application installée sur les appareils mobiles des clients. Pour plus d’informations, consultez cette [cette page](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

Les étapes d&#39;utilisation du canal [!DNL LINE] sont les suivantes :

1. [Configuration du canal LINE](#setting-up-line-channel)
1. [Création d&#39;une diffusion](#creating-the-delivery)
1. [Configuration du type de contenu](#defining-the-content)
1. [Suivi de la diffusion (tracking, mise en quarantaine, rapports, etc.)](#accessing-reports)

## Configuration du canal LINE {#setting-up-line-channel}

Avant de créer un compte [!DNL LINE] et un compte externe, vous devez installer le package LINE sur votre instance. Pour plus d&#39;informations à ce sujet, consultez la section [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package) du Guide d&#39;installation.

Vous devez d’abord créer un compte [!DNL LINE] afin de pouvoir ensuite le lier à Adobe Campaign. Vous pouvez ensuite envoyer des [!DNL LINE] messages aux utilisateurs qui ont ajouté votre compte [!DNL LINE] dans leur application mobile. Les comptes externes et le compte [!DNL LINE] ne peuvent être gérés que par l&#39;administrateur fonctionnel de la plateforme.

Pour créer et configurer un compte [!DNL LINE], consultez la [documentation destinée aux développeurs LINE](https://developers.line.me/).

### Création et configuration du service LINE {#configure-line-service}

Pour créer votre service [!DNL LINE] :

1. Sur la page d’accueil de Adobe Campaign Classic, sélectionnez l’onglet **[!UICONTROL Profils et cibles]** .

1. Dans le menu de gauche, sélectionnez **[!UICONTROL Services et abonnements]** et cliquez sur **[!UICONTROL Créer]**.

   ![](assets/line_service_1.png)

1. Ajoutez un **[!UICONTROL libellé]** et un **[!UICONTROL nom interne]** à votre nouveau service.

1. Sélectionnez **[!UICONTROL LINE]** dans la liste déroulante **[!UICONTROL Type]**.

   ![](assets/line_service_2.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Pour plus d’informations sur les abonnements et les services, voir [Gestion des abonnements](managing-subscriptions.md).

### Configuration du compte externe LINE {#configure-line-external}

Après avoir créé votre service [!DNL LINE], vous devez configurer le compte externe [!DNL LINE] sur Adobe Campaign :

1. Dans l&#39;arborescence **[!UICONTROL Administration]** > **[!UICONTROL Plate-forme]**, cliquez sur l&#39;onglet **[!UICONTROL Comptes externes]**.

1. Sélectionnez le compte externe **[!UICONTROL Routage LINE V2]** intégré.

   ![](assets/line_config.png)

1. Cliquez sur l’onglet **[!UICONTROL LINE]** de votre compte externe pour commencer à configurer votre compte externe. Renseignez les champs suivants :

   ![](assets/line_config_2.png)

   * **[!UICONTROL Alias du canal]**[!DNL LINE] : est fourni via votre compte dans l&#39;onglet **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]**.
   * **[!UICONTROL Identifiant du canal]**[!DNL LINE] : est fourni via votre compte dans l&#39;onglet **[!UICONTROL Channels]**> **[!UICONTROL Basic Information panel]**.
   * **[!UICONTROL Clé secrète du canal]**[!DNL LINE] : est fourni via votre compte dans l&#39;onglet **[!UICONTROL Channels]**> **[!UICONTROL Basic Information panel]**.
   * **[!UICONTROL Jeton d&#39;accès]**[!DNL LINE] : est fourni via votre compte sur le portail destiné aux développeurs ou en cliquant sur le bouton **[!UICONTROL Récupérer le jeton d&#39;accès]**.
   * **[!UICONTROL Date d&#39;expiration du jeton d&#39;accès]** : permet de spécifier la date d&#39;expiration d&#39;Access token.
   * **[!UICONTROL Service d&#39;abonnement LINE]** : permet de spécifier le service auquel les utilisateurs seront abonnés.

1. Une fois la configuration terminée, cliquez sur **[!UICONTROL Enregistrer]**.

1. Dans l&#39;**[!UICONTROL Explorateur]**, sélectionnez **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Workflows techniques]** > **[!UICONTROL Workflows LINE]** pour vérifier si la **[!UICONTROL mise à jour du jeton d’accès LINE V2 (updateLineAccessToken)&lt;a> Les workflows 11/> et**[!UICONTROL  Supprimer les utilisateurs LINE bloqués (deleteBlockedLineUsers)]**ont commencé.]**

[!DNL LINE] est maintenant configuré dans Adobe Campaign. Vous pouvez commencer à créer et envoyer des diffusions LINE aux abonnés.

## Créer une diffusion LINE {#creating-the-delivery}

>[!NOTE]
>
>Lors de l&#39;envoi initial d&#39;une diffusion [!DNL LINE] à un nouveau destinataire, vous devez y ajouter le message officiel LINE concernant les conditions d&#39;utilisation et de consentement. Le message officiel est disponible à l&#39;adresse [suivante ](https://terms.line.me/OA_privacy/).

Pour créer une diffusion [!DNL LINE] vous devez suivre les étapes suivantes :

1. Depuis l&#39;onglet **[!UICONTROL Campagnes]**, sélectionnez **[!UICONTROL Diffusions]** puis cliquez sur le bouton **[!UICONTROL Créer]**.

   ![](assets/line_message_07.png)

1. Sélectionnez le modèle de diffusion **[!UICONTROL Diffusion LINE V2]** .

   ![](assets/line_message_01.png)

1. Identifiez votre diffusion avec un **[!UICONTROL Libellé]**, **[!UICONTROL Code de diffusion]** et une **[!UICONTROL Description]**. Pour plus d&#39;informations à ce sujet, consultez [cette section](steps-create-and-identify-the-delivery.md#identifying-the-delivery).

1. Cliquez sur **[!UICONTROL Continuer]** pour valider la création de votre diffusion.

1. Dans l&#39;éditeur de diffusion, sélectionnez **[!UICONTROL Pour]** afin de cibler les destinataires de votre diffusion [!DNL LINE]. Le ciblage est réalisé sur les **[!UICONTROL abonnements des visiteurs (nms:visitorSub)]**.

   Pour plus d&#39;informations, voir la section [Identification des populations ciblées](steps-defining-the-target-population.md).

   ![](assets/line_message_08.png)

1. Cliquez sur **[!UICONTROL Ajouter]** pour sélectionner votre **[!UICONTROL population cible de diffusion]**.

   ![](assets/line_message_09.png)

1. Choisissez si vous souhaitez cibler directement les abonnés [!DNL LINE] ou si vous souhaitez cibler les utilisateurs en fonction de leur abonnement [!DNL LINE] et cliquez sur **[!UICONTROL Suivant]**. Dans cet exemple, nous avons sélectionné **[!UICONTROL Par abonnement LINE V2]**.

1. Sélectionnez **[!UICONTROL Line-V2]** dans la liste déroulante **[!UICONTROL Dossier]**, puis votre service [!DNL LINE]. Cliquez sur **[!UICONTROL Terminer]** puis sur **[!UICONTROL Ok]** pour commencer à personnaliser votre diffusion.

   ![](assets/line_message_10.png)

1. Dans l&#39;éditeur de diffusion, cliquez sur **[!UICONTROL Ajouter]** pour ajouter un ou plusieurs messages et sélectionnez le **[!UICONTROL Type de contenu]**.

   Pour plus d&#39;informations sur les différents **[!UICONTROL Type de contenu]** disponibles, consultez la section [Définition du type de contenu](#defining-the-content).

   ![](assets/line_message_11.png)

1. Lorsque votre diffusion est correctement créée et paramétrée, vous pouvez l&#39;envoyer à la cible définie précédemment.

   Pour plus d&#39;informations sur l&#39;envoi d&#39;une diffusion, consultez la section [Envoyer les messages](sending-messages.md).

1. Une fois votre message envoyé, accédez à votre rapport pour mesurer l&#39;efficacité de votre diffusion.

   Pour plus d’informations sur les rapports [!DNL LINE], voir [Accéder aux rapports](#accessing-reports).

## Définition du type de contenu {#defining-the-content}

Pour définir le contenu d&#39;une diffusion [!DNL LINE], vous devez d&#39;abord ajouter un type de message à votre diffusion. Chaque diffusion [!DNL LINE] peut contenir jusqu’à 5 messages.

Vous pouvez choisir entre trois types de message :

* [Message texte](#configuring-a-text-message-delivery)
* [Image et lien](#configuring-an-image-and-link-delivery)
* [Message vidéo](#configuring-a-video-message-delivery)

### Paramétrer une diffusion de type Message texte {#configuring-a-text-message-delivery}

>[!NOTE]
>
>La syntaxe `<%@ include option='NmsServer_URL' %>/webApp/APP3?id=<%=escapeUrl(cryptString(visitor.id))%>` permet d&#39;inclure dans un message LINE un lien vers une application web.

Une diffusion de type **[!UICONTROL Message texte]** est un message envoyé aux destinataires sous forme de texte.[!DNL LINE]

![](assets/line_message_02.png)

La configuration de ce type de message est similaire à la configuration de **[!UICONTROL Text]** dans un email. Pour plus d’informations, consultez cette [page](defining-the-email-content.md#message-content).

### Paramétrer une diffusion de type Image et lien {#configuring-an-image-and-link-delivery}

Une diffusion de type **[!UICONTROL Image et lien]** est un message envoyé aux destinataires sous la forme d&#39;une image pouvant contenir une ou plusieurs URL.[!DNL LINE]

Vous pouvez utiliser :

* une **[!UICONTROL image personnalisée]**,

   >[!NOTE]
   >
   >Vous pouvez utiliser la variable **%SIZE%** pour optimiser l&#39;affichage de l&#39;image en fonction de la taille d&#39;écran de l&#39;appareil mobile du destinataire.

   ![](assets/line_message_04.png)

* une **[!UICONTROL URL d’image]** par taille d’écran de l’appareil,

   ![](assets/line_message_03.png)

   L’option **[!UICONTROL Définir les images par taille d’écran d’appareil]** vous permet d’utiliser différentes résolutions d’image pour optimiser la visibilité de la diffusion sur les appareils mobiles. Seules les images de même hauteur et largeur sont prises en charge.

   Les images peuvent être définies en fonction de la taille de l&#39;écran :

   * 1040 px
   * 700 px
   * 460 px
   * 300 px
   * 240 px

   >[!CAUTION]
   >
   >La taille 1 040 x 1 040 px est obligatoire pour toutes les images LINE avec un lien.

   Vous devez ensuite ajouter un texte alternatif qui apparaîtra en pop-up sur l&#39;appareil mobile du destinataire.

* et les **[!UICONTROL Liens]**.

   La section **[!UICONTROL Liens]** vous permet de choisir entre différentes dispositions qui divisent votre image en plusieurs zones interactives. Vous pouvez ensuite affecter à chacun d’eux une **[!UICONTROL URL de lien]** dédiée.

   ![](assets/line_message_05.png)

### Configuration d&#39;une diffusion de message vidéo {#configuring-a-video-message-delivery}

Une diffusion **[!UICONTROL Message vidéo]** [!DNL LINE] est un message envoyé aux destinataires sous la forme d’une vidéo pouvant contenir une URL.

Le champ **[!UICONTROL URL de l’image d’aperçu]** permet d’ajouter l’URL d’une image d’aperçu avec une limite de caractères de 1 000. Les formats JPEG et PNG sont pris en charge avec une taille de fichier limitée à 1 Mo.

Le champ **[!UICONTROL URL de l’image vidéo]** vous permet d’ajouter l’URL de votre fichier vidéo avec une limite de caractères de 1 000. Seul le format mp4 est pris en charge avec une taille de fichier limitée à 200 Mo.

Notez que les vidéos larges ou de grande taille peuvent être recadrées lors de la lecture sur certains périphériques.

![](assets/line_message_06.png)

## Accéder aux rapports {#accessing-reports}

Après l&#39;envoi de votre diffusion, vous pouvez afficher vos [!DNL LINE] rapports à partir du menu **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Diffusions]** à partir de l&#39;**[!UICONTROL Explorateur]**.

>[!NOTE]
>
>Les rapports de suivi indiquent le taux de clics publicitaires. [!DNL LINE] ne prend pas en compte le taux d’ouverture.

![](assets/line_reports_01.png)

Pour les [!DNL LINE] rapports de service, accédez au menu **[!UICONTROL Profils et cibles]** > **[!UICONTROL Services et abonnements]** > **[!UICONTROL LINE-V2]** à partir de l’onglet **[!UICONTROL Explorateur]**. Cliquez ensuite sur l’icône **[!UICONTROL Rapports]** dans le service [!DNL LINE].

![](assets/line_reports.png)

## Exemple : créer et envoyer un message LINE personnalisé {#example--create-and-send-a-personalized-line-message}

Dans cet exemple, nous allons créer et paramétrer un message texte et une image contenant des données qui seront personnalisées en fonction du destinataire.

1. Créez votre [!DNL LINE] diffusion en cliquant sur le bouton **[!UICONTROL Créer]** dans l’onglet **[!UICONTROL Campagne]**.

   ![](assets/line_usecase.png)

1. Sélectionnez le modèle de diffusion **[!UICONTROL Diffusion LINE V2]** et nommez votre diffusion.

   ![](assets/line_usecase_01.png)

1. Dans la fenêtre de paramétrage de votre diffusion, sélectionnez votre population cible.

   Pour plus d&#39;informations, voir la section [Identification des populations ciblées](steps-defining-the-target-population.md).

   ![](assets/line_usecase_02.png)

1. Cliquez sur **[!UICONTROL Ajouter]** pour créer votre message et sélectionnez le **[!UICONTROL Type de contenu]**.

   Ici, nous allons d’abord créer un **[!UICONTROL message texte]**.

   ![](assets/line_usecase_03.png)

1. Placez le curseur à l’endroit où vous souhaitez insérer le texte personnalisé, cliquez sur l’icône déroulante, puis sélectionnez **[!UICONTROL Visiteur]** **[!UICONTROL Prénom]**.

   ![](assets/line_usecase_05.png)

1. Suivez la même procédure pour ajouter une image, en sélectionnant **[!UICONTROL Image et liens]** dans la liste déroulante **[!UICONTROL Type de message]**.

   Ajoutez votre **[!UICONTROL URL de l’image]**.

   ![](assets/line_usecase_07.png)

1. Dans la section **[!UICONTROL Liens]**, sélectionnez la disposition qui divisera l&#39;image en plusieurs zones interactives.

1. Affectez une URL à chaque zone de votre image.

   ![](assets/line_usecase_08.png)

1. Sauvegardez votre diffusion puis cliquez sur **[!UICONTROL Envoyer]** afin de l&#39;analyser puis de l&#39;envoyer à la cible.

   La diffusion est envoyée à la cible :

   ![](assets/line_usecase_06.png)


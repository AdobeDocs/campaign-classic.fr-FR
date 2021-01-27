---
solution: Campaign Classic
product: campaign
title: Canal LINE
description: Canal LINE
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 100%

---


# Canal LINE{#line-channel}

LINE est une application de messagerie instantanée et d&#39;appels vocaux et vidéos gratuits, disponible sur tous les smartphones (iPhone, Android, Windows Phone, Blackberry, Nokia) et sur PC. Adobe Campaign vous permet d&#39;envoyer des messages LINE.

LINE est uniquement disponible pour les installations On-premise ou Managed Services.

LINE peut aussi être combinée au module de message transactionnel pour envoyer des messages en temps réel sur l&#39;application LINE installée sur les appareils mobiles du consommateur. Pour en savoir plus, consultez cette [page](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

Les sections ci-dessous contiennent des informations spécifiques au canal LINE. Pour plus d&#39;informations sur la création d&#39;une diffusion, voir [cette section](../../delivery/using/steps-about-delivery-creation-steps.md).

Pour utiliser le canal LINE, les étapes de réalisation sont les suivantes :

1. Création d&#39;une diffusion
1. Paramétrage de contenu du message
1. Choisir la population cible
1. Diffusion des messages
1. Suivi de la diffusion (tracking, mise en quarantaine, rapports, etc.).

## Configuration du canal LINE {#setting-up-line-channel}

### Création d&#39;un compte LINE et d&#39;un compte externe {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>Avant de créer un compte LINE et un compte externe, vous devez installer le package LINE sur votre instance. Pour en savoir plus, consultez la section [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package) dans le guide d&#39;installation.

Dans un premier temps, vous devez créer un compte LINE pour ensuite le lier à Adobe Campaign. Ainsi, vous pourrez envoyer des messages LINE aux utilisateurs qui ont ajouté votre compte LINE dans leur application mobile. Les comptes externes et le compte LINE ne peuvent être gérés que par l&#39;administrateur fonctionnel de la plateforme.

Pour créer et paramétrer un compte LINE, voir [https://developers.line.me/](https://developers.line.me/).

Pour créer et paramétrer un service LINE, voir la section [Gestion des inscriptions](../../delivery/using/managing-subscriptions.md).

![](assets/line_service.png)

Enfin, pour créer un compte externe sur Adobe Campaign :

1. Dans l&#39;arborescence **Administration** > **Plate-forme**, cliquez sur l&#39;onglet **Comptes externes**.
1. Cliquez ensuite sur l&#39;icône **Nouveau**.

   ![](assets/line_config.png)

1. Complètez les champs **Libellé** et **Nom interne**.
1. Dans le champ **[!UICONTROL Type]**, sélectionnez Routage. Dans le champ **Canal**, sélectionnez LINE.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour créer votre compte externe LINE.
1. Un champ de personnalisation **LINE** apparaît sous l&#39;icône **Général**. Renseignez les champs suivants :

   ![](assets/line_config_2.png)

   * **Alias du canal** : est fourni via votre compte LINE dans l&#39;onglet **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]**.
   * **Identifiant du canal** : est fourni via votre compte LINE dans l&#39;onglet **Channels**> **Basic Information panel**.
   * **Clé secrète du canal** : est fourni via votre compte LINE dans l&#39;onglet **Channels**> **Basic Information panel**.
   * **Jeton d&#39;accès** : est fourni via votre compte LINE sur le portail destiné aux développeurs ou en cliquant sur le bouton **[!UICONTROL Récupérer le jeton d&#39;accès]**.
   * **Date d&#39;expiration du jeton d&#39;accès** : permet de spécifier la date d&#39;expiration d&#39;Access token.
   * **Service d&#39;abonnement LINE** : permet de spécifier le service auquel les utilisateurs seront abonnés.

>[!NOTE]
>
>Vous devez vérifier que les workflows **[!UICONTROL Mise à jour du jeton d&#39;accès LINE (updateLineAccessToken)]** et **[!UICONTROL Nettoyage des utilisateurs LINE bloqués (deleteBlockedLineUsers)]** sont démarrés. Depuis l&#39;explorateur, cliquez sur **[!UICONTROL Administration > Exploitation > Workflows techniques > Workflows LINE]** pour vérifier l&#39;état des workflows.

## Créer la diffusion {#creating-the-delivery}

Pour créer une diffusion **LINE** vous devez suivre les étapes suivantes :

>[!NOTE]
>
>Les concepts généraux relatifs à la création d&#39;une diffusion sont présentés dans [cette section](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Depuis l&#39;onglet **[!UICONTROL Campagnes]**, sélectionnez **[!UICONTROL Diffusions]** puis cliquez sur le bouton **[!UICONTROL Créer]**.
1. Dans la fenêtre qui s&#39;affiche, sélectionnez le modèle de diffusion **[!UICONTROL Diffusion LINE V2]**.

   ![](assets/line_message_01.png)

1. Identifiez la diffusion avec un libellé, un code et une description. Voir à ce propos [cette section](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Cliquez sur **[!UICONTROL Continuer]** pour valider la création de votre diffusion.

## Définir le contenu {#defining-the-content}

Pour définir le contenu d&#39;une diffusion LINE, vous devez d&#39;abord ajouter un type de message à votre diffusion. Chaque diffusion LINE peut contenir jusqu&#39;à 5 messages.

Vous pouvez effectuer un choix entre deux types de messages :

* Message texte
* Image et lien

### Paramétrer une diffusion de type Message texte {#configuring-a-text-message-delivery}

Une diffusion LINE de type **Message texte** est un message envoyé aux destinataires sous forme de texte.

![](assets/line_message_02.png)

Le paramétrage de ce type de message est similaire au paramétrage du format **texte** dans un email. Pour plus d&#39;informations, voir [cette page](../../delivery/using/defining-the-email-content.md#message-content).

### Paramétrer une diffusion de type Image et lien {#configuring-an-image-and-link-delivery}

Une diffusion LINE de type **Image et lien** est un message envoyé aux destinataires sous la forme d&#39;une image pouvant contenir une ou plusieurs URL.

Vous pouvez utiliser :

* une **image personnalisée**,

   >[!NOTE]
   >
   >Vous pouvez utiliser la variable **%SIZE%** : cette variable permet d&#39;optimiser l&#39;affichage de l&#39;image en fonction de la taille de l&#39;écran de l&#39;appareil mobile du destinataire de la diffusion.

   ![](assets/line_message_04.png)

* une **image URL**,

   ![](assets/line_message_03.png)

   Les images URL vous permettent d&#39;utiliser des images de résolutions différentes afin d&#39;optimiser la visibilité de la diffusion sur différents appareils mobiles. Seules les images dont la hauteur et la largeur sont identiques sont prises en charge.

   Les images peuvent être définies en fonction de la taille de l&#39;écran :

   * 1040 px
   * 700 px
   * 460 px
   * 300 px
   * 240 px

   >[!NOTE]
   >
   >La taille 1 040 x 1 040 px est obligatoire pour toutes les images LINE avec un lien.

   Vous devez ensuite ajouter un texte alternatif qui apparaîtra en pop-up sur l&#39;appareil mobile du destinataire.

* et les **[!UICONTROL Liens]**.

   ![](assets/line_message_05.png)

   La section **[!UICONTROL Liens]** vous permet d&#39;effectuer un choix parmi différentes dispositions qui divisent votre image en plusieurs zones interactives. Vous pouvez ensuite affecter à chaque zone un lien dédié.

>[!NOTE]
>
>La syntaxe &lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(visitor.id))%> permet d&#39;inclure un lien vers une web app dans un message LINE.

### Recommandations     {#recommendations}

* Lorsque vous envoyez une diffusion LINE pour la première fois à un nouveau destinataire, vous devez y ajouter le message officiel de LINE à propos des règles d&#39;utilisation et de consentement. Ce message officiel est disponible à l&#39;adresse suivante : [https://terms.line.me/OA_privacy/sp?lang=fr](https://terms.line.me/OA_privacy/sp?lang=fr).

## Choisir la population cible {#selecting-the-target-population}

La sélection des destinataires d&#39;une diffusion LINE est similaire à la définition des destinataires pour une diffusion par email. Pour plus d&#39;informations, voir la section [Identification des populations ciblées](../../delivery/using/steps-defining-the-target-population.md).

Le ciblage est réalisé sur les **visiteurs**.

## Envoyer les messages {#sending-messages}

Lorsque votre diffusion est correctement créée et paramétrée, vous pouvez l&#39;envoyer à la cible définie précédemment.

L&#39;envoi de diffusions LINE est similaire à l&#39;envoi d&#39;une diffusion par email. Pour plus d&#39;informations sur l&#39;envoi d&#39;une diffusion, voir la section [Envoyer les messages](../../delivery/using/sending-messages.md).

## Accéder aux rapports {#accessing-reports}

Vous pouvez visualiser les rapports du service LINE en cliquant sur **[!UICONTROL Profils et Cibles > Services et abonnements > LINE]** dans l&#39;explorateur. Cliquez ensuite sur l&#39;icône **[!UICONTROL Rapports]** dans le service LINE.

![](assets/line_reports.png)

Pour visualiser les rapports des diffusions LINE, cliquez sur **[!UICONTROL Gestion de campagne > Diffusions]** puis sélectionnez la diffusion désirée. Les rapports de tracking indiquent le taux de clic. LINE ne prend pas en compte le taux d&#39;ouverture.

![](assets/line_reports_01.png)

## Exemple : créer et envoyer un message LINE personnalisé {#example--create-and-send-a-personalized-line-message}

Dans cet exemple, nous allons créer et paramétrer un message texte et une image contenant des données qui seront personnalisées en fonction du destinataire.

1. Créez votre diffusion LINE en cliquant sur le bouton **[!UICONTROL Créer]** depuis l&#39;onglet **[!UICONTROL Campagnes]**.

   ![](assets/line_usecase.png)

1. Sélectionnez le modèle de diffusion **[!UICONTROL Diffusion LINE V2]** et nommez votre diffusion.

   ![](assets/line_usecase_01.png)

1. Dans la fenêtre de paramétrage de votre diffusion, sélectionnez votre population cible.

   ![](assets/line_usecase_02.png)

1. Cliquez sur **[!UICONTROL Ajouter]** pour créer votre message et sélectionnez le **[!UICONTROL Type de message]**.

   Nous voulons d&#39;abord créer un message texte.

   ![](assets/line_usecase_03.png)

1. Positionnez votre curseur à l&#39;endroit où vous souhaitez insérer le texte personnalisé, cliquez sur l&#39;icône déroulante, puis sélectionnez **[!UICONTROL Visiteur > Prénom]**.

   ![](assets/line_usecase_05.png)

1. Suivez la même procédure pour ajouter une image, en sélectionnant **[!UICONTROL Image et liens]** dans la liste déroulante **[!UICONTROL Type de message]**.

   Ajoutez l&#39;image URL.

   ![](assets/line_usecase_07.png)

1. Dans la section **[!UICONTROL Liens]**, sélectionnez la disposition qui divisera l&#39;image en plusieurs zones interactives.
1. Affectez une URL à chaque zone de votre image.

   ![](assets/line_usecase_08.png)

1. Sauvegardez votre diffusion puis cliquez sur **[!UICONTROL Envoyer]** afin de l&#39;analyser puis de l&#39;envoyer à la cible.

   La diffusion est envoyée à la cible :

   ![](assets/line_usecase_06.png)

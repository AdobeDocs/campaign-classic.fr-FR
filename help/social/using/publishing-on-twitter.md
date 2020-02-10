---
title: Publier sur Twitter
seo-title: Publier sur Twitter
description: Publier sur Twitter
seo-description: null
page-status-flag: never-activated
uuid: 405bce50-a63c-4bd3-8f03-c71809bb1cfd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 2dc278ce-477c-493d-8abb-8bbdf2e988a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20174427735b90129cd4cbd9ee1ba5fd705fa302

---


# Publier sur Twitter{#publishing-on-twitter}

## Publier sur vos comptes Twitter {#publishing-on-your-twitter-accounts}

Une fois le paramétrage effectué, Social Marketing permet d&#39;envoyer des tweets sur vos comptes Twitter.

### Limitations {#limitations}

Les limitations suivantes sont des contraintes inhérentes à Twitter.

* La longueur du message ne peut pas dépasser 140 caractères.
* Le format HTML n&#39;est pas supporté.

### Créer la diffusion {#creating-the-delivery}

Create a new delivery based on the **[!UICONTROL Tweet (twitter)]** delivery template.

![](assets/social_twitter_delivery_001.png)

### Choisir la cible principale {#selecting-the-main-target}

Vous devez sélectionner le ou les comptes sur lesquels vous souhaitez envoyer votre tweet.

1. Cliquez sur le **[!UICONTROL To]** lien.

   ![](assets/social_twitter_delivery_002.png)

1. Cliquez sur le **[!UICONTROL Add]** bouton.

   ![](assets/social_twitter_delivery_006.png)

1. Sélectionner **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. In the **[!UICONTROL Folder]** field, select the service folder which contains the Twitter account. Sélectionnez ensuite le compte Twitter auquel vous souhaitez envoyer votre tweet.

   ![](assets/social_twitter_delivery_011.png)

### Choisir la cible du BAT {#selecting-the-target-of-the-proof}

L’ **[!UICONTROL Target of the proofs]** onglet vous permet de définir le compte Twitter à utiliser pour les remises de test avant la remise finale.  Nous vous recommandons donc de créer un compte Twitter privé dédié à l&#39;envoi de preuves. Pour plus d’informations sur la création d’un compte Twitter privé, voir [Création d’un compte de test sur Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Les étapes de sélection de la cible d’épreuve sont identiques à celles de sélection de la cible principale. Reportez-vous à [Création d’un compte test sur Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Si vous utilisez le même compte de test Twitter pour toutes vos livraisons, vous pouvez enregistrer la cible de preuve dans le modèle de **[!UICONTROL Tweet]** livraison, accessible via le **[!UICONTROL Resources > Templates > Delivery templates]** noeud. La cible d’épreuve sera alors saisie par défaut pour chaque nouvelle remise.

### Définir le contenu du message {#defining-the-message-content}

Type the content of your tweet in the **[!UICONTROL Content]** tab.

![](assets/social_twitter_delivery_005.png)

### Visualiser l&#39;aperçu {#viewing-the-preview}

The **[!UICONTROL Preview]** tab lets you view a rendering of the tweet.

1.  Cliquez sur l’ **[!UICONTROL Preview]** onglet.
1. Cliquez sur le menu **[!UICONTROL Test personalization]** déroulant et sélectionnez **[!UICONTROL Service]**.
1. In the **[!UICONTROL Folder]** field, select the service folder which contains your Twitter account.
1. Sélectionnez le compte Twitter sur lequel vous souhaitez tester l&#39;aperçu.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>L’aperçu peut différer légèrement du tweet final. Nous vous recommandons vivement d’envoyer une preuve avant la remise finale afin d’afficher le rendu exact du tweet. Reportez-vous à [Envoi de la preuve](#sending-the-proof).

### Configurer le tracking {#configuring-tracking}

Tracking can be viewed in the delivery reports and in the **[!UICONTROL Edit > Tracking]** tab of the delivery and the service.

La configuration du tracking s’effectue de la même manière que pour une diffusion email. Voir à ce sujet [cette section](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>In the **[!UICONTROL Tweet]** delivery template, tracking is enabled by default.

>[!CAUTION]
>
>Il n&#39;est pas possible de distinguer l&#39;activité des robots qui analysent les tweets des utilisateurs qui cliquent réellement.

### Envoyer le BAT {#sending-the-proof}

Nous vous recommandons vivement d’envoyer une preuve de votre publication avant la livraison finale afin d’obtenir un rendu exact de la publication sur une page de test Twitter privée. Pour plus d’informations sur la création d’un compte Twitter privé, voir [Création d’un compte de test sur Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Les étapes de sélection de la cible de l&#39;épreuve sont détaillées dans [Sélection de la cible de l&#39;épreuve](#selecting-the-target-of-the-proof).

L’envoi du BAT s’effectue de la même manière que pour une diffusion email. Reportez-vous à [cette section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Envoyer le message {#sending-the-message}

1. Once the content is approved, click the **[!UICONTROL Send]** button.
1. Sélectionnez **[!UICONTROL Deliver as soon as possible]** puis cliquez sur le **[!UICONTROL Analyze]** bouton.

   >[!NOTE]
   >
   >The **[!UICONTROL Postpone the delivery]** option lets you postpone delivery to a later date.

   ![](assets/social_twitter_delivery_012.png)

1. Une fois l&#39;analyse terminée, vérifiez le résultat de l&#39;analyse.
1. Cliquez sur **[!UICONTROL Confirm delivery]**, puis sur **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Envoyer des messages directs à vos abonnés {#sending-direct-messages-to-subscribers}

### Principe de fonctionnement {#operating-principle}

Le **[!UICONTROL Synchronize Twitter accounts]** processus (voir [Synchronisation des comptes](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)Twitter) récupère la liste des abonnés Twitter afin que vous puissiez leur envoyer des messages directs. Les abonnés récupérés sont stockés dans un tableau spécifique : le tableau des visiteurs. Pour afficher la liste des abonnés Twitter, accédez au **[!UICONTROL Profiles and Targets > Visitors]** noeud.

![](assets/social_twitter_visitors_001.png)

>[!CAUTION]
>
>In order for the workflow to recover the list of Twitter followers, the **[!UICONTROL Synchronize Twitter accounts]** box must be checked in the Edit screen of the service linked to the account. Pour plus d’informations à ce sujet, voir : La [délégation de l’accès en écriture à Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Pour chaque abonné, Adobe Campaign récupère les informations suivantes :

* **[!UICONTROL Origin]**: nom du réseau social (**Twitter** dans ce cas)
* **[!UICONTROL External ID]**: identifiant utilisateur
* **[!UICONTROL User name]**: nom de compte de l’utilisateur
* **[!UICONTROL Full name]**: nom de l’utilisateur
* **[!UICONTROL Language]**: langage utilisateur
* **[!UICONTROL Number of friends]**: nombre d’abonnés
* **[!UICONTROL Time zone]**: fuseau horaire utilisateur
* **[!UICONTROL Verified]**: ce champ indique si l’utilisateur dispose d’un compte Twitter vérifié.

### Limitations {#limitations-1}

Les limitations suivantes sont des contraintes inhérentes à Twitter.

* La longueur du message ne peut pas dépasser 140 caractères.
* Le format HTML n&#39;est pas supporté.
* Vous ne pouvez pas envoyer plus de 250 messages directs par jour. Afin de ne pas dépasser cette limite, il est possible d’effectuer un envoi en plusieurs vagues. L’envoi en plusieurs vagues s’effectue de la même manière que pour une diffusion email. Voir à ce sujet [cette section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Créer la diffusion {#creating-the-delivery-}

Create a new delivery based on the **[!UICONTROL Tweet (Direct Message)]** delivery template.

![](assets/social_twitter_delivery_010.png)

### Choisir la cible principale {#selecting-the-main-target-1}

Vous devez sélectionner les abonnés à qui vous souhaitez envoyer votre message direct.

1. Cliquez sur le **[!UICONTROL To]** lien.

   ![](assets/social_twitter_delivery_016.png)

1. Cliquez sur le **[!UICONTROL Add]** bouton.

   ![](assets/social_twitter_delivery_006.png)

1. Choisissez un type de ciblage.

   ![](assets/social_twitter_delivery_017.png)

   * Select **[!UICONTROL Twitter subscribers]** to send a direct message to all account followers.

      >[!CAUTION]
      >
      >Vous ne pouvez pas envoyer plus de 250 messages par jour. Si votre compte Twitter comporte plus de 250 abonnés, il est vivement recommandé d’effectuer un envoi en plusieurs vagues. L’envoi en plusieurs vagues s’effectue de la même manière que pour une diffusion email. Reportez-vous à [cette section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Sélectionnez **[!UICONTROL Filter conditions]** pour définir une requête et afficher son résultat. Cette option est la même que pour les diffusions par courrier électronique. Pour plus d&#39;informations, consultez [cette section](../../platform/using/defining-filter-conditions.md).

      ![](assets/social_twitter_delivery_018.png)

### Choisir la cible du BAT {#selecting-the-target-of-the-proof-1}

L&#39; **[!UICONTROL Target of the proofs]** onglet vous permet de sélectionner l&#39;abonné qui recevra la preuve de votre message direct. Le processus de sélection est le même que pour la cible principale. Reportez-vous à [Sélection de la cible](#selecting-the-main-target)principale.

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Si vous souhaitez envoyer toutes vos épreuves de message direct au même suiveur Twitter, vous pouvez enregistrer la cible de preuve dans le modèle de **[!UICONTROL Tweet (Direct Message)]** diffusion, accessible via le **[!UICONTROL Resources > Templates > Delivery templates]** noeud. La cible d’épreuve sera alors saisie par défaut pour chaque nouvelle remise.

### Définir le contenu du message {#defining-message-content-}

Enter the content of the tweet in the **[!UICONTROL Content]** tab.

![](assets/social_twitter_delivery_015.png)

Comme pour une diffusion email, il est possible d’utiliser les champs de personnalisation, par exemple si vous souhaitez ajouter le nom de l’abonné dans le corps du message. La personnalisation du contenu est présentée dans [cette section](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

Les étapes suivantes sont identiques à celles de l’envoi d’un tweet à un compte Twitter. Reportez-vous à [Publication sur vos comptes](#publishing-on-your-twitter-accounts)Twitter.

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
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Publier sur Twitter{#publishing-on-twitter}

## Publier sur vos comptes Twitter {#publishing-on-your-twitter-accounts}

Une fois le paramétrage effectué, Social Marketing permet d&#39;envoyer des tweets sur vos comptes Twitter.

### Limitations {#limitations}

Les limitations suivantes sont des contraintes inhérentes à Twitter.

* La longueur du message ne peut pas dépasser 140 caractères.
* Le format HTML n&#39;est pas supporté.

### Créer la diffusion {#creating-the-delivery}

Créez une nouvelle diffusion basée sur le modèle de diffusion **[!UICONTROL Tweeter (twitter)]**.

![](assets/social_twitter_delivery_001.png)

### Choisir la cible principale {#selecting-the-main-target}

Vous devez sélectionner le ou les comptes sur lesquels vous souhaitez envoyer votre tweet.

1. Cliquez sur le lien **[!UICONTROL Pour]**.

   ![](assets/social_twitter_delivery_002.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/social_twitter_delivery_006.png)

1. Sélectionnez **[!UICONTROL Un compte Twitter]**.

   ![](assets/social_twitter_delivery_007.png)

1. Dans le champ **[!UICONTROL Dossier]**, sélectionnez le dossier de services contenant le compte Twitter. Sélectionnez ensuite le compte Twitter sur lequel vous souhaitez envoyer votre tweet.

   ![](assets/social_twitter_delivery_011.png)

### Choisir la cible du BAT {#selecting-the-target-of-the-proof}

L’onglet **[!UICONTROL Cible des épreuves]** permet de définir le compte Twitter à utiliser pour les remises de test avant la remise finale. Nous vous recommandons donc de créer un compte Twitter privé dédié à l&#39;envoi de preuves. Pour plus d’informations sur la création d’un compte Twitter privé, voir [Création d’un compte de test sur Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Les étapes de sélection de la cible d’épreuve sont identiques à celles de sélection de la cible principale. Reportez-vous à [Création d’un compte test sur Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Si vous utilisez le même compte Twitter de test pour toutes vos diffusions, vous pouvez enregistrer la cible du BAT dans le modèle de diffusion **[!UICONTROL Tweeter]**, accessible à partir du noeud **[!UICONTROL Ressources > Modèles > Modèles de diffusion]**. La cible du BAT sera alors renseignée par défaut pour chaque nouvelle diffusion.

### Définir le contenu du message {#defining-the-message-content}

Saisissez le contenu du tweet dans l&#39;onglet **[!UICONTROL Contenu]**.

![](assets/social_twitter_delivery_005.png)

### Visualiser l&#39;aperçu {#viewing-the-preview}

L&#39;onglet **[!UICONTROL Aperçu]** permet de visualiser le rendu du tweet.

1. Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]**.
1. Cliquez sur le menu déroulant **[!UICONTROL Tester la personnalisation]** et sélectionnez **[!UICONTROL Service]**.
1. Dans le champ **[!UICONTROL Dossier]**, sélectionnez le dossier de services contenant votre compte Twitter.
1. Sélectionnez le compte Twitter sur lequel vous souhaitez tester l&#39;aperçu.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>L’aperçu peut différer légèrement du tweet final. Nous vous recommandons vivement d’envoyer une preuve avant la remise finale afin d’afficher le rendu exact du tweet. Reportez-vous à [Envoi de la preuve](#sending-the-proof).

### Configurer le tracking {#configuring-tracking}

Le tracking est visualisable dans les rapports de diffusion et dans l&#39;onglet **[!UICONTROL Edition > Tracking]** de la diffusion et du service.

La configuration du tracking s’effectue de la même manière que pour une diffusion email. Voir à ce sujet [cette section](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>Dans le modèle de diffusion **[!UICONTROL Tweeter]**, le tracking est activé par défaut.

>[!IMPORTANT]
>
>Il n&#39;est pas possible de distinguer l&#39;activité des robots qui analysent les tweets des utilisateurs qui cliquent réellement.

### Envoyer le BAT {#sending-the-proof}

Nous vous recommandons vivement d’envoyer une preuve de votre publication avant la livraison finale afin d’obtenir un rendu exact de la publication sur une page de test Twitter privée. Pour plus d’informations sur la création d’un compte Twitter privé, voir [Création d’un compte de test sur Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Les étapes de sélection de la cible de l&#39;épreuve sont détaillées dans [Sélection de la cible de l&#39;épreuve](#selecting-the-target-of-the-proof).

L’envoi du BAT s’effectue de la même manière que pour une diffusion email. Reportez-vous à [cette section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Envoyer le message {#sending-the-message}

1. Une fois le contenu validé, cliquez sur le bouton **[!UICONTROL Envoyer]**.
1. Choisissez **[!UICONTROL Diffuser dès que possible]** et cliquez sur le bouton **[!UICONTROL Analyser]**.

   >[!NOTE]
   >
   >L&#39;option **[!UICONTROL Différer la diffusion]** permet de différer l&#39;envoi de la diffusion à une date ultérieure.

   ![](assets/social_twitter_delivery_012.png)

1. Une fois l&#39;analyse terminée, vérifiez le résultat de l&#39;analyse.
1. Cliquez sur le bouton **[!UICONTROL Confirmer l&#39;envoi]**, puis cliquez sur **[!UICONTROL Oui]**.

![](assets/social_facebook_delivery_016.png)

## Envoyer des messages directs à vos abonnés {#sending-direct-messages-to-subscribers}

### Principe de fonctionnement {#operating-principle}

Le processus **[!UICONTROL Synchroniser les comptes]** Twitter (voir [Synchronisation des comptes](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)Twitter) récupère la liste des abonnés Twitter afin que vous puissiez leur envoyer des messages directs. Les abonnés récupérés sont stockés dans un tableau spécifique : le tableau des visiteurs. Pour afficher la liste des abonnés Twitter, accédez au noeud **[!UICONTROL Profils et cibles > Visiteurs]** .

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>In order for the workflow to recover the list of Twitter followers, the **[!UICONTROL Synchronize Twitter accounts]** box must be checked in the Edit screen of the service linked to the account. Pour plus d’informations à ce sujet, voir : La [délégation de l’accès en écriture à Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Pour chaque abonné, Adobe Campaign récupère les informations suivantes :

* **[!UICONTROL Origine]** : nom du réseau social (**Twitter**, dans ce cas)
* **[!UICONTROL Id externe]** : identifiant de l&#39;utilisateur
* **[!UICONTROL Pseudo]** : nom de compte de l&#39;utilisateur
* **[!UICONTROL Nom]** complet : nom de l’utilisateur
* **[!UICONTROL Langue]** : langue de l&#39;utilisateur
* **[!UICONTROL Nombre d&#39;amis]** : nombre d&#39;abonnés au compte de l&#39;utilisateur
* **[!UICONTROL Fuseau horaire]** : fuseau horaire de l&#39;utilisateur
* **[!UICONTROL Vérifié]** : ce champ indique si l&#39;utilisateur possède un compte Twitter vérifié

### Limitations {#limitations-1}

Les limitations suivantes sont des contraintes inhérentes à Twitter.

* La longueur du message ne peut pas dépasser 140 caractères.
* Le format HTML n&#39;est pas supporté.
* Vous ne pouvez pas envoyer plus de 250 messages directs par jour. Afin de ne pas dépasser cette limite, il est possible d’effectuer un envoi en plusieurs vagues. L’envoi en plusieurs vagues s’effectue de la même manière que pour une diffusion email. Voir à ce sujet [cette section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Créer la diffusion {#creating-the-delivery-}

Créez une nouvelle diffusion basée sur le modèle de diffusion **[!UICONTROL Tweeter (Direct Message)]**.

![](assets/social_twitter_delivery_010.png)

### Choisir la cible principale {#selecting-the-main-target-1}

Vous devez sélectionner les abonnés à qui vous souhaitez envoyer votre message direct.

1. Cliquez sur le lien **[!UICONTROL Pour]**.

   ![](assets/social_twitter_delivery_016.png)

1. Cliquez sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/social_twitter_delivery_006.png)

1. Choisissez un type de ciblage.

   ![](assets/social_twitter_delivery_017.png)

   * Sélectionnez **[!UICONTROL Abonnés d&#39;un compte Twitter]** pour envoyer un message direct à tous les abonnés d&#39;un compte.

      >[!IMPORTANT]
      >
      >Vous ne pouvez pas envoyer plus de 250 messages par jour. Si votre compte Twitter comporte plus de 250 abonnés, il est vivement recommandé d’effectuer un envoi en plusieurs vagues. L’envoi en plusieurs vagues s’effectue de la même manière que pour une diffusion email. Reportez-vous à [cette section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Sélectionnez **[!UICONTROL Conditions de filtrage]** afin de définir une requête et d’en visualiser le résultat. Cette option s’utilise de la même manière que pour une diffusion email. Reportez-vous à [cette section](../../platform/using/defining-filter-conditions.md) pour plus d’informations.

      ![](assets/social_twitter_delivery_018.png)

### Choisir la cible du BAT {#selecting-the-target-of-the-proof-1}

The **[!UICONTROL Target of the proofs]** tab lets you select the follower who will receive the proof of your direct message. The selection process is the same as for the main target. Reportez-vous à [Sélection de la cible](#selecting-the-main-target)principale.

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Si vous souhaitez envoyer tous les BAT de vos messages directs au même abonné Twitter, vous pouvez enregistrer la cible du BAT dans le modèle de diffusion **[!UICONTROL Tweeter (Direct Message)]**, accessible à partir du noeud **[!UICONTROL Ressources > Modèles > Modèles de diffusion]**. La cible du BAT sera alors renseignée par défaut pour chaque nouvelle diffusion.

### Définir le contenu du message {#defining-message-content-}

Saisissez le contenu du tweet dans l&#39;onglet **[!UICONTROL Contenu]**.

![](assets/social_twitter_delivery_015.png)

Comme pour une diffusion email, il est possible d’utiliser les champs de personnalisation, par exemple si vous souhaitez ajouter le nom de l’abonné dans le corps du message. La personnalisation du contenu est présentée dans [cette section](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

Les étapes suivantes sont identiques à celles de l’envoi d’un tweet à un compte Twitter. Reportez-vous à [Publication sur vos comptes](#publishing-on-your-twitter-accounts)Twitter.

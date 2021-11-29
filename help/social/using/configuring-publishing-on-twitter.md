---
product: campaign
title: Configurer la publication Twitter
description: Configurer la publication Twitter
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 62%

---

# Étapes de configuration de la publication sur Twitter{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

Pour qu&#39;Adobe Campaign puisse envoyer des tweets sur vos comptes Twitter, vous devez déléguer, à Adobe Campaign, les droits d&#39;écriture sur ces comptes. Les étapes de paramétrage sont les suivantes :

* Créez un compte Twitter.
* Créez un compte Twitter de test dédié à l&#39;envoi de BAT.
* Créez une application Twitter par compte Twitter.
* Pour chaque application Twitter, créez un nouveau service de type **[!UICONTROL Twitter]**.

![](assets/social_diagram_twitter_service.png)

## Conditions préalables requises {#prerequisites}

Vous devez tout d&#39;abord créer un ou plusieurs comptes Twitter sur lesquels vous enverrez vos tweets.

Pour créer un compte Twitter, accédez à [https://twitter.com](https://twitter.com){target=&quot;_blank&quot;}.

## Création d’un compte test sur Twitter {#creating-a-test-account-on-twitter}

Création d’un compte Twitter privé qui peut être utilisé pour l’envoi [BAT de tweet](../../social/using/publishing-on-twitter.md#sending-the-proof). Pour créer un compte Twitter privé, procédez comme suit :

1. Créez un nouveau compte Twitter.
1. Accès au compte  **[!UICONTROL Paramètres]**.
1. Accédez à **[!UICONTROL Confidentialité et sécurité]** et **[!UICONTROL Audience et balisage]** et vérifiez la variable **[!UICONTROL Protect de vos tweets]** . Vos tweets et autres informations de compte ne sont visibles que par les personnes qui vous suivent.

![](assets/social_twitter_test_page.png)

## Création d’une application sur Twitter {#creating-an-application-on-twitter}

Pour qu&#39;Adobe Campaign puisse envoyer des tweets sur vos comptes Twitter, vous devez créer une application Twitter par compte Twitter. Les étapes sont les suivantes :

1. Connectez-vous à votre compte Twitter.
1. Saisissez l&#39;adresse suivante dans votre navigateur Internet : [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps).
1. Cliquez ensuite sur le bouton **[!UICONTROL Création d’une application]** sur la droite.

   ![](assets/social_create_twitter_app_001.png)

1. Laissez-vous guider par l&#39;assistant.

   Pour que cette application permette à Adobe Campaign d&#39;envoyer des tweets sur votre compte, rendez-vous sur l&#39;onglet **[!UICONTROL Autorisations]** de l&#39;application et sélectionnez **[!UICONTROL Read and Write]** dans la section **[!UICONTROL Access]**. Sur l&#39;onglet **[!UICONTROL Settings]**, vous devez également laisser le champ **[!UICONTROL Callback URL]** vide.

   ![](assets/social_create_twitter_app_002.png)

## Déléguer les droits d’écriture à Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Pour chaque application Twitter, vous devez créer un service de type **[!UICONTROL Twitter]** différent, dans lequel vous renseignerez les paramètres de chacune des applications.

Cette étape requiert l&#39;accès simultané à votre console Adobe Campaign ainsi qu&#39;à un navigateur Internet connecté à votre compte Twitter :

* in **Twitter**: de [cette page](https://developer.twitter.com/en/portal/projects-and-apps), sélectionnez l’application créée précédemment et modifiez la variable **Autorisations d’application**.

   ![](assets/social_twitter_service_002.png)

   Modifiez la variable **Clés et jetons** pour accéder aux détails de votre application.

* in **Adobe Campaign**: accédez à la **[!UICONTROL Profils et cibles]** , cliquez sur l’onglet **[!UICONTROL Services et abonnements]** et cliquez sur le lien **[!UICONTROL Créer]** bouton .

   ![](assets/social_twitter_service_007.png)

1. Sélectionnez le type **[!UICONTROL Twitter]**.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >L’option **[!UICONTROL Synchroniser les abonnements]** est activée par défaut. Lorsque cette case est cochée, le processus de synchronisation des comptes Twitter (voir [Synchronisation des comptes Twitter](#synchronizing-twitter-accounts)) récupère la liste des abonnés Twitter afin que vous puissiez leur envoyer des messages directs (voir [Envoyer des messages directs à vos abonnés](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Si vous ne souhaitez pas récupérer la liste des abonnés, décochez cette case.

1. Renseignez le libellé et le nom interne du service.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >Le **[!UICONTROL Nom interne]** du service doit être identique au nom du compte Twitter. Pour vous assurer qu’il n’y a aucune erreur d’entrée, procédez comme suit.

   * Cliquez sur le bouton **[!UICONTROL Enregistrer]**.
   * Dans la vue d&#39;ensemble des services, cliquez sur le service de Twitter que vous venez de créer.

   <!-- * Select the **[!UICONTROL Twitter page]** tab. The Twitter account should be displayed. 
    
      ![](assets/social_twitter_service_010.png)-->

1. Dans le **[!UICONTROL Dossier du visiteur]** , sélectionnez le dossier dans lequel les abonnés seront créés. Pour plus d’informations, consultez [cette section](../../social/using/publishing-on-twitter.md#operating-principle). Par défaut, les abonnés sont enregistrés dans la variable **[!UICONTROL Visiteurs]** dossier.

   ![](assets/social_twitter_service_010_b.png)

1. Sur Twitter, copiez le contenu de la variable **[!UICONTROL Clé client (clé API)]** et **[!UICONTROL Secret du client (secret d’API)]** et collez-les dans le champ **[!UICONTROL Clé du client]** et **[!UICONTROL Secret du client]** des champs de la console cliente Campaign.

   ![](assets/social_twitter_service_012.png)

1. Sur Twitter, copiez le contenu de la variable **[!UICONTROL Jeton d’accès]** et **[!UICONTROL Secret du jeton d’accès]** et collez-les dans le champ **[!UICONTROL Jeton d’accès]** et **[!UICONTROL Secret du jeton d’accès]** des champs de la console cliente Campaign.

   ![](assets/social_twitter_service_013.png)

1. Dans la console cliente Campaign, cliquez sur **[!UICONTROL Enregistrer]**. Vous avez désormais délégué l’accès en écriture à Adobe Campaign.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Vous devez créer un service de **[!UICONTROL Twitter]** par application Twitter.

Le workflow **[!UICONTROL Synchronisation des comptes Twitter]** synchronise les comptes Twitter dans Adobe Campaign. Pour plus dʼinformations, consultez [cette page](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Synchronisation des comptes Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Pour que le workflow récupère la liste des abonnés d&#39;un compte Twitter, la case **[!UICONTROL Synchronisation des comptes Twitter]** doit être cochée dans la section d’édition du service lié au compte. Pour plus d’informations, consultez [cette section](#delegating-write-access-to-adobe-campaign).

Le workflow **[!UICONTROL Synchronisation des comptes Twitter]**, accessible à partir du noeud **[!UICONTROL Administration > Exploitation > Workflows techniques > Gestion des réseaux sociaux]** permet de synchroniser, dans Adobe Campaign, les comptes Twitter paramétrés précédemment. Ce workflow est configuré par défaut pour se déclencher tous les jeudis à 7 heures 30 du matin.

>[!NOTE]
>
>Vous pouvez démarrer le workflow à tout moment en exécutant le traitement anticipé des tâches. Vous pouvez également modifier le planificateur pour modifier la fréquence de déclenchement du workflow. Pour plus d’informations sur le planificateur, reportez-vous à [cette section](../../workflow/using/scheduler.md).

Vous pouvez désormais envoyer des tweets à vos comptes Twitter et envoyer des messages directs à vos abonnés. Pour plus dʼinformations, consultez [cette page](../../social/using/publishing-on-twitter.md).

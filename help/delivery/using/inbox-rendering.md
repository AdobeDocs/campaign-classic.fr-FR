---
title: Inbox rendering
seo-title: Inbox rendering
description: Inbox rendering
seo-description: null
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 30f313cecf1c3d7c65f6524a3f86a1c28b35f679

---


# Inbox rendering{#inbox-rendering}

## A propos de l&#39;inbox rendering {#about-inbox-rendering}

Avant d&#39;appuyer sur le bouton **Envoyer**, vérifiez que l&#39;affichage de votre message sera optimal pour les destinataires sur divers clients web, webmails et appareils.

Pour permettre cette vérification, Adobe Campaign utilise la solution web de test d&#39;email [Litmus](https://litmus.com/email-testing) afin de capturer les rendus et les rendre disponibles dans un rapport dédié. Vous pouvez ainsi visualiser l&#39;affichage du message envoyé dans les différents contextes de réception et vérifier la compatibilité sur les principaux postes de travail et dans les applications majeures.

Litmus est une application de validation et de prévisualisation d&#39;emails offrant de nombreuses fonctionnalités. Elle permet aux créateurs de contenus d&#39;email de prévisualiser le contenu d&#39;un message dans plus de 70 outils de rendu d&#39;email, tels que la boîte de réception Gmail ou le client Apple Mail.

Les clients mobiles, de messagerie et webmail disponibles pour l&#39;**Inbox rendering** dans Adobe Campaign sont répertoriés sur le [site web de Litmus](https://litmus.com/email-testing) (cliquez sur **View all email clients**).

>[!NOTE]
>
>L&#39;Inbox rendering n&#39;est pas nécessaire pour tester les personnalisations dans les diffusions. Celles-ci peuvent être vérifiées à l&#39;aide des outils d&#39;Adobe Campaign tels que l&#39;**[!UICONTROL aperçu]** et les [bons à tirer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Activation du rendu de la boîte de réception{#activating-inbox-rendering}

Pour les clients hébergés et hybrides, le rendu de la boîte de réception est configuré sur votre instance par l’assistance technique et les consultants d’Adobe. Pour plus d’informations, contactez votre gestionnaire de compte Adobe.

Pour les installations sur site, suivez les étapes ci-dessous pour configurer le rendu de la boîte de réception.

1. Installez le package de rendu de la **[!UICONTROL boîte de]** réception (IR) **[!UICONTROL via le menu]** Outils **[!UICONTROL >]** Avancé **[!UICONTROL >Importer le package.]** Pour plus d’informations, voir [Installation des packs](../../installation/using/installing-campaign-standard-packages.md)standard Campaign Classic.
1. Configurez un compte externe de type HTTP via le noeud **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > Comptes **** externes. For more on this, see [Creating an external account](../../platform/using/external-accounts.md#creating-an-external-account).
1. Définissez les paramètres du compte externe comme suit :
   * **[!UICONTROL Étiquette]**: Informations sur le serveur de délivrabilité
   * **[!UICONTROL Nom]** interne : délivrabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Serveur]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Chiffrement]**: Aucun
   * Cochez l&#39;option **[!UICONTROL Activé]**.
   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Accédez au noeud **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]** . Recherchez l’option **[!UICONTROL DmRendering_cuid]** et contactez l’assistance technique pour obtenir l’identifiant des rapports de livraison qui doit être copié dans le champ **[!UICONTROL Valeur (texte)]** .
1. Modifiez le fichier **serverConf.xml** pour autoriser un appel au serveur Litmus. Ajoutez la ligne suivante à la `<urlPermission>` section :

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Rechargez la configuration à l’aide de la commande suivante :

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Vous devrez peut-être vous déconnecter de la console et vous reconnecter pour pouvoir utiliser le rendu de la boîte de réception.

## A propos des jetons Litmus {#about-litmus-tokens}

Litmus étant un service tiers, il fonctionne selon un modèle de crédit déduit par utilisation. Chaque fois qu&#39;un utilisateur fait appel à la fonctionnalité Litmus, un crédit est déduit.

Dans Adobe Campaign, le crédit correspond au nombre de rendus disponibles (appelés jetons).

>[!NOTE]
>
>Le nombre de jetons Litmus disponibles dépend de la licence Campaign que vous avez achetée. Vérifiez votre contrat de licence.

Chaque fois que vous utilisez la fonctionnalité **[!UICONTROL Inbox rendering]** dans une diffusion, un rendu généré réduit les jetons disponibles d&#39;une unité.

>[!IMPORTANT]
>
>Les jetons représentent chaque rendu et non le rapport d&#39;inbox rendering complet, ce qui signifie que :
>
>* Chaque fois que le rapport d&#39;inbox rendering est généré, un jeton est déduit par client de messagerie : un jeton pour le rendu Outlook 2000, un pour le rendu Outlook 2010, un pour le rendu Apple Mail 9, etc.
>* Pour une même diffusion, si vous régénérez le rapport d&#39;inbox rendering, le nombre de jetons disponibles est à nouveau réduit en fonction du nombre de rendus générés.
>



The number of remaining available tokens is displayed in the **[!UICONTROL General summary]** of the [Inbox rendering report](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

En règle générale, la fonctionnalité Inbox rendering est utilisée pour tester la structure HTML d&#39;un nouvel email. Chaque rendu nécessite environ 70 jetons (en fonction du nombre d&#39;environnements dans lequel il est généralement testé). Toutefois, dans certains cas, vous devrez peut-être générer plusieurs rapports d&#39;inbox rendering pour tester entièrement votre diffusion. Plusieurs vérifications peuvent donc nécessiter des jetons supplémentaires.

>[!NOTE]
>
>Si vous êtes un client Litmus, vous pouvez utiliser votre compte Litmus pour activer et utiliser l&#39;option Inbox rendering dans Adobe Campaign. Pour plus d&#39;informations, contactez votre chargé de compte Adobe.
>
>La modification de vos identifiants Litmus peut entraîner des problèmes d&#39;authentification au sein d&#39;Adobe Campaign.

## Accéder au rapport d&#39;inbox rendering {#accessing-the-inbox-rendering-report}

Une fois que vous avez créé votre diffusion email et défini son contenu ainsi que la population ciblée, suivez la procédure décrite ci-après.

Pour plus d&#39;informations sur la conception et le ciblage d&#39;une diffusion, consultez [cette section](../../delivery/using/about-email-channel.md).

1. Dans la barre supérieure de la diffusion, cliquez sur le bouton **[!UICONTROL Inbox rendering]**.
1. Sélectionnez **[!UICONTROL Analyser]** pour commencer la capture.

   ![](assets/s_tn_inbox_rendering_button.png)

   Un BAT est envoyé. Les vignettes de rendu sont accessibles dans ce BAT quelques minutes après l&#39;envoi des emails. Pour plus d&#39;informations sur l&#39;envoi de BAT, consultez [cette section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. Une fois envoyé, le BAT apparaît dans la liste de diffusion. Double-cliquez dessus.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Accédez à l&#39;onglet **Inbox Rendering** du BAT.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Le rapport d&#39;inbox rendering s&#39;affiche.

## Rapport d&#39;inbox rendering {#inbox-rendering-report}

Ce rapport présente les inbox renderings tels qu&#39;ils apparaissent côté destinataire. Ils peuvent être différents selon le mode d&#39;ouverture de la diffusion email par le destinataire : dans un navigateur, sur un appareil mobile ou via une application de messagerie.

La **[!UICONTROL synthèse générale]** présente le nombre de messages reçus, indésirables (spam), non reçus ou en attente de réception sous la forme d&#39;une liste et dans une représentation graphique avec un code-couleur.

![](assets/s_tn_inbox_rendering_summary.png)

Survolez le graphique avec la souris pour afficher les détails de chaque couleur.

Le rapport est divisé en trois parties : **[!UICONTROL Mobile]**, **[!UICONTROL Clients de messagerie]** et **[!UICONTROL Webmails]**. Faites défiler le rapport pour afficher tous les rendus regroupés dans ces trois catégories.

![](assets/s_tn_inbox_rendering_report.png)

Pour voir les détails de chaque rapport, cliquez sur la vignette correspondante. Le rendu s&#39;affiche pour le moyen de réception sélectionné.

![](assets/s_tn_inbox_rendering_example.png)

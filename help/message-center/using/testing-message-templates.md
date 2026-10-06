---
product: campaign
title: Test des modèles de message transactionnel
description: Découvrez comment gérer les adresses de contrôle dans les messages transactionnels afin de les prévisualiser et de les tester dans Adobe Campaign Classic.
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
TQID: 'https://experienceleague.adobe.com/jcmXX4aMPaTBatt4m3s-IAaAeoXnjmPaEE4oqIDoIOI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 100%
---
# Test des modèles de message transactionnel {#testing-message-templates}



Une fois que votre [modèle de message](../../message-center/using/creating-the-message-template.md) est prêt, suivez les étapes ci-dessous pour le prévisualiser et le tester.

## Gestion des adresses de contrôle dans les messages transactionnels {#managing-seed-addresses-in-transactional-messages}

Une adresse de contrôle vous permet d’afficher une prévisualisation de votre message, d’envoyer un BAT et de tester la personnalisation du message avant la diffusion par e-mail ou SMS. Les adresses de contrôle sont liées à la diffusion et ne peuvent pas être utilisées pour d&#39;autres diffusions.

Pour créer des adresses de contrôle dans un message transactionnel, procédez comme suit :

1. Dans le modèle de message transactionnel, cliquez sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Attribuez-lui un libellé afin de pouvoir sélectionner l&#39;adresse ultérieurement si nécessaire.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Entrez l&#39;adresse de contrôle, soit l&#39;email ou le numéro de portable selon le canal de communication de la diffusion.

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Saisissez l’identifiant externe : ce champ facultatif vous permet de saisir une clé métier (ID unique, nom + adresse e-mail, etc.) commune à toutes les applications de votre site web, utilisée pour identifier vos profils. Si ce champ est également présent dans la base de données marketing Adobe Campaign, vous pouvez ensuite réconcilier un événement avec un profil dans la base de données.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Insérez des données de test (voir [Données de personnalisation](#personalization-data)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Cliquez sur le lien **[!UICONTROL Ajouter d&#39;autres adresses de contrôle]**, puis sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Répétez l&#39;opération pour créer le nombre d&#39;adresses voulu.

   ![](assets/messagecenter_create_seedaddr_008.png)

Lorsque les adresses sont créées, vous pouvez dès lors afficher l&#39;aperçu de votre message et sa personnalisation. Voir [Aperçu du message transactionnel](#transactional-message-preview).

## Données de personnalisation {#personalization-data}

Il est possible d’utiliser des données dans le modèle de message pour tester la personnalisation des messages transactionnels. Cette fonctionnalité est utilisée pour générer une prévisualisation ou envoyer un BAT. Vous pouvez également afficher le rendu du message pour différents fournisseurs d&#39;accès Internet. Pour plus d&#39;informations, consultez la section [Inbox rendering](../../delivery/using/inbox-rendering.md).

Ces données ont pour but de tester vos messages avant leur diffusion finale. Ces messages ne correspondent pas aux données réelles à traiter. Cependant, la structure XML doit être identique à celle de l’événement stocké dans l’instance d’exécution, comme illustré ci-dessous :

![](assets/messagecenter_create_custo_006.png)

Ces informations permettent de personnaliser le contenu du message à l&#39;aide de balises de personnalisation (voir à ce sujet la section [Création du contenu du message](../../message-center/using/creating-the-message-template.md#creating-message-content)).

1. Sélectionnez le modèle de message transactionnel.

1. Dans le modèle de , cliquez sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**.

1. Dans le contenu de l&#39;événement, entrez les informations de test au format XML.

   ![](assets/messagecenter_create_custo_001.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Aperçu du message transactionnel {#transactional-message-preview}

Lorsque vous avez créé une ou plusieurs adresses de contrôle, ainsi que le corps du message, vous pouvez afficher l&#39;aperçu de votre message et vérifier la personnalisation de ce dernier.

1. Dans le modèle de message, cliquez sur l&#39;onglet **[!UICONTROL Aperçu]**.

   ![](assets/messagecenter_preview_001.png)

1. Sélectionnez **[!UICONTROL Adresse de contrôle]** dans la liste déroulante.

   ![](assets/messagecenter_preview_002.png)

1. Sélectionnez l&#39;adresse de contrôle préalablement créée afin d&#39;afficher le message personnalisé.

   ![](assets/messagecenter_create_seedaddr_009.png)

À l&#39;aide des adresses de contrôle, vous pouvez également afficher le rendu du message pour les différents fournisseurs d&#39;accès Internet. Pour plus d&#39;informations, consultez la section [Inbox rendering](../../delivery/using/inbox-rendering.md).

## Envoyer un BAT {#sending-a-proof}

Vous pouvez tester la diffusion du message en envoyant un BAT vers une adresse de contrôle créée précédemment.

L’envoi d’un BAT engage le même processus que pour une diffusion standard. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=fr){target="_blank"}. Toutefois, avec les messages transactionnels, vous devez effectuer au préalable les opérations suivantes :

* Création d&#39;une ou plusieurs [adresses de contrôle](#managing-seed-addresses-in-transactional-messages)[ avec des données de de personnalisation](#personalization-data).
* [Création du contenu du message](../../message-center/using/creating-the-message-template.md#creating-message-content).

Pour effectuer l&#39;envoi :

1. Cliquez sur bouton **[!UICONTROL Envoyer un BAT]** dans la fenêtre de diffusion.
1. Analysez la diffusion.
1. Corrigez les erreurs et validez la diffusion.

   ![](assets/messagecenter_send_proof_001.png)

1. Vérifiez que le message est bien parvenu à l&#39;adresse de contrôle et que son contenu est conforme à ce que vous aviez paramétré.

   ![](assets/messagecenter_send_proof_002.png)

Les BAT sont accessibles au niveau de chaque modèle, depuis l&#39;onglet **[!UICONTROL Suivi.]** Pour plus d’informations à ce sujet, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=fr){target="_blank"}.

![](assets/messagecenter_send_proof_003.png)

Votre modèle de message est maintenant prêt à être [publié](../../message-center/using/publishing-message-templates.md).
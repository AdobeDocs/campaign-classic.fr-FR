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
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 60%
---
# Test des modèles de message transactionnel {#testing-message-templates}

Une fois que votre [modèle de message](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentation de Campaign v8) est prêt, suivez les étapes ci-dessous pour le prévisualiser et le tester.

Dans le cadre de la transition de Campaign v7 vers v8, le jeu de documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour savoir comment ajouter des adresses de contrôle, prévisualiser un message transactionnel et envoyer un BAT, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}

## Données de personnalisation {#personalization-data}

Il est possible d’utiliser des données dans le modèle de message pour tester la personnalisation des messages transactionnels. Cette fonctionnalité est utilisée pour générer une prévisualisation ou envoyer un BAT. Vous pouvez également afficher le rendu du message pour différents fournisseurs d&#39;accès Internet. Pour plus d&#39;informations, consultez la section [Inbox rendering](../../delivery/using/inbox-rendering.md).

Ces données ont pour but de tester vos messages avant leur diffusion finale. Ces messages ne correspondent pas aux données réelles à traiter. Cependant, la structure XML doit être identique à celle de l’événement stocké dans l’instance d’exécution, comme illustré ci-dessous :

![](assets/messagecenter_create_custo_006.png)

Ces informations permettent de personnaliser le contenu du message à l&#39;aide de balises de personnalisation (pour plus d&#39;informations, consultez la section [Créer le contenu du message](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/real-time/transactional-template#create-message-content){target="_blank"} (documentation de Campaign v8)).

1. Sélectionnez le modèle de message transactionnel.

1. Dans le modèle de , cliquez sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**.

1. Dans le contenu de l&#39;événement, entrez les informations de test au format XML.

   ![](assets/messagecenter_create_custo_001.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

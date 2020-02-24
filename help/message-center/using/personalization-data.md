---
title: Données de personnalisation
seo-title: Données de personnalisation
description: Données de personnalisation
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Données de personnalisation{#personalization-data}

Vous pouvez utiliser des données dans le modèle de message afin de tester la personnalisation de vos messages transactionnels. Cette fonctionnalité est utilisée pour générer un aperçu ou envoyer un BAT. Si vous installez le module **Délivrabilité**, ces données vous permettent d&#39;afficher le rendu des messages chez différents fournisseurs d&#39;accès (**Inbox rendering**, voir à ce sujet [cette section](../../delivery/using/about-deliverability.md)).

Ces données n&#39;ont pour but que de tester vos messages avant leur envoi effectif et ne correspondent pas aux données réelles qui seront traitées par Message Center. En revanche, la structure XML doit être identique à celle de l&#39;événement qui est stocké dans l&#39;instance d&#39;exécution, comme illustré ci-dessous.

![](assets/messagecenter_create_custo_006.png)

This information enables you to personalize message content using personalization tags (for more on this, refer to [Creating message content](../../message-center/using/creating-message-content.md)).

1. Dans le modèle de message, cliquez sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**.
1. Dans le contenu de l&#39;événement, entrez les informations de test au format XML.

   ![](assets/messagecenter_create_custo_001.png)


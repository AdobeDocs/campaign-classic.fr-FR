---
solution: Campaign Classic
product: campaign
title: Données de personnalisation
description: Données de personnalisation
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 100%

---


# Données de personnalisation{#personalization-data}

Vous pouvez utiliser des données dans le modèle de message afin de tester la personnalisation de vos messages transactionnels. Cette fonctionnalité est utilisée pour générer un aperçu ou envoyer un BAT. Si vous installez le module **Délivrabilité**, ces données vous permettent d&#39;afficher le rendu des messages chez différents fournisseurs d&#39;accès (**Inbox rendering**, voir à ce sujet [cette section](../../delivery/using/inbox-rendering.md)).

Ces données n&#39;ont pour but que de tester vos messages avant leur envoi effectif et ne correspondent pas aux données réelles qui seront traitées par Message Center. En revanche, la structure XML doit être identique à celle de l&#39;événement qui est stocké dans l&#39;instance d&#39;exécution, comme illustré ci-dessous.

![](assets/messagecenter_create_custo_006.png)

Ces informations permettent de personnaliser le contenu du message à l’aide de balises de personnalisation (voir à ce sujet la section [Création du contenu du message](../../message-center/using/creating-message-content.md)).

1. Dans le modèle de message, cliquez sur l&#39;onglet **[!UICONTROL Adresses de contrôle]**.
1. Dans le contenu de l&#39;événement, entrez les informations de test au format XML.

   ![](assets/messagecenter_create_custo_001.png)

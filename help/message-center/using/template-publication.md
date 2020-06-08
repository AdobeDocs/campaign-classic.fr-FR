---
title: Publication des modèles
seo-title: Publication des modèles
description: Publication des modèles
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1486e897a125520c51661db3030c62ab380fb173
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 62%

---


# Publication des modèles{#template-publication}

Une fois le modèle de message créé sur l’instance de pilotage terminé, vous pouvez le publier sur toutes les instances d&#39;exécution. La publication vous permet de créer automatiquement deux modèles de messages sur l’instance d&#39;exécution, ce qui vous permet d’envoyer des messages liés à des messages en temps réel et à des événements batch.

>[!IMPORTANT]
>
>Toute modification du modèle doit être suivie d&#39;une nouvelle publication afin que les changements soient pris en compte lors de l&#39;envoi des messages transactionnels.

>[!NOTE]
>
>Lors de la publication de modèles de messages transactionnels, les règles de typologie sont automatiquement publiées sur les instances d&#39;exécution.

1. Dans l&#39;instance de pilotage, positionnez-vous au niveau du dossier **[!UICONTROL Message Center > Modèle de messages transactionnels]** dans l&#39;arborescence.
1. Sélectionnez le modèle que vous souhaitez publier sur vos instances d&#39;exécution.
1. Cliquez sur **[!UICONTROL Publier]**.

   ![](assets/messagecenter_publish_model_008.png)

Once publication is complete, both message templates to be applied to batch and real-time type events are created in the tree of the production instance in the **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** folder.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Si vous remplacez par une valeur vide un champ existant du modèle de message transactionnel, tel que l’adresse de l’expéditeur, le champ correspondant sur la ou les instances d’exécution ne sera pas mis à jour lors de la nouvelle publication du message transactionnel. Il contiendra toujours la valeur précédente. Toutefois, si vous avez une valeur non vide, le champ correspondant sera mis à jour de manière habituelle après la publication suivante.

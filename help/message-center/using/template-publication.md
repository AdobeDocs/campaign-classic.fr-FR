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
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Publication des modèles{#template-publication}

Lorsque le modèle de message créé sur l&#39;instance de pilotage est finalisé, vous devez le publier sur toutes les instances d&#39;exécution. La publication permet de créer automatiquement deux modèles de message sur l&#39;instance d&#39;exécution qui serviront à envoyer des messages correspondant respectivement aux événements temps réel et batch.

>[!CAUTION]
>
>Toute modification du modèle doit être suivie d&#39;une nouvelle publication afin que les changements soient pris en compte lors de l&#39;envoi des messages transactionnels.

>[!NOTE]
>
>Lors de la publication de modèles de messages transactionnels, les règles de typologie sont automatiquement publiées sur les instances d&#39;exécution.

1. Dans l&#39;instance de pilotage, positionnez-vous au niveau du dossier **[!UICONTROL Message Center > Modèle de messages transactionnels]** dans l&#39;arborescence.
1. Sélectionnez le modèle que vous souhaitez publier sur vos instances d&#39;exécution.
1. Cliquez sur **[!UICONTROL Publication]** .

   ![](assets/messagecenter_publish_model_008.png)

Lorsque la publication est terminée, les deux modèles de messages destinés à être appliqués aux types d&#39;événements batch et temps réel sont créés dans l&#39;arborescence de l&#39;instance d&#39;exploitation dans le dossier **[!UICONTROL Administration > Exploitation > Message Center > Défaut > Modèles de messages transactionnels]**.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Si vous remplacez par une valeur vide un champ existant du modèle de message transactionnel, tel que l’adresse de l’expéditeur, le champ correspondant sur la ou les instances d’exécution ne sera pas mis à jour lors de la nouvelle publication du message transactionnel. Il contiendra toujours la valeur précédente. Toutefois, si vous avez une valeur non vide, le champ correspondant sera mis à jour de manière habituelle après la publication suivante.


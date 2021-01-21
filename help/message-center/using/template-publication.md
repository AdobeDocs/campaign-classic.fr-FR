---
solution: Campaign Classic
product: campaign
title: Publication des modèles
description: Publication de modèles de message transactionnel
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: ht
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---


# Publication des modèles{#template-publication}

Lorsque le modèle de message créé sur l’instance de pilotage est terminé, vous pouvez le publier. Ce processus le publiera également sur toutes les instances d&#39;exécution.

La publication vous permet de créer automatiquement deux modèles de messages sur les instances d’exécution. Vous pouvez ainsi envoyer des messages liés à des événements temps réel et par lots.

>[!NOTE]
>
>Lors de la publication de modèles de messages transactionnels, les règles de typologie sont également automatiquement publiées sur les instances d&#39;exécution.

>[!IMPORTANT]
>
>Chaque fois que vous apportez des modifications à un modèle, veillez à le republier pour que ces modifications soient effectives pendant la diffusion du message transactionnel.

1. Dans l’instance de pilotage, positionnez-vous au niveau du dossier **[!UICONTROL Message Center > Modèle de messages transactionnels]** dans l’arborescence.
1. Sélectionnez le modèle que vous souhaitez publier sur vos instances d&#39;exécution.
1. Cliquez sur **[!UICONTROL Publier]**.

   ![](assets/messagecenter_publish_model_008.png)

Lorsque la publication est terminée, les deux modèles de messages destinés à être appliqués aux types d’événements temps réel et par lots sont créés dans l’arborescence de l’instance d’exploitation dans le dossier **[!UICONTROL Administration > Production > Message Center (Exécution) > Défaut > Modèles de messages transactionnels]**.

![](assets/messagecenter_deployed_model_001.png)

Une fois qu’un modèle est publié, si l’événement correspondant est déclenché, l’instance d&#39;exécution reçoit l’événement, le lie au modèle transactionnel et envoie le message transactionnel correspondant à chaque destinataire.

>[!NOTE]
>
>Si vous remplacez un champ existant du modèle de message transactionnel, tel que l’adresse de l’expéditeur, par une valeur vide, le champ correspondant sur l’instance ou les instances d&#39;exécution ne sera pas mis à jour une fois le message transactionnel republié. Il contiendra toujours la valeur précédente.
>
>Cependant, si vous ajoutez une valeur non vide, le champ correspondant sera mis à jour comme d’habitude après la publication suivante.

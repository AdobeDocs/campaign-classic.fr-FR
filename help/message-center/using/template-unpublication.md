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
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 10%

---


# Annulation de la publication du modèle{#template-unpublication}

Une fois qu’un modèle de message est publié sur les instances d&#39;exécution, il peut être annulé.

En effet, un modèle publié peut encore être appelé. Par conséquent, si vous n’utilisez plus de modèle de message, il est recommandé de l’annuler. Ceci est pour éviter d&#39;envoyer un message transactionnel indésirable par erreur. Par exemple, vous avez publié un modèle de message que vous utilisez uniquement pour les campagnes de Noël. Vous pouvez annuler sa publication une fois la période de Noël terminée et la publier de nouveau l’année prochaine.

En outre, vous ne pouvez pas supprimer un modèle de message transactionnel dont l’état est **[!UICONTROL Publié]** . Vous devez d’abord annuler sa publication.

Pour annuler la publication d’un modèle de message transactionnel, procédez comme décrit ci-dessous.

1. Dans l&#39;instance de pilotage, positionnez-vous au niveau du dossier **[!UICONTROL Message Center > Modèle de messages transactionnels]** dans l&#39;arborescence.
1. Sélectionnez le modèle que vous souhaitez annuler la publication.
1. Cliquez sur **[!UICONTROL Annuler la publication]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Cliquez sur **[!UICONTROL Démarrer]**.

![](assets/message-center-unpublish.png)

L’état du modèle de message transactionnel passe de **[!UICONTROL Publié]** à **[!UICONTROL Eté modifié]**.

Une fois la publication annulée :

* Les deux modèles de message (appliqués aux événements de type par lot et en temps réel) sont supprimés de chaque instance d&#39;exécution. Ils n’apparaissent plus dans le dossier **[!UICONTROL Administration > Production > Message Center Execution > Default > Modèles de message transactionnel]** .

* Une fois qu’un modèle n’est plus publié, vous pouvez le supprimer de l’instance de pilotage, si nécessaire. Pour ce faire, sélectionnez-la dans la liste et cliquez sur le bouton **[!UICONTROL Supprimer]** en haut à droite de l’écran.
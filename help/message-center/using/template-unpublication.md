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
translation-type: ht
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

---


# Annulation de la publication des modèles{#template-unpublication}

Lorsqu’un modèle de message a été publié sur les instances d’exécution, il est possible d’en annuler la publication.

En effet, il est encore possible d’appeler un modèle publié. Dans ce cas, si vous n’utilisez plus de modèle de message, il est recommandé d’annuler sa publication. Vous éviterez ainsi d’envoyer par erreur un message transactionnel indésirable. Par exemple, vous avez publié un modèle de message utilisé uniquement pour les campagnes de Noël. Vous pouvez annuler sa publication une fois la période de Noël terminée et le publier de nouveau l’année suivante.

En outre, vous ne pouvez pas supprimer un modèle de message transactionnel dont le statut est **[!UICONTROL Publié]**. Vous devez d’abord annuler sa publication.

Pour annuler la publication d’un modèle de message transactionnel, procédez comme décrit ci-dessous.

1. Dans l’instance de pilotage, positionnez-vous au niveau du dossier **[!UICONTROL Message Center > Modèle de messages transactionnels]** dans l’arborescence.
1. Sélectionnez le modèle dont vous souhaitez annuler la publication.
1. Cliquez sur **[!UICONTROL Annuler la publication]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Cliquez sur **[!UICONTROL Démarrer]**.

![](assets/message-center-unpublish.png)

Le statut du modèle de message transactionnel passe de **[!UICONTROL Publié]** à **[!UICONTROL En édition]**.

Une fois la publication annulée :

* Les deux modèles de message (appliqués aux types d’événements par lot et temps réel) sont supprimés de chaque instance d’exécution. Ils n’apparaissent plus dans le dossier **[!UICONTROL Administration > Production > Message Center (Exécution) > Défaut > Modèles de messages transactionnels]**.

* Une fois la publication d’un modèle annulée, vous pouvez le supprimer de l’instance de pilotage, si nécessaire. Pour ce faire, sélectionnez-le dans la liste et cliquez sur le bouton **[!UICONTROL Supprimer]** en haut à droite de l’écran.
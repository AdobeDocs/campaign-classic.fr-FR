---
solution: Campaign Classic
product: campaign
title: Publication des modèles
description: Publication des modèles
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: ht
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: ht
source-wordcount: '247'
ht-degree: 100%

---


# Annulation de la publication des modèles{#template-unpublication}

Lorsqu’un modèle de message a été publié sur les instances d’exécution, il est possible de le dépublier. Pour plus d’informations sur le processus de publication de modèles, consultez [cette section](../../message-center/using/template-publication.md).

* En effet, un modèle publié peut toujours être appelé si l&#39;événement correspondant est déclenché : si vous n’utilisez plus de modèle de message, il est recommandé de le dépublier. Vous éviterez ainsi d’envoyer par erreur un message transactionnel indésirable.

   Par exemple, vous avez publié un modèle de message utilisé uniquement pour les campagnes de Noël. Vous pouvez le dépublier une fois la période de Noël terminée et le publier de nouveau l’année suivante.

* En outre, vous ne pouvez pas supprimer un modèle de message transactionnel dont le statut est **[!UICONTROL Publié]**. Vous devez d’abord le dépublier.

>[!NOTE]
>
>Cette fonctionnalité est disponible à partir de la version Campaign 20.2.

Pour dépublier un modèle de message transactionnel, procédez comme décrit ci-dessous.

1. Dans l’instance de pilotage, positionnez-vous au niveau du dossier **[!UICONTROL Message Center > Modèle de messages transactionnels]** dans l’arborescence.
1. Sélectionnez le modèle que vous souhaitez dépublier.
1. Cliquez sur **[!UICONTROL Dépublier]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Cliquez sur **[!UICONTROL Démarrer]**.

![](assets/message-center-unpublish.png)

Le statut du modèle de message transactionnel passe de **[!UICONTROL Publié]** à **[!UICONTROL En édition]**.

Une fois la publication annulée :

* Les deux modèles de message (appliqués aux types d’événements par lot et temps réel) sont supprimés de chaque instance d’exécution.

   Ils n’apparaissent plus dans le dossier **[!UICONTROL Administration > Exploitation > Message Center (Exécution) > Défaut > Modèles de messages transactionnels]** (voir [cette section](../../message-center/using/template-publication.md)).

* Une fois la dépublication d’un modèle effectuée, vous pouvez le supprimer de l’instance de pilotage.

   Pour ce faire, sélectionnez-le dans la liste et cliquez sur le bouton **[!UICONTROL Supprimer]** en haut à droite de l’écran.
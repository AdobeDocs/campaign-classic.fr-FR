---
title: Workflows techniques
seo-title: Workflows techniques
description: Workflows techniques
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Workflows techniques{#technical-workflows}

Vous devez vous assurer que les workflows techniques de l&#39;instance de pilotage et des différentes instances d&#39;exécution sont bien créés et démarrés avant de procéder au déploiement des modèles de messages transactionnels.

Les différents workflows techniques associés aux messages transactionnels (Message Center) sont répartis entre l&#39;instance de pilotage et la ou les instances d&#39;exécution.

## Workflows de l&#39;instance de pilotage {#control-instance-workflows}

Sur l&#39;instance de pilotage, vous devez créer un workflow d&#39;archivage par instance d&#39;exécution. Les workflows d&#39;archivage sont ensuite accessibles à partir du dossier **Administration > Exploitation > Message Center**. Une fois créés, les workflows d&#39;archivage sont automatiquement démarrés.

**Architecture répartie**

Si une ou plusieurs instances d’exécution sont enregistrées, sur l’instance de contrôle, vous devez créer un processus d’archivage pour chaque compte **[!UICONTROL Message Center execution instance]** externe. Cliquez sur le **[!UICONTROL Create the archiving workflow]** bouton pour créer et démarrer le processus.

![](assets/messagecenter_archiving_002.png)

**Architecture minimale**

Une fois les modules de contrôle et d’exécution installés sur la même instance, vous devez créer le processus d’archivage à l’aide de l’assistant de déploiement. Cliquez sur le **[!UICONTROL Create the archiving workflow]** bouton pour créer et démarrer le processus.

![](assets/messagecenter_archiving_001.png)

## Workflows de l&#39;instance d&#39;exécution {#execution-instance-workflows}

Sur la ou les instances d&#39;exécution, les workflows techniques des messages transactionnels sont accessibles depuis le dossier **Administration > Exploitation > Message Center**. Vous devez simplement les démarrer. La liste des workflows est la suivante :

* **[!UICONTROL Processing batch events]** (nom interne : **[!UICONTROL batchEventsProcessing]** ) : ce processus vous permet de ventiler les événements de lot dans une file d’attente avant qu’ils ne soient liés à un modèle de message.
* **[!UICONTROL Processing real time events]** (nom interne : **[!UICONTROL rtEventsProcessing]** ) : ce processus vous permet de ventiler les événements en temps réel dans une file d’attente avant qu’ils ne soient liés à un modèle de message.
* **[!UICONTROL Update event status]** (nom interne : **[!UICONTROL updateEventStatus]** ) : ce processus vous permet d’attribuer un état à l’événement.

   Les statuts d&#39;un événement sont les suivants :

   * **[!UICONTROL Pending]** : l’événement se trouve dans la file d’attente. Aucun modèle de message ne lui a encore été associé.
   * **[!UICONTROL Pending delivery]** : l’événement se trouve dans la file d’attente, un modèle de message lui a été affecté et est en cours de traitement par la remise.
   * **[!UICONTROL Sent]** : cet état est copié à partir des journaux de remise. Cela signifie que la livraison a été envoyée.
   * **[!UICONTROL Ignored by the delivery]** : cet état est copié à partir des journaux de remise. Il signifie que la diffusion a été ignorée.
   * **[!UICONTROL Delivery failed]** : cet état est copié à partir des journaux de remise. Il signifie que la diffusion a échoué.
   * **[!UICONTROL Event not taken into account]** : l&#39;événement n&#39;a pas pu être lié à un modèle de message. L&#39;événement ne sera pas retraité.


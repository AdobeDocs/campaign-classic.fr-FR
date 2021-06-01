---
solution: Campaign Classic
product: campaign
title: Traitement des événements
description: Découvrez comment les événements de messagerie transactionnelle sont traités dans Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: c41ca3d518391a648629ebc3fcd4c916e92c3a79
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 30%

---

# Traitement des événements {#about-event-processing}

Dans le cadre d’un message transactionnel, un événement est généré par un système d’information externe et envoyé à Adobe Campaign via les méthodes **[!UICONTROL PushEvent]** et **[!UICONTROL PushEvents]** (voir [Description de l’événement](../../message-center/using/event-description.md)).

Cet événement contient des données liées à l&#39;événement, telles que son [type](../../message-center/using/creating-event-types.md) (confirmation de commande, création de compte sur un site web, etc.), son adresse email ou son numéro de mobile, ainsi que d&#39;autres informations permettant d&#39;enrichir et de personnaliser le message transactionnel avant sa diffusion (informations de contact du client, langue du message, format de l&#39;email, etc.).

Exemple de données d&#39;un événement :

![](assets/messagecenter_events_request_001.png)

## Étapes de traitement des événements {#event-processing}

Pour traiter les événements de messages transactionnels, les étapes suivantes sont appliquées sur la ou les instances d&#39;exécution :

1. [Collecte des événements](#event-collection)
1. [Acheminement de l&#39;événement vers un modèle de message](#routing-towards-a-template)
1. Enrichissement de l&#39;événement avec des données de personnalisation
1. [Exécution de la diffusion](../../message-center/using/delivery-execution.md)
1. [Recyclage des ](#event-recycling) événements dont la diffusion associée a échoué (via un workflow Adobe Campaign)

Une fois toutes les étapes ci-dessus effectuées via l&#39;instance d&#39;exécution, chaque destinataire ciblé reçoit un message personnalisé.

>[!NOTE]
>
>Pour plus d’informations sur les instances de messagerie transactionnelle, voir [Architecture des messages transactionnels](../../message-center/using/transactional-messaging-architecture.md).


## Collecte des événements {#event-collection}

Les événements générés par le système d&#39;information peuvent être collectés selon deux modes :

* Les appels aux méthodes SOAP permettent de pousser les événements dans Adobe Campaign : La méthode PushEvent permet d&#39;envoyer un événement à la fois, la méthode PushEvents d&#39;envoyer plusieurs événements à la fois. Voir à ce propos [Description de l’événement](../../message-center/using/event-description.md).

* La réalisation d&#39;un workflow permet de récupérer les événements par import de fichier ou via une passerelle SQL (avec l&#39;option [Federated Data Access](../../installation/using/about-fda.md)).

Une fois collectés, les événements sont répartis par les workflows techniques entre les files d&#39;attente temps réel et par lots de la ou des instances d&#39;exécution, en attendant d&#39;être associés à un modèle de message.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Sur les instances d’exécution, les dossiers **[!UICONTROL Événements en temps réel]** ou **[!UICONTROL Événements par lots]** ne doivent pas être définis comme des vues, car cela pourrait entraîner des problèmes de droit d’accès. Pour plus d’informations sur la définition d’un dossier en tant que vue, consultez [cette section](../../platform/using/access-management-folders.md).

## Acheminement vers un modèle {#routing-towards-a-template}

Une fois le modèle de message publié sur la ou les instances d&#39;exécution, deux modèles sont automatiquement générés : l’un à lier à un événement en temps réel, l’autre à lier à un événement batch.

L’étape d’acheminement consiste à lier un événement au modèle de message approprié, en fonction des éléments suivants :

* Type d’événement spécifié dans les propriétés de l’événement lui-même :

   ![](assets/messagecenter_event_type_001.png)

* Type d’événement spécifié dans les propriétés du modèle de message :

   ![](assets/messagecenter_event_type_002.png)

Par défaut, le routage repose sur les informations suivantes :

* Le type d&#39;événement
* Le canal à utiliser (email par défaut)
* Le modèle de diffusion le plus récent, selon la date de publication

## Statuts des événements {#event-statuses}

L&#39;**historique des événements** (sous **[!UICONTROL Message Center]** > **[!UICONTROL Historique des événements]**), regroupe dans une même vue tous les événements traités. Ils peuvent être catégorisés par type d&#39;événement ou par **statut**. Ces statuts sont les suivants :

* **En attente** : L’événement peut être :

   * Un événement qui vient d’être collecté et qui n’a pas encore été traité. La colonne **[!UICONTROL Nombre d&#39;erreurs]** a la valeur 0. Le modèle d&#39;email n&#39;a pas encore été associé.
   * Un événement traité, mais dont la confirmation est erronée. La colonne **[!UICONTROL Nombre d&#39;erreurs]** a une valeur différente de 0. Pour savoir quand cet événement sera traité à nouveau, consultez la colonne **[!UICONTROL Traitement demandé le]**.

* **En attente de diffusion** : L&#39;événement a été traité et le modèle de diffusion est lié. L&#39;email est en attente de diffusion et le processus de diffusion classique est appliqué. Pour plus d&#39;informations, vous pouvez ouvrir la  [diffusion](../../delivery/using/about-message-tracking.md).
* **Envoyé**,  **** Ignoré et  **Erreur de diffusion** : Ces statuts de diffusion sont récupérés via le workflow  **** updateEventsStatus . Pour plus d&#39;informations, vous pouvez ouvrir la diffusion correspondante.
* **Événement non pris en charge** : La phase de routage des messages transactionnels a échoué. Par exemple, Adobe Campaign n’a pas trouvé l’email qui sert de modèle pour l’événement.
* **Evénement expiré** : Le nombre maximal de tentatives d’envoi a été atteint. L’événement est considéré comme nul.

## Recyclage de l&#39;événement {#event-recycling}

Si l&#39;envoi d&#39;un message sur un canal spécifique échoue, Adobe Campaign peut renvoyer le message en utilisant un autre canal. Par exemple, si l&#39;envoi d&#39;un message sur le canal SMS échoue, le message est renvoyé en utilisant le canal email.

Pour cela, vous devez paramétrer un workflow qui recrée tous les événements dont le statut est **Erreur de diffusion**, et leur assigner un canal différent de celui utilisé précédemment.

>[!CAUTION]
>
>Cette étape ne peut être réalisée qu&#39;à l&#39;aide d&#39;un workflow et est donc réservée à des utilisateurs experts. Pour plus d’informations, contactez votre chargé de compte d’Adobe.
---
title: A propos des messages transactionnels
seo-title: A propos des messages transactionnels
description: A propos des messages transactionnels
seo-description: null
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 833907c7a7b84b94a00b131738c73ff54a744a40

---


# A propos des messages transactionnels{#about-transactional-messaging}

Les messages transactionnels (Message Center) sont un module de gestion des messages transactionnels de Campaign. Ces messages (factures, confirmation de commande, changement de mot de passe ou création d&#39;un compte sur un site web par exemple) sont générés à partir des événements déclenchés depuis des systèmes d&#39;information.

>[!CAUTION]
>
>La messagerie transactionnelle nécessite une licence spécifique. Veuillez vérifier votre contrat de licence.

Le module Message Center d&#39;Adobe Campaign s&#39;intègre à un système d&#39;information qui lui envoie des événements destinés à être transformés en messages transactionnels personnalisés. Ces messages peuvent être envoyés à l&#39;unité ou en lot via email, SMS ou notifications push.

Dans cette architecture spécifique, l&#39;instance d&#39;exécution est séparée de l&#39;instance de pilotage, ce qui offre une plus grande disponibilité et une meilleure gestion de la charge.

>[!NOTE]
>
>Pour créer des utilisateurs pour les instances d&#39;exécution Message Center hébergées sur Adobe Cloud, vous devez contacter l&#39;assistance client Adobe. Les utilisateurs de Message Center sont des opérateurs spécifiques qui nécessitent des permissions dédiées pour accéder aux dossiers &#39;Evénements temps réel&#39; (nmsRtEvent).

---
solution: Campaign Classic
product: campaign
title: A propos des messages transactionnels
description: 'Envoyer des messages de déclenchement en fonction des événements générés à partir de systèmes d''information. '
audience: message-center
content-type: reference
topic-tags: introduction
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '164'
ht-degree: 100%

---


# A propos des messages transactionnels{#about-transactional-messaging}

Les messages transactionnels (Message Center) sont un module de gestion des messages transactionnels de Campaign. Ces messages (factures, confirmation de commande, changement de mot de passe ou création d&#39;un compte sur un site web par exemple) sont générés à partir des événements déclenchés depuis des systèmes d&#39;information.

>[!IMPORTANT]
>
>Les messages transactionnels nécessitent une licence spécifique. Veuillez vérifier votre accord de licence.

Le module Message Center d&#39;Adobe Campaign s&#39;intègre à un système d&#39;information qui lui envoie des événements destinés à être transformés en messages transactionnels personnalisés. Ces messages peuvent être envoyés à l&#39;unité ou en lot via email, SMS ou notifications push.

Dans cette architecture spécifique, l&#39;instance d&#39;exécution est séparée de l&#39;instance de pilotage, ce qui offre une plus grande disponibilité et une meilleure gestion de la charge.

>[!NOTE]
>
>Pour créer des utilisateurs pour les instances d&#39;exécution Message Center hébergées sur Adobe Cloud, vous devez contacter l&#39;Assistance clientèle d&#39;Adobe. Les utilisateurs de Message Center sont des opérateurs spécifiques qui nécessitent des permissions dédiées pour accéder aux dossiers &#39;Evénements temps réel&#39; (nmsRtEvent).

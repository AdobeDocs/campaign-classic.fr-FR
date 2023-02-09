---
product: campaign
title: Tracking et surveillance des messages
description: Découvrez comment effectuer le tracking et la surveillance des messages
feature: Monitoring
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 100%

---

# Tracker et suivre vos diffusions {#track-and-monitor}

![](../../assets/common.svg)

Vous avez cliqué sur le bouton **Envoyer** ? Voyons maintenant ce qui se passe. Une fois la diffusion envoyée, Adobe Campaign vous permet de conserver une trace des messages envoyés et de découvrir la réaction des destinataires face à votre diffusion. Vous pourrez ainsi améliorer les prochains envois et optimiser vos campagnes suivantes.

## Surveillance des diffusions {#monitoring-deliveries}

Pour contrôler vos campagnes, vous devez vérifier que le message a bien été délivré à vos destinataires.

Depuis le tableau de bord des diffusions de Campaign, vous pouvez vérifier les messages traités et consulter les logs d’audit de diffusion.
Vous pouvez également contrôler le statut des messages dans les logs de diffusion. [En savoir plus](about-delivery-monitoring.md).

Que faire si les diffusions ne sont pas envoyées et restent dans un état **En attente** ?

* Le processus d&#39;exécution attend la disponibilité de certaines ressources. Le MTA n&#39;a peut-être pas été démarré.
Vérifiez que vos modules mta@instance sont lancés sur vos serveurs MTA et démarrez le module MTA si nécessaire. [En savoir plus](../../production/using/administration.md).

* La diffusion peut utiliser une affinité qui n&#39;a pas été configurée sur l&#39;instance d&#39;envoi.
Conseil : vérifiez la configuration relative à la gestion du trafic (affinité IP). Pour plus d&#39;informations, consultez la section Contrôle du trafic SMTP sortant.

>[!NOTE]
>
>Ces étapes ne peuvent être effectuées que par un utilisateur expert.

## Tracking du comportement {#track-behaviour}

Pour mieux connaître le comportement de vos destinataires, vous pouvez suivre leur réaction à une diffusion : réception, ouverture, clics sur des liens, désabonnements, etc. Dans Campaign Classic, ces informations figurent dans l’onglet Tracking des destinataires ciblés par la diffusion et dans l’onglet Tracking de la diffusion.

**Conseil** : le tracking des messages est activé par défaut. Pour configurer les URL, sélectionnez lʼoption Afficher les URL, située dans la section inférieure de l’assistant de diffusion. Pour chaque URL du message, vous pouvez choisir dʼactiver ou non le tracking.

Pour en savoir plus à ce sujet, consultez la section [Configuration du tracking](how-to-configure-tracked-links.md) et la description des [Indicateurs de tracking](../../reporting/using/delivery-reports.md#tracking-indicators).

## Performances des diffusions {#delivery-performances}

Pour mesurer la vitesse à laquelle les messages sont diffusés, vous pouvez contrôler le débit de diffusion. Les critères constituent le nombre de messages diffusés par heure et la taille des messages, en bits par seconde. Pour plus d&#39;informations, consultez la section [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput).

**Conseils** :

* Ne gardez pas les diffusions en échec sur l&#39;instance, car cela conserve les tables temporaires et a un impact sur les performances.

* Supprimez les diffusions qui ne sont plus nécessaires et les destinataires inactifs de la base pour conserver la qualité des adresses.

* N&#39;essayez pas de planifier des diffusions volumineuses ensemble. 5 à 10 minutes sont nécessaires pour répartir la charge uniformément sur le système.

## Résolution des problèmes liés aux diffusions {#delivery-troubleshooting}

Des actions spécifiques peuvent être effectuées en cas de problèmes liés aux diffusions :

* [Problèmes de délivrabilité](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problèmes liés à l&#39;affichage des images](../../production/using/image-display-issues.md)

* [Problèmes de performances des diffusions](delivery-performances.md)

* [Problèmes de fichiers temporaires](../../production/using/temporary-files.md) - *clients On-premise uniquement*

---
title: Tracking et surveillance des messages
seo-title: Tracking et surveillance des messages
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: ht
source-wordcount: '448'
ht-degree: 100%

---


# Tracker et suivre vos diffusions {#track-and-monitor}

Vous avez cliqué sur le bouton Envoyer ? Voyons maintenant ce qui se passe. Une fois la diffusion envoyée, Adobe Campaign vous permet de conserver une trace des messages envoyés et de découvrir la réaction des destinataires face à votre diffusion. Vous pourrez ainsi améliorer les prochains envois et optimiser vos campagnes suivantes.

## Surveillance des diffusions {#monitoring-deliveries}

Pour contrôler vos campagnes, vous devez vérifier que le message a bien été délivré à vos destinataires.

Depuis le tableau de bord des diffusions de Campaign, vous pouvez vérifier les messages traités et consulter les logs d’audit de diffusion.
Vous pouvez également contrôler le statut des messages dans les logs de diffusion. [En savoir plus](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Que faire si les diffusions ne sont pas envoyées et restent dans un état **En attente** ?

* Le processus d&#39;exécution attend la disponibilité de certaines ressources. Le MTA n&#39;a peut-être pas été démarré.
Vérifiez que vos modules mta@instance sont lancés sur vos serveurs MTA et démarrez le module MTA si nécessaire. [En savoir plus](../../production/using/administration.md).

* La diffusion peut utiliser une affinité qui n&#39;a pas été configurée sur l&#39;instance d&#39;envoi.
Conseil : vérifiez la configuration relative à la gestion du trafic (affinité IP). Voir à ce propos la section Contrôle du trafic SMTP sortant.

>[!NOTE]
>
>Ces étapes ne peuvent être effectuées que par un utilisateur expert.

## Tracking {#tracking-deliveries}

Pour mieux connaître le comportement de vos destinataires, vous pouvez suivre leur réaction à une diffusion : réception, ouverture, clics sur des liens, désabonnements, etc. Dans Campaign Classic, ces informations figurent dans l’onglet Tracking des destinataires ciblés par la diffusion et dans l’onglet Tracking de la diffusion. Dans Campaign Standard, elles sont affichées dans l’onglet Logs de tracking de la diffusion.

**Conseil** : Le tracking des messages est activé par défaut. Pour paramétrer les URL, sélectionnez l&#39;option Afficher les URL, située dans la section inférieure de l’assistant de diffusion. Pour chaque URL du message, vous pouvez choisir d&#39;activer ou non le tracking.

Pour plus d&#39;informations, reportez-vous à la section [Configuration du tracking](../../delivery/using/how-to-configure-tracked-links.md) et à la description des [Indicateurs de tracking](../../reporting/using/delivery-reports.md#tracking-indicators).

## Performances des diffusions {#delivery-performances}

Pour mesurer la vitesse à laquelle les messages sont diffusés, vous pouvez contrôler le débit de diffusion. Les critères constituent le nombre de messages diffusés par heure et la taille des messages, en bits par seconde. Voir à ce propos la section [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput).

**Conseils** :

* Ne gardez pas les diffusions en échec sur l&#39;instance, car cela conserve les tables temporaires et a un impact sur les performances.

* Supprimez les diffusions qui ne sont plus nécessaires et les destinataires inactifs de la base pour conserver la qualité des adresses.

* N&#39;essayez pas de planifier des diffusions volumineuses ensemble. 5 à 10 minutes sont nécessaires pour répartir la charge uniformément sur le système.

## Résolution des problèmes liés aux diffusions {#delivery-troubleshooting}

Des actions spécifiques peuvent être effectuées en cas de problèmes liés aux diffusions :

* [Problèmes de délivrabilité](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problèmes liés à l’affichage des images](../../production/using/image-display-issues.md)

* [Problèmes de performances des diffusions](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problèmes de fichiers temporaires](../../production/using/temporary-files.md) - *clients On-premise uniquement*

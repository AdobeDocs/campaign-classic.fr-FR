---
title: Suivi et surveillance des messages
seo-title: Suivi et surveillance des messages
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
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 56%

---


# Trackez et suivez vos diffusions {#track-and-monitor}

Vous avez cliqué sur le bouton Envoyer ? Voyons maintenant ce qui se passe. Une fois la diffusion envoyée, Adobe Campaign vous permet de conserver une trace des messages envoyés et de découvrir la réaction des destinataires face à votre diffusion. Cela vous permettra d&#39;améliorer l&#39;envoi futur et d&#39;optimiser vos prochaines campagnes.

## Surveillance des diffusions {#monitoring-deliveries}

Pour contrôler vos campagnes, vous devez vérifier que le message a bien été délivré à vos destinataires.

Depuis le tableau de bord de diffusion Campaign, vous pouvez vérifier les messages traités et les journaux d&#39;audit des diffusions.
Vous pouvez également contrôler le statut des messages dans les logs de diffusion. [En savoir plus](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Que faire si les diffusions ne sont pas envoyées et restent dans un état **En attente** ?

* Le processus d&#39;exécution attend la disponibilité de certaines ressources. Le MTA n&#39;a peut-être pas été démarré.
Vérifiez que vos mta@instance de données sont lancés sur vos serveurs MTA et début le module MTA si nécessaire. [En savoir plus](../../production/using/administration.md).

* La diffusion peut utiliser une affinité qui n&#39;a pas été configurée sur l&#39;instance d&#39;envoi.
Conseil : Vérifiez la configuration relative à la gestion du trafic (affinité IP). Voir à ce propos la section Contrôle du trafic SMTP sortant.

>[!NOTE]
>
>Ces étapes ne peuvent être effectuées que par un utilisateur expert.

## Effectuer un tracking {#tracking-deliveries}

Pour mieux connaître le comportement de vos destinataires, vous pouvez suivre leur réaction à une diffusion : réception, ouverture, clics sur des liens, désinscriptions, etc. En Campaign Classic, ces informations s’affichent dans l’onglet Suivi des destinataires ciblés par la diffusion et dans l’onglet Suivi de la diffusion. En Campaign Standard, il s’affiche dans l’onglet Logs de tracking de la diffusion.

**Conseil**: Le suivi des messages est activé par défaut. Pour configurer les URL, sélectionnez l’option Afficher les URL dans la section inférieure de l’assistant de diffusion. Pour chaque URL du message, vous pouvez choisir d’activer ou non le suivi.

Pour plus d&#39;informations, reportez-vous à la section [Configuration du suivi](../../delivery/using/how-to-configure-tracked-links.md) et à la description des indicateurs [de](../../reporting/using/delivery-reports.md#tracking-indicators) suivi.

## Performances des diffusions {#delivery-performances}

Pour mesurer la vitesse à laquelle les messages sont diffusés, vous pouvez contrôler le débit de diffusion. Les critères constituent le nombre de messages diffusés par heure et la taille des messages, en bits par seconde. Voir à ce propos la section [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput).

**Conseils**:

* Ne gardez pas les diffusions en échec sur l&#39;instance, car cela conserve les tables temporaires et a un impact sur les performances.

* Supprimez les diffusions qui ne sont plus nécessaires et les destinataires inactifs de la base pour conserver la qualité des adresses.

* N&#39;essayez pas de planifier des diffusions volumineuses ensemble. 5 à 10 minutes sont nécessaires pour répartir la charge uniformément sur le système.

## Dépannage de la diffusion {#delivery-troubleshooting}

Des actions spécifiques peuvent être exécutées en cas de problème avec des diffusions :

* [Problèmes de délivrabilité](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problèmes liés à l’affichage des images](../../production/using/image-display-issues.md)

* [Problèmes de performances des diffusions](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problèmes](../../production/using/temporary-files.md) de fichiers temporaires - clients *sur site uniquement*

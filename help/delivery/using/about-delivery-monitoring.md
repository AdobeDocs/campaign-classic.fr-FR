---
product: campaign
title: Prise en main de la surveillance des diffusions
description: Découvrez les fonctionnalités de surveillance des diffusions dans Campaign Classic
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: e60a8391416bc9899548971bddb61705467a80e5
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 64%

---

# Prise en main de la surveillance des diffusions {#about-delivery-monitoring}

>[!IMPORTANT]
>
>Cette page présente les fonctionnalités de surveillance spécifiques à Campaign Classic v7 **pour les déploiements hybrides et on-premise.**

## Fonctionnalités de surveillance

### Suivre des diffusions {#monitoring-deliveries}

**Pour les déploiements hybrides/on-premise de Campaign Classic v7**, une surveillance supplémentaire est requise pour les ressources du serveur et la configuration du MTA (Mail Transfer Agent).

#### Résolution des problèmes liés aux diffusions en attente {#pending-deliveries}

Que faire si les diffusions ne sont pas envoyées et restent dans un état **En attente** ?

* Le processus d&#39;exécution attend la disponibilité de certaines ressources. Le MTA n&#39;a peut-être pas été démarré.
Vérifiez que vos modules mta@instance sont lancés sur vos serveurs MTA et démarrez le module MTA si nécessaire. [En savoir plus](../../production/using/administration.md).

* La diffusion peut utiliser une affinité qui n&#39;a pas été configurée sur l&#39;instance d&#39;envoi.
Conseil : vérifiez la configuration relative à la gestion du trafic (affinité IP). Pour plus d&#39;informations, consultez la section Contrôle du trafic SMTP sortant.

>[!NOTE]
>
>Ces étapes ne peuvent être effectuées que par un utilisateur expert sur les installations on-premise.

### Surveillance de la délivrabilité {#deliverability-monitoring}

#### Installation du package de délivrabilité {#deliverability-package}

Cette fonctionnalité est disponible via un package dédié dans Adobe Campaign. Pour l’utiliser, ce package doit être installé. Une fois linstallation terminée, redémarrez le serveur pour que le package soit pris en compte.

* Pour les clients hébergés et hybrides, la **supervision de la délivrabilité** est configurée sur votre instance par l&#39;assistance technique et les consultants d&#39;Adobe. Pour plus d&#39;informations, contactez votre chargé de compte Adobe.

* Pour les installations on-premise, vous devez installer le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** via le menu **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Import de package]**. Pour plus d&#39;informations, consultez la section [Installer des packages standard Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

#### Workflow de délivrabilité {#deliverability-workflow}

Dans Adobe Campaign Classic, la **supervision de la délivrabilité** est gérée par le workflow **[!UICONTROL Mise à jour pour la délivrabilité]**. Il est installé par défaut sur toutes les instances et permet d’initialiser la liste des règles de qualification des e-mails rejetés, la liste des domaines et la liste des MX. Une fois le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** installé, ce workflow s’exécute de nuit pour mettre à jour régulièrement la liste des règles et vous permettre de gérer activement la délivrabilité des plateformes.

**Le package Délivrabilité vous donne accès à :**

* [Rapport Inbox rendering](inbox-rendering.md), qui permet la prévisualisation de vos messages sur les principaux clients de messagerie afin d’analyser le contenu et la réputation.
* Vue d’ensemble de la qualité des messages (boîte de réception, spam).

#### Outils de surveillance {#monitoring-tools}

**Pour les installations on-premise** vous pouvez utiliser les outils de surveillance suivants :

* Rapport **[!UICONTROL Débit de diffusion]**, qui donne une vue d’ensemble du débit global de la plateforme pour une période donnée. Voir à ce propos [cette section](../../reporting/using/global-reports.md#delivery-throughput).
* Chaque diffusion génère un rapport de statistiques de diffusion pour les différents fournisseurs d’accès à internet (FAI). Il présente certaines mesures de réputation et de qualité des données qui peuvent avoir un impact sur votre délivrabilité, notamment les chiffres suivants :
   * **[!UICONTROL Rebonds définitifs]**, qui indiquent la qualité des données. Ce chiffre doit être inférieur à 2 %.
   * **[!UICONTROL Rebonds temporaires]**, qui indiquent la réputation. Cette valeur ne doit pas être supérieure à 10 % pour un fournisseur d’accès à internet donné.

  Pour plus d&#39;informations, consultez la section [Statistiques de diffusion](../../reporting/using/global-reports.md#delivery-statistics).

#### Instructions de surveillance {#monitoring-guidelines}

**Pour les installations on-premise** voici quelques instructions supplémentaires pour le suivi de la délivrabilité :

* Vérifiez régulièrement le [débit des diffusions](../../reporting/using/global-reports.md#delivery-throughput) pour l’ensemble de la plateforme afin de contrôler qu’il correspond à la configuration d’origine.
* Vérifiez que les [reprises](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) sont paramétrées correctement (30 minutes pour la période des reprises et plus de 20 reprises) dans les modèles de diffusion.
* Vérifiez régulièrement que la boîte des [emails rebonds](understanding-delivery-failures.md#bounce-mail-management) est accessible et que le compte n’arrive pas à expiration.
* Vérifiez chaque débit de diffusion, accessible à partir du [tableau de bord de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}, pour vous assurer qu’il correspond à la validité du contenu de la diffusion (par exemple, les ventes Flash doivent être diffusées en quelques minutes et non en plusieurs jours).
* Lors de l’utilisation des vagues, vérifiez que chaque vague a le temps de se terminer avant le déclenchement de la suivante.
* Vérifiez que le nombre d’erreurs et les nouvelles [mises en quarantaine](understanding-quarantine-management.md) correspondent aux autres diffusions.
* Consultez attentivement les [logs de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} pour déterminer le type des erreurs indiquées (listes bloquées, problèmes liés aux DNS, règles anti-spam, etc.).

### Résolution des problèmes {#delivery-troubleshooting}

Des actions spécifiques peuvent être effectuées lorsque vous rencontrez des problèmes avec les diffusions sur les **déploiements hybrides/on-premise** :

* [Problèmes de délivrabilité](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problèmes liés à l&#39;affichage des images](../../production/using/image-display-issues.md)
* [Problèmes de performances des diffusions](delivery-performance-troubleshooting.md)
* [Problèmes de fichiers temporaires](../../production/using/temporary-files.md) - *clients On-premise uniquement*

## Surveillance de vos diffusions

Les ressources suivantes vous aideront à surveiller et à suivre les performances de vos diffusions dans Campaign Classic v7 :

### Accès au tableau de bord de la diffusion

Découvrez comment accéder aux listes de diffusion et utiliser le tableau de bord des diffusions pour surveiller votre activité d’envoi :

* [Surveiller les diffusions dans l’interface utilisateur de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (la documentation de Campaign v8 s’applique aux versions 7 et 8)
* [Statuts des diffusions](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentation de Campaign v8)
* [Avancé : personnalisation des logs de diffusion](customize-delivery-logs.md) (v7 hybride/on-premise uniquement - extension de schéma)

### Suivi des interactions des messages

Suivez les ouvertures, les clics et les interactions des destinataires avec vos diffusions :

* [Documentation sur le tracking des messages](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (documentation de Campaign v8 - s’applique aux versions 7 et 8)
* [Configuration des liens trackés](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (documentation de Campaign v8)
* [Accéder aux logs de tracking](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (documentation de Campaign v8)

### Optimisation des performances de diffusion

Bonnes pratiques et résolution des problèmes de performances de diffusion :

* [Bonnes pratiques de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentation de Campaign v8 - s’applique aux versions 7 et 8)
* [Performances de diffusion et dépannage](delivery-performance-troubleshooting.md) (configurations hybrides v7/spécifiques à on-premise)

### Présentation des échecs et des quarantaines

Gérez les diffusions en échec, les e-mails bounce et les adresses en quarantaine :

* [Comprendre les échecs de diffusion](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentation de Campaign v8 - guide complet pour les versions 7 et 8)
* [Gestion des quarantaines](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentation de Campaign v8 - guide complet pour les versions 7 et 8)
* [Échecs de diffusion et configuration de la quarantaine](delivery-failures-quarantine.md) (configurations hybrides v7/spécifiques à on-premise)

---
solution: Campaign Classic
product: campaign
title: Supervision de la délivrabilité dans Adobe Campaign Classic
description: Découvrez les outils et les directives concernant la supervision de la délivrabilité dans Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 88%

---


# Contrôle de la délivrabilité{#monitoring-deliverability}

Vous trouverez ci-dessous des détails sur les différents outils de surveillance fournis par Adobe Campaign, ainsi que des directives supplémentaires sur l&#39;exploitation des fonctionnalités offertes par Adobe Campaign pour surveiller la délivrabilité de votre plateforme.

## Supervision de la délivrabilité {#configuration}

Cette fonctionnalité est disponible via un package dédié dans Adobe Campaign. Pour l’utiliser, ce package doit être installé. Une fois l&#39;installation terminée, redémarrez le serveur pour que le package soit pris en compte.
* Pour les clients hébergés et hybrides, la **supervision de la délivrabilité** est configurée sur votre instance par l&#39;assistance technique et les consultants d&#39;Adobe. Pour plus d&#39;informations, contactez votre chargé de compte Adobe.

* Pour les installations on-premise, vous devez installer le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** via le menu **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Import de package]**. Pour plus d&#39;informations, voir la section [Installer des packages standard Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

Dans Adobe Campaign Classic, la **supervision de la délivrabilité** est gérée par le workflow **[!UICONTROL Mise à jour pour la délivrabilité]**. Il est installé par défaut sur toutes les instances et permet d&#39;initialiser la liste des règles de qualification des emails bounce, la liste des domaines et la liste des MX. Une fois le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** installé, ce workflow s&#39;exécute de nuit pour mettre à jour régulièrement la liste des règles et vous permettre de gérer activement la délivrabilité des plateformes.

Le package Délivrabilité vous donne accès aux informations suivantes :

* [Rapport Inbox rendering](../../delivery/using/inbox-rendering.md), qui permet la prévisualisation de vos messages sur les principaux clients de messagerie afin d’analyser le contenu et la réputation.
* Vue d’ensemble de la qualité des messages (boîte de réception, spam).

## Outils de monitoring {#monitoring-tools}

Vous pouvez également utiliser les outils suivants :

* Rapport **[!UICONTROL Débit de diffusion]**, qui donne une vue d’ensemble du débit global de la plateforme pour une période donnée. Voir à ce propos [cette section](../../reporting/using/global-reports.md#delivery-throughput).
* Chaque diffusion génère un rapport de statistiques de diffusion pour les différents fournisseurs d’accès à internet (FAI). Il présente certaines mesures de réputation et de qualité des données qui peuvent avoir un impact sur votre délivrabilité, notamment les chiffres suivants :
   * **[!UICONTROL Erreurs hard]**, qui indiquent la qualité des données. Ce chiffre doit être inférieur à 2 %.
   * **[!UICONTROL Erreurs soft]** qui indiquent la réputation. Cette valeur ne doit pas être supérieure à 10 % pour un fournisseur d’accès à internet donné.

   Voir à ce propos la section [Statistiques de diffusion](../../reporting/using/global-reports.md#delivery-statistics).
* Plus généralement, le [tableau de bord des diffusions](../../delivery/using/about-delivery-monitoring.md) donne accès aux éléments suivants :
   * [Synthèse des diffusions](../../delivery/using/delivery-dashboard.md#delivery-summary), qui indique le détail de l’envoi et le nombre de messages à envoyer, traités et envoyés avec succès.
   * [Logs et historique de la diffusion](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history), qui montrent les cibles exclues et le motif d’exclusion.
   * [Logs de tracking](../../delivery/using/delivery-dashboard.md#tracking-logs), qui affichent les informations de tracking, telles que les ouvertures et les clics.

## Directives de supervision {#monitoring-guidelines}

Voici quelques directives supplémentaires concernant la supervision de la délivrabilité :

* Vérifiez régulièrement le [débit des diffusions](../../reporting/using/global-reports.md#delivery-throughput) pour l’ensemble de la plateforme afin de contrôler qu’il correspond à la configuration d’origine.
* Vérifiez que les [reprises](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) sont paramétrées correctement (30 minutes pour la période des reprises et plus de 20 reprises) dans les modèles de diffusion.
* Vérifiez régulièrement que la boîte des [emails rebonds](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) est accessible et que le compte n’arrive pas à expiration.
* Vérifiez le débit de chaque diffusion, accessible à partir du [tableau de bord de diffusion](../../delivery/using/delivery-dashboard.md), pour vous assurer qu&#39;il est conforme à la validité du contenu de la diffusion (par ex. Les &quot;ventes Flash&quot; doivent être livrées en minutes et non en jours).
* Lors de l’utilisation des [vagues](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), vérifiez que chaque vague a le temps de se terminer avant le déclenchement de la suivante.
* Vérifiez que le nombre d’erreurs et les [mises en quarantaine](../../delivery/using/understanding-quarantine-management.md) correspondent aux autres diffusions.
* Consultez attentivement les [logs de diffusion](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) pour déterminer le type des erreurs indiquées (listes bloquées, problèmes liés aux DNS, règles anti-spam, etc.).

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->

---
product: campaign
title: Surveiller la délivrabilité dans Adobe Campaign
description: Découvrez les outils et les instructions concernant la surveillance de la délivrabilité dans Adobe Campaign.
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 100%

---

# Suivi de votre délivrabilité{#monitoring-deliverability}



Vous trouverez ci-dessous des détails sur les différents outils de surveillance fournis par Adobe Campaign, ainsi que des directives supplémentaires sur l’exploitation des fonctionnalités offertes par Adobe Campaign pour surveiller la délivrabilité de votre plateforme.

## A propos du suivi de la délivrabilité {#about-deliverability-monitoring}

Cette fonctionnalité est disponible via un package dédié dans Adobe Campaign. Pour l’utiliser, ce package doit être installé. Une fois l&#39;installation terminée, redémarrez le serveur pour que le package soit pris en compte.
* Pour les clients hébergés et hybrides, la **supervision de la délivrabilité** est configurée sur votre instance par l&#39;assistance technique et les consultants d&#39;Adobe. Pour plus d&#39;informations, contactez votre chargé de compte Adobe.

* Pour les installations on-premise, vous devez installer le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** via le menu **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Import de package]**. Pour plus dʼinformations, consultez la section [Installation de packages standard Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

Dans Adobe Campaign Classic, la **supervision de la délivrabilité** est gérée par le workflow **[!UICONTROL Mise à jour pour la délivrabilité]**. Il est installé par défaut sur toutes les instances et permet d&#39;initialiser la liste des règles de qualification des emails bounce, la liste des domaines et la liste des MX. Une fois le package **[!UICONTROL Supervision de la délivrabilité (Email Deliverability)]** installé, ce workflow s&#39;exécute de nuit pour mettre à jour régulièrement la liste des règles et vous permettre de gérer activement la délivrabilité des plateformes.

Le package Délivrabilité vous donne accès aux informations suivantes :

* [Rapport Inbox rendering](inbox-rendering.md), qui permet la prévisualisation de vos messages sur les principaux clients de messagerie afin d’analyser le contenu et la réputation.
* Vue d’ensemble de la qualité des messages (boîte de réception, spam).

## Outils de surveillance {#monitoring-tools}

Vous pouvez également utiliser les outils suivants :

* Rapport **[!UICONTROL Débit de diffusion]**, qui donne une vue d’ensemble du débit global de la plateforme pour une période donnée. Voir à ce propos [cette section](../../reporting/using/global-reports.md#delivery-throughput).
* Chaque diffusion génère un rapport de statistiques de diffusion pour les différents fournisseurs d’accès à internet (FAI). Il présente certaines mesures de réputation et de qualité des données qui peuvent avoir un impact sur votre délivrabilité, notamment les chiffres suivants :
   * **[!UICONTROL Erreurs hard]**, qui indiquent la qualité des données. Ce chiffre doit être inférieur à 2 %.
   * **[!UICONTROL Erreurs soft]** qui indiquent la réputation. Cette valeur ne doit pas être supérieure à 10 % pour un fournisseur d’accès à internet donné.

  Pour plus d&#39;informations, consultez la section [Statistiques de diffusion](../../reporting/using/global-reports.md#delivery-statistics).
* Plus généralement, le [tableau de bord des diffusions](about-delivery-monitoring.md) donne accès aux éléments suivants :
   * [Synthèse des diffusions](delivery-dashboard.md#delivery-summary), qui indique le détail de l’envoi et le nombre de messages à envoyer, traités et envoyés avec succès.
   * [Logs et historique de la diffusion](delivery-dashboard.md#delivery-logs-and-history), qui montrent les cibles exclues et le motif d’exclusion.
   * [Logs de tracking](delivery-dashboard.md#tracking-logs), qui affichent les informations de tracking, telles que les ouvertures et les clics.

## Instructions de surveillance {#monitoring-guidelines}

Voici quelques directives supplémentaires concernant la supervision de la délivrabilité :

* Vérifiez régulièrement le [débit des diffusions](../../reporting/using/global-reports.md#delivery-throughput) pour l’ensemble de la plateforme afin de contrôler qu’il correspond à la configuration d’origine.
* Vérifiez que les [reprises](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) sont paramétrées correctement (30 minutes pour la période des reprises et plus de 20 reprises) dans les modèles de diffusion.
* Vérifiez régulièrement que la boîte des [emails rebonds](understanding-delivery-failures.md#bounce-mail-management) est accessible et que le compte n’arrive pas à expiration.
* Vérifiez chaque débit de diffusion, accessible à partir du [tableau de bord de diffusion](delivery-dashboard.md), pour vous assurer qu’il correspond à la validité du contenu de la diffusion (par exemple, les ventes Flash doivent être diffusées en quelques minutes et non en plusieurs jours).
* Lors de l’utilisation des [vagues](steps-sending-the-delivery.md#sending-using-multiple-waves), vérifiez que chaque vague a le temps de se terminer avant le déclenchement de la suivante.
* Vérifiez que le nombre d’erreurs et les [mises en quarantaine](understanding-quarantine-management.md) correspondent aux autres diffusions.
* Consultez attentivement les [logs de diffusion](delivery-dashboard.md#delivery-logs-and-history) pour déterminer le type des erreurs indiquées (listes bloquées, problèmes liés aux DNS, règles anti-spam, etc.).

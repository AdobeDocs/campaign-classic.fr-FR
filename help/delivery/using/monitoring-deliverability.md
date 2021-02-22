---
solution: Campaign Classic
product: campaign
title: Supervision de la délivrabilité dans Adobe Campaign Classic
description: Découvrez les outils et les directives concernant la supervision de la délivrabilité dans Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: fa5679d91808edb8e3916d5f0e0f54c73198e934
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---


# Contrôle de la délivrabilité{#monitoring-deliverability}

Vous trouverez ci-dessous des informations détaillées sur les différents outils de monitoring d’Adobe Campaign ainsi qu’un certain nombre de directives supplémentaires concernant la supervision de la délivrabilité.

## Outils de monitoring {#monitoring-tools}

Utilisez les outils proposés par Adobe Campaign pour superviser la délivrabilité de votre plateforme.

Le package Délivrabilité vous donne accès aux informations suivantes :

* [Rapport Inbox rendering](../../delivery/using/inbox-rendering.md), qui permet la prévisualisation de vos messages sur les principaux clients de messagerie afin d’analyser le contenu et la réputation.
* Vue d’ensemble de la qualité des messages (boîte de réception, spam).

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
* Vérifiez chaque débit de diffusion pour vous assurer qu&#39;il correspond à la validité du contenu de la diffusion (par exemple, les ventes Flash doivent être diffusées en quelques minutes et non en plusieurs jours).
* Lors de l’utilisation des [vagues](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), vérifiez que chaque vague a le temps de se terminer avant le déclenchement de la suivante.
* Vérifiez que le nombre d’erreurs et les [mises en quarantaine](../../delivery/using/understanding-quarantine-management.md) correspondent aux autres diffusions.
* Consultez attentivement les [logs de diffusion](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) pour déterminer le type des erreurs indiquées (listes bloquées, problèmes liés aux DNS, règles anti-spam, etc.).

## Signal Spam {#signal-spam}

Signal Spam est un service français qui propose un reporting de rétroaction anonyme pour les FAI français (Orange, SFR).

* Ce service permet de suivre la réputation des FAI français et l’évolution de l’activité des clients.

* Signal Spam fournit permet également aux utilisateurs finaux de déposer des plaintes directes via une interface dédiée. Ces plaintes sont ensuite mises en quarantaine dans la base de données des adresses email.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) est une solution de monitoring complémentaire des outils internes de délivrabilité d&#39;Adobe. Elle produit des listes bloquées de domaines et d&#39;adresses IP et des indicateurs de réputation.

Les informations fournies sont disponibles en temps réel, ce qui permet une assistance proactive.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->

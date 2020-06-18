---
title: Supervision de la délivrabilité dans Adobe Campaign Classic
description: Découvrez les outils et les directives concernant la supervision de la délivrabilité dans Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7c040ceffcce20805d7cc8d1e4e46c77e611056
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 91%

---


# Contrôle de la délivrabilité{#monitoring-deliverability}

Vous trouverez ci-dessous des informations détaillées sur les différents outils de monitoring d’Adobe Campaign ainsi qu’un certain nombre de directives supplémentaires concernant la supervision de la délivrabilité.

## Outils de monitoring {#monitoring-tools}

Utilisez les outils proposés par Adobe Campaign pour superviser la délivrabilité de votre plateforme.

Le package Délivrabilité vous donne accès aux informations suivantes :

* Rapport de suivi technique, au jour le jour, des performances de délivrabilité (monitoring technique). Disponible sur demande, ce rapport permet de recevoir un rapport quotidien envoyé par email à une adresse spécifiée. Pour en savoir plus à ce sujet, contactez l’équipe Assistance clientèle d’Adobe.
* [Rapport Inbox rendering](../../delivery/using/inbox-rendering.md), qui permet la prévisualisation de vos messages sur les principaux clients de messagerie afin d’analyser le contenu et la réputation.
* Vue d’ensemble de la qualité des messages (boîte de réception, spam).

Vous pouvez également utiliser les outils suivants :

* Rapport **[!UICONTROL Débit de diffusion]**, qui donne une vue d’ensemble du débit global de la plateforme pour une période donnée. Voir à ce propos [cette section](../../reporting/using/global-reports.md#delivery-throughput).
* Rapport de **[!UICONTROL supervision de la délivrabilité technique]**, qui comprend un certain nombre d’indicateurs de qualité de la délivrabilité pour votre plateforme. Voir à ce propos [cette section](#technical-deliverability-monitoring).
* Chaque diffusion génère un rapport de statistiques de diffusion pour les différents fournisseurs d’accès à internet (FAI). Il présente certaines mesures de réputation et de qualité des données qui peuvent avoir un impact sur votre délivrabilité, notamment les chiffres suivants :
   * **[!UICONTROL Erreurs hard]**, qui indiquent la qualité des données. Ce chiffre doit être inférieur à 2 %.
   * **[!UICONTROL Erreurs soft]** qui indiquent la réputation. Cette valeur ne doit pas être supérieure à 10 % pour un fournisseur d’accès à internet donné.
   Voir à ce propos la section [Statistiques de diffusion](../../reporting/using/global-reports.md#delivery-statistics).
* Plus généralement, le [tableau de bord des diffusions](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) donne accès aux éléments suivants :
   * [Synthèse des diffusions](../../delivery/using/monitoring-a-delivery.md#delivery-summary), qui indique le détail de l’envoi et le [nombre de messages](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent) à envoyer, traités et envoyés avec succès.
   * [Logs et historique de la diffusion](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history), qui montrent les cibles exclues et le motif d’exclusion.
   * [Logs de tracking](../../delivery/using/monitoring-a-delivery.md#tracking-logs), qui affichent les informations de tracking, telles que les ouvertures et les clics.

## Directives de supervision {#monitoring-guidelines}

Voici quelques directives supplémentaires concernant la supervision de la délivrabilité :

* Vérifiez régulièrement le [débit des diffusions](../../reporting/using/global-reports.md#delivery-throughput) pour l’ensemble de la plateforme afin de contrôler qu’il correspond à la configuration d’origine.
* Vérifiez que les [reprises](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) sont paramétrées correctement (30 minutes pour la période des reprises et plus de 20 reprises) dans les modèles de diffusion.
* Vérifiez régulièrement que la boîte des [emails rebonds](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) est accessible et que le compte n’arrive pas à expiration.
* Vérifiez chaque débit de diffusion pour vous assurer qu&#39;il correspond à la validité du contenu de la diffusion (par exemple, les ventes Flash doivent être diffusées en quelques minutes et non en plusieurs jours).
* Lors de l’utilisation des [vagues](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), vérifiez que chaque vague a le temps de se terminer avant le déclenchement de la suivante.
* Vérifiez que le nombre d’erreurs et les [mises en quarantaine](../../delivery/using/understanding-quarantine-management.md) correspondent aux autres diffusions.
* Carefully consult the [delivery logs](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) in detail to check the kind of errors that are highlighted (block lists, DNS issues, anti-spam rules, etc.).

## Signal Spam {#signal-spam}

Signal Spam est un service français qui propose un reporting de rétroaction anonyme pour les FAI français (Orange, SFR).

* Ce service permet de suivre la réputation des FAI français et l&#39;évolution de l&#39;activité des clients.

* Signal Spam fournit permet également aux utilisateurs finaux de déposer des plaintes directes via une interface dédiée. Ces plaintes sont ensuite mises en quarantaine dans la base de données des adresses email.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) est une solution complémentaire de surveillance des outils internes de délivrabilité de l&#39;Adobe qui fournit des listes bloquées IP et domaine, et des indicateurs de réputation.

Les informations fournies sont disponibles en temps réel, ce qui permet une assistance proactive.

## Rapport de supervision de la délivrabilité technique {#technical-deliverability-monitoring}

Le rapport de supervision de la délivrabilité technique est mis à jour quotidiennement et disponible en accédant à **[!UICONTROL Surveillance]** > **[!UICONTROL Aperçu]** et en cliquant sur le lien **[!UICONTROL Monitoring technique]** dans l’onglet **[!UICONTROL Accueil]** d’Adobe Campaign. Il comprend plusieurs indicateurs de qualité de la délivrabilité pour votre plateforme.

Ces indicateurs sont mis à jour tous les jours à 9 h.

>[!NOTE]
>
>En complément, vous avez la possibilité de recevoir un rapport quotidien par email à l’adresse souhaitée. Nous vous invitons à nous communiquer cette adresse par email ou via l’Extranet Adobe Campaign.

![](assets/s_tn_del_monitoring.png)

Les indicateurs utilisés dans ce rapport sont les suivants :

* **[!UICONTROL Reverse DNS]** : Adobe Campaign vérifie qu&#39;un reverse DNS est bien renseigné pour une adresse IP et que celui-ci reboucle bien sur l&#39;IP.

* **[!UICONTROL SPF]** (Sender Policy Framework) : mécanisme d’authentification qui permet aux fournisseurs d’accès à Internet et de messagerie de vérifier si l’expéditeur de l’email autorisé sur le domaine d’envoi.

* **[!UICONTROL DomainKeys]** : Service développé par Yahoo visant à certifier l&#39;identité de l&#39;émetteur d&#39;un email.

* **[!UICONTROL Domaine]** IP et RBL (Liste Blackhole en temps réel) : liste d’adresses et de domaines IP qui ont été marqués par les organisations de liste bloquée pour mauvaise réputation d’envoi. Ces listes sont enrichies par des organismes dédiés tels que Spamhaus, Spamcop, SURBL/URIBL, etc. Adobe Campaign traite actuellement les contrôles par rapport aux RBL qui ont un impact significatif sur la délivrabilité. Ces RBL sont les témoins de votre réputation d’envoi et peuvent être interrogés par les ISP avant acceptation de vos emails.

* **[!UICONTROL SNDS]** (Smart Network Data Services) : un [service Windows Live Hotmail de lutte contre le spam](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail est le seul FAI qui fournit ce type d&#39;informations. Les scores de référence sont un résultat de filtre vert, un taux de plainte inférieur à 0,1 % et un taux zéro de pourriel.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->

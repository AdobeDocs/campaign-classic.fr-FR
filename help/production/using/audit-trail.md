---
product: campaign
title: Journal d’audit
description: Découvrez comment surveiller votre instance à lʼaide du journal dʼaudit Campaign
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3d1ed85dcafc5afc4088db98c09d78fb7e9c0a39
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 100%

---

# Journal d’audit{#audit-trail}

>[!INFO]
>
>En savoir plus sur la fonctionnalité Journal d’audit dans la [documentation Adobe Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/analytics/audit-trail).

Dans Adobe Campaign, le **[!UICONTROL Suivi]** vous donne accès à l’historique complet des modifications apportées à votre instance.

Le **[!UICONTROL Suivi]** capture en temps réel la liste complète des actions et des événements qui se produisent au sein de votre instance Adobe Campaign. Il vous permet d’accéder à un historique de données en libre-service afin de vous aider à répondre à des questions portant notamment sur ce qui arrivé à vos workflows, les personnes qui les ont mis à jour pour la dernière fois et ce qu’ont fait vos utilisateurs dans l’instance.

>[!NOTE]
>
>Adobe Campaign n’effectue pas le suivi des modifications apportées aux droits des utilisateurs, aux modèles, aux personnalisations ni aux campagnes.\
>Le Suivi peut uniquement être géré par les administrateurs de l’instance.

![](assets/audit_trail_2.png)

+++ En savoir plus sur les entités disponibles du journal d’audit

* **Journal d’audit du schéma** : permet d’explorer les modifications apportées à vos schémas, ainsi que d’identifier qui a effectué ces modifications et quand elles ont eu lieu.

  Pour plus d’informations sur les schémas, consultez [cette page](../../configuration/using/data-schemas.md).

* **Journal d’audit des workflows** : effectue le suivi de toutes les actions liées à vos workflows, notamment :

   * Démarrer
   * Pause
   * Arrêter
   * Redémarrer
   * Nettoyer qui correspond à l’action Purge de l’historique
   * Simuler qui correspond à l’action Démarrer en mode simulation
   * Réveiller qui correspond à l’action Traitement anticipé des tâches en attente
   * Arrêt inconditionnel

  Pour plus d’informations sur les workflows, consultez [cette page](../../workflow/using/about-workflows.md).

  Pour plus d’informations sur la surveillance des workflows, consultez la [section dédiée](../../workflow/using/monitoring-workflow-execution.md).

* **Journal d’audit des options** : permet de vérifier les activités et les dernières modifications apportées à vos options.

  Pour plus d’informations sur les options, consultez [cette page](../../installation/using/configuring-campaign-options.md).

* **Journal d’audit des diffusions** : permet de vérifier les activités et les dernières modifications apportées à vos diffusions.

  Pour plus d’informations sur les diffusions, consultez cette [page](../../delivery/using/communication-channels.md).

* **Compte externe** : permet de vérifier les modifications apportées aux comptes externes, utilisé par des processus techniques tels que des workflows techniques ou des workflows de campagne.

  Pour plus d’informations sur les comptes externes, consultez cette [page](../../installation/using/external-accounts.md).

* **Mapping de diffusion** : permet de surveiller les activités et les modifications récentes apportées à vos mappings de diffusion.

  Pour plus d’informations sur les mappings de diffusion, consultez cette [page](../../configuration/using/target-mapping.md).

* **Application web** : permet de vérifier les modifications apportées aux formulaires web dans Campaign v8 servant à créer des pages avec des champs de saisie et de sélection et pouvant inclure des données de la base de données.

  Pour plus d’informations sur les applications web, consultez cette [page](../../web/using/about-web-applications.md).

* **Offre** : permet de vérifier les activités et les dernières modifications apportées à vos offres.

  Pour plus d’informations sur l’offre, consultez cette [page](../../interaction/using/interaction-and-offer-management.md).

* **Opérateur ou opératrice** : permet de surveiller les activités et les modifications récentes apportées à vos opérateurs et opératrices.

  Pour plus d’informations sur les opérateurs et opératrices, consultez cette [page](../../platform/using/access-management-operators.md).

+++

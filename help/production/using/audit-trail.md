---
title: Suivi
seo-title: Suivi
description: Suivi
seo-description: null
page-status-flag: never-activated
uuid: b96b93b6-e002-4c67-b9ce-b66cdcd395d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: aa147a8c-9d93-45c8-bb4a-db714739f4c0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Suivi{#audit-trail}

In Adobe Campaign, the **[!UICONTROL Audit trail]** gives you access to the complete history of changes made within your instance.

**[!UICONTROL Audit trail]** capture, en temps réel, une liste complète des actions et événements survenant dans votre instance Adobe Campaign. Il comprend un moyen en libre-service d’accéder à l’historique des données afin de répondre à des questions telles que : ce qui est arrivé à vos processus et qui les a mis à jour en dernier ou ce que vos utilisateurs ont fait dans l’instance.

>[!NOTE]
>
>Adobe Campaign n’effectue pas le suivi des modifications apportées aux droits des utilisateurs, aux modèles, aux personnalisations ni aux campagnes.\
>Le Suivi peut uniquement être géré par les administrateurs de l’instance.

Le Suivi comprend trois composants :

* **Suivi Schéma** : consultez les activités et les dernières modifications apportées à vos schémas.

   Pour plus d’informations sur les schémas, consultez [cette page](../../configuration/using/data-schemas.md).

* **Suivi Workflow** : consultez les activités et les dernières modifications apportées aux workflows, ainsi que l’état de vos workflows, tel que :

   * Démarrer
   * Pause
   * Arrêter
   * Redémarrer
   * Nettoyer qui correspond à l’action Purge de l’historique
   * Simuler qui correspond à l’action Démarrer en mode simulation
   * Réveiller qui correspond à l’action Traitement anticipé des tâches en attente
   * Arrêt inconditionnel
   Pour plus d’informations sur les workflows, consultez [cette page](../../workflow/using/about-workflows.md).

   For more on how to monitor workflows, refer to the [dedicated section](../../workflow/using/monitoring-workflow-execution.md).

* **Suivi Option** : consultez les activités et les dernières modifications apportées à vos options.

   Pour plus d’informations sur les options, consultez [cette page](../../installation/using/configuring-campaign-options.md).

## Accéder au Suivi {#accessing-audit-trail}

Pour accéder à votre instance **[!UICONTROL Audit trail]** :

1. Access the **[!UICONTROL Explorer]** menu of your instance.
1. Dans le **[!UICONTROL Administration]** menu, sélectionnez **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. La **[!UICONTROL Audit trail]** fenêtre s&#39;ouvre avec la liste de vos entités. Adobe Campaign vérifie les actions de création, de modification et de suppression pour les flux de travaux, les options et les schémas.

   Sélectionnez l’une des entités pour en savoir plus sur les dernières modifications.

   ![](assets/audit_trail_2.png)

1. The **[!UICONTROL Audit entity]** window gives you more detailed information on the chosen entity such as:

   * **[!UICONTROL Type]** : Processus, options ou schémas.
   * **[!UICONTROL Entity]** : Nom interne de vos activités.
   * **[!UICONTROL Modified by]** : Nom d&#39;utilisateur de la dernière personne qui a modifié cette entité pour la dernière fois.
   * **[!UICONTROL Action]** : dernière action réalisée sur cette entité (création, édition ou suppression).
   * **[!UICONTROL Modification date]** : Date de la dernière action effectuée sur cette entité.
   Ce bloc de code vous donne davantage d’informations sur ce qui a été modifié dans votre entité.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>By default, retention period is set to 180 days for **[!UICONTROL Audit logs]** . To learn more on how to change the retention period, refer to this [page](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Activer/désactiver le Suivi {#enable-disable-audit-trail}

Le Suivi peut être facilement activé ou désactivé pour une activité spécifique, par exemple si vous voulez économiser de l’espace sur la base de données.

Pour ce faire :

1. Access the **[!UICONTROL Explorer]** menu of your instance.
1. Dans le **[!UICONTROL Administration]** menu, sélectionnez **[!UICONTROL Platform]** puis **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Sélectionnez l’une des options suivantes selon l’entité que vous voulez activer/désactiver :

   * For Workflow: **[!UICONTROL XtkAudit_Workflows]**
   * For Schemas: **[!UICONTROL XtkAudit_DataSchema]**
   * For Options: **[!UICONTROL XtkAudit_Option]**
   * For every entity: **[!UICONTROL XtkAudit_Enable_All]**
   ![](assets/audit_trail_5.png)

1. Change the **[!UICONTROL Value]** to 1 if you want to enable the entity or to 0 if you want to disable it.

   ![](assets/audit_trail_6.png)

1. Clics **[!UICONTROL Save]** .


---
title: Exécution des workflows
seo-title: Exécution des workflows
description: Exécution des workflows
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 69b562979f3b32a4d30dfed0695cf3cf6c0fd26a

---


# Exécution des workflows{#workflow-execution}

La section ci-dessous présente des informations sur les problèmes courants liés à l’exécution des processus et sur la manière de les résoudre.

Pour plus d’informations sur les flux de travail, voir les sections suivantes :

* [A propos des workflows](../../workflow/using/about-workflows.md)
* [Exécuter un workflow](../../workflow/using/executing-a-workflow.md)
* [Recommandations relatives à l’utilisation des processus](../../workflow/using/workflow-best-practices.md)

## Commencer dès que possible dans les campagnes {#start-as-soon-as-possible-in-campaigns}

Dans certains cas, les processus exécutés à partir d’une campagne ne commencent pas lorsque vous cliquez sur le bouton **[!UICONTROL Démarrer]** . Au lieu de commencer, il passe à l’état &quot;Démarrer dès que possible&quot;.

Il peut y avoir plusieurs causes à ce problème, procédez comme suit pour le résoudre :

1. Vérifiez l’état du flux de travail technique [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) . Ce processus gère les tâches ou les processus au sein d’une campagne. En cas d’échec, les processus ne démarrent/ne s’arrêtent pas. Redémarrez-le pour reprendre l’exécution des processus de campagne.

   Pour en savoir plus sur la surveillance des processus techniques, consultez [cette page](../../workflow/using/monitoring-technical-workflows.md).

   >[REMARQUE]
   >
   >Une fois le processus redémarré, assurez-vous d’exécuter les tâches en attente (cliquez avec le bouton droit de la souris sur l’activité du **[!UICONTROL planificateur]** / **[!UICONTROL Exécuter les tâches en attente maintenant]**) afin de vérifier si l’une des activités échoue à nouveau.

   Si le processus échoue toujours, recherchez une erreur spécifique dans le journal d’audit, dépanner en conséquence, puis redémarrez le processus.

1. Vérifiez l’état du module **[!UICONTROL wfserver]** dans l’onglet **[!UICONTROL Surveillance]** , accessible à partir de la page d’accueil de Campaign Classic (voir [Surveillance des processus](../../production/using/monitoring-processes.md)). Ce processus est responsable de l’exécution de tous les processus.

   Un utilisateur administrateur peut également vérifier que le module **wfserver@`<instance>`**est lancé sur votre serveur d’applications principal à l’aide de la commande ci-dessous.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Si le module n’est pas en cours d’exécution, contactez le service à la clientèle Adobe. Si vous disposez d’une installation sur site, un utilisateur administrateur doit redémarrer le service à l’aide de la commande ci-dessous.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Remplacez **`<instancename>`** par le nom de votre instance (production, développement, etc.). Le nom de l’instance est identifié via les fichiers de configuration :
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Pour plus d&#39;informations sur le redémarrage des modules, reportez-vous à [cette section](../../production/using/usual-commands.md#module-launch-commands).

1. Vérifiez si le **nombre de processus de campagne exécutés** sur l’instance est supérieur au seuil. Une limite est définie par l&#39;option [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) sur le nombre de processus de campagne pouvant être exécutés sur l&#39;instance en parallèle. Lorsque cette limite est atteinte, le processus reste à l’état &quot;Démarrer le plus tôt possible&quot; tant que le nombre de processus en cours d’exécution est supérieur à la limite.

   Pour résoudre ce problème, arrêtez les processus indésirables et supprimez les livraisons en échec. Si le seuil a été atteint, cela permettra l’exécution de nouveaux processus.

   Pour vérifier le nombre de processus en cours d’exécution de votre instance, nous vous recommandons d’utiliser les vues prédéfinies, accessibles par défaut dans le dossier **[!UICONTROL Administration]** / **[!UICONTROL Audit]** . For more information, refer to [this page](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[ATTENTION]
   >
   >L’augmentation du seuil de l’option **[!UICONTROL NmsOperation_LimitConcurrency]** peut entraîner des problèmes de performances sur votre instance. Dans tous les cas, n’effectuez pas cette opération vous-même et contactez votre contact Adobe Campaign.

Pour plus d’informations sur la manière de surveiller vos processus, reportez-vous à [cette section](../../workflow/using/monitoring-workflow-execution.md).

## Démarrage en cours {#start-in-progress}

Si les workflows ne s&#39;exécutent pas et restent dans un état **Démarrage en cours**, il se peut que le module de workflow ne soit pas lancé.

Pour le vérifier, puis au besoin le lancer, les étapes sont les suivantes :

1. Vérifiez l’état du module **[!UICONTROL wfserver]** dans l’onglet **[!UICONTROL Surveillance]** , accessible à partir de la page d’accueil de Campaign Classic (voir [Surveillance des processus](../../production/using/monitoring-processes.md)).

   Un utilisateur administrateur peut également vérifier que le module **wfserver@`<instance>`**est lancé sur votre serveur d’applications principal à l’aide de la commande ci-dessous.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Pour plus d&#39;informations sur la manière de surveiller les modules, reportez-vous à [cette section](../../production/using/usual-commands.md#monitoring-commands-).

1. Si le module n’est pas en cours d’exécution, contactez le service à la clientèle Adobe. Si vous disposez d’une installation sur site, un administrateur doit la redémarrer à l’aide de la commande ci-dessous.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Remplacez **`<instancename>`** par le nom de votre instance (production, développement, etc.). Le nom de l’instance est identifié via les fichiers de configuration :
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Pour plus d&#39;informations sur le redémarrage des modules, reportez-vous à [cette section](../../production/using/usual-commands.md#module-launch-commands).

## Workflow en échec {#failed-workflow}

Si un workflow est en échec, procédez comme suit :

1. Vérifiez le journal du workflow. Voir à ce propos les sections [Suivre l&#39;exécution des workflows](../../workflow/using/monitoring-workflow-execution.md) et [Afficher les logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Effectuez un suivi des workflows techniques. Voir à ce propos [cette section](../../workflow/using/monitoring-technical-workflows.md).
1. Recherchez des échecs dans chaque activité du workflow.

---
product: campaign
title: Exécution des workflows
description: Exécution des workflows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: ht
source-wordcount: '651'
ht-degree: 100%

---

# Exécution des workflows{#workflow-execution}



La section ci-dessous présente des informations sur les problèmes courants liés à l’exécution des workflows et sur la manière de les résoudre.

Pour plus d&#39;informations sur les workflows, consultez les sections suivantes :

* [À propos des workflows](../../workflow/using/about-workflows.md)
* [Démarrer un workflow](../../workflow/using/starting-a-workflow.md)
* [Cycle de vie d&#39;un workflow](../../workflow/using/workflow-life-cycle.md)
* [Bonnes pratiques relatives à l’utilisation des workflows](../../workflow/using/workflow-best-practices.md)

## Démarrage dès que possible dans les campagnes {#start-as-soon-as-possible-in-campaigns}

Dans certains cas, les workflows exécutés à partir d’une campagne ne commencent pas lorsque vous cliquez sur le bouton **[!UICONTROL Démarrer]**. Au lieu de commencer, il passe à l’état « Démarrage dès que possible ».

Il peut y avoir plusieurs causes à ce problème. Procédez comme suit pour le résoudre :

1. Vérifiez le statut du workflow technique [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md). Ce processus gère les traitements ou les workflows au sein d’une campagne. En cas d’échec, les workflows ne démarrent pas / ne s’arrêtent pas. Redémarrez-le pour reprendre l’exécution des workflows de campagne.

   Pour en savoir plus sur la surveillance des workflows techniques, consultez [cette page](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Une fois le processus redémarré, assurez-vous d’exécuter les tâches en attente (cliquez avec le bouton droit de la souris sur l’activité **[!UICONTROL Planificateur]** / **[!UICONTROL Traitement anticipé de la (des) tâche(s)]**) afin de vérifier si l’une des activités échoue à nouveau.

   Si le workflow échoue toujours, recherchez une erreur spécifique dans le log d’audit, dépannez en conséquence, puis redémarrez le workflow.

1. Vérifiez l’état du module **[!UICONTROL wfserver]** dans l’onglet **[!UICONTROL Surveillance]**, accessible à partir de la page d’accueil de Campaign Classic (voir [Surveillance des processus](../../production/using/monitoring-processes.md)). Ce processus est responsable de l’exécution de tous les workflows.

   Un utilisateur administrateur peut également vérifier que le module **wfserver@`<instance>`** est lancé sur votre serveur d’applications principal à l’aide de la commande ci-dessous.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Si le module n’est pas en cours d’exécution, contactez l’assistance clientèle d’Adobe. Si vous disposez d’une installation on-premise, un utilisateur administrateur doit redémarrer le service à l’aide de la commande ci-dessous.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Remplacez **`<instance-name>`** par le nom de votre instance (production, développement, etc.). Le nom de l’instance est identifié via les fichiers de configuration :
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Pour plus d&#39;informations sur le redémarrage des modules, consultez [cette section](../../production/using/usual-commands.md#module-launch-commands).

1. Vérifiez si le **nombre de processus de campagne en cours d’excution** sur l’instance est supérieur au seuil. Une limite est définie par l&#39;option [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) concernant le nombre de workflows de campagne pouvant être exécutés sur l&#39;instance en parallèle. Lorsque cette limite est atteinte, le workflow reste à l’état « Démarrage dès que possible » tant que le nombre de workflows en cours d’exécution est supérieur à la limite.

   Pour résoudre ce problème, arrêtez les workflows indésirables et supprimez les diffusions en échec. Si le seuil a été atteint, cela permettra l’exécution de nouveaux processus.

   Pour vérifier le nombre de workflows en cours d’exécution de votre instance, nous vous recommandons d’utiliser les vues prédéfinies, accessibles par défaut dans le dossier **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Pour plus d’informations, consultez [cette page](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >L’augmentation du seuil de l’option **[!UICONTROL NmsOperation_LimitConcurrency]** peut entraîner des problèmes de performances sur votre instance. Dans tous les cas, n’effectuez pas cette opération vous-même et communiquez avec votre contact Adobe Campaign.

Pour plus d’informations sur la manière de surveiller vos workflows, consultez [cette section](../../workflow/using/monitoring-workflow-execution.md).

## Démarrage en cours {#start-in-progress}

Si les workflows ne s&#39;exécutent pas et restent dans un état **Démarrage en cours**, il se peut que le module de workflow ne soit pas lancé.

Pour le vérifier, puis au besoin le lancer, les étapes sont les suivantes :

1. Vérifiez l’état du module **[!UICONTROL wfserver]** dans l’onglet **[!UICONTROL Surveillance]** , accessible à partir de la page d’accueil de Campaign Classic (voir [Surveillance des processus](../../production/using/monitoring-processes.md)).

   Un utilisateur administrateur peut également vérifier que le module **wfserver@`<instance>`** est lancé sur votre serveur d’applications principal à l’aide de la commande ci-dessous.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Pour plus d&#39;informations sur la manière de surveiller les modules, consultez [cette section](../../production/using/usual-commands.md#monitoring-commands-).

1. Si le module n’est pas en cours d’exécution, contactez l’assistance clientèle d’Adobe. Si vous disposez d’une installation on-premise, un administrateur doit la redémarrer à l’aide de la commande ci-dessous.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Remplacez **`<instance-name>`** par le nom de votre instance (production, développement, etc.). Le nom de l’instance est identifié via les fichiers de configuration :
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Pour plus d&#39;informations sur le redémarrage des modules, consultez [cette section](../../production/using/usual-commands.md#module-launch-commands).

## Workflow en échec {#failed-workflow}

Si un workflow est en échec, procédez comme suit :

1. Vérifiez le journal du workflow. Voir à ce propos les sections [Suivre l&#39;exécution des workflows](../../workflow/using/monitoring-workflow-execution.md) et [Afficher les logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Effectuez un suivi des workflows techniques. Voir à ce propos [cette section](../../workflow/using/monitoring-technical-workflows.md).
1. Recherchez des échecs dans chaque activité du workflow.

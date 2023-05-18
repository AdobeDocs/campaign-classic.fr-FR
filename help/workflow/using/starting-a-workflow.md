---
product: campaign
title: Démarrer un workflow
description: Découvrez comment démarrer un workflow et la barre d’outils des actions de workflows ainsi que le menu contextuel
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Démarrage dʼun workflow {#starting-a-workflow}



Un workflow est toujours démarré manuellement. Au démarrage, il peut toutefois rester inactif en fonction des informations spécifiées par le biais d&#39;un planificateur (voir [Planificateur](scheduler.md)) ou d&#39;une planification d&#39;activité.

Les actions relatives à l&#39;exécution du workflow de ciblage (lancement, arrêt, pause, etc.) sont des processus **asynchrones** : la commande est enregistrée et sera effective dès que le serveur sera disponible pour l&#39;appliquer.

La barre d&#39;outils permet de lancer et suivre l&#39;exécution du workflow.

La liste des options disponibles dans le menu **[!UICONTROL Actions]** et le menu contextuel sont présentées dans les sections suivantes.

>[!IMPORTANT]
>
>Gardez à l’esprit que, lorsque un opérateur exécute une action sur un workflow (démarrer, arrêter, mettre en pause, etc.), l&#39;action n&#39;est pas exécutée immédiatement, mais placée dans une file d’attente pour être traitée par le [module de workflow](architecture.md).

## Barre d&#39;outils des actions {#actions-toolbar}

Les boutons de la barre d&#39;outils sont décrits dans cette [section](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). Le bouton **[!UICONTROL Actions]** vous donne accès à des options d&#39;exécution supplémentaires permettant d&#39;agir individuellement sur le ou les workflows sélectionnés. Vous pouvez également utiliser le menu **[!UICONTROL Fichier > Actions]** ou cliquer avec le bouton droit sur un workflow et sélectionner **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Début]**

   Cette action permet de lancer l&#39;exécution d&#39;un workflow : un workflow **Terminé**, **En édition** ou **En pause** passe alors en état **Démarré**. Le moteur de workflow va prendre en charge l&#39;exécution de ce workflow. Si le workflow était en pause, il s&#39;agit d&#39;une reprise, sinon il s&#39;agit d&#39;un démarrage et les activités initiales sont alors activées.

   Le démarrage est un processus asynchrone : la demande est enregistrée et sera traitée dès que possible par un serveur de workflow.

* **[!UICONTROL Pause]**

   Cette action a pour effet de passer le workflow **En pause**. Aucune activité ne sera activée jusqu&#39;à la prochaine reprise mais les opérations en cours ne seront pas suspendues.

* **[!UICONTROL Stopper]**

   Cette action arrête un workflow en cours d&#39;exécution : l&#39;instance passe alors en état **Terminé**. Les opérations en cours sont interrompues, si possible. Les imports ou requêtes SQL en cours sont immédiatement annulées.

   >[!IMPORTANT]
   >
   >L’arrêt d’un workflow suit un processus asynchrone : la demande est enregistrée, puis le ou les serveurs de workflow annulent les opérations en cours. L’arrêt d’une instance de workflow peut donc prendre du temps, surtout si le workflow est exécuté sur plusieurs serveurs, car chacun d’eux doit alors prendre le contrôle pour annuler les tâches en cours. Pour éviter tout problème, attendez que l’opération d’arrêt soit terminée et n’effectuez pas plusieurs demandes d’arrêt sur le même workflow.

* **[!UICONTROL Redémarrer]**

   Cette action consiste à arrêter puis démarrer un workflow. Dans la plupart des cas, elle permet de redémarrer plus vite. Elle est également utile pour automatiser le redémarrage lorsque l&#39;arrêt prend un certain temps : en effet la commande &#39;Démarrer&#39; n&#39;est disponible que lorsque l&#39;arrêt est effectif.

   Les actions **[!UICONTROL Démarrer / Pause / Stopper / Redémarrer]** sont également disponibles via les icônes d&#39;exécution de la barre d&#39;outils. Voir à ce sujet cette [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge de l&#39;historique]**

   Cette action vous permet de purger l&#39;historique du workflow. Pour plus d&#39;informations, consultez la section [Purger l&#39;historique](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Démarrer en mode simulation]**

   Cette option permet de démarrer le workflow, non pas en mode réel, mais en mode simulation. Lorsque vous activez ce mode, seules les activités n&#39;ayant pas d&#39;impact sur la base ni sur le système de fichiers sont exécutées, par exemple les activités de type **[!UICONTROL Requête]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, etc. Les activités ayant un impact (**[!UICONTROL Export]**, **[!UICONTROL Import]**, etc) ainsi que celles qui leur succèdent (dans la même branche) ne sont pas exécutées.

* **[!UICONTROL Traitement anticipé des tâches en attente]**

   Cette action permet de lancer dès que possible toutes les tâches en attente. Si vous souhaitez lancer une tâche particulière, cliquez avec le bouton droit sur l&#39;activité correspondante et sélectionnez **[!UICONTROL Traitement anticipé de la (des) tâche(s)]**.

* **[!UICONTROL Arrêt inconditionnel]**

   Lorsque cette option est sélectionnée, l&#39;état du workflow passe à **[!UICONTROL Terminé]**. Cette action ne doit être utilisée qu&#39;en dernier recours, lorsqu&#39;un arrêt normal ne fonctionne pas après plusieurs minutes. N&#39;utilisez l&#39;arrêt inconditionnel que si vous êtes sûr qu&#39;il n&#39;y a aucun traitement réel en cours sur le workflow.

   >[!CAUTION]
   >
   >Cette option est réservée à un utilisateur expert.

* **[!UICONTROL Sauver comme modèle]**

   Cette action crée un nouveau modèle de workflow à partir du workflow sélectionné. Vous devez indiquer son dossier d&#39;enregistrement (dans le champ **[!UICONTROL Dossier]**).

   Les options **[!UICONTROL Mettre à jour en masse les lignes sélectionnées]** et **[!UICONTROL Fusionner les lignes sélectionnées]** sont des options génériques de la plateforme disponibles dans tous les menus **[!UICONTROL Actions]**. Voir à ce sujet cette [section](../../platform/using/updating-data.md).

## Menu contextuel {#right-click-menu}

Lorsqu&#39;une ou plusieurs activités d&#39;un workflow sont sélectionnées, vous pouvez cliquer avec le bouton droit de la souris afin d&#39;agir sur votre sélection.

![](assets/contextual_menu.png)

Les options disponibles dans le menu contextuel sont les suivantes :

**[!UICONTROL Ouvrir :]** cette option permet d&#39;accéder aux propriétés de l&#39;activité.

**[!UICONTROL Afficher le journal :]** cette option permet de visualiser le journal d&#39;exécution des tâches de l&#39;activité sélectionnée. Pour plus d&#39;informations, consultez la section [Afficher le journal](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Traitement anticipé de la (des) tâche(s) :]** cette action permet de lancer dès que possible la ou les tâches en attente de l&#39;activité.

**[!UICONTROL Redémarrage du workflow à partir d&#39;une tâche :]** cette option permet de redémarrer le workflow en utilisant les résultats précédemment stockés pour cette activité.

**[!UICONTROL Couper/Copier/Coller/Supprimer :]** ces options permettent de couper, copier, coller et supprimer les activités.

**[!UICONTROL Copier en tant qu&#39;image :]** cette option permet d&#39;effectuer une capture d&#39;écran de l&#39;ensemble des activités.

**[!UICONTROL Exécution normale / Activer mais ne pas exécuter / Ne pas activer :]** ces options sont également disponibles dans l&#39;onglet **[!UICONTROL Avancé]** des propriétés de l&#39;activité. Elles sont présentées dans la section [Exécution](advanced-parameters.md#execution).

**[!UICONTROL Enregistrer/Annuler :]** permet d&#39;enregistrer ou d&#39;annuler les modifications effectuées sur le workflow.

>[!NOTE]
>
>Vous pouvez sélectionner un groupe d&#39;activités pour leur appliquer une de ces commandes.

Le menu contextuel est également présenté dans cette [section](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).

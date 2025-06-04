---
product: campaign
title: À propos des workflows
description: Automatisez les processus avec des workflows, gérez les données et les audiences, envoyez des messages, et bien plus encore.
feature: Workflows, Data Management
exl-id: 024a7344-9376-4ff3-926a-003148229f9f
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 10%

---

# Automatisation à l’aide de workflows {#gs-workflows}

Les workflows d’Adobe Campaign permettent à votre équipe de rationaliser et d’automatiser les processus d’entreprise de bout en bout sur la plateforme. Grâce à une interface graphique intuitive, vous pouvez concevoir et gérer des workflows qui coordonnent des tâches telles que la segmentation des données, l’exécution de campagnes, la gestion de fichiers et même les approbations d’utilisateurs, le tout à un seul endroit.

Par exemple, vous pouvez automatiser un processus de récupération d’un fichier d’un serveur distant, d’extraction de son contenu et de chargement transparent des données dans le serveur Adobe Campaign, ce qui réduit les efforts manuels et accroît l’efficacité opérationnelle. Le moteur de workflow garantit que chaque étape est exécutée de manière fiable et suivie pour la visibilité et le contrôle.

>[!BEGINTABS]

>[!TAB Documentation des workflows]

Pour en savoir plus sur la gestion des workflows, consultez la documentation [Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=fr){target=_blank}.


[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=fr){target=_blank}


>[!TAB Liens utiles]

Découvrez les étapes clés liées à la gestion des workflows dans la documentation de Campaign v8 :

* [Activités de workflow](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html?lang=fr){target=_blank} : une activité est un modèle de tâche. Les workflows comprennent les activités de ciblage, de contrôle de flux, d&#39;action et d&#39;événement.

* [Créer un workflow](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=fr){target=_blank} : découvrez comment créer et exécuter des workflows de ciblage, de campagne et techniques.

* [Bonnes pratiques ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=fr){target=_blank} : découvrez les conseils pour optimiser les performances des workflows Campaign, améliorer la conception de vos workflows et définir les paramètres appropriés.

* [Surveiller les workflows](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=fr){target=_blank} : découvrez comment surveiller l’exécution des workflows pour vous assurer que tout fonctionne correctement.

* [Cas d’utilisation de workflow](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/workflow-use-cases.html?lang=fr){target=_blank} : découvrez les contextes dans lesquels les workflows peuvent être utilisés et comment les implémenter par le biais de cas d’utilisation de bout en bout.


>[!ENDTABS]





<!--

Adobe Campaign uses workflows to:

* Carry out targeting campaigns. [Learn more](building-a-workflow.md#implementation-steps-)
* Build campaigns: for each campaign, the **[!UICONTROL Workflow]** tab lets you build the target and create the deliveries. [Learn more](building-a-workflow.md#campaign-workflows)
* Perform technical processes: cleanup, collecting tracking information or provisional calculations. [Learn more](building-a-workflow.md#technical-workflows)

A workflow can mean both a process definition (the workflow model, which is a representation of what is supposed to happen) and an instance of this process (a workflow instance, which is a representation of what is actually happening).

The workflow template describes the various tasks to be performed and how they are linked together. The task templates are called activities and are represented by icons. They are linked together by transitions.

![](assets/example1.png)

Each workflow contains:

* **[!UICONTROL Activities]**

  An activity describes a task template. The various activities available are represented on the diagram by icons. Each type has common properties and specific properties. For example, while all activities have a name and label, only the **[!UICONTROL Approval]** activity has an assignment.

  In a workflow diagram, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

  All workflow activities are listed in [this section](about-activities.md), including use cases and samples.

* **[!UICONTROL Transitions]**

  Transitions enable you to link activities and to define their sequence. A transition links a source activity to a destination activity. There are several sorts of transitions, which depend on the source activity. Some transitions have additional parameters such as a duration, a condition or a filter.

  A transition which is not linked to a destination activity is colored orange and the arrow head is shown as a diamond.

  >[!NOTE]
  >
  >A workflow containing unterminated transitions can still be executed: a warning message will be generated and the workflow will pause once it reaches the transition but it will not generate an error. It is thus possible to start a workflow without it being finished and to add to it as you go along.

  For more information about how to build a workflow, refer to [this section](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  The worktable contains all the information carried by the transition. Each workflow uses several worktables. The data conveyed in these tables can be accelerated and used throughout the workflow's life cycle, as long as it is not purged. Indeed, unneeded tables are purged each time the workflow is passivated, and possibly during the execution of the largest workflows to avoid overloading the server.

  Learn more on workflow data and tables in [this section](how-to-use-workflow-data.md).

## Key principles and best practices{#principles-workflows}

Refer to these sections to find guidance and best practices to automate processes with workflows:

* Learn more about workflow activities in [this page](how-to-use-workflow-data.md).
* Learn how to build a workflow in [this section](building-a-workflow.md).
* Discover how to use workflows to import data in Campaign in [this section](../../platform/using/import-export-workflows.md).
* Workflow best practices are detailed in [this page](workflow-best-practices.md).
* Find guidance about workflow execution in [this section](starting-a-workflow.md).
* Learn how to monitor workflows in [this page](monitoring-workflow-execution.md).
* Learn how to grant access to users to use workflows in [this page](managing-rights.md).

-->
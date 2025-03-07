---
product: campaign
title: Coordonner les mises à jour de données
description: Coordonner les mises à jour de données
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '303'
ht-degree: 100%

---

# Coordonner les mises à jour de données{#coordinating-data-updates}



Ce cas pratique présente la création d’un workflow permettant de gérer des mises à jour concomitantes lors de l’utilisation de plusieurs exécutions d’un workflow.

Le but est de vérifier que la procédure de mise à jour est terminée avant d&#39;exécuter une autre opération de mise à jour. Pour cela, nous allons configurer une variable d&#39;instance et laisser le workflow tester si l&#39;instance est en cours d&#39;exécution afin de décider de poursuivre ou non l&#39;exécution du workflow et d&#39;effectuer la mise à jour.

![](assets/uc_dataupdate_wkf.png)

Ce workflow se compose de :

* une activité **Planificateur** exécutant le workflow à une fréquence spécifique,
* une activité **Test** vérifiant si le workflow est déjà en cours d&#39;exécution,
* des activités **Requête** et **Mise à jour de données** si le workflow n&#39;est pas déjà en cours d&#39;exécution, suivies d&#39;une activité **Fin** réinitialisant la variable d&#39;instance du workflow à la valeur false.
* une activité **Fin** si le workflow est déjà en cours d&#39;exécution.

Pour créer le workflow, procédez comme suit :

1. Ajoutez une activité **Planificateur**, puis configurez sa fréquence selon vos besoins.
1. Ajoutez une activité **Test** pour vérifier si le workflow est déjà en cours d&#39;exécution, puis configurez-la comme indiqué ci-dessous.

   >[!NOTE]
   >
   >&quot;isRunning&quot; est le nom de la variable d&#39;instance choisi pour cet exemple. Il ne s&#39;agit pas d&#39;une variable intégrée.

   ![](assets/uc_dataupdate_test.png)

1. Ajoutez une activité **Fin** au branchement **Non**. Ainsi, rien ne sera exécuté si le workflow est déjà en cours d&#39;exécution.
1. Ajoutez les activités souhaitées au branchement **Oui**. Dans le cas présent, il s&#39;agit des activités **Requête** et **Mise à jour des données**.
1. Ouvrez la première activité, puis ajoutez la commande **instance.vars.isRunning = true** dans l&#39;onglet **[!UICONTROL Avancé]**. Ainsi, la variable d&#39;instance est définie comme étant en cours d&#39;exécution.

   ![](assets/uc_dataupdate_query.png)

1. Ajoutez une activité **Fin** à l&#39;extrémité du branchement **[!UICONTROL Oui]**, puis la commande **instance.vars.isRunning = false** dans l&#39;onglet **[!UICONTROL Avancé]**.

   De cette manière, aucune action ne sera exécutée tant que le workflow sera en cours d&#39;exécution.

   ![](assets/uc_dataupdate_end.png)

**Rubriques connexes :**

* [Empêcher les exécutions multiples simultanées](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Activité Mise à jour de données](update-data.md)

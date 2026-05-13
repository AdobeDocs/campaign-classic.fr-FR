---
product: campaign
title: Coordonner les mises à jour de données
description: Coordonner les mises à jour de données
feature: Workflows, Data Management
hide: true
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
TQID: https://experienceleague.adobe.com/G82StaXeELHRHF4C1qMnRK0IekJoF0n-r6xQi63KPlk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 304
ht-degree: 70%

---

# Coordonner les mises à jour de données{#coordinating-data-updates}



Ce cas pratique présente la création d’un workflow permettant de gérer des mises à jour concomitantes lors de l’utilisation de plusieurs exécutions d’un workflow.

Le but est de vérifier que le processus de mise à jour est terminé avant d&#39;exécuter une autre opération de mise à jour. Pour ce faire, nous allons configurer une variable d’instance et laisser le workflow tester si l’instance est en cours d’exécution afin de décider de continuer ou non l’exécution du workflow et d’effectuer la mise à jour.

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
   >« isRunning » est le nom de la variable d&#39;instance choisi pour cet exemple. Il ne s’agit pas d’une variable intégrée.

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

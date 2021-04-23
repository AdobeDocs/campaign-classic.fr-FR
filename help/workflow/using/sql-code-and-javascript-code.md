---
solution: Campaign Classic
product: campaign
title: Code SQL et code JavaScript
description: En savoir plus sur les activités du workflow des codes SQL et JavaScript
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '291'
ht-degree: 100%

---

# Code SQL et code JavaScript{#sql-code-and-javascript-code}

## Code SQL {#sql-code}

Une activité de type **[!UICONTROL Code SQL]** exécute un script SQL. Le script est un template JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   La zone centrale de l&#39;éditeur contient le script à exécuter. Ce script est un template JST et peut donc être paramétré en fonction du contexte du workflow.

* **[!UICONTROL Traiter les erreurs]**

   Voir la section [Traiter les erreurs](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Code JavaScript et code JavaScript avancé {#javascript-code}

Les activités **[!UICONTROL code JavaScript]** et **[!UICONTROL code JavaScript avancé]** exécutent un script JavaScript dans le cadre d’un workflow. Pour plus d’informations sur les scripts, voir la section [Scripts/Templates JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

### Délai d‘exécution {#exec-delay}

À compter de la version 20.2, un délai d‘exécution a été ajouté aux activités **[!UICONTROL code JavaScript]** et **[!UICONTROL code JavaScript avancé]**. Par défaut, la phase d’exécution ne peut pas dépasser 1 heure. Après ce délai, le processus est abandonné avec un message d‘erreur et l‘échec de l’exécution.

Vous pouvez modifier ce délai dans le champ **[!UICONTROL Arrêter l’exécution après]**, disponible dans ces activités.

Pour ignorer cette limite, vous devez définir la valeur sur **0**.

### Code JavaScript {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]** : la zone centrale de l’éditeur contient le script à exécuter.

* **[!UICONTROL Traiter les erreurs]** : voir la section [Traitement des erreurs](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

### Code JavaScript avancé {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL Premier appel]** : la première zone de l’éditeur contient le script à exécuter lors du premier appel.
* **[!UICONTROL Appels suivants]** : la deuxième zone de l’éditeur contient le script à exécuter lors des appels suivants.
* **[!UICONTROL Transitions]** : vous pouvez définir plusieurs transitions en sortie de l’activité.
* **[!UICONTROL Planificateur]**: l’onglet **[!UICONTROL Planning]** permet de planifier le déclenchement de l’activité.

JavaScript avancé est une tâche persistante et est régulièrement rappelé s’il n’a pas été marqué comme terminé. Pour terminer la tâche et empêcher les rappels ultérieurs, vous devez utiliser la méthode **task.setCompleted()** dans la section **[!UICONTROL Appels suivants]** :

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```

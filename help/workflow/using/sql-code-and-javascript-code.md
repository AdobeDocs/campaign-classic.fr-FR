---
title: Code SQL et code JavaScript
seo-title: Code SQL et code JavaScript
description: Code SQL et code JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 26ba86073e4f1569bf05a7d8aa864ca87baed3ea
workflow-type: tm+mt
source-wordcount: '234'
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

>[!NOTE]
>
>Par défaut, la phase d’exécution des activités **[!UICONTROL code JavaScript]** et **[!UICONTROL code JavaScript avancé]** ne peut pas dépasser 1 heure. Après ce délai, le processus est abandonné avec un message d’erreur et l’échec de l’exécution.
>
>Vous pouvez modifier ce délai dans le champ **[!UICONTROL Arrêter l’exécution après]**, disponible dans les propriétés des activités.

* **[!UICONTROL Code JavaScript]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]** : la zone centrale de l’éditeur contient le script à exécuter.
   * **[!UICONTROL Erreurs de traitement]** : voir la section [Erreurs de traitement](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Code JavaScript avancé]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL Premier appel]** : la première zone de l’éditeur contient le script à exécuter lors du premier appel.
   * **[!UICONTROL Appels suivants]** : la deuxième zone de l’éditeur contient le script à exécuter lors des appels suivants.
   * **[!UICONTROL Transitions]** : vous pouvez définir plusieurs transitions en sortie de l’activité.
   * **[!UICONTROL Planificateur]**: l’onglet **[!UICONTROL Planning]** permet de planifier le déclenchement de l’activité.

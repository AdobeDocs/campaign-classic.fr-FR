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
source-git-commit: 16e35b62cdf42c04139cc17645095a3d1f6e0fa7

---


# Code SQL et code JavaScript{#sql-code-and-javascript-code}

## Code SQL {#sql-code}

An **[!UICONTROL SQL code*]* activity executes an SQL script. The script is a JST template.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   La zone centrale de l&#39;éditeur contient le script à exécuter. Ce script est un template JST et peut donc être paramétré en fonction du contexte du workflow.

* **[!UICONTROL Traiter les erreurs]**

   Voir la section [Traiter les erreurs](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Code JavaScript et code JavaScript avancé {#javascript-code}

**[!UICONTROL Le code]** JavaScript et le code **[!UICONTROL JavaScript]** avancé  exécutent un script JavaScript dans le cadre d’un processus. Pour plus d’informations sur les scripts, voir la section [Scripts/Templates JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

>[!NOTE]
>
>Par défaut, la phase d’exécution du code **** JavaScript et du code **[!UICONTROL JavaScript]** avancé  le  ne peut pas dépasser 1 heure. Après ce délai, le processus sera abandonné avec un message d’erreur et l’exécution du   échouera.
>
>Vous pouvez modifier ce délai dans le champ **[!UICONTROL Arrêter l’exécution après]** , disponible dans les propriétés  du .

* **[!UICONTROL Code JavaScript]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: La zone centrale de l’éditeur contient le script à exécuter.
   * **[!UICONTROL Erreurs]** de traitement : Reportez-vous à la section Erreurs [de](../../workflow/using/monitoring-workflow-execution.md#processing-errors)traitement.

* **[!UICONTROL Code JavaScript avancé]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL Premier appel]**: La première zone de l’éditeur contient le script à exécuter lors du premier appel.
   * **[!UICONTROL Appels]** suivants : La deuxième zone de l’éditeur contient le script à exécuter lors des appels suivants.
   * ****: Vous pouvez définir plusieurs   de sortie .
   * **[!UICONTROL Planification]**: L’onglet **[!UICONTROL Planifier]** vous permet de programmer le moment où déclencher le  .

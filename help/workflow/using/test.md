---
title: Test
seo-title: Test
description: Test
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: b78db689958c9b240da9a0315060fe63bcb48e0a
workflow-type: ht
source-wordcount: '182'
ht-degree: 100%

---


# Test{#test}

Une activité de type **Test** active la première transition qui vérifie la condition qui lui est associée. Si aucune condition n&#39;est vérifiée et si l&#39;option **[!UICONTROL Utiliser le branchement par défaut]** est activée, la transition par défaut sera activée.

Une condition est une expression JavaScript qui doit être évaluée à &#39;true&#39; ou &#39;false&#39;. Pour saisir l&#39;expression, cliquez sur l&#39;icône située à droite du nom de la condition et choisissez **[!UICONTROL Editer...]**.

![](assets/edit_test.png)

Pour plus d’informations sur toutes les autres fonctions JavaScript et méthodes SOAP du serveur applicatif accessibles via workflow, consultez la [documentation JSAPI](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Vous pouvez insérer directement des variables également depuis cet éditeur.

Les conditions peuvent être ajoutées, supprimées, ordonnées depuis la fenêtre d&#39;édition des propriétés de l&#39;activité, mais aussi modifiées depuis la transition.

Si le résultat d&#39;un calcul doit être réutilisé par différentes conditions, il est possible de le calculer dans le script d&#39;initialisation de l&#39;activité. Le résultat doit être stocké dans une variable de la tâche pour être accessible par les scripts de conditions (task.vars.xxx).

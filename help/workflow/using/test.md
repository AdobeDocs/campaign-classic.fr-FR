---
product: campaign
title: Test
description: En savoir plus sur l’activité de workflow de test
feature: Workflows
hide: true
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
TQID: https://experienceleague.adobe.com/NaQuMb-U9z0U8QZZnmwgPdKaFacOduVvGWDl9P68qR4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: c35995a47788db080636c66827a4bd6dc98806cf
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 59%

---

# Test{#test}



Une activité de type **Test** active la première transition satisfaisant la condition qui lui est associée. Si aucune condition n’est remplie et si l’option **[!UICONTROL Utiliser le branchement par défaut]** est activée, la transition par défaut est activée.

Une condition est une expression JavaScript qui doit être déterminée par « true » ou « false ». Pour saisir l’expression, cliquez sur l’icône située à droite du nom de la condition, puis sélectionnez **[!UICONTROL Modifier...]**.

![](assets/edit_test.png)

Pour plus d’informations sur toutes les autres fonctions JavaScript et méthodes SOAP du serveur applicatif accessibles via workflow, consultez la [documentation JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=fr).

Vous pouvez insérer directement des variables également depuis cet éditeur. Pour plus d’informations sur l’utilisation des variables, consultez [cette section](javascript-scripts-and-templates.md#variables).

Les conditions peuvent être ajoutées, supprimées, ordonnées depuis la fenêtre d&#39;édition des propriétés de l&#39;activité, mais aussi modifiées depuis la transition.

Si le résultat d&#39;un calcul doit être réutilisé par des conditions différentes, il est possible de le calculer dans le script d&#39;initialisation de l&#39;activité. Le résultat doit être stocké dans une variable de la tâche pour être accessible par les scripts de condition (task.vars.xxx).


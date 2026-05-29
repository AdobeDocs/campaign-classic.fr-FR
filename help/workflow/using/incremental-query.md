---
product: campaign
title: Requête incrémentale
description: En savoir plus sur l’activité de workflow de requête incrémentale
feature: Workflows, Targeting Activity
hide: true
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
TQID: https://experienceleague.adobe.com/RBw8ii57Yhf9IHnK9Q-v7zUqq0cJKx3JMuaS84w1Y7E
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 379
ht-degree: 61%

---

# Requête incrémentale{#incremental-query}



Une requête incrémentale permet de sélectionner périodiquement une cible selon un critère, mais d&#39;exclure les personnes qui ont déjà été ciblées sur ce critère les fois précédentes.

La population déjà ciblée est stockée en mémoire par instance de workflow et par activité, c’est-à-dire que deux workflows démarrés à partir du même modèle ne partagent pas le même journal. D’un autre côté, deux tâches basées sur la même requête incrémentale pour la même instance de workflow utiliseront le même journal.

La requête est définie selon le même mode que pour les requêtes standard, mais son exécution est planifiée.

**Rubriques connexes :**

* [Cas pratique : mise à jour de la liste trimestrielle à l’aide d’une requête incrémentielle](quarterly-list-update.md)
* [Créer une requête](query.md#creating-a-query)

>[!CAUTION]
>
>Si le résultat d&#39;une requête incrémentale est égal à **0** lors de l&#39;une de ses exécutions, le workflow est suspendu jusqu&#39;à la prochaine exécution programmée de la requête. Les transitions et activités qui suivent la requête incrémentale ne sont donc pas traitées avant l&#39;exécution suivante.

Pour ce faire :

1. Dans l&#39;onglet **[!UICONTROL Planification et historique]**, sélectionnez l&#39;option **[!UICONTROL Planifier l&#39;exécution]**. La tâche reste active une fois créée et ne sera déclenchée qu&#39;aux heures spécifiées par le planning d&#39;exécution de la requête. En revanche, si l&#39;option est désactivée, la requête est exécutée immédiatement **et une seule fois**.
1. Cliquez sur le bouton **[!UICONTROL Changer]**.

   Dans la fenêtre **[!UICONTROL Assistant d’édition d’un planning]**, vous pouvez configurer le type de fréquence, la périodicité des événements et la période de validité des événements.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Cliquez sur **[!UICONTROL Terminer]** pour enregistrer le planning.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. La section inférieure de l&#39;onglet **[!UICONTROL Planification &amp; Historique]** permet de sélectionner le nombre de jours d&#39;historique à prendre en compte.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL Jours d&#39;historique]**

     Les destinataires déjà ciblés peuvent être enregistrés un nombre maximal de jours à partir du jour où ils ont été ciblés. Si cette valeur est égale à zéro, les personnes destinataires ne sont jamais purgées du log.

   * **[!UICONTROL Conserver l&#39;historique au démarrage]**

     Cette option permet de ne pas effacer l&#39;historique lors de l&#39;activation de l&#39;activité.

   * **[!UICONTROL Nom de la table SQL]**

     Ce champ permet de surcharger la table SQL par défaut contenant les données d&#39;historique.

## Paramètres de sortie {#output-parameters}

* tableName
* schéma
* recCount

Ce jeu de trois valeurs identifie la population ciblée par la requête. **[!UICONTROL tableName]** est le nom de la table qui enregistre les identifiants de la cible, **[!UICONTROL schema]** est le schéma de la population (généralement nms:recipient) et **[!UICONTROL recCount]** est le nombre d’éléments dans la table.

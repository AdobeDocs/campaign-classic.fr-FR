---
product: campaign
title: Requête incrémentale
description: En savoir plus sur l’activité de workflow de requête incrémentale
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Requête incrémentale{#incremental-query}

![](../../assets/v7-only.svg)

Une requête incrémentale permet de sélectionner périodiquement une cible selon un critère, mais d&#39;exclure les personnes qui ont déjà été ciblées sur ce critère les fois précédentes.

La population déjà ciblée est mémorisée par instance de workflow et par activité, c&#39;est-à-dire que deux workflows démarrés à partir du même modèle ne partagent pas le même historique. En revanche, deux tâches basées sur la même requête incrémentale pour la même instance de workflow utiliseront le même historique.

La requête est définie selon le même mode que pour les requêtes standard, mais son exécution est planifiée.

**Rubriques connexes :**

* [Cas pratique : mise à jour de la liste trimestrielle à l’aide d’une requête incrémentielle](quarterly-list-update.md)
* [Créer une requête](query.md#creating-a-query)

>[!CAUTION]
>
>Si le résultat de la requête incrémentale est égal à **0** lors de l&#39;une de ses exécutions, le workflow est mis en pause jusqu&#39;à la prochaine exécution programmée de la requête. Les transitions et activités qui suivent la requête incrémentale ne sont alors pas traitée avant l&#39;exécution suivante.

Pour cela :

1. Dans l&#39;onglet **[!UICONTROL Planification &amp; Historique]**, sélectionnez l&#39;option **[!UICONTROL Planifier l&#39;exécution]**. La tâche reste active une fois créée et ne se déclenchera qu&#39;aux heures spécifiées par le planning pour exécuter la requête. En revanche, si l&#39;option est désactivée, la requête est exécutée immédiatement **et une seule fois**.
1. Cliquez sur le bouton **[!UICONTROL Changer]**.

   Dans la fenêtre **[!UICONTROL Assistant d&#39;édition d&#39;un planning]** qui s&#39;affiche, vous pouvez paramétrer le type de périodicité, les événements de la périodicité et la période de validité des événements.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Cliquez sur **[!UICONTROL Terminer]** pour enregistrer le planning.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. La section inférieure de l&#39;onglet **[!UICONTROL Planification &amp; Historique]** permet de sélectionner le nombre de jours d&#39;historique à prendre en compte.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL Jours d&#39;historique]**

      Les destinataires déjà ciblés peuvent être historisés un nombre maximum de jours à partir du jour où ils sont ciblés. Si cette valeur vaut zéro, les destinataires ne sont jamais supprimés de l&#39;historique.

   * **[!UICONTROL Conserver l&#39;historique au démarrage]**

      Cette option permet de ne pas effacer l&#39;historique lors de l&#39;activation de l&#39;activité.

   * **[!UICONTROL Nom de la table SQL]**

      Ce champ permet de surcharger la table SQL par défaut contenant les données d&#39;historique.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Ce triplet de valeurs identifie la population ciblée par la requête. **[!UICONTROL tableName]** est le nom de la table qui mémorise les identifiants de la cible, **[!UICONTROL schema]** est le schéma de la population (habituellement nms:recipient) et **[!UICONTROL recCount]** est le nombre d&#39;éléments dans la table.

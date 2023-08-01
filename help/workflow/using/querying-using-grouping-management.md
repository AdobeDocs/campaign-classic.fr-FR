---
product: campaign
title: Exécuter des requêtes avec gestion des regroupements
description: Découvrez comment exécuter des requêtes avec gestion des regroupements.
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 98%

---

# Requête avec gestion des regroupements {#querying-using-grouping-management}



Vous allez effectuer une requête pour retrouver les domaines d&#39;email ciblés plus de 30 fois au cours de diffusions précédentes.

* Quelle table doit-on sélectionner ?

  La table des destinataires (nms:recipient).

* Quels sont les champs à sélectionner en colonne de sortie ?

  Domaine de l&#39;email et clé primaire (avec un comptage).

* Groupement des données ?

  En fonction du domaine d&#39;email avec un comptage des clés primaires supérieures à 30. Cette opération s&#39;effectue avec l&#39;option **[!UICONTROL Group by + Having]**. **[!UICONTROL Group by + Having]** sert à effectuer un groupement (&quot;group by&quot;) et une sélection de ce qui a été groupé (&quot;having&quot;).

Pour réaliser cet exemple, les étapes sont les suivantes :

1. Ouvrez le **[!UICONTROL Requêteur générique]** et choisissez la table des Destinataires (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. Dans la fenêtre **[!UICONTROL Données à extraire]**, sélectionnez les champs **[!UICONTROL Domaine de l&#39;email]** et **[!UICONTROL Clé primaire]**. Faites un comptage du champ **[!UICONTROL Clé primaire]**.

   Pour plus d&#39;informations sur le comptage d&#39;une clé primaire, consultez [cette section](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Sélectionnez l&#39;option **[!UICONTROL Gérer les groupements (GROUP BY + HAVING)]**.

   ![](assets/query_editor_nveau_29.png)

1. Dans la fenêtre **[!UICONTROL Tris]**, ordonnez les domaines d&#39;email en tri descendant. Pour cela, cochez **[!UICONTROL Oui]** dans la colonne **[!UICONTROL Tri descendant]**. Cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/query_editor_nveau_70.png)

1. Dans **[!UICONTROL Filtrage des données]**, sélectionnez **[!UICONTROL Critères de filtrage]**, puis dans la fenêtre **[!UICONTROL Elément de la cible]**, cliquez sur **[!UICONTROL Suivant]**.
1. Dans la fenêtre **[!UICONTROL Groupement des données]**, sélectionnez le **[!UICONTROL Domaine de l&#39;email]** en cliquant sur **[!UICONTROL Ajouter]**.

   C&#39;est dans cette fenêtre que s&#39;opère le regroupement (GROUP BY) : cette fenêtre ne s&#39;affiche que si l&#39;option **[!UICONTROL Gérer les groupements (GROUP BY + HAVING)]** a été sélectionnée.

   ![](assets/query_editor_blocklist_04.png)

1. Dans la fenêtre **[!UICONTROL Condition de groupement]**, indiquez un comptage de la clé primaire supérieur à 30. Ainsi, seuls les domaines d&#39;email ciblés plus de 30 fois seront retournés en résultat.

   Cette fenêtre s&#39;affiche si la case **[!UICONTROL Gérer les groupements (GROUP BY + HAVING)]** a été cochée au préalable : c&#39;est là que le résultat du groupement est filtré (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. Dans la fenêtre **[!UICONTROL Formatage des données]**, cliquez sur **[!UICONTROL Suivant]** : aucun formatage n&#39;est nécessaire dans cet exemple.
1. Dans la fenêtre de prévisualisation des données, cliquez sur **[!UICONTROL Lancer la prévisualisation des données]** : ici, neuf domaines d&#39;emails différents ciblés plus de 30 fois sont retournés en résultat.

   ![](assets/query_editor_blocklist_06.png)

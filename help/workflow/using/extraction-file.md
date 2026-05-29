---
product: campaign
title: Extraction (fichier)
description: En savoir plus sur l’activité de workflow d’extraction (fichier)
feature: Workflows, Data Management Activity
hide: true
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
TQID: https://experienceleague.adobe.com/PfUnc-SMvRTO9JSmB3BW49fGTXpgJL6fMtnXtSBglMM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a658c786-869b-4194-a780-2594d663adda
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 354
ht-degree: 100%

---

# Extraction (fichier){#extraction-file}



Vous pouvez extraire les données d&#39;une table de workflow dans un fichier externe en utilisant l&#39;activité **[!UICONTROL Extraction (fichier)]**.

>[!CAUTION]
>
>Cette activité doit toujours avoir une transition entrante qui contient les données à extraire.

Pour paramétrer l&#39;extraction des données, les étapes sont les suivantes :

1. Indiquez le nom du fichier de sortie : ce nom peut contenir des variables, insérées à partir du bouton de personnalisation situé à droite du champ.
1. Cliquez sur **[!UICONTROL Editer le format du fichier...]** pour sélectionner les données à extraire.

   ![](assets/s_advuser_extract_file_param.png)

   L’option **[!UICONTROL Gérer les groupements (GROUP BY + HAVING)]** ajoute une étape supplémentaire afin de filtrer sur le résultat final de l’agrégat, par exemple sur tel type de bon de commande, sur les clientes et clients ayant passé plus de 10 commandes, etc.

1. Au besoin, vous pouvez ajouter de nouvelles colonnes dans le fichier de sortie, comme résultat de calculs ou de traitement sur les données. Pour ce faire, cliquez sur l’icône **[!UICONTROL Ajouter]**.

   ![](assets/s_advuser_extract_file_add_col.png)

   Dans la ligne supplémentaire, cliquez sur l&#39;icône **[!UICONTROL Modifier l’expression]** pour définir le contenu de la nouvelle colonne.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Vous accédez alors à la fenêtre de sélection. Cliquez sur **[!UICONTROL Sélection avancée]** pour choisir le processus à appliquer aux données.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Sélectionnez la formule souhaitée dans la liste.

   ![](assets/s_advuser_extract_file_agregate_values.png)

Vous pouvez définir un post-traitement à exécuter pendant l’extraction des données, ce qui vous permet de compresser ou de chiffrer les fichiers. Pour ce faire, la commande souhaitée doit être ajoutée dans l’onglet **[!UICONTROL Script]** de l’activité.

Pour plus d’informations à ce sujet, consultez cette section : [Compression ou chiffrement d’un fichier](../../platform/using/zip-encrypt.md)

![](assets/postprocessing_dataextraction.png)

## Liste des fonctions d&#39;agrégats {#list-of-aggregate-functions}

Les fonctions d&#39;agrégat disponibles sont les suivantes :

* **[!UICONTROL Comptage]** pour compter toutes les valeurs non nulles du champ à agréger, y compris les valeurs en double (du champ agrégé),

  **[!UICONTROL Comptage distinct]** pour compter le nombre total de valeurs différentes et non nulles du champ à agréger (les valeurs en double sont éliminées avant le calcul),

* **[!UICONTROL Somme]** pour calculer la somme des valeurs d&#39;un champ numérique,
* **[!UICONTROL Minimum]** pour calculer le minimum des valeurs d&#39;un champ (numérique ou non),
* **[!UICONTROL Maximum]** pour calculer le maximum des valeurs d&#39;un champ (numérique ou non),
* **[!UICONTROL Moyenne]** pour calculer la moyenne des valeurs d&#39;un champ numérique.

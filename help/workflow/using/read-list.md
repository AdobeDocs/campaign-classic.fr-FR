---
product: campaign
title: Lecture de liste
description: En savoir plus sur l’activité de workflow de lecture de liste
feature: Workflows, Targeting Activity
hide: true
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
TQID: https://experienceleague.adobe.com/BpoGip5vK0telNbSNDqQeEobF-5cXml0fD-Wnr2kUy8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 508
ht-degree: 67%

---

# Lecture de liste{#read-list}



Les données traitées dans un workflow peuvent provenir de listes dont les données ont été préparées et structurées au préalable (lors d&#39;une segmentation antérieure ou d&#39;un chargement de fichier).

L&#39;activité **[!UICONTROL Lecture de liste]** permet de copier les données d&#39;une liste dans la table de travail d&#39;un workflow, comme les données d&#39;une requête. Il est ensuite accessible dans l’ensemble du workflow.

La liste à traiter peut être spécifiée explicitement, calculée par un script ou localisée dynamiquement, selon les options sélectionnées et les paramètres définis dans l&#39;activité **[!UICONTROL Lecture de liste]**.

![](assets/list_edit_select_option_01.png)

Si la liste n&#39;est pas spécifiée explicitement, vous devez indiquer une liste qui sera utilisée comme modèle pour connaître sa structure.

![](assets/s_advuser_list_template_select.png)

Une fois la sélection de la liste paramétrée, vous pouvez ajouter un filtre en utilisant l&#39;option **[!UICONTROL Éditer la requête]** afin de ne conserver qu&#39;une partie de la population pour la suite du workflow.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>Pour pouvoir créer un filtre dans une activité de lecture de liste, la liste concernée doit être de type &quot;fichier&quot;.

Les listes peuvent être créées directement dans Adobe Campaign à partir du lien **[!UICONTROL Profils et Cibles > Listes]** de la page d&#39;accueil. Elles peuvent également être créées dans un workflow en utilisant l&#39;activité **[!UICONTROL Mise à jour de liste]**.

**Exemple : exclure une liste d&#39;adresses d&#39;un envoi**

L&#39;exemple suivant permet d&#39;utiliser une liste d&#39;adresses emails à exclure de la cible d&#39;une diffusion par email.

![](assets/s_advuser_list_read_sample_1.png)

Les profils contenus dans le dossier **Nouveaux contacts** doivent être ciblés par une diffusion. Les adresses e-mail à exclure de la cible sont stockées dans une liste externe. Dans notre exemple, seules les informations relatives aux adresses e-mail sont requises pour l’exclusion.

1. La requête de sélection du dossier **NvxContact** doit permettre de charger l&#39;adresse email des profils sélectionnés, ceci afin de permettre le rapprochement avec les informations contenues dans la liste.

   ![](assets/s_advuser_list_read_sample_0.png)

1. Ici, la liste est stockée dans le dossier **Externes** et son libellé est calculé.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Pour exclure les adresses e-mail de la liste externe de la cible principale, vous devez configurer l’activité d’exclusion et spécifier que le dossier **Nouveaux contacts** contient les données à conserver. Les données conjointes entre cet ensemble et tout autre ensemble entrant provenant de l&#39;activité d&#39;exclusion seront supprimées de la cible.

   ![](assets/s_advuser_list_read_sample_3.png)

   Les règles d&#39;exclusion sont paramétrées dans la section centrale de l&#39;éditeur. Cliquez sur le bouton **[!UICONTROL Ajouter]** pour définir le type d&#39;exclusion à appliquer.

   Vous pouvez définir plusieurs exclusions, selon le nombre de transitions en entrée de l&#39;activité.

1. Dans le champ **[!UICONTROL Ensemble exclu]**, sélectionnez l&#39;activité **[!UICONTROL Lecture de liste]** : ce sont les données contenues dans cette activité qui sont à exclure de l&#39;ensemble principal.

   Dans notre exemple, il s’agit d’une exclusion sur jointure : les données contenues dans la liste seront réconciliées avec celles de l’ensemble principal via le champ qui contient l’adresse e-mail. Pour paramétrer la jointure, sélectionnez **[!UICONTROL Jointures]** dans le champ **[!UICONTROL Changement de dimension]**.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Sélectionnez ensuite le champ correspondant à l’adresse e-mail dans les deux ensembles (Source et Destination). Les colonnes seront alors liées et les destinataires dont l&#39;adresse e-mail figure dans la liste des adresses importées seront exclus de la cible.

---
title: Utilisation de la fonctionnalité de fusion des activités d’Déduplication
description: Découvrez comment utiliser la fonctionnalité de fusion d’activité Déduplication
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 32a14eb99847dc04a582623204bc856c29fa4359
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 8%

---


# Utilisation de la fonctionnalité de fusion des activités de Déduplication {#deduplication-merge}

## A propos de ce cas d&#39;utilisation {#about-this-use-case}

Ce cas d’utilisation décrit l’utilisation de la fonctionnalité **[!UICONTROL Fusionner]** dans l’activité **[!UICONTROL Déduplication]**.

Pour plus d&#39;informations sur cette fonctionnalité, consultez [cette section](../../workflow/using/deduplication.md#merging-fields-into-single-record).

L&#39;activité **[!UICONTROL Déduplication]** est utilisée pour supprimer des lignes de duplicata d&#39;un jeu de données. Dans ce cas d’utilisation, les données présentées ci-dessous sont dupliquées en fonction du champ Courriel.

| Date de dernière modification | Prénom | Nom | Email | Téléphone mobile | Phone |
|-----|------------|-----------|-------|--------------|------|
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 03/10/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Avec la fonctionnalité **[!UICONTROL Fusionner]** de la activité d&#39;Déduplication, vous pouvez configurer un ensemble de règles pour que la déduplication définisse un groupe de champs à fusionner dans un seul enregistrement de données obtenu. Par exemple, avec un ensemble d’enregistrements de duplicata, vous pouvez choisir de conserver le numéro de téléphone le plus ancien ou le nom le plus récent.

## Activation de la fonctionnalité de fusion {#activating-merge}


Pour activer la fonctionnalité de fusion, vous devez d&#39;abord configurer l&#39;activité **[!UICONTROL Déduplication]**. Pour ce faire, procédez comme suit :

1. Ouvrez l’activité, puis cliquez sur le lien **[Modifier la configuration]**.

1. Sélectionnez le champ de rapprochement à utiliser pour la déduplication, puis cliquez sur **[!UICONTROL Suivant]**. Dans cet exemple, nous voulons dédupliquer en fonction du champ de courrier électronique.

   ![](assets/uc_merge_edit.png)

1. Cliquez sur le lien **[!UICONTROL Paramètres avancés]**, puis activez les options **[!UICONTROL Fusionner les enregistrements]** et **[!UICONTROL Utiliser plusieurs critères de fusion d&#39;enregistrements]**.

   ![](assets/uc_merge_advanced_parameters.png)

1. L&#39;onglet **[!UICONTROL Fusionner]** est ajouté à l&#39;écran de configuration de **[!UICONTROL Déduplication]**. Cet onglet permet de spécifier les données à fusionner lors de l&#39;exécution de la déduplication.

## Configuration des champs à fusionner {#configuring-rules}

Voici les règles à utiliser pour fusionner les données en un seul enregistrement :

* Conserver le nom le plus récent (champs de prénom et de nom),
* Conservez le téléphone portable le plus récent,
* Conservez le numéro de téléphone le plus ancien,
* Tous les champs d’un groupe doivent être non nuls pour être éligibles à l’enregistrement final.

Pour configurer ces règles, procédez comme suit :

1. Ouvrez l&#39;onglet **[!UICONTROL Fusionner]**, puis cliquez sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/uc_merge_add.png)

1. Spécifiez l’identifiant et l’étiquette du groupe de champs à fusionner.

   ![](assets/uc_merge_identifier.png)

1. Indiquer les conditions de sélection des enregistrements à prendre en compte.

   ![](assets/uc_merge_filter.png)

1. Triez la date de la dernière modification afin de sélectionner le nom le plus récent.

   ![](assets/uc_merge_sort.png)

1. Sélectionnez les champs à fusionner. Dans cet exemple, nous voulons conserver les champs de prénom et de nom.

   ![](assets/uc_merge_keep.png)

1. Les champs sont ajoutés à l’ensemble de données à fusionner et un nouvel élément est ajouté au schéma de processus.

   Répétez ces étapes pour configurer les champs de téléphone et de téléphone mobile.

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## Résultats {#results}

Après avoir configuré ces règles, les données suivantes sont reçues à la fin de l&#39;activité **[!UICONTROL Déduplication]**.

| Date de modification | Prénom | Nom | Courriel | Téléphone mobile | Téléphone |
-----|------------|-----------|-------|--------------|------|
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 03/10/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Le résultat est fusionné à partir des trois enregistrements selon les règles configurées précédemment. Après comparaison, il est conclu que le nom et le téléphone mobile les plus récents sont utilisés, ainsi que le numéro de téléphone original.

| Prénom | Nom | Courriel | Téléphone mobile | Téléphone |
|------------|-----------|-------|--------------|------|
| Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> Notez que le prénom qui a été fusionné est &quot;Bobby&quot;, car nous avons configuré une règle &quot;Nom&quot; composée à la fois du prénom et du dernier champ.
>
>Par conséquent, &quot;Bob&quot; (prénom le plus récent) n’a pas pu être pris en compte car le champ de nom associé était vide. La combinaison la plus récente de prénoms et de noms a été fusionnée dans l’enregistrement final.

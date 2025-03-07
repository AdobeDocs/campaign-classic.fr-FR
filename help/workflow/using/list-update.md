---
product: campaign
title: Mise à jour de liste
description: Mise à jour de liste
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '538'
ht-degree: 100%

---

# Mise à jour de liste{#list-update}



Une activité de type **Mise à jour de liste** enregistre la population spécifiée par la transition dans une liste de destinataires.

![](assets/s_user_segmentation_update_group.png)

La liste peut être sélectionnée parmi les listes existantes.

Elle peut également être créée en utilisant les options **[!UICONTROL Créer la liste si besoin (Nom calculé)]** et **[!UICONTROL Créer la liste si besoin (Dossier et Nom calculé)]**. Ces options vous permettent de saisir le libellé de votre choix pour créer la liste et éventuellement le dossier dans lequel elle sera enregistrée. Le libellé peut également être calculé automatiquement via l’insertion de champs dynamiques ou d’un script. Les différents champs dynamiques sont disponibles dans le menu pop-up situé à droite du libellé.

![](assets/s_user_segmentation_update_list_calc.png)

Si la liste existe déjà, les destinataires seront ajoutés au contenu existant, sauf si vous cochez l&#39;option **[!UICONTROL Purger la liste si elle existe (sinon la complète)]**. Dans ce cas, le contenu de la liste est supprimé avant de la mettre à jour.

Si vous souhaitez que la liste créée ou mise à jour utilise une autre table que la table des destinataires, cochez l&#39;option **[!UICONTROL Créer ou utiliser une liste ayant sa propre table]**.

Pour utiliser cette option, les tables spécifiques concernées doivent avoir été configurées dans votre instance Adobe Campaign.

Généralement, la sauvegarde d&#39;une cible dans une liste marque la fin d&#39;un workflow. Par défaut, l&#39;activité **[!UICONTROL Mise à jour de liste]** n&#39;a donc pas de transition sortante. Cochez l&#39;option **[!UICONTROL Générer une transition sortante]** pour en ajouter une.

![](assets/do-not-localize/how-to-video.png) [Découvrez comment créer une liste de destinataires à partir de l‘Explorateur dans une vidéo](#video)

## Exemple : mise à jour de liste {#example--list-update}

Dans l&#39;exemple suivant, l&#39;activité de mise à jour de liste suit une requête permettant de cibler les hommes de plus de 30 ans vivant en France. Dans un premier temps, la liste sera créée à partir des résultats de la requête. Elle sera mise à jour à chaque lancement ultérieur du workflow. Elle pourra par exemple être utilisée régulièrement dans le cadre de campagnes d&#39;offres promotionnelles ciblées.

1. Placez une activité de type **[!UICONTROL Mise à jour de liste]** directement à la suite d&#39;une requête puis ouvrez-la pour pouvoir l&#39;éditer.

   Pour plus d&#39;informations sur la création d&#39;une requête dans un workflow, consultez la section [Requête](query.md).

1. Choisissez éventuellement un libellé pour l&#39;activité.
1. Sélectionnez l&#39;option **[!UICONTROL Créer la liste si besoin (Nom calculé)]** afin d&#39;indiquer que la liste sera créée lors de la première exécution du workflow, puis mise à jour lors des exécutions suivantes.
1. Sélectionnez le dossier dans lequel vous souhaitez enregistrer la liste.
1. Saisissez le libellé de la liste. Insérez éventuellement des champs dynamiques afin de calculer automatiquement le nom de la liste. Dans cet exemple, la liste porte le même nom que la requête, afin d&#39;identifier plus simplement son contenu.
1. Laissez l&#39;option **[!UICONTROL Purger la liste si elle existe (sinon la complète)]** sélectionnée afin de supprimer les destinataires ne correspondant plus aux critères de ciblage et d&#39;y insérer les nouveaux.
1. Laissez également l&#39;option **[!UICONTROL Créer ou utiliser une liste ayant sa propre table]** sélectionnée.
1. Laissez l&#39;option **[!UICONTROL Générer une transition sortante]** désélectionnée.
1. Cliquez sur **[!UICONTROL Ok]** puis lancez l&#39;exécution du workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   La liste de destinataires correspondante est alors créée ou mise à jour.

## Paramètres d&#39;entrée {#input-parameters}

* tableName
* schema

Identifie la population à sauvegarder dans le groupe.

## Paramètres de sortie {#output-parameters}

* groupId : Identifiant du groupe.

## Tutoriel vidéo {#video}

Cette vidéo montre comment créer une liste de destinataires à partir de l’Explorateur.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

D’autres vidéos pratiques sur Campaign Classic sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).

---
title: Créer et gérer des listes
seo-title: Créer et gérer des listes
description: Créer et gérer des listes
seo-description: null
page-status-flag: never-activated
uuid: 17d1a7d0-a728-490e-a820-19f469fddbcd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 9fc243b2-7b7b-4083-83f6-04c12336492d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Créer et gérer des listes{#creating-and-managing-lists}

## A propos des listes dans Adobe Campaign {#about-lists-in-adobe-campaign}

Une liste est un ensemble statique de profils qui peut être ciblé dans les actions de diffusion ou mis à jour lors d&#39;opérations d&#39;import ou lors de l&#39;exécution d&#39;un workflow. Par exemple, une population extraite de la base via une requête peut alimenter une liste.

Des diffusions (par email, SMS ou autre) peuvent alors être mises en place à destination de ces différentes listes, dans le respect des règles déontologiques de la gestion du consentement (permission marketing).

Les listes sont créées et gérées via le **[!UICONTROL Lists]** lien de l’ **[!UICONTROL Profiles and targets]** onglet.

![](assets/s_ncs_user_interface_group_link.png)

Dans Adobe Campaign, deux types de listes sont disponibles :

* **[!UICONTROL Group]** type : Les listes de **[!UICONTROL Group]** type appartiennent à une liste **statique** de personnes sélectionnées selon des critères spécifiques. La liste ressemble à un instantané d’un ensemble de profils. Veuillez noter qu&#39;il n&#39;est pas mis à jour automatiquement en cas d&#39;ajout de profils à la base de données.

   For more information on how to create a **[!UICONTROL Group]** type list, refer to this [page](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** type : Les listes de **[!UICONTROL List]** types vous permettent d’utiliser des processus pour créer et gérer des listes. Il s’agira de listes spécifiques résultant des importations de données, qui peuvent être mises à jour via l’activité de **[!UICONTROL List update]** flux de travaux dédiée.

   Contrairement à la liste **[!UICONTROL Group]** de types, cette liste peut être automatiquement mise à jour avec une **[!UICONTROL Scheduler]** activité. Notez que pour un exemple sur la création de listes de **[!UICONTROL List]** types, reportez-vous à [cette page](../../workflow/using/list-update.md).

## Création d&#39;une liste de profils à partir d&#39;un groupe {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** les listes de types créées via le **[!UICONTROL Profiles and targets]** lien doivent être basées sur la table de profil Adobe Campaign par défaut (nms:destinataire).

>[!NOTE]
>
>Pour créer des listes contenant d&#39;autres types de données, vous devez passer par un workflow. Par exemple, en utilisant une requête sur la table des visiteurs puis une mise à jour de liste, vous pouvez créer une liste de visiteurs. Pour plus d&#39;informations sur les workflows, consultez [cette section](../../workflow/using/about-workflows.md).

To create a new **[!UICONTROL Group]** type list, apply the following steps:

1. Cliquez sur le **[!UICONTROL Create]** bouton et sélectionnez **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Enter the information in the **[!UICONTROL Edit]** tab of the list creation window.

   * Enter the list name in the **[!UICONTROL Label]** field and, if necessary, change the internal name.
   * Ajoutez une description pour cette liste.
   * Vous pouvez définir une date d&#39;expiration : lorsque cette date est atteinte, la liste est purgée et automatiquement supprimée.

      ![](assets/list_expiration_date.png)

1. In the **[!UICONTROL Content]** tab, click **[!UICONTROL Add]** to select the profiles belonging to the list.

   ![](assets/s_ncs_user_add_group.png)

1. Cliquez sur **[!UICONTROL Save]** pour enregistrer la liste. Il est ensuite ajouté à l’aperçu des listes.

You can create new profiles directly from the &#39;add profiles&#39; window by clicking **[!UICONTROL Create]**. The profile will be added to the database.

![](assets/s_ncs_user_new_recipient_from_group.png)

La liste des profils peut être configurée comme les autres listes. Voir [Configuration des listes](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Associer les données à une liste {#linking-data-to-a-list}

>[!NOTE]
>
>Linking data to a list can only been done with a **[!UICONTROL Group]** type list.

Les profils d&#39;un ensemble de profils peuvent être filtrés puis associés à une liste. Des actions de diffusions pourront alors être menées sur cette liste afin de cibler les profils. Pour regrouper les profils :

1. Sélectionnez les profils et cliquez avec le bouton droit de la souris.
1. Sélectionner **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Select the desired list or create a new list using the **[!UICONTROL Create]** button, then click **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Cliquez sur le **[!UICONTROL Start]** bouton.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

L’ **[!UICONTROL Recreate the list]** option supprime le contenu précédent de la liste. Ce mode est optimisé car aucune requête n’est nécessaire pour vérifier si les profils sont déjà liés à la liste.

Si vous désélectionnez l’ **[!UICONTROL No trace of this job is saved in the database]** option, vous pouvez sélectionner (ou créer) le dossier d’exécution dans lequel seront stockées les informations liées à ce processus.

La section supérieure de la fenêtre vous permet de surveiller l’exécution. Le **[!UICONTROL Stop]** bouton permet d’arrêter le processus. Les contacts déjà traités seront liés à la liste.

You can monitor the process via the **[!UICONTROL Lists]** tab on the profiles concerned by this operation:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Vous pouvez également modifier la liste sur la page d’accueil d’Adobe Campaign : cliquez sur le **[!UICONTROL Profiles and Targets > Lists]** menu et sélectionnez la liste concernée. L’ **[!UICONTROL Content]** onglet affiche les profils liés à cette liste.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Retirer un profil d&#39;une liste {#removing-a-profile-from-a-list}

Pour supprimer un profil d&#39;une liste, vous pouvez :

* Edit the list, select the profile in the **[!UICONTROL Content]** tab, then click the **[!UICONTROL Delete]** icon.

   ![](assets/list_remove_a_recipient.png)

* Edit the profile, click the **[!UICONTROL List]** tab, then click the **[!UICONTROL Delete]** icon.

   ![](assets/recipient_remove_a_list.png)

## Supprimer une liste de profils {#deleting-a-list-of-profiles}

Vous pouvez supprimer une ou plusieurs listes de la liste des groupes dans l’arborescence Adobe Campaign. Pour ce faire, modifiez l’arborescence via le **[!UICONTROL Advanced > Explorer]** lien dans la page d’accueil d’Adobe Campaign. Sélectionnez le ou les groupes concernés et cliquez avec le bouton droit de la souris. Sélectionner **[!UICONTROL Delete]**. Un message d’avertissement vous demande de confirmer la suppression.

>[!NOTE]
>
>Lorsque vous supprimez une liste, les profils qui appartenaient à cette liste ne sont pas affectés. Les données de leur profil seront toutefois mises à jour.


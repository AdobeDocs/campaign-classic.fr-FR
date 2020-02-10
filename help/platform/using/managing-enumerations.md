---
title: Gestion des énumérations
seo-title: Gestion des énumérations
description: Gestion des énumérations
seo-description: null
page-status-flag: never-activated
uuid: 23ad4cae-237f-48e5-b111-cfe88cf0b864
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 7674c856-2b64-4a85-9ffa-3e14a142028e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Gestion des énumérations{#managing-enumerations}

## A propos des énumérations {#about-enumerations}

Une énumération est une liste de valeurs proposées par le système pour renseigner certains champs. Les énumérations permettent de standardiser les valeurs de ces champs et de faciliter leur saisie ou leur utilisation au sein de requêtes.

La liste de valeurs apparaît sous forme d&#39;une liste déroulante dans laquelle vous pouvez sélectionner la valeur à attribuer au champ. La liste déroulante permet également la saisie prédictive : l&#39;opérateur saisit les premières lettres et l&#39;application complète d&#39;elle-même la suite.

Un certain nombre de champs de la console ont ainsi été définis avec ce type d&#39;énumération. Ces énumérations sont dites &quot;ouvertes&quot; si vous pouvez ajouter des valeurs par une saisie directe dans le champ correspondant.

## Accès aux valeurs {#access-to-values}

The values for this type of field are defined and overall administration of these fields (adding/deleting a value) is performed via the **[!UICONTROL Administration > Platform > Enumerations]** node of the tree.

![](assets/s_ncs_user_itemized_list_node.png)

* La section supérieure propose la liste des champs pour lesquels une énumération a été définie.
* La section inférieure liste les valeurs proposées. Ces valeurs seront reprises dans les éditeurs utilisant ce champ.

   ![](assets/s_ncs_user_itemized_list_values.png)

   To create a new enumeration value, click **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_itemized_list.png)

   Si l’ **[!UICONTROL Open]** option est sélectionnée, l’utilisateur peut ajouter une nouvelle valeur de liste détaillée directement dans le champ correspondant. Un message de confirmation vous permet de créer cette valeur.

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* If the **[!UICONTROL Closed]** option is selected, users will not be able to create new values, but merely choose from the values available.

## Normaliser les données {#standardizing-data}

### A propos de la gestion des alias {#about-alias-cleansing}

Dans les champs énumérés, il est possible de saisir d&#39;autres valeurs que les valeurs de l&#39;énumération. Ces valeurs peuvent être stockées telles quelles ou faire l&#39;objet d&#39;une normalisation.

>[!CAUTION]
>
>La normalisation des données est un processus critique qui affecte les données de la base. En effet, Adobe Campaign procède à la mise à jour en masse de données, ce qui peut impliquer la suppression de certaines valeurs. Cette opération est donc réservée à des utilisateurs avertis.

En effet, la valeur saisie peut être :

* Added to the itemized list values: in this case the **[!UICONTROL Open]** option must be selected,
* remplacée automatiquement par son  : cet alias doit être défini dans l&#39;onglet **[!UICONTROL Alias]** Alias de l&#39;énumération,
* stockée dans la liste des alias : un alias pourra lui être attribué ultérieurement.

   >[!NOTE]
   >
   >If you need to use data cleansing capabilities, select the **[!UICONTROL Alias cleansing]** option in the itemized list.

### Utilisation des alias {#using-aliases}

Cette option **[!UICONTROL Alias cleansing]** permet d’utiliser des alias pour la liste détaillée sélectionnée. Lorsque cette option est sélectionnée, l’ **[!UICONTROL Alias]** onglet s’affiche au bas de la fenêtre.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Créer un alias {#creating-an-alias}

To create an alias, click **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Saisissez l&#39;alias à transformer et la valeur qui sera appliquée et cliquez sur **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Vérifiez les paramètres avant de valider cette opération.

>[!CAUTION]
>
>Une fois cette étape validée, il n&#39;est plus possible de récupérer les valeurs saisies antérieurement : les valeurs sont remplacées.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

Thus, when a user enters the value **NEILSEN** in a &quot;company&quot; field (in the Adobe Campaign console or in a form), it will automatically be replaced by the value **NIELSEN Ltd**. Value replacement is performed by the **Alias cleansing** workflow. Reportez-vous à [Exécution du nettoyage](#running-data-cleansing)des données.

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Conversion des valeurs en alias {#converting-values-into-aliases}

To convert an enumeration value into an alias, right-click in the list of values and choose **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Choose the values you want to convert and click **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Click **[!UICONTROL Start]** to run the conversion.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

Une fois l&#39;exécution terminée, l&#39;alias est ajouté dans la liste des alias.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Récupération des apparitions des alias {#retrieving-alias-hits}

Les valeurs saisies par les utilisateurs peuvent être converties en alias. En effet, lorsque l’utilisateur saisit une valeur qui n’est pas incluse dans la liste détaillée, la valeur est stockée dans l’ **[!UICONTROL Alias]** onglet.

The **Alias cleansing** technical workflow recovers these values every night to update itemized list. Reportez-vous à la section [Exécution du nettoyage des données](#running-data-cleansing)

Si nécessaire, la **[!UICONTROL Hits]** colonne peut afficher le nombre de fois où cette valeur a été saisie. Le calcul de cette valeur peut prendre du temps et de la mémoire. Pour plus d’informations, reportez-vous à la section [Calcul des occurrences](#calculating-entry-occurrences)d’entrée.

### Exécution de la normalisation des données {#running-data-cleansing}

Le nettoyage des données est effectué par le processus **[!UICONTROL Alias cleansing]** technique. Les configurations définies pour les énumérations sont appliquées pendant l’exécution. Reportez-vous à la section Processus [de nettoyage des](#alias-cleansing-workflow)alias.

Cleansing can be triggered via the **[!UICONTROL Cleanse values...]** link.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

The **[!UICONTROL Advanced parameters...]** link lets you set the date starting from which collected values are taken into account.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Click the **[!UICONTROL Start]** button to run data cleansing.

#### Calcul des occurrences de saisie {#calculating-entry-occurrences}

Le **[!UICONTROL Alias]** sous-onglet d’une liste détaillée peut afficher le nombre d’occurrences d’un alias parmi toutes les valeurs saisies. Ces informations sont une estimation et seront affichées dans la **[!UICONTROL Hits]** colonne.

>[!CAUTION]
>
>Le calcul des occurrences de saisie d&#39;un alias peut être long. Cette fonctionnalité doit par conséquent être utilisée avec précaution.

Vous pouvez exécuter le calcul des accès manuellement via le **[!UICONTROL Cleanse values...]** lien. Pour ce faire, cliquez sur le **[!UICONTROL Advanced parameters...]** lien et sélectionnez une ou plusieurs options.

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: vous pouvez ainsi mettre à jour les accès qui ont déjà été calculés, en fonction de la date saisie.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: vous permet d’exécuter le calcul sur l’ensemble de la plateforme Adobe Campaign.

Vous pouvez également créer un workflow dédié afin que ce calcul s&#39;exécute automatiquement pour une période donnée, par exemple toutes les semaines.

To do this, create a copy of the **[!UICONTROL Alias cleansing]** workflow, change the scheduler and use the following settings in the **[!UICONTROL Enumeration value cleansing]** activity:

* **-updateHits** pour mettre à jour le nombre d&#39;accès d&#39;alias,
* **-updateHits:full** pour recalculer toutes les apparitions des alias.

#### Workflow de gestion des alias {#alias-cleansing-workflow}

Le workflow **Gestion des alias** exécute la normalisation des valeurs d&#39;énumération. Par défaut, sa fréquence d&#39;exécution est quotidienne.

Il est accessible via le **[!UICONTROL Administration > Production > Technical workflows]** noeud.

![](assets/s_ncs_user_itemized_list_alias_wf.png)


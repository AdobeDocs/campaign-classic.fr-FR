---
title: Utilisation d'agrégats
seo-title: Utilisation d'agrégats
description: Utilisation d'agrégats
seo-description: null
page-status-flag: never-activated
uuid: 70556745-56b2-4f22-bbc5-7f8106fb0d4a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9ca649b4-2226-4cfe-bae1-4632c421975b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Utilisation d&#39;agrégats{#using-aggregates}

Ce cas pratique présente l&#39;identification automatique des derniers destinataires ajoutés dans la base.

Pour cela, la date de création des destinataires dans la base est comparée à la dernière date connue à laquelle un destinataire a été créé à l&#39;aide d&#39;un agrégat. Tous les destinataires créés le même jour seront ainsi sélectionnés.

Pour parvenir à effectuer un filtre du type **Date de création = max (Date de création)** sur les destinataires, il est nécessaire de passer par un workflow afin de réaliser les étapes suivantes :

1. Récupérez les destinataires de la base de données à l’aide d’une requête de base. Pour plus d&#39;informations sur cette étape, consultez [Création d&#39;une requête](../../workflow/using/query.md#creating-a-query).
1. Calculer la dernière date connue de création d&#39;un destinataire via le résultat de la fonction d&#39;agrégation **max (Date de création)**.
1. Lier chaque destinataire au résultat de la fonction d&#39;agrégation dans un même schéma.
1. Filtrer les destinataires à l&#39;aide de l&#39;agrégat via le schéma édité.

![](assets/datamanagement_usecase_1.png)

## Etape 1 : calculer le résultat de l&#39;agrégat {#step-1--calculating-the-aggregate-result}

1. Créez une requête. Ici, le but est de calculer la dernière date de création connue parmi la totalité des destinataires de la base. La requête ne contient donc pas de filtre.
1. Sélectionner **[!UICONTROL Add data]**.
1. Dans les fenêtres qui s’ouvrent, sélectionnez **[!UICONTROL Data linked to the filtering dimension]** puis **[!UICONTROL Filtering dimension data]**.
1. Dans la **[!UICONTROL Data to add]** fenêtre, ajoutez une colonne qui calcule la valeur maximale du champ Date **de** création dans la table des destinataires. Vous pouvez utiliser l’éditeur d’expression ou saisir **max(@created)** directement dans un champ de la **[!UICONTROL Expression]** colonne. Then click the **[!UICONTROL Finish]** button.

   ![](assets/datamanagement_usecase_2.png)

1. Cliquez **[!UICONTROL Edit additional data]** alors **[!UICONTROL Advanced parameters...]**. Cochez l’ **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** option.

   Cette option permet de ne pas renvoyer tous les destinataires comme résultat et de ne conserver que les données explicitement ajoutées. Dans le cas présent, il s&#39;agit de la dernière date à laquelle un destinataire a été créé.

   Laissez l’ **[!UICONTROL Remove duplicate rows (DISTINCT)]** option cochée.

## Etape 2 : lier les destinataires et le résultat de la fonction d&#39;agrégation {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Afin de lier la requête portant sur les destinataires à la requête servant au calcul de la fonction d&#39;agrégation, il est nécessaire d&#39;utiliser une activité d&#39;édition du schéma.

1. Définissez la requête portant sur les destinataires comme ensemble principal.
1. In the **[!UICONTROL Links]** tab, add a new link and enter the information in the window that opens as follows:

   * Sélectionnez le schéma temporaire correspondant à l&#39;agrégat. Les données de ce schéma seront ajoutées aux membres de l&#39;ensemble principal.
   * Select **[!UICONTROL Use a simple join]** to link the aggregate result to every recipient of the main set.
   * Enfin, spécifiez que le lien est un **[!UICONTROL Type 11 simple link]**.
   ![](assets/datamanagement_usecase_3.png)

Le résultat de la fonction d&#39;agrégation est ainsi lié à chaque destinataire.

## Step 3: Filtering recipients using the aggregate. {#step-3--filtering-recipients-using-the-aggregate-}

Une fois le lien établi, le résultat de l&#39;agrégat et les destinataires font partie du même schéma temporaire. Il est alors possible de réaliser un filtrage sur ce schéma afin d&#39;effectuer la comparaison entre la date de création des destinataires et la dernière date de création connue, représentée par la fonction d&#39;agrégation. Ce filtrage est réalisé grâce à une activité de partage.

1. In the **[!UICONTROL General]** tab, select **Recipients** as the targeting dimension and **Edit schema** as the filtering dimension (to filter on the inbound transition schema activity).
1. Dans l’ **[!UICONTROL subsets]** onglet, sélectionnez **[!UICONTROL Add a filtering condition on the inbound population]** puis cliquez **[!UICONTROL Edit...]**.
1. Via l&#39;éditeur d&#39;expression, ajoutez un critère d&#39;égalité entre la date de création des destinataires et la date de création calculée par l&#39;agrégat.

   Les champs de type date de la base de données sont généralement enregistrés à la milliseconde près. Il faut alors étendre ces derniers à la journée entière afin de ne pas limiter le filtre aux destinataires créés à la même milliseconde.

   Pour cela, utilisez la fonction **ToDate** disponible via l&#39;éditeur d&#39;expression, qui convertit les dates et heures en dates simples.

   Les expressions à utiliser pour le critère sont donc :

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`, où expr#### correspond à l&#39;agrégat spécifié dans la requête de fonction d&#39;agrégation.
   ![](assets/datamanagement_usecase_4.png)

Le résultat de l&#39;activité de partage correspond ainsi aux destinataires créés le même jour que la dernière date de création connue.

Vous pouvez par la suite ajouter d&#39;autres activités telle qu&#39;une mise à jour de liste ou une diffusion afin de compléter votre workflow.

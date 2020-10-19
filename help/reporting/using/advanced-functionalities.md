---
title: Fonctionnalités avancées
description: Fonctionnalités avancées
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
translation-type: tm+mt
source-git-commit: 2a82493deada11cb22ef37d215b6eae8274ce890
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 54%

---


# Fonctionnalités avancées{#advanced-functionalities}

En tant qu’utilisateur technique, en plus des propriétés [](../../reporting/using/properties-of-the-report.md)générales, vous pouvez tirer parti de fonctionnalités avancées pour configurer vos rapports, telles que :

* Créez des requêtes complexes pour traiter les données dans une activité de **script** . [En savoir plus](#script-activity)

* Ajoutez un script externe à exécuter côté serveur ou client. [En savoir plus](#external-script)

* Appelez un rapport avec une **activité de vidage** . [En savoir plus](#calling-up-another-report)

* Ajoutez un paramètre d’URL à un rapport pour le rendre plus accessible. [En savoir plus](#calling-up-another-report)

* Ajoutez les variables à utiliser dans le contexte du rapport. [En savoir plus](#adding-variables)

## Utilisation de scripts {#adding-a-script}

### Scripts externes de référence {#external-script}

Vous pouvez référencer des codes JavaScript qui seront exécutés côté client et/ou serveur lorsque la page du rapport sera appelée.

Pour cela :

1. Edit the [report properties](../../reporting/using/properties-of-the-report.md) and click the **[!UICONTROL Scripts]**.
1. Cliquez sur **[!UICONTROL Ajouter]** et sélectionnez le script à référencer.
1. Choisissez ensuite le mode d&#39;exécution.

   Si vous ajoutez plusieurs scripts, utilisez les flèches de la barre d&#39;outils pour définir leur ordre d&#39;exécution.

   ![](assets/reporting_custom_js.png)

Pour une exécution normale côté client, les scripts référencés doivent être écrits en JavaScript et doivent être compatibles avec les navigateurs courants. Voir à ce propos [cette section](../../web/using/web-forms-answers.md).

### Adding a Script activity {#script-activity}

Lors de la [conception de votre rapport](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), utilisez l&#39;activité **[!UICONTROL Script]** pour traiter les données et créer facilement des requêtes complexes qui n&#39;activent pas le langage SQL. Vous pouvez saisir directement votre requête dans la fenêtre de script.

L’onglet **[!UICONTROL Textes]** vous permet de définir des chaînes de texte. Elles peuvent ensuite être utilisées avec la syntaxe suivante : **$(Identifiant)**. Pour plus d’informations sur l’utilisation de textes, voir [Ajouter un en-tête et un pied de page](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Il est FORTEMENT déconseillé d&#39;utiliser du code Javascript pour créer des agrégats.

Si vous souhaitez créer un historique de votre rapport, vous devez rajouter la ligne suivante à votre requête JavaScript, afin de conserver vos données historisées :

```
if( ctx.@_historyId.toString().length == 0 )
```

Sinon, seules les données actives s’afficheront.

## Ajouter un paramètre d’URL {#defining-additional-settings}

The **[!UICONTROL Parameters]** tab of the [report properties](../../reporting/using/properties-of-the-report.md) lets you define additional settings for the report: these settings will be passed into the URL during the call up.

>[!CAUTION]
>
>Pour des questions de sécurité, ces paramètres doivent être utilisés avec précaution.

Pour créer un nouveau paramètre :

1. Cliquez sur le bouton **[!UICONTROL Ajouter]** et saisissez le nom du paramètre.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Au besoin, indiquez si ce paramètre doit être obligatoire.

1. Choisissez le type de paramètre à créer : **[!UICONTROL Filtre]** ou **[!UICONTROL Variable]**.

   L&#39;option **[!UICONTROL Filtrer les entités]** permet d&#39;utiliser un champ de la base comme paramètre.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Les données sont directement récupérées au niveau de l&#39;entité : **ctx/recipient/@account**.

   L&#39;option **[!UICONTROL Variable]** permet de créer ou sélectionner une variable qui sera passée en paramètre de l&#39;URL et pourra être utilisée au niveau des filtres.

Les **[!UICONTROL En-têtes HTTP de réponse]** permettent d’empêcher le détournement de clics (clickjacking) si la page du rapport est incorporée dans une page HTML à l’aide d’iframe. Pour éviter le détournement de clics, vous pouvez choisir le comportement de l’**[!UICONTROL En-tête X-Frame-Options]** :

* **[!UICONTROL Aucun]** : le rapport ne comporte pas d’**[!UICONTROL En-tête X-Frame-Options]**.
* **[!UICONTROL Même origine]** : défini par défaut pour les nouveaux rapports et les rapports republiés. Le nom d’hôte sera identique à l’URL du rapport.
* **[!UICONTROL Refuser]** : le rapport ne peut pas être incorporé dans une page HTML à l’aide d’iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Ajouter des variables {#adding-variables}

L&#39;onglet **[!UICONTROL Variables]** contient la liste des variables paramétrées dans le rapport. Ces variables sont exposées dans le contexte du rapport et utilisables dans les calculs.

Cliquez sur le bouton **[!UICONTROL Ajouter]** pour créer une nouvelle variable.

Pour consulter la définition d&#39;une variable, sélectionnez-la et cliquez sur le bouton **[!UICONTROL Détail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Cas d’utilisation : utilisation de variables et de paramètres dans un rapport

Dans l&#39;exemple vidéo ci-dessous, vous apprendrez comment ajouter un paramètre &quot;_type&quot; pour créer différentes vues d&#39;un rapport, en fonction de la valeur de cet attribut.

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## Appeler un autre rapport {#calling-up-another-report}

A **Jump** activity is like a transition without an arrow: it lets you go from one activity to another or access another report.

---
title: Fonctionnalités avancées
seo-title: Fonctionnalités avancées
description: Fonctionnalités avancées
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Fonctionnalités avancées{#advanced-functionalities}

## Ajouter un script {#adding-a-script}

### Activité Script {#script-activity}

Cette activité vous permet de traiter vos données et créer facilement des requêtes complexes que ne permettrait pas le langage SQL.

Il vous suffit de taper votre requête dans la fenêtre de script.

L’onglet **[!UICONTROL Textes]** permet de définir des chaînes de texte. Ils peuvent ensuite être utilisés avec la syntaxe suivante : **$(Identifiant)**. Pour plus d’informations sur l’utilisation de textes, voir [Ajout d’un en-tête et d’un pied de page](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Il est FORTEMENT déconseillé d&#39;utiliser du code Javascript pour créer des agrégats.

Si vous souhaitez créer un historique de votre rapport, vous devez rajouter la ligne suivante à votre requête JavaScript, afin de conserver vos données historisées :

```
if( ctx.@_historyId.toString().length == 0 )
```

Dans le cas contraire, les données en cours seront affichées.

### Script externe {#external-script}

Vous pouvez ajouter un script externe qui sera exécuté côté serveur et/ou côté client. Pour cela :

1. Editez les propriétés du rapport et cliquez sur l&#39;onglet **[!UICONTROL Scripts]**.
1. Cliquez sur **[!UICONTROL Ajouter]** et sélectionnez le script à référencer.
1. Choisissez ensuite le mode d&#39;exécution.

   Si vous ajoutez plusieurs scripts, utilisez les flèches de la barre d&#39;outils pour définir leur ordre d&#39;exécution.

   ![](assets/reporting_custom_js.png)

## Appeler un autre rapport {#calling-up-another-report}

### Activité Saut {#jump-activity}

Un saut est comme une transition sans flèche : il permet de passer d&#39;une activité à une autre ou d&#39;accéder à un autre rapport.

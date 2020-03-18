---
title: À propos du modèle de données  Adobe Campaign Classic
description: Ce décrit les bases du modèle de données  Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 87966db35779f0e6a4b09a1a3ba1c30d4d002518

---


# About the Campaign data model{#about-data-model}

Cette section décrit les bases du modèle de données  Adobe Campaign Classic pour une meilleure compréhension des tableaux intégrés et de leurs interactions.

Le modèle de données conceptuelles de la base de données Adobe Campaign  est constitué d’un ensemble de tables intégrées et de leur interaction.

Pour accéder à la description de chaque tableau, accédez à **[!UICONTROL Admin > Configuration > Data schemas]**, sélectionnez une ressource dans le et cliquez sur l’ **[!UICONTROL Documentation]** onglet.

![](assets/data-model_documentation-tab.png)

Pour plus d’informations sur la description du modèle de données Campaign Classic par défaut, reportez-vous à cette [section](../../configuration/using/data-model-description.md).

La structure physique et logique des données véhiculées dans l&#39;application est décrite en XML et respecte une grammaire propre à Adobe Campaign appelée schéma. Pour en savoir plus sur  Adobe Campaign, lisez cette [section](../../configuration/using/about-schema-reference.md).

## Présentation {#data-model-overview}

 Adobe Campaign s&#39;appuie sur une base de données relationnelle contenant des tables qui sont reliées entre elles. La structure de base du modèle de données Adobe Campaign  peut être décrite comme suit.

>[!NOTE]
>
>Pour plus d’informations sur l’architecture du modèle de données Campaign et les bonnes pratiques connexes, reportez-vous à cette [section](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### Tableau {#recipient-table}

Le modèle de données repose sur un tableau principal qui est par défaut le tableau (**NmsRecipient**). Ce tableau permet de stocker tous les  marketing.

Pour plus d’informations sur le tableau du, reportez-vous à cette [section](#default-recipient-table).

### Tableau {#delivery-table}

Le modèle de données comprend également une partie dédiée au stockage de tous les  de  marketing. Généralement, il s&#39;agit de la table  (**NmsDelivery**). Chaque enregistrement de ce tableau représente une action  ou un . Il contient tous les paramètres nécessaires pour effectuer des  tels que les  de, le contenu, etc.

### Journaux des tableaux {#log-tables}

Une autre partie du modèle de données permet de stocker temporairement tous les journaux associés à l’exécution des campagnes.

 sont tous des messages envoyés aux ou aux périphériques sur tous les . Le tableau de  principal du (**NmsBroadLog**) contient le  pour tous les.
Le tableau de  principal (**NmsTrackingLog**) stocke le  pour tous les. Le  fait référence aux réactions des, telles que les ouvertures de courrier électronique et les clics. Chaque réaction correspond à un journal de suivi.
Les  de et les  de sont supprimés après une certaine période, qui est spécifiée dans le  et qui peut être modifiée. Il est donc vivement recommandé d’exporter les journaux régulièrement.

### Tableaux techniques {#technical-tables}

Enfin, une partie du modèle de données est constituée de données techniques utilisées pour le processus applicatif, y compris les opérateurs et les droits d’utilisateur (**NmsGroup**), les dossiers (**XtkFolder**).

## Utilisation du tableau de par défaut {#default-recipient-table}

Le tableau de prêt à l’emploi dans  Adobe Campaign fournit un bon point de départ pour la création de votre modèle de données. Il comporte un certain nombre de champs prédéfinis et de liens de tableau qui peuvent être facilement étendus. Cela s’avère particulièrement utile lorsque vous ciblez principalement des, car il s’adapte à un modèle de données centré sur le.

Les avantages de l’utilisation du tableau de standard sont les suivants :

* Utilisation prête à l’emploi avec des fonctionnalités telles que  , de base,social, etc.
* Fourniture d’une base de données marketing avec un modèle de données centré sur les.
* Mise en oeuvre plus rapide.
* Facilité de maintenance par l&#39;assistance et les partenaires.

Il est toutefois possible d’étendre le tableau du, mais pas de réduire le nombre de champs ou de liens dans le tableau.

>[!IMPORTANT]
>
>Il est recommandé de ne pas supprimer les champs (même s’ils sont inutiles) dans le tableau du, car cela peut entraîner des erreurs dans les modules intégrés.

En outre, comme le tableau du fait partie du produit, le tableau et le formulaire qui lui est associé évoluent au fur et à mesure que le produit change. Par conséquent, une maintenance supplémentaire est nécessaire pour vérifier que les extensions sont toujours valides lors de la mise à niveau.

## Extension du modèle de données {#extending-data-model}

Lorsque vous commencez par  Adobe Campaign, vous devez évaluer le modèle de données par défaut afin de vérifier quel tableau est le mieux adapté au stockage de vos données marketing.

Le cas échéant, vous pouvez utiliser le tableau de par défaut avec les champs prêts à l’emploi, comme décrit dans cette [section](#default-recipient-table).

Si nécessaire, vous pouvez l’étendre à l’aide de deux mécanismes :

* Etendez un tableau existant avec de nouveaux champs. Par exemple, vous pouvez ajouter un nouveau champ &quot;Fidélité&quot; à la table du.
* Créez une table, par exemple une table &quot;Achat&quot; répertoriant tous les achats effectués par chaque de la base de données et liez-la à la table.

Pour plus d’informations sur la configuration des  pour étendre le modèle de données conceptuelles, voir [A propos de l’édition](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>L’extension du modèle de données est réservée aux utilisateurs avancés.

## Using a custom recipient table {#custom-recipient-table}

Lors de la conception de votre modèle de données  Adobe Campaign, vous pouvez utiliser le tableau [de prêt à l’emploi ou décider de créer un tableau de](#default-recipient-table)non standard pour stocker vos  marketing.

En effet, si votre modèle de données ne correspond pas à la structure centrée sur le, vous pouvez configurer d’autres tables comme  de dans  Adobe Campaign. Par exemple, cela peut s’avérer pertinent lorsque vous devez des ménages, des comptes (comme des téléphones portables) et des /sites de plutôt que simplement des.

>[!NOTE]
>
>Dans ce cas, vous devrez créer un nouveau  [](../../configuration/using/target-mapping.md).

Tous les principes et étapes nécessaires lors de l’utilisation d’un tableau de personnalisé sont détaillés dans cette [section](../../configuration/using/about-custom-recipient-table.md).

Les avantages de l’utilisation d’un tableau de personnalisé sont les suivants :

### Modèle de données flexible {#flexible-data-model}

Le tableau de prêt à l’emploi est inutile si vous n’avez pas besoin de la plupart des champs du tableau de ou si le modèle de données n’est pas centré sur les.

### Évolutivité {#scalability}

Les gros volumes nécessitent un tableau rationalisé avec peu de champs pour une conception efficace. Le tableau de prêt à l’emploi comporte trop de champs inutiles, ce qui peut avoir un impact sur les performances et un manque d’efficacité.

### Emplacement des données {#data-location}

Si les données résident dans une base de données marketing externe existante, il peut s’avérer nécessaire de faire trop d’efforts pour utiliser la table de prête à l’emploi. Il est plus simple de créer une nouvelle structure basée sur une structure existante.

### Migration aisée {#easy-migration}

Aucune maintenance n’est nécessaire pour vérifier que toutes les extensions sont toujours valides lors de la mise à niveau.

>[!IMPORTANT]
>
>L’utilisation d’un tableau de personnalisé est réservée aux utilisateurs avancés et est soumise à certaines restrictions. Voir à ce propos cette section.

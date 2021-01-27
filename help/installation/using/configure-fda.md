---
solution: Campaign Classic
product: campaign
title: Configuration des connecteurs de FDA
description: Découvrir les étapes de configuration de FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 100%

---


# Configuration des connecteurs FDA {#specific-configurations-by-database-type}

En fonction des bases de données externes auxquelles vous souhaitez pouvoir accéder depuis Adobe Campaign, certains paramétrages spécifiques sont nécessaires. Ces paramétrages concernent essentiellement l&#39;installation de pilotes et la déclarations de variables d&#39;environnement propres à chaque SGBDR sur le serveur Adobe Campaign.

En règle générale, il est nécessaire d’installer la couche cliente correspondant à la base de données externe utilisée sur le serveur Adobe Campaign.

>[!NOTE]
>
>Les versions compatibles sont répertoriées dans la [Matrice de compatibilité Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).


## Etapes de configuration {#fda-configuration-steps}

Pour configurer l’accès à une base de données externe avec FDA, les étapes de configuration sont les suivantes :

1. installer les pilotes qui correspondent à votre base de données sur le serveur marketing Adobe Campaign. Les pilotes sont répertoriés dans les pages spécifiques à la base de données [répertoriées ci-dessous](#fda-specific-configuration).
1. [créer et paramétrer un compte externe](../../installation/using/connecting-to-database.md) permettant d’établir la connexion entre Adobe Campaign et la base externe. Pour plus d&#39;informations sur les comptes externes de Campaign, consultez [cette page](../../installation/using/external-accounts.md).
1. [créer le schéma](../../installation/using/creating-data-schema.md) de la base de données externe dans Adobe Campaign. Il est ainsi possible de reconnaître la structure des données de la base de données externe.
1. Si nécessaire, [créez un mapping de ciblage](../../installation/using/defining-data-mapping.md) à partir du schéma créé précédemment. Ceci est nécessaire si les destinataires de vos diffusions proviennent de la base de données externe. Cette implémentation s’accompagne de limitations liées à la personnalisation des messages.

Une fois le schéma de données créé, les données peuvent être traitées dans Adobe Campaign. Voir à ce propos [cette section](../../workflow/using/accessing-an-external-database--fda-.md).

## Configuration spécifique à la base de données {#fda-specific-configuration}

En fonction des bases de données externes auxquelles vous souhaitez pouvoir accéder depuis Adobe Campaign, certains paramétrages spécifiques sont nécessaires. Ces paramétrages concernent essentiellement l’installation de pilotes et la déclarations de variables d’environnement propres à chaque SGBDR sur le serveur Adobe Campaign.

Suivez les liens ci-dessous pour en savoir plus :

* [Azure Synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [Sybase IQ ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

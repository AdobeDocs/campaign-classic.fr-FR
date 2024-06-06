---
product: campaign
title: Configuration des connecteurs de FDA
description: Découvrir les étapes de configuration de FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '347'
ht-degree: 100%

---

# Configuration des connecteurs FDA {#specific-configurations-by-database-type}



En fonction des bases de données externes auxquelles vous souhaitez pouvoir accéder depuis Adobe Campaign, certains paramétrages spécifiques sont nécessaires. Ces paramétrages concernent essentiellement l&#39;installation de pilotes et la déclarations de variables d&#39;environnement propres à chaque SGBDR sur le serveur Adobe Campaign.

En règle générale, il est nécessaire d&#39;installer la couche cliente correspondant à la base externe utilisée sur le serveur Adobe Campaign.

>[!NOTE]
>
>Les versions compatibles sont répertoriées dans la [Matrice de compatibilité Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
>

## Étapes de configuration {#fda-configuration-steps}

Pour configurer l&#39;accès à une base de données externe avec FDA, les étapes de configuration sont les suivantes :

1. Installez les pilotes et configurer le compte externe correspondant à votre base de données sur le serveur Adobe Campaign. Voir à ce sujet les pages spécifiques à la base de données [répertoriées ci-dessous](#fda-specific-configuration).
1. Testez le compte externe ou créer une connexion temporaire entre Adobe Campaign et la base de données externe. [En savoir plus](../../installation/using/connecting-to-database.md)
1. Créez le schéma de la base de données externe dans Adobe Campaign. Il est ainsi possible d&#39;identifier la structure des données de la base de données externe. [En savoir plus](../../installation/using/creating-data-schema.md)
1. Si nécessaire, créez un mapping de ciblage à partir du schéma créé précédemment. Ceci est nécessaire si les destinataires de vos diffusions proviennent de la base de données externe. Cette implémentation s&#39;accompagne de limitations liées à la personnalisation des messages. [En savoir plus](../../installation/using/defining-data-mapping.md)

Une fois le schéma de données créé, les données peuvent être traitées dans Adobe Campaign. Voir à ce propos [cette section](../../workflow/using/accessing-an-external-database-fda.md).

## Configuration spécifique à la base de données {#fda-specific-configuration}

Selon les bases de données externes auxquelles vous souhaitez accéder à partir d’Adobe Campaign, vous devrez effectuer certaines configurations spécifiques. Ces configurations impliquent essentiellement l’installation de pilotes et la déclaration des variables d’environnement appartenant à chaque SGBDR sur le serveur Adobe Campaign, ainsi que la configuration du compte externe.

Suivez les liens ci-dessous pour en savoir plus :

* Connecter Campaign et [Amazon Redshift](../../installation/using/configure-fda-redshift.md)
* Connecter Campaign et [Azure Synapse](../../installation/using/configure-fda-synapse.md)
* Connecter Campaign et [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Connecter Campaign et [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Connecter Campaign et [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* Connecter Campaign et [Netezza](../../installation/using/configure-fda-netezza.md)
* Connecter Campaign et [Oracle](../../installation/using/configure-fda-oracle.md)
* Connecter Campaign et [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* Connecter Campaign et [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Connecter Campaign et [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Connectez Campaign et [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Connecter Campaign et [Teradata](../../installation/using/configure-fda-teradata.md)
* Connecter Campaign et [Vertica Analytics](../../installation/using/configure-fda-vertica.md)

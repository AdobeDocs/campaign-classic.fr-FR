---
solution: Campaign Classic
product: campaign
title: Configuration des connecteurs de FDA
description: Découvrir les étapes de configuration de FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
translation-type: tm+mt
source-git-commit: 7ce5a01b57092043b8d9b52761b243f771cf74f2
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 56%

---

# Configuration des connecteurs FDA {#specific-configurations-by-database-type}

En fonction des bases de données externes auxquelles vous souhaitez pouvoir accéder depuis Adobe Campaign, certains paramétrages spécifiques sont nécessaires. Ces paramétrages concernent essentiellement l&#39;installation de pilotes et la déclarations de variables d&#39;environnement propres à chaque SGBDR sur le serveur Adobe Campaign.

En règle générale, il est nécessaire d’installer la couche cliente correspondant à la base de données externe utilisée sur le serveur Adobe Campaign.

>[!NOTE]
>
>Les versions compatibles sont répertoriées dans la [Matrice de compatibilité Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).


## Etapes de configuration {#fda-configuration-steps}

Pour configurer l’accès à une base de données externe avec FDA, les étapes de configuration sont les suivantes :

1. Installez les pilotes et configurez le compte externe correspondant à votre base de données sur le serveur Adobe Campaign. Reportez-vous aux pages spécifiques à la base de données [répertoriées ci-dessous](#fda-specific-configuration).
1. Testez le compte externe ou créez une connexion temporaire entre Adobe Campaign et la base de données externe. [En savoir plus](../../installation/using/connecting-to-database.md)
1. créer le schéma de la base de données externe dans Adobe Campaign. Vous pouvez ainsi identifier la structure des données de la base de données externe. [En savoir plus](../../installation/using/creating-data-schema.md)
1. Si nécessaire, créez un mapping de ciblage à partir du schéma créé précédemment. Ceci est nécessaire si les destinataires de vos diffusions proviennent de la base de données externe. Cette implémentation s’accompagne de limitations liées à la personnalisation des messages. [En savoir plus](../../installation/using/defining-data-mapping.md)

Une fois le schéma de données créé, les données peuvent être traitées dans Adobe Campaign. Voir à ce propos [cette section](../../workflow/using/accessing-an-external-database--fda-.md).

## Configuration spécifique à la base de données {#fda-specific-configuration}

Selon les bases de données externes auxquelles vous souhaitez accéder à partir d&#39;Adobe Campaign, vous devrez effectuer certaines configurations spécifiques. Ces configurations impliquent essentiellement l&#39;installation de pilotes et la déclaration des variables d&#39;environnement qui appartiennent à chaque RDBMS sur le serveur Adobe Campaign, ainsi que la configuration du compte externe.

Suivez les liens ci-dessous pour en savoir plus :

* Connecter Campaign et [Azure synapse](../../installation/using/configure-fda-synapse.md)

* Connectez Campaign et [Snowflake](../../installation/using/configure-fda-snowflake.md)

* Connecter Campaign et [Hadoop](../../installation/using/configure-fda-hadoop.md)

* Connecter Campaign et [Oracle](../../installation/using/configure-fda-oracle.md)

* Connecter Campaign et [Netezza](../../installation/using/configure-fda-netezza.md)

* Connectez Campaign et [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* Connecter Campaign et [Teradata](../../installation/using/configure-fda-teradata.md)

* Connectez Campaign et [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

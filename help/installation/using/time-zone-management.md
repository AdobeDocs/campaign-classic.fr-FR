---
product: campaign
title: Gestion des fuseaux horaires
description: Gestion des fuseaux horaires
feature: Installation, Instance Settings
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
TQID: https://experienceleague.adobe.com/Y-SOL0Lu44eD9pGpBm7x18TRcHy-oKR5SSZAlMPsb34
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1000
ht-degree: 77%

---

# Gestion des fuseaux horaires{#time-zone-management}



## Principe de fonctionnement {#operating-principle}

Adobe Campaign permet d&#39;exprimer les dates en fonction de leur fuseau horaire : les utilisateurs internationaux peuvent ainsi collaborer à travers le monde sur différents fuseaux horaires. Chaque pays utilisant la même instance peut gérer l&#39;exécution des campagnes, le tracking, l&#39;archivage, etc. en fonction de l&#39;heure locale.

Afin de permettre l&#39;utilisation de la plateforme Adobe Campaign à l&#39;échelle internationale, toutes les dates utilisées par les systèmes doivent pouvoir être associées à un fuseau horaire. Une date dont le fuseau horaire est connu peut ainsi être importée dans n&#39;importe quel autre fuseau horaire, ou indépendamment de tout fuseau horaire.

Adobe Campaign vous permet de stocker les dates/heures au format UTC (Temps universel coordonné). Lorsque des données sont exposées, elles sont converties en date/heure locale de l’opérateur. La conversion est effectuée automatiquement lorsque la base de données est paramétrée au format UTC (voir la section [Configuration](#configuration)). Si la base de données n&#39;est pas paramétrée au format UTC, les informations relatives aux fuseaux horaires des dates de la plateforme sont stockées dans une option.

Les principales fonctionnalités de la plateforme concernées par la gestion des fuseaux horaires sont : les imports/exports de données, la gestion des opérateurs et les Workflows. La **notion d&#39;héritage** est disponible pour les imports/exports ou les Workflows. Par défaut, ils sont paramétrés sur le fuseau horaire du serveur de base de données, mais il est possible de redéfinir de nouveaux fuseaux horaires pour un workflow et même pour une seule activité.

Les **opérateurs** peuvent agir sur les fuseaux horaires lors du **paramétrage d&#39;une diffusion** et en particulier définir le fuseau horaire dans lequel la diffusion va être exécutée.

>[!IMPORTANT]
>
>Si la base de données ne gère pas le multi-fuseaux horaires, alors pour toutes les manipulations de filtrage de données, les requêtes SQL doivent être exécutées dans le fuseau horaire du serveur de base de données.

Chaque opérateur Adobe Campaign est associé à un fuseau horaire : cette information est paramétrée dans son profil. Voir à ce sujet [ce document](../../platform/using/access-management.md).

Lorsque la plateforme Adobe Campaign ne nécessite pas la gestion des fuseaux horaires, il est possible de conserver un mode de stockage au format local, avec un fuseau horaire spécifique associé.

## Recommandations {#recommendations}

Les fuseaux horaires recouvrent plusieurs réalités : le terme peut désigner un décalage constant par rapport à la date UTC, ou les horaires d&#39;une région qui peut changer d&#39;heure deux fois dans l&#39;année (heure d&#39;hiver/heure d&#39;été).

Par exemple, en postgreSQL, la commande **SET TIME ZONE &#39;Europe/Paris&#39;;** tiendra compte des heures d&#39;été et d&#39;hiver : la date sera exprimée en GMT+1 ou GMT+2 selon la période de l&#39;année.

Par contre, si l&#39;on utilise commande **SET TIME ZONE 0200;**, le décalage sera toujours GMT+2.

## Configuration {#configuration}

Le mode de stockage des dates et heures est choisi lors de la création de la base de données (voir la section [Création d&#39;une nouvelle instance](#creating-a-new-instance)). En cas de migration, les heures liées aux dates sont converties en dates et heures locales (voir la section [Migration](#migration)).

D&#39;un point de vue technique, les informations de type **Date+heure** peuvent être stockées dans la base de données selon deux modes différents :

1. Format TIMESTAMP WITH TIMEZONE : le moteur de base de données stocke les dates en UTC. Chaque session ouverte aura un fuseau horaire et les dates seront converties en fonction de celui-ci.
1. Format local + fuseau horaire local : toutes les dates sont stockées au format local (pas de gestion des décalages horaires) et un fuseau horaire unique leur est associé. Le fuseau horaire est stocké dans l&#39;option **WdbcTimeZone** de l&#39;instance Adobe Campaign et peut être modifié à partir du menu **[!UICONTROL Administration > Plateforme > Options]** de l&#39;arborescence.

>[!IMPORTANT]
>
>Notez que cette modification peut entraîner des problèmes de cohérence des données et de synchronisation.

### Création d&#39;une nouvelle instance {#creating-a-new-instance}

Afin de permettre à plusieurs utilisateurs internationaux de collaborer sur une même instance, vous devez configurer les fuseaux horaires (timezone) lors de la création de l&#39;instance pour gérer les décalages horaires entre les pays. Pour cela, lors de la création de l&#39;instance, sélectionnez le mode de gestion des dates et heures dans la section **[!UICONTROL Fuseau horaire]** de l&#39;étape de configuration de la base de données.

Cochez l&#39;option **[!UICONTROL Base UTC (champs dates avec fuseau horaire)]** pour stocker toutes les données comportant des dates et heures au format UTC (champs SQL et champs XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Dans le cas d&#39;**Oracle**, il faut que les fichiers de fuseaux horaires (.dat) des couches clientes Oracle soient compatibles avec les fichiers de fuseaux horaires installés sur le serveur.

Si la base de données n’est pas en UTC, vous pouvez sélectionner l’un des fuseaux horaires proposés dans la liste déroulante. Vous pouvez également utiliser le fuseau horaire du serveur ou sélectionner l’option UTC (Temps universel coordonné) .

![](assets/install_wz_unselect_utc_option.png)

Lorsque l&#39;option **[!UICONTROL Base UTC (champs dates avec fuseau horaire)]** est sélectionnée, les champs SQL sont stockés au format TIMESTAMP WITH TIMEZONE.

Dans le cas contraire, ils sont stockés au format local et vous devez sélectionner le fuseau horaire à appliquer à la base de données.

### Migration {#migration}

Lors d&#39;une migration d&#39;une version antérieure (sans gestion des fuseaux horaires), vous devez définir le mode de stockage des dates dans la base de données.

Afin de garantir la compatibilité avec les outils externes accédant à la base de données Adobe Campaign, les champs SQL de type **Date+heure** restent par défaut stockés au format local.

Les champs XML contenant des dates sont désormais stockés en UTC. Lors du chargement, les champs qui ne sont pas au format UTC sont automatiquement convertis à l’aide du fuseau horaire du serveur. Cela signifie que tous les champs XML seront progressivement convertis au format UTC.

Pour utiliser une instance existante, ajoutez l&#39;option **WdbcTimeZone** et saisissez le fuseau horaire de l&#39;instance.

>[!IMPORTANT]
>
>Vous devez veiller à paramétrer la bonne valeur pour l&#39;option WdbcTimeZone : toute modification ultérieure pourrait provoquer des incohérences.

Exemple de valeurs possibles :

* Europe/Paris,
* Europe/London,
* America/New_York, etc.

  Ces valeurs sont extraites de la base de données tz (Olson). Pour plus d&#39;informations, voir la page [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Base de données Oracle et fuseau horaire du serveur

Pour la base de données principale, Campaign utilise le fuseau horaire du serveur pour définir le fuseau horaire de la session sur la connexion à la base de données. L’option « WdbcTimeZone » n’a aucun impact. Le fuseau horaire du serveur doit donc correspondre à celui de la base de données principale utilisée par Campaign. Si vous ne pouvez pas modifier le fuseau horaire du serveur, le fuseau horaire utilisé par Campaign peut être remplacé en définissant la variable d’environnement TZ dans customer.sh.
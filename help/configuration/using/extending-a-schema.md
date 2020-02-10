---
title: Extension d'un schéma
seo-title: Extension d'un schéma
description: Extension d'un schéma
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Extension d&#39;un schéma{#extending-a-schema}

>[!CAUTION]
>
>Certains schémas intégrés ne doivent pas être étendus. Il s’agit principalement de ceux pour lesquels les paramètres suivants sont définis :\
>**dataSource=&quot;file&quot;** et **mappingType=&quot;xmlFile&quot;**.\
>Les schémas suivants ne doivent pas être étendus : **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form, xtk:srcSchema,ncm:publishing,nl:monitoring,nms:calendarnms:remoteTracking,nms:userAgentRules,xtk:builder,xtk:connections, xtk:dbInit,xtk:funcList, xtk:fusion, xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, xtk:schema, xtk:scriptContext,xtk:session,xtk:sqlSchema, xtk:strings.********************************************************************
>Cette liste n&#39;est pas exhaustive.

Il existe deux solutions pour étendre un schéma déjà existant :

1. Modifier directement le schéma source.
1. Créer un autre schéma de même nom, mais avec un espace de nommage différent. L&#39;avantage est de pouvoir étendre une table sans avoir à modifier le schéma d&#39;origine.

   L&#39;élément racine du schéma doit contenir l&#39;attribut **extendedSchema** avec comme valeur le nom du schéma à étendre.

   Un schéma d&#39;extension ne possède pas son propre schéma : c&#39;est le schéma généré à partir du schéma source qui sera complété avec les champs du schéma d&#39;extension.

   >[!CAUTION]
   >
   >Vous n’êtes pas autorisé à modifier les schémas intégrés à l’application ; vous devez utiliser le mécanisme d’extension des schémas. En effet, lors des futures mises à jour de l’application, les schémas modifiés ne seraient pas mis à jour, ce qui peut entraîner des dysfonctionnements dans l’utilisation d’Adobe Campaign.

   **Exemple** : extension du schéma **nms:recipient**.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Le schéma étendu **nms:recipient** est complété avec le champ renseigné dans le schéma d&#39;extension :

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   L&#39;attribut **dependingSchemas** sur l&#39;élément racine du schéma référence les dépendances sur les schémas d&#39;extension.

   L&#39;attribut **belongsTo** sur le champ renseigne le schéma où il est déclaré.

>[!CAUTION]
>
>Pour que les modifications soient prises en compte, vous devez régénérer les schémas. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Si les modifications affectent la structure de la base de données, vous devez exécuter une mise à jour. Voir à ce sujet la section [Mettre à jour la structure de la base de données](../../configuration/using/updating-the-database-structure.md).


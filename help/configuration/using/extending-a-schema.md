---
product: campaign
title: Extension dʼun schéma
description: Découvrez comment étendre un schéma
role: Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 81%

---

# Extension dʼun schéma{#extending-a-schema}

>[!IMPORTANT]
>
>Certains schémas intégrés ne doivent pas être étendus. Il s’agit principalement de ceux pour lesquels les paramètres suivants sont définis :\
>**dataSource=&quot;file&quot;** et **mappingType=&quot;xmlFile&quot;**.\
>Les schémas suivants ne doivent pas être étendus : **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>Cette liste n&#39;est pas exhaustive.

Il existe deux solutions pour étendre un schéma déjà existant :

1. Modifier directement le schéma source.
1. Création d’un autre schéma portant le même nom, mais avec un espace de noms différent. L’avantage est que vous pouvez étendre une table sans avoir à modifier le schéma d’origine.

   L&#39;élément racine du schéma doit contenir l&#39;attribut **extendedSchema** avec comme valeur le nom du schéma à étendre.

   Un schéma d&#39;extension ne possède pas son propre schéma : c&#39;est le schéma généré à partir du schéma source qui sera complété avec les champs du schéma d&#39;extension.

   >[!IMPORTANT]
   >
   >Vous n’êtes pas autorisé à modifier les schémas intégrés de l’application, mais plutôt le mécanisme d’extension de schéma. Sinon, les schémas modifiés ne seront pas mis à jour au moment des futures mises à niveau de l’application. Cela peut entraîner des dysfonctionnements dans l’utilisation d’Adobe Campaign.

   **Exemple** : extension du schéma **nms:recipient**.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Le schéma étendu **nms:recipient** est complété avec le champ renseigné dans le schéma d’extension :

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   L’attribut **dependingSchemas** sur l’élément racine du schéma référence les dépendances sur les schémas d’extension.

   L&#39;attribut **belongsTo** sur le champ renseigne le schéma où il est déclaré.

>[!IMPORTANT]
>
>Pour que les modifications soient prises en compte, vous devez régénérer les schémas. Pour plus dʼinformations, consultez [cette page](../../configuration/using/regenerating-schemas.md).\
>Si les modifications affectent la structure de la base de données, vous devez exécuter une mise à jour. Pour plus d’informations, consultez [cette page](../../configuration/using/updating-the-database-structure.md).

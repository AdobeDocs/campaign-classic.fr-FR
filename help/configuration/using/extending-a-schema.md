---
product: campaign
title: Extension dʼun schéma
description: Découvrez comment étendre un schéma
role: Data Engineer, Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '327'
ht-degree: 100%

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
1. Créer un autre schéma de même nom, mais avec un espace de noms différent. L&#39;avantage est de pouvoir étendre une table sans avoir à modifier le schéma d&#39;origine.

   L&#39;élément racine du schéma doit contenir l&#39;attribut **extendedSchema** avec comme valeur le nom du schéma à étendre.

   Un schéma d&#39;extension ne possède pas son propre schéma : c&#39;est le schéma généré à partir du schéma source qui sera complété avec les champs du schéma d&#39;extension.

   >[!IMPORTANT]
   >
   >Vous n’êtes pas autorisé à modifier les schémas intégrés à l’application ; vous devez utiliser le mécanisme d’extension des schémas. En effet, lors des futures mises à jour de l’application, les schémas modifiés ne seraient pas mis à jour, ce qui peut entraîner des dysfonctionnements dans l’utilisation d’Adobe Campaign.

   **Exemple** : extension du schéma **nms:recipient**.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Le schéma étendu **nms:recipient** est complété avec le champ renseigné dans le schéma d&#39;extension :

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
>Si les modifications affectent la structure de la base de données, vous devez exécuter une mise à jour. Pour plus dʼinformations, consultez [cette page](../../configuration/using/updating-the-database-structure.md).

---
product: campaign
title: Filtrage des schémas
description: Filtrage des schémas
feature: Custom Resources
role: Developer
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
TQID: https://experienceleague.adobe.com/-EcD9suVVxnqRIgsLdaADQ7T0CIMw1CzSnoqJqNe8xs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 387
ht-degree: 79%

---

# Filtrage des schémas{#filtering-schemas}

## Filtres système {#system-filters}

Vous pouvez filtrer l’accès aux schémas pour des utilisateurs spécifiques, selon leurs autorisations. Les filtres système vous permettent de gérer les autorisations de lecture et d’écriture des entités détaillées dans les schémas, à l’aide des paramètres **readAccess** et **writeAccess**.

>[!NOTE]
>
>Cette restriction s’applique uniquement aux utilisateurs n’ayant pas de connaissances techniques : un utilisateur technique, avec les autorisations associées ou utilisant un workflow, sera en mesure de récupérer les données et de les mettre à jour.

* **readAccess** : permet d&#39;accéder aux données d&#39;un schéma en lecture seule.

  **Avertissement** - Toutes les tables liées doivent être définies avec la même restriction. Cette configuration peut avoir un impact sur les performances.

* **writeAccess** : permet d&#39;accéder aux données d&#39;un schéma en écriture.

Ces filtres sont renseignés au niveau de l’**élément** principal des schémas et peuvent être formés comme dans les exemples suivants afin de restreindre l’accès :

* Restreindre les autorisations d’ÉCRITURE

  Ici, le filtre sert à interdire les autorisations d’ÉCRITURE sur le schéma aux opérateurs ne disposant pas de l’autorisation ADMINISTRATION. Cela signifie que seuls les administrateurs disposeront d’autorisations en écriture sur les entités décrites par ce schéma.

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* Restreindre les autorisations de LECTURE et d’ÉCRITURE :

  Ici, le filtre sert à interdire à la fois les autorisations de LECTURE et d’ÉCRITURE du schéma à tous les opérateurs. Seul le compte **interne**, représenté par l’expression &quot;$(loginId)!=0&quot;, possède ces autorisations.

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  Les valeurs possibles de l’attribut **expr** utilisé pour définir la condition sont TRUE ou FALSE.

>[!NOTE]
>
>Si aucun filtre n&#39;est défini, tous les opérateurs peuvent accéder librement en lecture et en écriture au schéma.

## Protection des schémas intégrés {#protecting-built-in-schemas}

Par défaut, les schémas intégrés ne sont accessibles avec les autorisations d’ÉCRITURE que par les opérateurs possédant le droit d’ADMINISTRATION :

* ncm:publishing
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>Le schéma **xtk:sessionInfo** n’est accessible en lecture et en écriture que par le compte interne d’une instance Adobe Campaign.

## Modification des filtres système des schémas intégrés {#modifying-system-filters-of-built-in-schemas}

Il est tout de même possible de modifier les filtres système des schémas d’usine, protégés par défaut, notamment pour des raisons de compatibilité avec les versions antérieures.

>[!NOTE]
>
>Adobe recommande toutefois de ne pas modifier les paramètres par défaut afin de garantir une sécurité optimale.

1. Créez une extension du schéma concerné ou ouvrez une extension existante.
1. Dans l’élément principal, ajoutez un élément enfant **`<sysfilter name="<filter name>" _operation="delete"/>`** afin de supprimer l’application du filtre du même nom dans le schéma d’origine.
1. Ajoutez un nouveau filtre si vous le souhaitez, comme décrit dans la section [Filtres système](#system-filters).

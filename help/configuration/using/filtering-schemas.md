---
title: Filtrage des schémas
seo-title: Filtrage des schémas
description: Filtrage des schémas
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Filtrage des schémas{#filtering-schemas}

## Filtres système {#system-filters}

Vous pouvez filtrer l’accès aux schémas pour des utilisateurs spécifiques, selon leurs permissions. Les filtres système vous permettent de gérer les permissions de lecture et d’écriture des entités figurant dans les schémas, au moyen des paramètres **readAccess** et **writeAccess**.

>[!NOTE]
>
>Cette restriction s’applique uniquement aux utilisateurs n’ayant pas de connaissances techniques : un utilisateur technique, avec les permissions associées ou utilisant un workflow, sera en mesure de récupérer les données et de les mettre à jour.

* **readAccess** : permet d&#39;accéder aux données d&#39;un schéma en lecture seule.

   **Attention** : toutes les tables liées doivent être définies avec la même restriction. Cette configuration peut avoir une incidence sur les performances.

* **writeAccess** : permet d&#39;accéder aux données d&#39;un schéma en écriture.

Ces filtres sont renseignés au niveau de l’**élément** principal des schémas et peuvent être formés comme dans les exemples suivants afin de restreindre l’accès :

* Restreindre les permissions d’ÉCRITURE

   Ici, le filtre sert à interdire les permissions d’ÉCRITURE sur le schéma aux opérateurs ne disposant pas de la permission ADMINISTRATION. Ainsi, seuls les administrateurs pourront accéder en écriture aux entités décrites par ce schéma.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Restreindre les permissions de LECTURE et d’ÉCRITURE :

   Ici, le filtre sert à interdire à la fois les permissions de LECTURE et d’ÉCRITURE du schéma à tous les opérateurs. Seul le compte **interne**, représenté par l’expression &quot;$(loginId)!=0&quot;, possède ces permissions.

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

Par défaut, les schémas intégrés ne sont accessibles avec les permissions d’ÉCRITURE que par les opérateurs possédant le droit d’ADMINISTRATION :

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

>[!CAUTION]
>
>Le schéma **xtk:sessionInfo** n’est accessible en lecture et en écriture que par le compte interne d’une instance Adobe Campaign.

## Modification des filtres système des schémas intégrés {#modifying-system-filters-of-built-in-schemas}

Il est tout de même possible de modifier les filtres système des schémas d’usine, protégés par défaut, notamment pour des raisons de compatibilité avec les versions antérieures.

>[!NOTE]
>
>Adobe recommande toutefois de ne pas modifier les paramètres par défaut afin de garantir une sécurité optimale.

1. Créez une extension du schéma concerné ou ouvrez une extension existante.
1. Add a child element **`<sysfilter name="<filter name>" _operation="delete"/>`** in the main element to delete application of the filter under the same in the origin schema.
1. If you like, you can add a new filter, as detailed in [System filters](#system-filters).


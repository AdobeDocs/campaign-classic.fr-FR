---
product: campaign
title: Méthodes SOAP en JavaScript
feature: Configuration, Instance Settings
description: Méthodes SOAP en JavaScript
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 95%

---

# Méthodes SOAP en JavaScript{#soap-methods-in-javascript}

Il s&#39;agit dans ce cas du JavaScript exécuté sur le serveur Adobe Campaign.

## Méthodes statiques {#static-methods}

L&#39;accès aux méthodes SOAPs statiques se fait par invocation d&#39;une méthode sur l&#39;objet représentant le schéma. Les schémas sont des propriétés des objets de type &#39;espace de noms&#39;. Ces espaces de noms sont des variables globales, ainsi par exemple, les variables xtk ou nms représentent les espaces de noms correspondants.

L&#39;exemple suivant invoque la méthode statique PostEvent du schéma xtk:workflow :

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Méthodes non statiques {#non-static-methods}

Pour utiliser les méthodes SOAPs non statiques, il faut d&#39;abord récupérer une entité en utilisant les méthodes &quot;get&quot; ou &quot;create&quot; sur les schémas correspondants.

L&#39;exemple suivant invoque la méthode ExecuteQuery du schéma &quot;xtk:queryDef&quot; :

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## Exemples     {#examples}

* Requête sur la table des destinataires avec une opération &quot;get&quot; :

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* Requête sur la table des destinataires avec une opération &quot;select&quot; :

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* Ecriture de données sur la table des destinataires :

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```

---
product: campaign
title: Méthodes SOAP en JavaScript
feature: Configuration, Instance Settings
description: Méthodes SOAP en JavaScript
role: Developer
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
TQID: https://experienceleague.adobe.com/pIvm36kXpJEzeG4mugpR-7kAQDJpyJ2YFXp4S9J7lUw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: ht
source-wordcount: 136
ht-degree: 100%

---

# Méthodes SOAP en JavaScript{#soap-methods-in-javascript}

Il s&#39;agit dans ce cas du JavaScript exécuté sur le serveur Adobe Campaign.

## Méthodes statiques {#static-methods}

Les méthodes SOAP statiques sont accessibles en appelant une méthode sur l’objet représentant le schéma.Les schémas sont des propriétés des objets « espace de noms ».Ces espaces de noms sont des variables globales. Par exemple, les variables xtk ou nms représentent les espaces de noms correspondants.

L’exemple suivant invoque la méthode statique PostEvent du schéma xtk:workflow :

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Méthodes non statiques {#non-static-methods}

Pour utiliser les méthodes SOAP non statiques, il faut d’abord récupérer une entité en utilisant les méthodes « get » ou « create » sur les schémas correspondants.

L’exemple suivant invoque la méthode ExecuteQuery du schéma « xtk:queryDef » :

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

## Exemples {#examples}

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

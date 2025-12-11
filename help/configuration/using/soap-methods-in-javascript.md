---
product: campaign
title: Méthodes SOAP en JavaScript
feature: Configuration, Instance Settings
description: Méthodes SOAP en JavaScript
role: Developer
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: ht
source-wordcount: '134'
ht-degree: 100%

---

# Méthodes SOAP en JavaScript{#soap-methods-in-javascript}

Il s&#39;agit dans ce cas du JavaScript exécuté sur le serveur Adobe Campaign.

## Méthodes statiques {#static-methods}

L.accès aux méthodes SOAP statiques se fait par invocation d’une méthode sur l’objet représentant le schéma. Les schémas sont des propriétés des objets de type « espace de noms ». Ces espaces de noms sont des variables globales, ainsi par exemple, les variables xtk ou nms représentent les espaces de noms correspondants.

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

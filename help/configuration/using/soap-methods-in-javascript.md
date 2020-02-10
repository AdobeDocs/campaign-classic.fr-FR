---
title: Méthodes SOAP en JavaScript
seo-title: Méthodes SOAP en JavaScript
description: Méthodes SOAP en JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 8fd1aabc-e51a-433d-835f-6b5a717c7aeb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 815d3eb9-ac45-441f-9a5f-0cd505fcf88a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Méthodes SOAP en JavaScript{#soap-methods-in-javascript}

Il s&#39;agit dans ce cas du JavaScript exécuté sur le serveur Adobe Campaign.

## Méthodes statiques {#static-methods}

L&#39;accès aux méthodes SOAPs statiques se fait par invocation d&#39;une méthode sur l&#39;objet représentant le schéma. Les schémas sont des propriétés des objets de type &#39;namespace&#39;. Ces namespaces sont des variables globales, ainsi par exemple, les variables xtk ou nms représentent les espaces de nommage correspondant.

L&#39;exemple suivant invoque la méthode statique PostEvent du schéma xtk:workflow :

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Méthodes non statiques {#non-static-methods}

Pour utiliser les méthodes SOAPs non statiques, il faut d&#39;abord récupérer une entité en utilisant les méthodes &quot;get&quot; ou &quot;create&quot; sur les schémas correspondants.

L&#39;exemple suivant invoque la méthode ExecuteQuery du schéma &quot;xtk:queryDef&quot; :

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

* Requête sur la table des destinataires avec une opération &quot;get&quot; :

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

* Requête sur la table des destinataires avec une opération &quot;select&quot; :

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

* Ecriture de données sur la table des destinataires :

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```


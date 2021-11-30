---
product: campaign
title: Exemples de code JavaScript dans les workflows
description: Ces exemples montrent comment utiliser du code JavaScript dans un workflow
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: c86559d5ab40b206d701c46bb01d3ba61c835e8b
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 4%

---

# Exemples de code JavaScript dans les workflows{#javascript-in-workflows}

![](../../assets/common.svg)

Ces exemples montrent comment utiliser du code JavaScript dans un workflow :

* [Ecrire dans la base de données](#write-example)
* [Interrogation de la base de données](#read-example)
* [Déclencher un workflow à l’aide d’une méthode SOAP statique](#trigger-example)
* [Interaction avec la base de données, à l&#39;aide d&#39;une méthode SOAP non statique](#interact-example)

[En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=fr) à propos des méthodes SOAP statiques et non statiques.

Dans ces exemples, l’extension ECMAScript pour XML (E4X) est utilisée. Avec cette extension, vous pouvez combiner des appels JavaScript et des primitives XML dans le même script.

Pour tester ces exemples, procédez comme suit :

1. Créez un workflow et ajoutez les activités suivantes au workflow :
   1. Activité de début
   1. Activité Code JavaScript
   1. Activité de fin

   [En savoir plus](building-a-workflow.md) à propos de la création de workflows.

1. Ajoutez le code JavaScript à une activité. [En savoir plus](advanced-parameters.md).
1. Enregistrez le workflow.
1. Testez les exemples :
   1. Démarrez le workflow. [En savoir plus](starting-a-workflow.md).
   1. Ouvrez le journal. [En savoir plus](monitoring-workflow-execution.md#displaying-logs).

## Exemple 1 : écrire dans la base de données{#write-example}

Pour écrire dans la base de données, vous pouvez utiliser le `Write` sur la méthode `xtk:session` schema :

1. Composer une requête d’écriture en XML.

1. Écrivez l’enregistrement :

   1. Appelez le `Write` sur la méthode `xtk:session` schéma.

      >[!IMPORTANT]
      > Si vous utilisez Adobe Campaign v8, nous vous recommandons d’utiliser le mécanisme d’évaluation avec la variable **Ingestion** et **Mise à jour/suppression de données** API pour la variable `Write` dans une table de Snowflake. [En savoir plus](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

   1. Transmettez le code XML en tant qu’argument de la requête d’écriture.

### Étape 1 : composer une requête d’écriture ;

Vous pouvez ajouter, mettre à jour et supprimer des enregistrements.

#### Insérer un enregistrement

Parce que la variable `insert` est l’opération par défaut, vous n’avez pas besoin de la spécifier.

Indiquez ces informations sous forme d’attributs XML :

* Le schéma de la table à modifier
* Champs du tableau à renseigner

Exemple :

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Mettre à jour un enregistrement

Utilisez la variable `_update` opération. [En savoir plus](../../configuration/using/data-oriented-apis.md).

Indiquez ces informations sous forme d’attributs XML :

* Le schéma de la table à modifier
* Champs du tableau à mettre à jour
* L’argument clé requis pour identifier l’enregistrement à mettre à jour

Exemple :

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Suppression d’un enregistrement

Utilisez la variable `DeleteCollection` . [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Indiquez les informations suivantes :

* Le schéma de la table à modifier
* Le `where` clause requise pour identifier l’enregistrement à mettre à jour, sous la forme d’un élément XML

Exemple :

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Étape 2 : écrire l’enregistrement

Appelez le paramètre non statique `Write` sur la méthode `xtk:session` schema :

```javascript
xtk.session.Write(myXML)
```

Aucune valeur n’est renvoyée pour cette méthode.

Ajoutez le code complet à une activité Code JavaScript dans le workflow :

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

Cette vidéo montre comment écrire dans la base de données :
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Exemple 2 : interroger la base de données ;{#read-example}

Pour interroger la base de données, vous pouvez utiliser le `xtk:queryDef` méthode d’instance :

1. Composer une requête au format XML.
1. Créez un objet de requête.
1. Exécutez la requête.

### Étape 1 : Rédiger une requête

Spécifiez le code XML pour un `queryDef` entité.

Syntaxe :

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Indiquez les informations suivantes :

* Le schéma de la table à lire
* L’opération
* Les colonnes à renvoyer, sous la forme d’une `select` clause
* Les conditions, dans une `where` clause
* Les critères de filtrage, dans un `orderBy` clause

Vous pouvez utiliser les opérations suivantes :

| Fonctionnement | Résultat |
| --- | --- |
| `select` | Aucun ou plusieurs éléments sont renvoyés en tant que collection. |
| `getIfExists` | Un élément est renvoyé. S’il n’existe aucun élément de correspondance, un élément vide est renvoyé. |
| `get` | Un élément est renvoyé. Si aucun élément de correspondance n’existe, une erreur est renvoyée. |
| `count` | Le nombre d&#39;enregistrements correspondants est renvoyé sous la forme d&#39;un élément avec un `count` attribut. |

Écrivez le `select`, `where`, et `orderBy` clauses en tant qu’éléments XML :

* `select` clause

   Indiquez les colonnes à renvoyer. Par exemple, pour sélectionner le prénom et le nom de la personne, écrivez le code suivant :

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Avec le `nms:recipient` schéma, les éléments sont renvoyés sous la forme suivante :

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` clause

   Pour spécifier des conditions, utilisez une `where` clause . Par exemple, pour sélectionner les enregistrements qui se trouvent dans le **Formation** , vous pouvez écrire ce code :

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   Lorsque vous combinez plusieurs expressions, utilisez l’opérateur booléen dans la première expression. Par exemple, pour sélectionner toutes les personnes appelées Isabel Garcia, vous pouvez écrire ce code :

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` clause

   Pour trier le jeu de résultats, spécifiez la variable `orderBy` sous la forme d’un élément XML avec la propriété `sortDesc` attribut. Par exemple, pour trier les noms par ordre croissant, vous pouvez écrire le code suivant :

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Étape 2 : créer un objet de requête ;

Pour créer une entité à partir du code XML, utilisez la variable `create(`*`content`*`)` method :

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Préfixe le `create(`*`content`*`)` avec le schéma de l’entité à créer.

Le *`content`* est un argument de chaîne et est facultatif. Cet argument contient le code XML qui décrit l’entité.

### Étape 3 : exécution de la requête

Procédez comme suit :

1. Appelez le `ExecuteQuery` sur la méthode `queryDef` entity:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Traiter les résultats :
   1. Effectuez une itération sur les résultats de la variable `select` en utilisant un concept de boucle.
   1. Testez les résultats à l’aide de la méthode `getIfExists` opération.
   1. Comptez les résultats à l’aide du `count` opération.

#### Résultats d’une `select` operation

Toutes les correspondances sont renvoyées en tant que collection :

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Pour effectuer une itération sur les résultats, utilisez le `for each` loop :

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

La boucle comprend une variable de destinataire locale. Pour chaque destinataire renvoyé dans la collection de destinataires, l&#39;email du destinataire est imprimé. [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) à propos de `logInfo` fonction .

#### Résultats d’une `getIfExists` operation

Chaque correspondance est renvoyée en tant qu’élément :

```xml
<recipient id="52,378,079">
```

Si aucune correspondance n’est trouvée, un élément vide est renvoyé :

```xml
<recipient/>
```

Vous pouvez vous référer au noeud de la clé Principale, par exemple : `@id` attribute:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Résultat d’un `get` operation

Une correspondance est renvoyée en tant qu’élément :

```xml
<recipient id="52,378,079">
```

Si aucune correspondance n’est trouvée, une erreur est renvoyée.

>[!TIP]
>
>Si vous savez qu’il existe une correspondance, utilisez la variable `get` opération. Sinon, utilisez la variable `getIfExists` opération. Si vous utilisez cette bonne pratique, les erreurs révèlent des problèmes inattendus. Si vous utilisez la variable `get` , n’utilisez pas la variable `try…catch` . Le problème est géré par le processus de gestion des erreurs du workflow.

#### Résultat d’un `count` operation

Un élément avec la fonction `count` est renvoyé :

```xml
<recipient count="200">
```

Pour utiliser le résultat, reportez-vous à la section `@count` attribute:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Pour le `select` ajoutez ce code à une activité Code JavaScript dans le workflow :

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

Parce que la variable `select` est l’opération par défaut, vous n’avez pas besoin de la spécifier.

Cette vidéo montre comment lire depuis la base de données :
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Déclencher un workflow {#trigger-example}

Vous pouvez déclencher des workflows par programmation, par exemple dans des workflows techniques ou pour traiter les informations saisies par un utilisateur sur une page d’application web.

Le déclenchement d’un workflow s’effectue à l’aide d’événements. Vous pouvez utiliser ces fonctionnalités pour les événements :

* Pour publier un événement, vous pouvez utiliser la méthode statique `PostEvent` . [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Pour recevoir un événement, vous pouvez utiliser la variable **[!UICONTROL Signal externe]** activité. [En savoir plus](external-signal.md).

Vous pouvez déclencher des workflows de différentes manières :

* Vous pouvez déclencher un workflow en ligne, c’est-à-dire à partir du script principal d’une **[!UICONTROL Code JavaScript]** activité.
* Vous pouvez déclencher un workflow à la fin d’un autre :
   * Ajoutez un script d’initialisation au **[!UICONTROL Fin]** activité du workflow initial.
   * Ajoutez la variable **[!UICONTROL Signal externe]** activité au début du workflow cible.

      Une fois le workflow initial terminé, un événement est publié. La transition sortante est activée et les variables d&#39;événement sont renseignées. Ensuite, l&#39;événement est reçu par le workflow cible.

      >[!TIP]
      >
      >Lorsque vous ajoutez un script à une activité, il est recommandé de placer le nom de l’activité entre deux tirets, par exemple : `-- end --`. [En savoir plus](workflow-best-practices.md) à propos des bonnes pratiques relatives aux workflows.

Syntaxe de la variable `PostEvent` method :

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

Dans cet exemple, une fois le workflow terminé, un texte court est transmis au **signal** l’activité **wkfExampleReceiver** workflow :

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Parce que le dernier paramètre est défini sur `false`, la variable **wkfExampleReceiver** est déclenché chaque fois que le workflow initial est terminé.

Lorsque vous déclenchez des workflows, tenez compte des principes suivants :

* Le `PostEvent` s’exécute de manière asynchrone. La commande est placée dans la file d’attente du serveur. La méthode renvoie une valeur une fois l’événement publié.
* Le workflow cible doit être démarré. Dans le cas contraire, une erreur est consignée dans le fichier journal.
* Si le workflow cible est suspendu, la variable `PostEvent` est mise en file d’attente jusqu’à la reprise du workflow.
* L’activité déclenchée ne nécessite pas qu’une tâche soit en cours.

Cette vidéo montre comment utiliser des méthodes d’API statiques :
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Cette vidéo montre comment déclencher des workflows :
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interaction avec la base de données {#interact-example}

Ces exemples montrent comment effectuer ces actions :

* Utilisez la variable `get` et `create` méthodes sur les schémas pour utiliser des méthodes SOAP non statiques
* Création de méthodes qui exécutent des requêtes SQL
* Utilisez la variable `write` pour insérer, mettre à jour et supprimer des enregistrements

Procédez comme suit :

1. Définissez la requête :

   * Récupérez une entité en utilisant la variable `create` sur le schéma correspondant, par exemple, la méthode `xtk:workflow` schéma. [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Utilisez la variable `queryDef` pour émettre une requête SQL.

1. Exécutez la requête à l’aide du `ExecuteQuery` . [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Utilisez la variable `for each` pour récupérer les résultats.

### Syntaxe de la variable `queryDef` avec une méthode `select` clause

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create` method

#### Exemple 1 : sélectionner des enregistrements et écrire dans le journal ;

Les noms internes des workflows situés dans la variable **wfExamples** sont sélectionnés. Les résultats sont triés par nom interne, par ordre croissant et écrits dans le journal.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Exemple 2 : suppression d’enregistrements

Le prénom, le nom, l&#39;email et l&#39;identifiant de tous les destinataires nommés Chris Smith sont sélectionnés. Les résultats sont triés par email, dans un ordre croissant et écrits dans le journal. A `delete` est utilisée pour supprimer les enregistrements sélectionnés.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Exemple 3 : sélectionner des enregistrements et écrire dans le journal ;

Dans cet exemple, une méthode non statique est utilisée. L&#39;email et l&#39;année de naissance de tous les destinataires dont les informations sont stockées dans la variable **1234** et dont le nom de domaine d’email commence par &quot;adobe&quot; sont sélectionnés. Les résultats sont triés par date de naissance dans l’ordre décroissant. L&#39;email du destinataire est écrit dans le journal.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write` method

Vous pouvez insérer, mettre à jour et supprimer des enregistrements. Vous pouvez utiliser la variable `Write` sur n’importe quel schéma dans Adobe Campaign. Cette méthode étant statique, il n’est pas nécessaire de créer un objet. Vous pouvez utiliser les opérations suivantes :

* Le `update` operation
* Le `insertOrUpdate` avec l’opérateur `_key` argument permettant d’identifier l’enregistrement à mettre à jour

   Si vous ne spécifiez pas la variable **Destinataires** s’il existe une correspondance, l’enregistrement est mis à jour dans n’importe quel sous-dossier. Sinon, l’enregistrement est créé à la racine. **Destinataires** dossier.

* Le `delete` operation

>[!IMPORTANT]
> Si vous utilisez Adobe Campaign v8, nous vous recommandons d’utiliser le mécanisme d’évaluation avec la variable **Ingestion** et **Mise à jour/suppression de données** API pour la variable `Write` dans une table de Snowflake. [En savoir plus](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

#### Exemple 1 : insérer ou mettre à jour un enregistrement

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Exemple 2 : suppression d’enregistrements

Cet exemple combine une méthode statique à une méthode non statique.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

Cette vidéo montre comment utiliser des méthodes d’API non statiques :
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

Cette vidéo présente un exemple d’utilisation d’une méthode d’API non statique dans un workflow :
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Rubriques connexes

* [API orientées données](../../configuration/using/data-oriented-apis.md)
* [Scripts/Templates JavaScript](javascript-scripts-and-templates.md)
* [Méthodes SOAP en JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### Documentation des API

* [Exemples d&#39;appels SOAP](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Méthodes:
   * [Créer](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Write](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [fonction logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)

---
product: campaign
title: Exemples de code JavaScript dans les workflows
description: Ces exemples montrent comment vous pouvez utiliser le code JavaScript dans un workflow
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '1702'
ht-degree: 100%

---

# Exemples de code JavaScript dans les workflows{#javascript-in-workflows}



Ces exemples montrent comment vous pouvez utiliser le code JavaScript dans un workflow :

* [Écriture dans la base de données](#write-example)
* [Interrogation de la base de données](#read-example)
* [Déclenchement d’un workflow, à l’aide d’une méthode SOAP statique](#trigger-example)
* [Interaction avec la base de données, à l’aide d’une méthode SOAP non statique](#interact-example)

[En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=fr) sur les méthodes SOAP statiques et non statiques.

Dans ces exemples, l’extension ECMAScript pour XML (E4X) est utilisée. Avec cette extension, vous pouvez combiner des appels JavaScript et des primitives XML dans le même script.

Pour tester ces exemples, procédez comme suit :

1. Créez un workflow et ajoutez-y les activités suivantes :
   1. Activité Début
   1. Activité Code JavaScript
   1. Activité Fin

   [En savoir plus](building-a-workflow.md) sur la création de workflows.

1. Ajoutez le code JavaScript à une activité. [En savoir plus](advanced-parameters.md).
1. Enregistrez le workflow.
1. Testez les exemples :
   1. Démarrez le workflow. [En savoir plus](starting-a-workflow.md).
   1. Ouvrez le journal. [En savoir plus](monitoring-workflow-execution.md#displaying-logs).

## Exemple 1 : écriture dans la base de données{#write-example}

Pour écrire dans la base de données, vous pouvez utiliser la méthode `Write` statique sur le schéma `xtk:session` :

1. Composez une demande d’écriture en XML.

1. Écrivez l’enregistrement :

   1. Appelez la méthode `Write` sur le schéma `xtk:session`.

      >[!IMPORTANT]
      > Si vous utilisez Adobe Campaign v8, nous vous recommandons d’utiliser le mécanisme d’évaluation avec les API d’**ingestion** et de **mise à jour/suppression des données** pour la méthode `Write` dans une table Snowflake. [En savoir plus](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=fr){target="_blank"}.

   1. Transmettez le code XML en tant qu’argument de la demande d’écriture.

### Étape 1 : composer une demande d’écriture

Vous pouvez ajouter, mettre à jour et supprimer des enregistrements.

#### Insertion d’un enregistrement

L’opération `insert` étant l’opération par défaut, vous n’avez pas besoin de la préciser.

Indiquez ces informations sous forme d’attributs XML :

* Le schéma de la table à modifier
* Les champs de la table à renseigner

Exemple :

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Mise à jour d’un enregistrement

Utilisez l’opération `_update`. [En savoir plus](../../configuration/using/data-oriented-apis.md).

Indiquez ces informations sous forme d’attributs XML :

* Le schéma de la table à modifier
* Les champs de la table à mettre à jour
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

Utilisez la méthode `DeleteCollection`. [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=fr).

Indiquez les informations suivantes :

* Le schéma de la table à modifier
* La clause `where` requise pour identifier l’enregistrement à mettre à jour, sous la forme d’un élément XML

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

### Étape 2 : écrire l’enregistrement

Appelez la méthode `Write` non statique sur le schéma `xtk:session` :

```javascript
xtk.session.Write(myXML)
```

Aucune valeur n’est renvoyée pour cette méthode.

Ajoutez le code complet à une activité Code JavaScript dans le workflow :

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

Cette vidéo montre comment écrire dans la base de données :
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Exemple 2 : interrogation de la base de données{#read-example}

Pour interroger la base de données, vous pouvez utiliser la méthode d’instance `xtk:queryDef` non statique :

1. Composez une requête au format XML.
1. Créez un objet de requête.
1. Exécutez la requête.

### Étape 1 : composer une requête

Spécifiez le code XML pour une entité `queryDef`.

Syntaxe :

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Indiquez les informations suivantes :

* Le schéma de la table à lire
* L’opération
* Les colonnes à renvoyer, dans une clause `select`
* Les conditions, dans une clause `where`
* Les critères de filtrage, dans une clause `orderBy`

Vous pouvez utiliser les opérations suivantes :

| Fonctionnement | Résultat |
| --- | --- |
| `select` | Aucun ou plusieurs éléments sont renvoyés sous forme de collection. |
| `getIfExists` | Un élément est renvoyé. S’il n’existe aucun élément de correspondance, un élément vide est renvoyé. |
| `get` | Un élément est renvoyé. Si aucun élément de correspondance n’existe, une erreur est renvoyée. |
| `count` | Le nombre d’enregistrements correspondants est renvoyé sous la forme d’un élément avec un attribut `count`. |

Écrivez les clauses `select`, `where` et `orderBy` en tant qu’éléments XML :

* Clause `select`

  Indiquez les colonnes à renvoyer. Par exemple, pour sélectionner le prénom et le nom de la personne, écrivez le code suivant :

  ```xml
  <select>
      <node expr="@firstName"/>
      <node expr="@lastName"/>
  </select>
  ```

  Avec le schéma `nms:recipient`, les éléments sont renvoyés sous la forme suivante :

  ```xml
  <recipient firstName="Bo" lastName="Didley"/>
  ```

* Clause `where`

  Pour spécifier des conditions, utilisez une clause `where`. Par exemple, pour sélectionner les enregistrements qui se trouvent dans le dossier **Formation**, vous pouvez écrire le code suivant :

  ```xml
  <where>
      <condition expr="[folder/@label]='Training'"/>
  </where>
  ```

  Lorsque vous combinez plusieurs expressions, utilisez l’opérateur booléen dans la première expression. Par exemple, pour sélectionner toutes les personnes nommées Isabel Garcia, vous pouvez écrire le code suivant :

  ```xml
  <condition boolOperator="AND" expr="@firstName='Isabel'"/>
  <condition expr="@lastName='Garcia'"/>
  ```

* Clause `orderBy`

  Pour trier le jeu de résultats, spécifiez la clause `orderBy` sous la forme d’un élément XML avec l’attribut `sortDesc`. Par exemple, pour trier les noms par ordre croissant, vous pouvez écrire le code suivant :

  ```xml
  <orderBy>
      <node expr="@lastName> sortDesc="false"/>
  </orderBy>
  ```

### Étape 2 : créer un objet de requête

Pour créer une entité à partir du code XML, utilisez la méthode `create(`*`content`*`)` :

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Préfixez la méthode `create(`*`content`*`)` avec le schéma de l’entité à créer.

L’argument *`content`* correspond à un argument de chaîne et est facultatif. Cet argument contient le code XML qui décrit l’entité.

### Étape 3 : exécuter la requête

Procédez comme suit :

1. Appelez la méthode `ExecuteQuery` sur l’entité `queryDef` :

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Traitez les résultats :
   1. Effectuez une itération sur les résultats de l’opération `select`, en utilisant une construction de boucle.
   1. Testez les résultats à l’aide de l’opération `getIfExists`.
   1. Comptez les résultats à l’aide de l’opération `count`.

#### Résultats d’une opération `select`

Toutes les correspondances sont renvoyées sous forme de collection :

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Pour effectuer une itération sur les résultats, utilisez la boucle `for each` :

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

La boucle comprend une variable de destinataire locale. L’e-mail de chaque destinataire renvoyé dans la collection de destinataires est imprimé. [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=fr) sur la fonction `logInfo`.

#### Résultats d’une opération `getIfExists`

Chaque correspondance est renvoyée en tant qu’élément :

```xml
<recipient id="52,378,079">
```

Si aucune correspondance n’est trouvée, un élément vide est renvoyé :

```xml
<recipient/>
```

Vous pouvez vous référer au nœud de la clé primaire, par exemple, l’attribut `@id` :

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Résultat d’une opération `get`

Une correspondance est renvoyée en tant qu’élément :

```xml
<recipient id="52,378,079">
```

Si aucune correspondance n’est trouvée, une erreur est renvoyée.

>[!TIP]
>
>Si vous savez qu’il existe une correspondance, utilisez l’opération `get`. Sinon, utilisez l’opération `getIfExists`. Si vous utilisez cette bonne pratique, les erreurs révèlent des problèmes inattendus. Si vous utilisez l’opération `get`, n’utilisez pas l’ordre `try…catch`. Le problème est géré par le processus de gestion des erreurs du workflow.

#### Résultat d’une opération `count`

Un élément avec l’attribut `count` est renvoyé :

```xml
<recipient count="200">
```

Pour utiliser le résultat, reportez-vous à l’attribut `@count` :

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Pour l’opération `select`, ajoutez ce code à une activité Code JavaScript dans le workflow :

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

L’opération `select` étant l’opération par défaut, vous n’avez pas besoin de la préciser.

Cette vidéo montre comment effectuer une lecture à partir de la base de données :
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Déclenchement d’un workflow {#trigger-example}

Vous pouvez déclencher des workflows par programme, par exemple dans des workflows techniques ou pour traiter les informations saisies par un utilisateur sur une page d’application web.

Le déclenchement d’un workflow s’effectue à l’aide d’événements. Vous pouvez utiliser ces fonctionnalités pour les événements :

* Pour publier un événement, vous pouvez utiliser la méthode statique `PostEvent`. [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=fr).
* Pour recevoir un événement, vous pouvez utiliser l’activité **[!UICONTROL Signal externe]**. [En savoir plus](external-signal.md).

Vous pouvez déclencher des workflows de différentes manières :

* Vous pouvez déclencher un workflow en ligne, c’est-à-dire à partir du script principal d’une activité **[!UICONTROL Code JavaScript]**.
* Vous pouvez déclencher un workflow à la fin d’un autre :
   * Ajoutez un script d’initialisation à l’activité de **[!UICONTROL Fin]** du workflow initial.
   * Ajoutez l’activité **[!UICONTROL Signal externe]** au début du workflow cible.

     Une fois le workflow initial terminé, un événement est publié. La transition sortante est activée et les variables d’événement sont renseignées. Ensuite, l’événement est reçu par le workflow cible.

     >[!TIP]
     >
     >Lorsque vous ajoutez un script à une activité, il est recommandé de placer le nom de l’activité entre des tirets doubles, par exemple : `-- end --`. [En savoir plus](workflow-best-practices.md) sur les bonnes pratiques relatives aux workflows.

Syntaxe de la méthode `PostEvent` :

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

Dans cet exemple, une fois le workflow terminé, un texte court est transmis à l’activité **Signal** du workflow **wkfExampleReceiver** :

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Comme le dernier paramètre est défini sur `false`, le workflow **wkfExampleReceiver** est déclenché chaque fois que le workflow initial est terminé.

Lorsque vous déclenchez des workflows, tenez compte des principes suivants :

* La commande `PostEvent` s’exécute de manière asynchrone. La commande est placée dans la file d’attente du serveur. La méthode renvoie une valeur une fois l’événement publié.
* Le workflow cible doit être démarré. Dans le cas contraire, une erreur est consignée dans le fichier journal.
* Si le workflow cible est suspendu, la commande `PostEvent` est mise en file d’attente jusqu’à la reprise du workflow.
* L’activité déclenchée ne nécessite pas qu’une tâche soit en cours.

Cette vidéo montre comment utiliser des méthodes d’API statiques :
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Cette vidéo montre comment déclencher des workflows :
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interaction avec la base de données {#interact-example}

Ces exemples montrent comment effectuer ces actions :

* Utilisation des méthodes `get` et `create` sur les schémas pour utiliser des méthodes SOAP non statiques
* Création de méthodes qui exécutent des requêtes SQL
* Utilisation de la méthode `write` pour insérer, mettre à jour et supprimer des enregistrements

Procédez comme suit :

1. Définissez la requête :

   * Récupérez une entité en utilisant la méthode `create` sur le schéma correspondant, par exemple, le schéma `xtk:workflow`. [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=fr).
   * Utilisez la méthode `queryDef` pour émettre une requête SQL.

1. Exécutez la requête à l’aide de la méthode `ExecuteQuery`. [En savoir plus](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=fr).

   Utilisez la boucle `for each` pour récupérer les résultats.

### Syntaxe de la méthode `queryDef` avec une clause `select`

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

### Méthode `Create`

#### Exemple 1 : sélection d’enregistrements et écriture dans le journal

Les noms internes des workflows situés dans le dossier **wfExamples** sont sélectionnés. Les résultats sont triés par nom interne, par ordre croissant et écrits dans le journal.

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

#### Exemple 2 : suppression d’enregistrements

Le prénom, le nom, l’e-mail et l’identifiant de tous les destinataires nommés Chris Smith sont sélectionnés. Les résultats sont triés par e-mail, par ordre croissant et écrits dans le journal. Une opération `delete` est utilisée pour supprimer les enregistrements sélectionnés.

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

#### Exemple 3 : sélection des enregistrements et écriture dans le journal

Dans cet exemple, une méthode non statique est utilisée. L’e-mail et l’année de naissance de tous les destinataires dont les informations sont stockées dans le dossier **1234** et dont le nom de domaine de messagerie commence par « adobe » sont sélectionnés. Les résultats sont triés par date de naissance dans l’ordre décroissant. L’e-mail du destinataire est écrit dans le journal.

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

### Méthode `Write`

Vous pouvez insérer, mettre à jour et supprimer des enregistrements. Vous pouvez utiliser la méthode `Write` sur n’importe quel schéma dans Adobe Campaign. Cette méthode étant statique, il n’est pas nécessaire de créer un objet. Vous pouvez utiliser les opérations suivantes :

* Opération `update`
* Opération `insertOrUpdate` avec argument `_key` permettant d’identifier l’enregistrement à mettre à jour

  Si vous ne spécifiez pas le dossier **Destinataires**, en cas de correspondance, l’enregistrement est mis à jour dans n’importe quel sous-dossier. Sinon, l’enregistrement est créé dans le dossier racine **Destinataires**.

* Opération `delete`

>[!IMPORTANT]
> Si vous utilisez Adobe Campaign v8, nous vous recommandons d’utiliser le mécanisme d’évaluation avec les API d’**ingestion** et de **mise à jour/suppression des données** pour la méthode `Write` dans une table Snowflake. [En savoir plus](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=fr){target="_blank"}.

#### Exemple 1 : insertion ou mise à jour d’un enregistrement

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

#### Exemple 2 : suppression d’enregistrements

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

Cette vidéo montre comment utiliser des méthodes d’API non statiques :
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

Cette vidéo présente un exemple d’utilisation d’une méthode d’API non statique dans un workflow :
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Rubriques connexes

* [API orientées données](../../configuration/using/data-oriented-apis.md)
* [Scripts et modèles JavaScript](javascript-scripts-and-templates.md)
* [Méthodes SOAP en JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### Documentation des API

* [Exemples d’appels SOAP](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=fr)
* Méthodes :
   * [Create](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=fr)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=fr)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=fr)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=fr)
   * [Write](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html?lang=fr)
* [fonction logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=fr)

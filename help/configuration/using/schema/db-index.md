---
product: campaign
title: Éléments et attributs - élément dbindex
description: élément dbindex
feature: Schema Extension
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 100%

---

# élément dbindex {#dbindex--element}


## Modèle de contenu {#content-model-3}

dbindex:==keyfield

## Attributs {#attributes-3}

* @_operation (string)
* @applicableIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (boolean)

## Parents {#parents-3}

`<element>`

## Enfants {#children-3}

`<keyfield>`

## Description {#description-3}

Cet élément permet de définir un index associé à une table.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-3}

Il est possible de définir plusieurs index. Un index peut référencer un ou plusieurs champs de la table. Généralement, la déclaration des index suit la définition de l&#39;élément principal du schéma.

L&#39;ordre des éléments `<keyfield>` définis dans un `<dbindex>` est très important. Le premier `<keyfield>` doit être le critère d&#39;indexation sur lequel reposent principalement les requêtes.

Le nom de l’index en base est calculé par concaténation du nom de la table et du nom de l’index. Exemple : Nom de la table : « Sample », Namespace : « Cus », nom de l’index : « MyIndex » - nom du champ de l’index lors de la requête de création de l’index en table : « CusSample_myIndex ».

## Description des attributs {#attribute-description-3}

* **_operation (string)**: définit le type d&#39;écriture dans la base.

  Cet attribut est principalement utilisé lors d&#39;une extension de schéma usine.

  Les valeurs accessibles sont:

   * &quot;none&quot; : Réconciliation seule. Signifie qu&#39;Adobe Campaign va retrouver l&#39;élément sans le mettre à jour ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;insertOrUpdate&quot; : Mise à jour avec insertion. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou le créer s&#39;il n&#39;existe pas.
   * &quot;insert&quot; : Insertion. Signifie qu&#39;Adobe Campaign va insérer l&#39;élément sans vérifier s&#39;il existe.
   * &quot;update&quot; : Mise à jour. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;delete&quot; : Suppression. Signifie qu&#39;Adobe Campaign va retrouver et supprimer l&#39;élément.

* **applicableIf (string)**: condition de prise en compte de l&#39;index - reçoit une XTK expression.
* **label (string)**: libellé de l&#39;index.
* **name (MNTOKEN)**: nom unique de l&#39;index.
* **unique (boolean)**: si cette option est activée (@unique=&quot;true&quot;), alors cet attribut garantie l&#39;unicité de l&#39;index sur l&#39;ensemble des champs qui le composent.

## Exemples       {#examples-3}

Création d’un index sur le champ « id ». (L’attribut « @unique » sur l’élément `<dbindex>` déclenche l’ajout du mot clé SQL « UNIQUE » lorsque l’index est créé dans la base de données (requête)).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Création d&#39;un index composite sur les champs &quot;@mail&quot; et &quot;@phoneNumber&quot;:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

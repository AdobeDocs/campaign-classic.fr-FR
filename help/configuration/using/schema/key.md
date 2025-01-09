---
product: campaign
title: Éléments et attributs de schéma - élément key
description: élément key
feature: Schema Extension
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# élément key {#key--element}


## Modèle de contenu {#content-model-8}

key:==keyfield

## Attributs {#attributes-8}

* @allowEmptyPart (boolean)
* @applicableIf (string)
* @internal (boolean)
* @label (string)
* @name (MNTOKEN)
* @noDbIndex (boolean)

## Parents {#parents-8}

`<element>`

## Enfants {#children-8}

`<keyfield>`

## Description {#description-8}

Cet élément permet de définir une clef permettant d&#39;identifier un enregistrement de la table.

Une table doit posséder au moins une clef.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-6}

Par convention, les clefs sont déclarées après la déclaration de l&#39;élément principal du schéma et à la suite des déclarations d&#39;index.

Une clé est connue sous le nom de composite si elle comprend plusieurs champs (plusieurs `<keyfield>` enfants, par exemple). N’utilisez pas de clé composite pour définir une clé primaire.

Si l&#39;élément principal du schéma contient l&#39;attribut &quot;@autopk=true&quot; alors la clef primaire est unique. Une seule clef primaire doit être déclarée par schéma.

Les 1000 premiers identifiants sont réservés donc si une plage de valeurs doit être définies pour les clefs, il faut la commencer après la valeur 1000.

## Description des attributs {#attribute-description-8}

* **allowEmptyPart (boolean)**: dans le cas d&#39;une clef composite, si cet attribut est activé, la clef est considérée comme valide si au moins une des clefs composant la clef composite n&#39;est pas vide. Dans ce cas, la notion de valeur vide est &quot;0&quot; (booléen ou pour tous les types de données numériques). Par défaut, toutes les clefs d&#39;une clef composite doivent être remplies.
* **applicableIf (string)**: cet attribut permet de rendre la clef optionnelle. Il définit la condition d&#39;applicabilité de la définition de la clef. Cet attribut reçoit une expression XTK.
* **internal (boolean)**: s&#39;il est activé, cet attribut signifie à Adobe Campaign que la clef est primaire.
* **label (string)**: libellé de la clef.
* **name (MNTOKEN)**: nom interne de la clef.
* **noDbIndex (boolean)**: s&#39;il est activé (noDbIndex=&quot;true&quot;), le champ correspondant à la clef ne sera pas indexé.

## Exemples       {#examples-------}

Déclaration d&#39;une clef composite autorisant un des deux champs la composant &quot;@expr&quot; ou &quot;@alias&quot; à être vide:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Déclaration d&#39;une clef primaire sur le champ « Name » de type STRING dans `<srcschema>` et la requête SQL correspondante :

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

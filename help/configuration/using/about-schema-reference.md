---
product: campaign
title: À propos de la référence de schéma dans Adobe Campaign Classic
description: Découvrez comment configurer des schémas d’extension afin d’étendre le modèle de données conceptuel de la base de données Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '381'
ht-degree: 100%

---

# À propos de la référence des schémas{#about-schema-reference}

Ce chapitre décrit le mécanisme et le langage des schémas du modèle conceptuel de données de la base de données Adobe Campaign. Il est destiné à tous les développeurs ou intégrateurs voulant créer et éditer un schéma ou étendre un schéma d&#39;usine dans Adobe Campaign.

Pour une meilleure compréhension des tables intégrées de Campaign et de leur interaction, voir la section [Modèle de données Campaign Classic](https://helpx.adobe.com/fr/campaign/kb/acc-datamodel.html).

La structure physique et logique des données véhiculées dans l&#39;application est décrite en XML et respecte une grammaire propre à Adobe Campaign appelée **schéma**.

Un schéma est un document XML associé à une table de la base de données, il définit la structuration des données et décrit la définition SQL de la table :

* le nom de la table,
* des champs ;
* des index ;
* les liens avec les autres tables,

mais aussi la structure XML utilisée pour stocker les données :

* Eléments et attributs
* la hiérarchie entre les éléments,
* les types des éléments et des attributs,
* Les valeurs par défaut
* les libellés, les descriptions et autres propriétés.

Les schémas servent à définir en base une entité. A chaque entité, correspond un schéma.

L&#39;illustration suivante montre la place des schémas dans le système de données d&#39;Adobe Campaign :

![](assets/reference_schema_intro.png)

## Syntaxe des schémas {#syntax-of-schemas}

L&#39;élément racine du schéma est **`<srcschema>`**. Il contient les sous-éléments **`<element>`** et **`<attribute>`**.

Le premier sous-élément **`<element>`** correspond à la racine de l&#39;entité.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>L&#39;élément racine de l&#39;entité porte le nom du schéma.

![](assets/s_ncs_configuration_schema_and_entity.png)

Les balises **`<element>`** définissent les noms des éléments d&#39;entité. Les balises **`<attribute>`** du schéma définissent les noms des attributs dans les balises **`<element>`** auxquelles elles ont été liées.

## Identification d&#39;un schéma {#identification-of-a-schema}

Un schéma de données est identifié par son nom et son espace de noms.

Un espace de noms permet de regrouper un ensemble de schémas par centres d&#39;intérêt. Par exemple, on utilisera l&#39;espace de noms **cus** pour le paramétrage spécifique aux clients (**customers**).

La clé d&#39;identification d&#39;un schéma est une chaîne construite avec l&#39;espace de noms et le nom séparés par le caractère &#39;:&#39;, par exemple **cus:recipient**.

>[!IMPORTANT]
>
>Le nom de l&#39;espace de noms doit être court et ne doit contenir que des caractères autorisés conformément aux règles de nommage XML.
>
>Les identifiants ne doivent pas commencer par des caractères numériques.
>
>Les espaces de noms suivants sont réservés à la description des entités système requises pour le fonctionnement de l’application Adobe Campaign et ne doivent pas être utilisés : **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.


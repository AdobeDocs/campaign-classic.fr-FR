---
product: campaign
title: Implémenter des méthodes SOAP
description: Implémenter des méthodes SOAP
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '420'
ht-degree: 100%

---

# Implémentation des méthodes SOAP{#implementing-soap-methods}



## Introduction {#introduction}

Il est possible de créer des méthodes SOAP en Javascript. Cette fonctionnalité permet simplement des traitements applicatifs, elle peut remplacer le développement de JSPs et leur invocation dans les formulaire.

Ces méthodes SOAP se comporteront de la même façon que celles définies nativement dans l&#39;application. Les mêmes attributs sont supportés : statique, clé seule et const.

## Définition dʼune bibliothèque de méthodes {#defining-a-method-library}

La création d&#39;une bibliothèque de méthodes se divise en deux parties :

* La déclaration SOAP des méthodes,
* La définition (ou l&#39;implémentation) en JavaScript.

### Déclaration {#declaration}

Les méthodes doivent d’abord être déclarées dans les schémas (pour en savoir plus sur la création et l’édition des schémas, consultez [cette section](../../configuration/using/about-schema-edition.md)).

Leur déclaration est similaire à celle des méthodes natives. La seule différence est l’ajout de l’attribut &#39;library&#39; spécifiant le nom de la bibliothèque de méthodes dans laquelle se trouve la définition.

Ce nom correspond au nom (avec l&#39;espace de noms) de l&#39;entité de type &#39;Code JavaScript&#39;.

Exemple:

La méthode testLog(msg) est déclarée dans une extension de nms:recipient

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>L&#39;espace de noms et le nom utilisés pour la bibliothèque sont indépendants de l&#39;espace de noms et du nom du schéma dans lequel se trouve la déclaration.

### Définition {#definition}

Les méthodes SOAP sont implémentées sous forme de fonctions Javascript regroupées dans un script représentant une bibliothèque.

>[!NOTE]
>
>Une bibliothèque de méthodes peut regrouper des fonctions pour différents schémas ou inversement, les fonctions d&#39;un même schéma peuvent être definies dans des bibliothèques séparées.

Le script peut contenir du code qui sera exécuté au chargement initial de la bibliothèque.

**1. Nom**

Le nom de la fonction doit respecter le format suivant :

```
 <schema-namespace>_<schema-name>_<method-name>
```

Exemple:

La fonction JavaScript suivante correspond à l&#39;implémentation de la méthode déclarée plus haut. Elle doit être définie dans l&#39;entité de type &#39;Code JavaScript&#39; et de nom &#39;cus:test&#39;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Signature**

La signature de la fonction doit inclure un argument correspondant à chaque paramètre de type &#39;in&#39; ou &#39;inout&#39; de la déclaration.

Cas particuliers :

* **les méthodes non statiques** : la fonction doit inclure un argument supplémentaire en première position correspondant à l&#39;entité XML passée sous forme d&#39;objet de type &#39;xml&#39; (E4X).
* **les méthodes de type &quot;clé seule&quot;** : la fonction doit inclure un argument supplémentaire en première position correspondant à clé passée sous forme de chaîne de caractères.

**3. Valeurs retournées**

La fonction doit retourner une valeur pour chaque paramètre déclaré de type &#39;out&#39; ou &#39;inout&#39;. Cas particulier : Si la méthode est déclarée avec aucun des attributs &#39;statique&#39;, &#39;clé seule&#39; et &#39;const&#39;, La première valeur retournée doit correspondre à l&#39;entité modifiée. Il est possible de retourner un nouvel objet ou de retourner le premier paramètre modifié.

Par exemple :

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Lorsque plusieurs valeurs doivent être retournées, celles-ci doivent être retournées sous la forme d&#39;un tableau.

Exemple:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

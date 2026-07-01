---
product: campaign
title: Implémenter des méthodes SOAP
description: Implémenter des méthodes SOAP
feature: Configuration
role: Developer
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
TQID: https://experienceleague.adobe.com/EN-Xu7KjcQ5GXDqnEIySe23eQbhb2JGORf-vmpplNFs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b12f6872-9271-4369-85e5-86969a0b99a2id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: ht
source-wordcount: 418
ht-degree: 100%

---

# Implémentation des méthodes SOAP{#implementing-soap-methods}



## Introduction {#introduction}

Il est possible de créer des méthodes SOAP en JavaScript.Cette fonctionnalité permet simplement des traitements applicatifs. Elle peut remplacer le développement de JSP et leur invocation dans les formulaire.

Ces méthodes SOAP se comporteront de la même façon que celles définies nativement dans l’application.Les mêmes attributs sont pris en charge : statique, clé seule et const.

## Définition dʼune bibliothèque de méthodes {#defining-a-method-library}

La création d&#39;une bibliothèque de méthodes se divise en deux parties :

* La déclaration SOAP des méthodes,
* La définition (ou l&#39;implémentation) en JavaScript.

### Déclaration {#declaration}

Les méthodes doivent d’abord être déclarées dans les schémas (pour en savoir plus sur la création et l’édition des schémas, consultez [cette section](../../configuration/using/about-schema-edition.md)).

Leur déclaration est similaire à celle des méthodes natives. La seule différence est l’ajout de l’attribut &#39;library&#39; spécifiant le nom de la bibliothèque de méthodes dans laquelle se trouve la définition.

Ce nom correspond au nom (avec l&#39;espace de noms) de l&#39;entité de type &#39;Code JavaScript&#39;.

Exemple:

La méthode testLog(msg) est déclarée dans une extension nms:recipient.

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>L’espace de noms et le nom utilisés pour la bibliothèque sont indépendants de l’espace de noms et du nom du schéma dans lequel se trouve la déclaration.

### Définition {#definition}

Les méthodes SOAP sont implémentées sous forme de fonctions Javascript regroupées dans un script représentant une bibliothèque.

>[!NOTE]
>
>Une bibliothèque de méthodes peut regrouper des fonctions pour différents schémas ou inversement, les fonctions d&#39;un même schéma peuvent être definies dans des bibliothèques séparées.

Le script peut contenir du code qui sera exécuté au chargement initial de la bibliothèque.

**1.Nom**

Le nom de la fonction doit respecter le format suivant :

```
 <schema-namespace>_<schema-name>_<method-name>
```

Exemple:

La fonction JavaScript suivante correspond à l&#39;implémentation de la méthode déclarée plus haut. Elle doit être définie dans l’entité de type « Code JavaScript » et de nom « cus:test ».

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2.Signature**

La signature de la fonction doit inclure un argument correspondant à chaque paramètre de type &#39;in&#39; ou &#39;inout&#39; de la déclaration.

Cas particuliers :

* **les méthodes non statiques** : la fonction doit inclure un argument supplémentaire en première position correspondant à l&#39;entité XML passée sous forme d&#39;objet de type &#39;xml&#39; (E4X).
* **les méthodes de type &quot;clé seule&quot;** : la fonction doit inclure un argument supplémentaire en première position correspondant à clé passée sous forme de chaîne de caractères.

**3.Valeurs retournées**

La fonction doit renvoyer une valeur pour chaque paramètre de type « out » ou « inout ».Cas particulier : si la méthode est déclarée avec aucun des attributs « statique », « clé seule » et « const », la première valeur renvoyée doit correspondre à l’entité modifiée.Il est possible de renvoyer un nouvel objet ou de renvoyer le premier paramètre modifié.

Par exemple :

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Lorsque plusieurs valeurs doivent être renvoyées, elles doivent l’être sous la forme d’un tableau.

Exemple:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

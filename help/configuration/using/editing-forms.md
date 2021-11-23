---
product: campaign
title: Les formulaires d'édition
description: Les formulaires d'édition
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 49a98ec82b1d62f3af19260888da8eb24e460938
workflow-type: tm+mt
source-wordcount: '1679'
ht-degree: 2%

---


# Les formulaires d&#39;édition{#editing-forms}

![](../../assets/common.svg)

## Vue d’ensemble

Les marketeurs et les opérateurs utilisent des formulaires de saisie pour créer, modifier et prévisualiser des enregistrements. Forms affiche une représentation visuelle des informations.

Vous pouvez créer et modifier des formulaires de saisie :

* Vous pouvez modifier les formulaires d’entrée d’usine fournis par défaut. Les formulaires de saisie d’usine sont basés sur les schémas de données d’usine.
* Vous pouvez créer des formulaires de saisie personnalisés, en fonction des schémas de données que vous définissez.

Forms sont des entités de `xtk:form` type. Vous pouvez afficher la structure du formulaire de saisie dans le `xtk:form` schéma. Pour afficher ce schéma, choisissez **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]** dans le menu. En savoir plus sur [structure de formulaire](form-structure.md).

Pour accéder aux formulaires de saisie, choisissez **[!UICONTROL Administration] > [!UICONTROL Configuration] > [!UICONTROL Formulaires de saisie]** dans le menu :

![](assets/d_ncs_integration_form_arbo.png)

Pour concevoir des formulaires, éditez le contenu XML dans l&#39;éditeur XML :

![](assets/d_ncs_integration_form_edit.png)

[En savoir plus](form-structure.md#formatting).

Pour prévisualiser un formulaire, cliquez sur le bouton **[!UICONTROL Aperçu]** tab :

![](assets/d_ncs_integration_form_preview.png)

## Types de formulaires

Vous pouvez créer différents types de formulaires de saisie. Le type de formulaire détermine la manière dont les utilisateurs naviguent dans le formulaire :

* Écran de console

   Il s’agit du type de formulaire par défaut. Le formulaire comprend une seule page.

   ![](assets/console_screen_form.png)

* Gestion de contenu

   Utilisez ce type de formulaire pour la gestion de contenu. Voir [cas pratique](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistant

   Ce formulaire comprend plusieurs écrans flottants organisés en séquences spécifiques. Les utilisateurs naviguent d’un écran à l’autre. [En savoir plus](form-structure.md#wizards).

* Iconbox

   Ce formulaire comprend plusieurs pages. Pour naviguer dans le formulaire, les utilisateurs sélectionnent les icônes à gauche.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Ce formulaire comprend plusieurs pages. Pour parcourir le formulaire, les utilisateurs sélectionnent des onglets dans la partie supérieure du formulaire.

   ![](assets/notebook_form_preview.png)

* Volet vertical

   Ce formulaire affiche une arborescence de navigation.

* Volet horizontal

   Ce formulaire affiche une liste d’éléments.

## Les conteneurs

Dans les formulaires, vous pouvez utiliser des conteneurs à diverses fins :

* Organisation du contenu dans les formulaires
* Définition de l’accès aux champs de saisie
* Imbrication de formulaires dans d’autres formulaires

[En savoir plus](form-structure.md#containers).

### Organisation du contenu

Utilisez des conteneurs pour organiser le contenu dans les formulaires :

* Vous pouvez regrouper des champs dans des sections.
* Vous pouvez ajouter des pages à des formulaires multi-pages.

Pour insérer un conteneur, utilisez la méthode `<container>` élément . [En savoir plus](form-structure.md#containers).

#### Champs de groupe

Utilisez des conteneurs pour regrouper les champs de saisie dans des sections organisées.

Pour insérer une section dans un formulaire, utilisez l’élément suivant : `<container type="frame">`. Si vous le souhaitez, vous pouvez ajouter un titre de section à l’aide de la méthode `label` attribut.

Syntaxe : `<container type="frame" label="`*section_title*`"> […] </container>`

Dans cet exemple, un conteneur définit la variable **Création** , qui comprend la fonction **[!UICONTROL Créé par]** et **[!UICONTROL Nom]** champs de saisie :

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Ajouter des pages à des formulaires multi-pages

Pour les formulaires multi-pages, utilisez un conteneur pour créer une page de formulaire.

Cet exemple affiche des conteneurs pour la variable **Général** et **Détails** pages d’un formulaire :

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Définition de l’accès aux champs

Utilisez des conteneurs pour définir ce qui est visible et pour définir l’accès aux champs. Vous pouvez activer ou désactiver des groupes de champs.

### Imbriquer des formulaires

Utilisez des conteneurs pour imbriquer des formulaires dans d’autres formulaires. [En savoir plus](#add-pages-to-multipage-forms).

## Références aux images

Pour rechercher des images, choisissez **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** dans le menu.

Pour associer une image à un élément du formulaire, par exemple une icône, vous pouvez ajouter une référence à une image. Utilisez la variable `img` , par exemple, dans la variable `<container>` élément .

Syntaxe: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Cet exemple affiche des références au `book.png` et `detail.png` des images de `ncm` namespace :

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Ces images sont utilisées pour les icônes sur lesquelles les utilisateurs cliquent pour naviguer dans un formulaire multi-page :

![](assets/nested_forms_preview.png)

## Création d’un formulaire simple {#create-simple-form}

Pour créer un formulaire, procédez comme suit :

1. Dans le menu, choisissez **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Formulaires de saisie]**.
1. Cliquez sur le bouton **[!UICONTROL Nouveau]** en haut à droite de la liste.

   ![](assets/input-form-create-1.png)

1. Spécifiez les propriétés du formulaire :

   * Indiquez le nom du formulaire et l’espace de noms.

      Le nom du formulaire et l’espace de noms peuvent correspondre au schéma de données associé.  Cet exemple illustre un formulaire pour le `cus:order` schéma de données :

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

      Vous pouvez également spécifier explicitement le schéma de données dans la variable `entity-schema` attribut.

      ```xml
      <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
        […]
      </form>
      ```

   * Indiquez le libellé à afficher sur le formulaire.
   * Vous pouvez éventuellement spécifier le type de formulaire. Si vous ne spécifiez pas de type de formulaire, le type d’écran de la console est utilisé par défaut.

      ![](assets/input-form-create-2.png)

      Si vous concevez un formulaire multi-page, vous pouvez omettre le type de formulaire dans la variable `<form>` et indiquez le type dans un conteneur.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Insérez les éléments de formulaire.

   Par exemple, pour insérer un champ de saisie, utilisez la méthode `<input>` élément . Définissez la variable `xpath` à la référence du champ en tant qu’expression XPath. [En savoir plus](schema-structure.md#referencing-with-xpath).

   Cet exemple présente les champs de saisie basés sur la variable `nms:recipient` schéma.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Si le formulaire est basé sur un type de schéma spécifique, vous pouvez rechercher les champs de ce schéma :

   1. Cliquez sur **[!UICONTROL Insérer]** > **[!UICONTROL Champs du document]**.

      ![](assets/input-form-create-4.png)

   1. Sélectionnez le champ et cliquez sur **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Vous pouvez éventuellement spécifier l’éditeur de champ.

   Un éditeur de champ par défaut est associé à chaque type de données :
   * Pour un champ de type date, le formulaire affiche un calendrier de saisie.
   * Pour un champ de type énumération, le formulaire affiche une liste de sélection.

   Vous pouvez utiliser les types d’éditeur de champ suivants :

   | Éditeur de champ | attribut de formulaire |
   | --- | --- |
   | Bouton radio | `type="radiobutton"` |
   | Bouton à cocher | `type="checkbox"` |
   | Modifier l’arborescence | `type="tree"` |

   En savoir plus sur [contrôles de liste de mémoire](form-structure.md#memory-list-controls).

1. Vous pouvez éventuellement définir l’accès aux champs :

   | Élément | Attribut | Description |
   | --- | --- | --- |
   | `<input>` | `read-only:"true"` | Fournit un accès en lecture seule à un champ |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Affiche de manière conditionnelle un groupe de champs |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | Active de manière conditionnelle un groupe de champs |

   Exemple :

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. Vous pouvez également utiliser des conteneurs pour regrouper des champs dans des sections.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Création d’un formulaire multipage {#create-multipage-form}

Vous pouvez créer des formulaires multi-pages. Vous pouvez également imbriquer des formulaires dans d’autres formulaires.

### Créez un `iconbox` formulaire

Utilisez la variable `iconbox` type de formulaire pour afficher les icônes à gauche du formulaire, qui redirigent les utilisateurs vers différentes pages du formulaire.

![](assets/iconbox_form_preview.png)

Pour modifier le type d’un formulaire existant en `iconbox`, procédez comme suit :

1. Modifiez la variable `type` de l’attribut `<form>` element to `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Définissez un conteneur pour chaque page de formulaire :

   1. Ajouter un `<container>` comme enfant de l’élément `<form>` élément .
   1. Pour définir un libellé et une image pour l’icône, utilisez le `label` et `img` attributs.

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```
   Vous pouvez également supprimer la variable `type="frame"` de l’attribut existant `<container>` éléments .

### Créez un `notebook` formulaire

Utilisez la variable `notebook` type de formulaire pour afficher les onglets dans la partie supérieure du formulaire, qui permettent aux utilisateurs d’accéder à différentes pages.

![](assets/notebook_form_preview.png)

Pour modifier le type d’un formulaire existant en `notebook`, procédez comme suit :

1. Modifiez la variable `type` de l’attribut `<form>` element to `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Ajoutez un conteneur pour chaque page de formulaire :

   1. Ajouter un `<container>` comme enfant de l’élément `<form>` élément .
   1. Pour définir le libellé et l’image de l’icône, utilisez le `label` et `img` attributs.

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   Vous pouvez également supprimer la variable `type="frame"` de l’attribut existant `<container>` éléments .

### Imbriquer des formulaires {#nest-forms}

Vous pouvez imbriquer des formulaires dans d’autres formulaires. Par exemple, vous pouvez imbriquer des formulaires pour notebook dans des formulaires pour icônes.

Le niveau d’imbrication contrôle la navigation. Les utilisateurs peuvent accéder aux sous-formulaires.

Pour imbriquer un formulaire dans un autre formulaire, insérez une `<container>` et définissez la variable `type` sur le type de formulaire. Pour le formulaire de niveau supérieur, vous pouvez définir le type de formulaire dans un conteneur externe ou dans le `<form>` élément .

### Exemple

Cet exemple illustre un formulaire complexe :

* Le formulaire de niveau supérieur est un formulaire iconbox. Ce formulaire comprend deux conteneurs étiquetés **Général** et **Détails**.

   Par conséquent, le formulaire externe affiche la valeur **Général** et **Détails** pages au niveau supérieur. Pour accéder à ces pages, les utilisateurs cliquent sur les icônes situées à gauche du formulaire.

* Le sous-formulaire est un formulaire de notebook imbriqué dans la fonction **Général** conteneur. Le sous-formulaire se compose de deux conteneurs intitulés **Nom** et **Contact**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Par conséquent, la variable **Général** La page du formulaire externe affiche la variable **Nom** et **Contact** onglets.

![](assets/nested_forms_preview.png)

## Modifier un formulaire de saisie d’usine {#modify-factory-form}

Pour modifier un formulaire de fabrique, procédez comme suit :

1. Vous pouvez éventuellement étendre le schéma de données associé :

   1. Dans le menu, choisissez **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]**.
   1. Sélectionnez un schéma de données et étendez-le. Vous pouvez par exemple ajouter des champs. [En savoir plus](extending-a-schema.md).

      >[!CAUTION]
      > Ne modifiez pas les données d’origine dans un espace de noms d’usine, mais étendez-le dans un espace de noms personnalisé. La raison est que, lors des mises à niveau du logiciel, toutes les données des espaces de noms d’usine sont écrasées. Par exemple, les données de la variable `xtk`, `ncm`, et `nms` les espaces de noms d’usine sont remplacés. Les données de vos espaces de noms personnalisés ne sont pas modifiées.

1. Modifiez le formulaire de saisie d’usine :

   1. Dans le menu, choisissez **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Formulaires de saisie]**.
   1. Sélectionnez un formulaire de saisie et modifiez-le.

   Vous pouvez étendre les schémas de données d’usine, mais vous ne pouvez pas étendre les formulaires d’entrée d’usine. Nous vous recommandons de modifier directement les formulaires de saisie d’usine sans les recréer. Lors des mises à niveau du logiciel, vos modifications dans les formulaires d’entrée d’usine sont fusionnées avec les mises à niveau. Si la fusion automatique échoue, vous pouvez résoudre les conflits. [En savoir plus](../../production/using/upgrading.md#resolving-conflicts).

   Par exemple, si vous étendez un schéma de fabrique avec un champ supplémentaire, vous pouvez ajouter ce champ au formulaire de fabrique associé.

## Validation des formulaires {#validate-forms}

Vous pouvez inclure des contrôles de validation dans les formulaires.

### Accorder un accès en lecture seule aux champs

Pour accorder un accès en lecture seule à un champ, utilisez la méthode `readOnly="true"` attribut. Par exemple, vous pouvez afficher la Principale clé d’un enregistrement, mais avec un accès en lecture seule. [En savoir plus](form-structure.md#non-editable-fields).

Dans cet exemple, la clé Principale (`iRecipientId`) de la variable `nms:recipient` schéma s’affiche en lecture seule :

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Vérifier les champs obligatoires

Vous pouvez vérifier les informations obligatoires :

* Utilisez la variable `required="true"` pour les champs obligatoires.
* Utilisez la variable `<leave>` pour vérifier ces champs et afficher les messages d’erreur.

Dans cet exemple, l’adresse électronique est requise et un message d’erreur s’affiche si l’utilisateur n’a pas fourni ces informations :

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

En savoir plus sur [champs d&#39;expression](form-structure.md#expression-field) et [contexte du formulaire](form-structure.md#context-of-forms).

### Validation des valeurs

Vous pouvez utiliser des appels SOAP JavaScript pour valider les données de formulaire à partir de la console. Utilisez ces appels pour une validation complexe, par exemple pour comparer une valeur à une liste de valeurs autorisées. [En savoir plus](form-structure.md#soap-methods).

1. Créez une fonction de validation dans un fichier JS.

   Exemple :

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   Dans cet exemple, la fonction est nommée `checkValue`. Cette fonction permet de vérifier la variable `recipient` type de données dans la variable `nms` espace de noms. La valeur en cours de vérification est consignée. Si la valeur n’est pas valide, un message d’erreur est consigné. Si la valeur est valide, la valeur 1 est renvoyée.

   Vous pouvez utiliser la valeur renvoyée pour modifier le formulaire.

1. Dans le formulaire, ajoutez le `<soapCall>` à l’élément `<leave>` élément .

   Dans cet exemple, un appel SOAP est utilisé pour valider la variable `@valueToCheck` string:

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   Dans cet exemple, la variable `checkValue` et la méthode `nms:recipient` sont utilisés :

   * Le service est l’espace de noms et le type de données.
   * La méthode est le nom de la fonction. Le nom est sensible à la casse.

   L’appel est effectué de manière synchrone.

   Toutes les exceptions s’affichent. Si vous utilisez la variable `<leave>` , les utilisateurs ne peuvent pas enregistrer le formulaire tant que les informations saisies ne sont pas validées.

Cet exemple montre comment effectuer des appels de service depuis les formulaires :

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

Dans cet exemple, la saisie est un identifiant, qui est une clé Principale. Lorsque les utilisateurs remplissent le formulaire pour cet identifiant, un appel SOAP est effectué avec cet identifiant comme paramètre d’entrée. La sortie est une valeur booléenne qui est écrite dans ce champ : `/tmp/@count`. Vous pouvez utiliser cette valeur booléenne dans le formulaire. En savoir plus sur [contexte du formulaire](form-structure.md#context-of-forms).

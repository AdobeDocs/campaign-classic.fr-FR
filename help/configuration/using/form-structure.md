---
title: Structure d'un formulaire
seo-title: Structure d'un formulaire
description: Structure d'un formulaire
seo-description: null
page-status-flag: never-activated
uuid: b4e2078e-5630-493b-8ed5-3553ffea105c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: input-forms
discoiquuid: f8ae9497-9ca2-4c0c-8dc8-c0563839b036
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Structure d&#39;un formulaire{#form-structure}

La description d&#39;un formulaire est un document XML structuré respectant la grammaire du schéma des formes **xtk:form**.

The XML document of the input form must contain the `<form>` root element with the  **name** and  **namespace** attributes to populate the form name and namespace.

```
<form name="form_name" namespace="name_space">
...
</form>
```

Par défaut, un formulaire est associé au schéma de données avec le même nom et le même espace de noms. Pour associer un formulaire avec un nom différent, définissez l’attribut **entity-schema** de l’ `<form>` élément sur le nom de la clé de schéma. Pour illustrer la structure d&#39;un formulaire de saisie, nous allons décrire une interface à partir du schéma d&#39;exemple &quot;cus:recipient&quot; :

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="Male" value="1"/>   
    <value name="female" label="Female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
    <attribute name="birthDate" type="datetime" label="Date"/>
    <attribute name="gender" type="byte" label="Gender" enum="gender"/>
  </element>
</srcSchema>
```

Le formulaire de saisie à partir du schéma d&#39;exemple :

![](assets/d_ncs_integration_form_exemple1.png)

```
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

The description of the edit controls starts from the `<form>` root element. An edit control is entered in an **`<input>`** element with the **xpath** attribute containing the path of the field in its schema.

Le contrôle d&#39;édition s&#39;adapte automatiquement au type de données correspondant et utilise le libellé défini dans le schéma.

>[!NOTE]
>
>You can overload the label defined in its data schema by adding the **label** attribute to the `<input>` element:\
>`<input label="E-mail address" xpath="@name" />`

Par défaut, chaque champ est affiché sur une seule ligne et occupe tout l&#39;espace disponible selon le type de données.

## Mise en forme {#formatting}

La disposition des contrôles entre eux ressemble à celle utilisée dans les tableaux HTML, avec la possibilité de diviser un contrôle en plusieurs colonnes, utiliser des imbrications d&#39;éléments ou de spécifier l&#39;occupation de l&#39;espace disponible. Il faut cependant retenir que la mise en page autorise seulement des répartitions de proportions, il n&#39;est pas possible de spécifier des dimensions fixes pour un objet.

Pour afficher les contrôles de l&#39;exemple précédent sur deux colonnes :

![](assets/d_ncs_integration_form_exemple2.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email"/>
  </container>
</form>
```

The **`<container>`** element with the **colcount** attribute lets you force the display of child controls onto two columns.

L&#39;attribut **colspan** sur un contrôle étend celui-ci avec le nombre de colonnes renseignées dans sa valeur :

![](assets/d_ncs_integration_form_exemple3.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form> 
```

En renseignant l&#39;attribut **type=&quot;frame&quot;**, le conteneur ajoute un habillage autour des contrôles fils avec le libellé contenu dans l&#39;attribut **label** :

![](assets/d_ncs_integration_form_exemple4.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2" type="frame" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form>
```

A **`<static>`** element can be used to format the input form:

![](assets/d_ncs_integration_form_exemple5.png)

```
<form name="recipient" namespace="cus">
  <static type="separator" colspan="2" label="General"/>
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email" colspan="2"/>
  <static type="help" label="General information about recipient with date of birth, gender, and e-mail address." colspan="2"/>
</form>
```

The **`<static>`** tag with the **separator** type lets you add a separator bar with a label contained in the **label** attribute.

Un texte d’aide a été ajouté à l’aide de la `<static>` balise avec le type d’aide. Le contenu du texte est saisi dans l’attribut **label** .

## Les conteneurs {#containers}

Les conteneurs vous permettent de grouper un ensemble de contrôles. Ils sont représentés par l’ **`<container>`** élément. Ils ont été utilisés ci-dessus pour mettre en forme les contrôles sur plusieurs colonnes.

L’attribut **xpath** sur une `<container>` page vous permet de simplifier le référencement des contrôles enfants. Le référencement des contrôles est alors relatif au `<container>` parent parent.

Exemple de conteneur sans &quot;xpath&quot; :

```
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

Exemple avec ajout du &quot;xpath&quot; sur l&#39;élément de nom &quot;location&quot; :

```
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

### Types de conteneurs {#types-of-container}

Les conteneurs sont utilisés pour construire des contrôles complexes ayant recours à un ensemble de champs mis en forme dans des pages.

#### Conteneur à onglets {#tab-container}

Un conteneur à onglets met en forme les données dans des pages accessibles depuis des onglets.

![](assets/d_ncs_integration_form_exemple6.png)

```
<container type="notebook">
  <container colcount="2" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location">
    ...
  </container>
</container>
```

Le conteneur principal est défini par l&#39;attribut **type=&quot;notebook&quot;**. Les onglets sont déclarés dans les conteneurs fils, le libellé des onglets est renseigné à partir de l&#39;attribut **label**.

>[!NOTE]
>
>Une propriété **style=&quot;down|up**(par défaut)**&quot;** force le positionnement vertical des libellés des onglets en bas ou en haut du contrôle. Cette propriété est optionnelle.
>![](assets/d_ncs_integration_form_exemple7.png)
>`<container style="down" type="notebook">  ... </container>`

#### Liste à icônes {#icon-list}

Ce conteneur affiche une barre d&#39;icônes verticale permettant de sélectionner les pages à afficher.

![](assets/d_ncs_integration_form_exemple8.png)

```
<container type="iconbox">
  <container colcount="2" label="General" img="xtk:properties.png">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location" img="nms:msgfolder.png">
    ...
  </container>
</container>
```

Le conteneur principal est défini par l&#39;attribut **type=&quot;iconbox&quot;**. Les pages associées aux icônes sont déclarées dans les conteneurs fils. Le libellé des icônes est renseigné à partir de l&#39;attribut **label**.

The icon of a page is populated from the `img="<image>"` attribute, where `<image>` is the name of the image corresponding to its key made up of the name and namespace (e.g., &quot;xtk:properties.png&quot;).

Les images sont disponibles à partir du noeud **[!UICONTROL Administration > Paramétrage > Images]**.

#### Conteneur de visibilité {#visibility-container}

Vous pouvez masquer un ensemble de contrôles à partir d&#39;une condition dynamique.

Cet exemple illustre la visibilité des contrôles sur la valeur du champ &quot;Genre&quot; :

```
<container type="visibleGroup" visibleIf="@gender=1">
  ...
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  ...
</container>
```

Un conteneur de visibilité est défini par l&#39;attribut **type=&quot;visibleGroup&quot;**. L&#39;attribut **visibleIf** contient la condition de visibilité.

Exemples de syntaxes de conditions :

* **visibleIf=&quot;@email=&#39;peter.martinezATneeolane.net&#39;&quot;**: teste l’égalité sur les données de type chaîne. La valeur de comparaison doit être entre guillemets.
* **visibleIf=&quot;@gender >= 1 and @gender != 2&quot;** : condition sur une valeur numérique.
* **visibleIf=&quot;@boolean1==true or @boolean2==false&quot;** : test sur des champs booléens.

#### Conteneur d&#39;activation {#enabling-container}

Ce conteneur pemet l&#39;activation ou la désactivation d&#39;un ensemble de données à partir d&#39;une condition dynamique. La désactivation d&#39;un contrôle empêche son édition. L&#39;exemple suivant illustre l&#39;activation des contrôles à partir de la valeur du champ &quot;Genre&quot; :

```
<container type="enabledGroup" enabledIf="@gender=1">
  ...
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  ...
</container>
```

Un conteneur d&#39;activation est défini par l&#39;attribut **type=&quot;enabledGroup&quot;**. L&#39;attribut **enabledIf** contient la condition d&#39;activation.

## Edition d&#39;un lien {#editing-a-link}

Pour rappel, un lien est déclaré dans le schéma de données de la façon suivante :

```
<element label="Company" name="company" target="cus:company" type="link"/>
```

Le contrôle d&#39;édition du lien dans son formulaire de saisie est :

![](assets/d_ncs_integration_form_exemple9.png)

```
<input xpath="company"/>
```

Le choix de la cible est accessible à partir de la zone d&#39;édition. Une aide à la saisie par auto-complétion permet de retrouver facilement un élément de la cible en fonction des premiers caractères renseignés. La recherche se base alors sur la **Compute string** définie dans le schéma ciblé. Si la cible n&#39;existe pas après validation dans le contrôle, un message de confirmation de création à la volée de la cible est affiché. La confirmation crée un nouvel enregistrement de la table cible et l&#39;associe sur le lien.

Une liste déroulante permet de sélectionner un élément de la cible parmi la liste des enregistrements déjà créés.

L&#39;icône **[!UICONTROL Modifier le lien]** (dossier) lance une forme de sélection avec la liste des éléments ciblés et une zone de filtrage :

![](assets/d_ncs_integration_form_exemple10.png)

L&#39;icône **[!UICONTROL Editer le lien]** (loupe) lance la forme d&#39;édition de l&#39;élément lié. La forme utilisée est déduite par défaut sur la clé du schéma ciblé, l&#39;attribut **form** permet de forcer le nom de la forme d&#39;édition (par exemple &quot;cus:company2&quot;).

You can restrict the choice of target elements by adding the **`<sysfilter>`** element from the link definition in the input form:

```
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

You can also sort the list with the **`<orderby>`** element:

```
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### Propriétés du contrôle {#control-properties}

* **noAutoComplete** : désactive l&#39;auto-complétion (avec la valeur &quot;true&quot;)
* **createMode** : crée le lien à la volée s&#39;il n&#39;existe pas, les valeurs possibles sont :

   * **none** : désactive la création, un message d&#39;erreur est affiché si le lien n&#39;existe pas
   * **inline** : crée le lien avec le contenu dans la zone d&#39;édition
   * **edition** : affiche la forme d&#39;édition sur le lien, la validation de la forme enregistre les données (mode par défaut)

* **noZoom** : pas de forme d&#39;édition sur le lien (avec la valeur &quot;true&quot;)
* **form** : surcharge la forme d&#39;édition de l&#39;élément ciblé

## Liste de liens {#list-of-links}

Un lien renseigné dans le schéma de données en tant que élément de collection (@unbound=&quot;true&quot;) doit obligatoirement passer par une liste afin de visualiser l&#39;ensemble des éléments qui lui sont associés.

Le principe consiste à afficher la liste des éléments liés avec un chargement des données optimisé (récupération par batch des données, exécution de la liste uniquement si elle est visible).

Exemple de lien de collection dans un schéma :

```
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
...
</element>
```

La liste dans son formulaire de saisie :

![](assets/d_ncs_integration_form_exemple11.png)

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Le contrôle liste est defini par l&#39;attribut **type=&quot;linklist&quot;**, le chemin de la liste doit porter sur le lien de collection.

The columns are declared via the **`<input>`** elements of the list. L’attribut **xpath** fait référence au chemin du champ dans le schéma cible.

Une barre d&#39;outils avec un libellé (défini sur le lien dans le schéma) est automatiquement positionnée au-dessus de la liste.

La liste peut être filtrée à partir du bouton **[!UICONTROL Filtres]** et configurée pour ajouter et trier les colonnes.

Les boutons **[!UICONTROL Ajouter]** et **[!UICONTROL Supprimer]** permettent l&#39;ajout et la suppression des éléments de collection du lien. L&#39;ajout d&#39;un élément lance par défaut la forme d&#39;édition du schéma cible.

The **[!UICONTROL Detail]** button is automatically added when the **zoom=&quot;true&quot;** attribute is completed on the **`<input>`** tag of the list: it lets you launch the edit form of the selected line.

Un filtre et un tri peuvent être appliqués lors du chargement de la liste :

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
  <orderBy>
    <node expr="@date" sortDesc="true"/>
  </orderBy>
</input>
```

### Table de relation {#relationship-table}

Une table de relation permet de lier deux tables avec une cardinalité N-N. La table de relation contient uniquement les liens vers les deux tables.

L&#39;ajout d&#39;un élément dans la liste doit donc permettre de renseigner une liste à partir d&#39;un des deux liens de la table de relation.

Exemple de table de relation dans un schéma :

```
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

Pour notre exemple, nous partirons du formulaire de saisie du schéma &quot;cus:recipient&quot;. La liste doit afficher les associations avec les abonnements aux services et permettre d&#39;ajouter un abonnement en sélectionnant un service déjà existant.

![](assets/d_ncs_integration_form_exemple12.png)

```
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

L&#39;attribut **xpathChoiceTarget** permet de lancer une forme de choix à partir du lien renseigné. La création de l&#39;enregistrement de la table de relation va automatiquement mettre à jour le lien sur le destinataire courant et le service sélectionné.

>[!NOTE]
>
>L&#39;attribut **xpathEditTarget** permet de forcer l&#39;édition de la ligne sélectionnée sur le lien renseigné.

### Propriétés de la liste {#list-properties}

* **noToolbar** : cache la barre d&#39;outils (avec la valeur &quot;true&quot;)
* **toolbarCaption** : surcharge le libellé de la barre d&#39;outils
* **toolbarAlign** : modifie la géométrie verticale ou horizontale de la barre d&#39;outils (valeurs possibles : &quot;vertical&quot;|&quot;horizontal&quot;)
* **img** : affiche l&#39;image associée à la liste
* **form** : surcharge la forme d&#39;édition de l&#39;élément ciblé
* **zoom** : ajoute le bouton **[!UICONTROL Zoom]** pour l&#39;édition de l&#39;élément ciblé
* **xpathEditTarget** : fixe l&#39;édition sur le lien renseigné
* **xpathChoiceTarget** : pour l&#39;ajout, lance la forme de choix sur le lien renseigné

## Contrôles liste mémoire {#memory-list-controls}

Les listes mémoire permettent d&#39;éditer les éléments de collection avec le préchargement des données la liste. Cette liste ne peut être ni filtrée, ni configurée.

Ces listes sont utilisées sur les éléments de collections mappés en XML ou sur les liens à faible volume.

### Liste en colonnes {#column-list}

Ce contrôle affiche une liste à colonnes éditable avec une barre d&#39;outils contenant les boutons d&#39;ajout et de suppression.

![](assets/d_ncs_integration_form_exemple13.png)

```
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Le contrôle liste doit être renseigné avec l&#39;attribut **type=&quot;list&quot;**, le chemin de la liste doit porter sur l&#39;élément de collection.

The columns are declared in the child **`<input>`** tags of the list. Le libellé et la taille de colonne peuvent être forcés avec les attributs **label** et **colSize** .

>[!NOTE]
>
>Les flèches d&#39;ordonnancement sont ajoutées automatiquement lorsque l&#39;attribut **ordered=&quot;true&quot;** est ajouté sur l&#39;élément de collection dans le schéma de données.

Les boutons de la barre d&#39;outils peuvent être alignés horizontalement :

![](assets/d_ncs_integration_form_exemple14.png)

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

L&#39;attribut **toolbarCaption** force l&#39;alignement horizontal de la barre d&#39;outils et renseigne le titre au dessus de la liste.

#### Zoom dans les listes {#zoom-in-a-list}

L&#39;insertion et l&#39;édition des données d&#39;une liste peut être renseigné dans une forme d&#39;édition séparée.

![](assets/d_ncs_integration_form_exemple15.png)

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true" zoomOnAdd="true">
  <input xpath="@label"/>
  <input xpath="@date"/>

  <form colcount="2" label="Event">
    <input xpath="@label"/>
    <input xpath="@date"/>
  </form>
</input>
```

Le formulaire de modification est rempli à partir de l’ `<form>` élément sous la définition de liste. Sa structure est identique à celle d’un formulaire d’entrée. Le bouton **[!UICONTROL Détail]** est ajouté automatiquement lorsque l’attribut **zoom=&quot;true&quot;** est renseigné sur la **`<input>`** balise de la liste. Cet attribut vous permet de lancer le formulaire de modification de la ligne sélectionnée.

>[!NOTE]
>
>L&#39;ajout de l&#39;attribut **zoomOnAdd=&quot;true&quot;** force l&#39;appel de la forme d&#39;édition sur l&#39;insertion d&#39;un élément de la liste.

### Propriétés de la liste {#list-properties-1}

* **noToolbar** : cache la barre d&#39;outils (avec la valeur &quot;true&quot;)
* **toolbarCaption** : surcharge le libellé de la barre d&#39;outils
* **toolbarAlign** : modifie le positionnement de la barre d&#39;outils (valeurs possibles : &quot;vertical&quot;|&quot;horizontal&quot;)
* **img** : affiche l&#39;image associée à la liste
* **form** : surcharge la forme d&#39;édition de l&#39;élément ciblé
* **zoom** : ajoute le bouton **[!UICONTROL Zoom]** pour l&#39;édition de l&#39;élément ciblé
* **zoomOnAdd** : lance le forme d&#39;édition sur l&#39;ajout
* **xpathChoiceTarget** : pour l&#39;ajout, lance la forme de choix sur le lien renseigné

## Champs non éditables {#non-editable-fields}

To display a field and prevent it from being edited, use the **`<value>`** tag or complete the **readOnly=&quot;true&quot;** attribute on the **`<input>`** tag.

Exemple sur le champ &quot;Genre&quot; :

![](assets/d_ncs_integration_form_exemple16.png)

```
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## Bouton radio {#radio-button}

Un bouton radio vous permet de choisir parmi plusieurs options. Les **`<input>`** balises sont utilisées pour répertorier les options possibles et l’attribut **checkValue** spécifie la valeur associée au choix.

Exemple sur le champ &quot;Genre&quot; :

```
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## Bouton à cocher {#checkbox}

Un bouton à cocher permet de refléter un état boolean (pressé ou non). Par défaut ce contrôle est utilisé par les champs de type &quot;boolean&quot; (true/false). On peut associer à ce bouton une variable qui prendra par défaut la valeur 0 ou 1 ; cette valeur peut être surchargée à partir de l&#39;attribut **checkValue**.

```
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## Edition arborescente {#navigation-hierarchy-edit}

Ce contrôle construit une arborescence sur un ensemble de champs à éditer.

The controls to be edited are grouped in a **`<container>`** entered under the **`<input>`** tag of the tree control:

```
<input nolabel="true" type="treeEdit">
  <container label="Text fields">
    <input xpath="@text1"/>
    <input xpath="@text2"/>
  </container>
  <container label="Boolean fields">
    <input xpath="@boolean1"/>
    <input xpath="@boolean2"/>
  </container>
</input>
```

![](assets/d_ncs_integration_form_exemple18.png)

## Champ d&#39;expression {#expression-field}

An expression field updates a field dynamically from an expression; the **`<input>`** tag is used with an **xpath** attribute to enter the path of the field to be updated and an **expr** attribute containing the update expression.

```
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## Contexte des formes {#context-of-forms}

L&#39;exécution d&#39;un formulaire de saisie initialise un document XML contenant les données de l&#39;entité en cours d&#39;édition. Ce document représente le contexte du formulaire et peut être utilisé comme espace de travail.

### Mise à jour du contexte {#updating-the-context}

To modify the context of the form, use the **`<set expr="<value>" xpath="<field>"/>`** tag, where **`<field>`** is the destination field, and **`<value>`** is the update expression or value.

Examples of use of the **`<set>`** tag:

* **`<set expr="'Test'" xpath="/tmp/@test" />`**: positionne la valeur &quot;Test&quot; à l’emplacement temporaire /tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**: met à jour l&#39;entité sur l&#39;attribut &quot;lastName&quot; avec la valeur &quot;Test&quot;
* **`<set expr="true" xpath="@boolean1" />`**: définit la valeur du champ &quot;boolean1&quot; sur &quot;true&quot;
* **`<set expr="@lastName" xpath="/tmp/@test" />`**: mises à jour avec le contenu de l’attribut &quot;lastName&quot;

The context of the form can be updated when initializing and closing the form via the **`<enter>`** and **`<leave>`** tags.

```
<form name="recipient" namespace="cus">
  <enter>
    <set...
  </enter>
  ...
  <leave>
    <set...
  </leave>
</form>
```

>[!NOTE]
>
>The `<enter>`  and  `<leave>`   tags can be used on the `<container>` of pages (&quot;notebook&quot; and &quot;iconbox&quot; types).

### Langage d&#39;expression {#expression-language-}

Un macro-langage peut être utilisé dans la définition d&#39;un formulaire afin d&#39;effectuer des tests conditionnels.

The **`<if expr="<expression>" />`** tag executes the instructions specified under the tag if the expression is verified:

```
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

The **`<check expr="<condition>" />`** tag combined with the **`<error>`** tag prevents validation of the form and displays an error message if the condition is not satisfied:

```
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

## Assistants {#wizards}

Un assistant permet une saisie guidée à travers un ensemble d&#39;étapes présentées sous forme de pages. La validation du formulaire enregistre les informations saisies.

Un assistant se construit de la façon suivante :

```
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Wizard example" entity-schema="nms:recipient">
  <container title="Title of page 1" desc="Long description of page 1">
    <input xpath="@lastName"/>
    <input xpath="comment"/>
  </container>
  <container title="Title of page 2" desc="Long description of page 2">
    ...
  </container>
  ...
</form>
```

![](assets/d_ncs_integration_form_exemple19.png)

The presence of the **type=&quot;wizard&quot;** attribute on the `<form>` element lets you define the wizard mode in the construction of the form. Les pages sont terminées à partir d’ `<container>` éléments, qui sont des enfants de l’ `<form>` élément. L’ `<container>` élément d’une page est rempli avec les attributs de titre du titre et du desc pour afficher la description sous le titre de la page. Les boutons **[!UICONTROL Précédent]** et **[!UICONTROL Suivant]** sont automatiquement ajoutés afin de naviguer de page en page.

Le bouton **[!UICONTROL Terminer]** enregistre les informations saisies et ferme le formulaire.

### Méthodes SOAP {#soap-methods}

SOAP method execution can be launched from a populated **`<leave>`** tag at the end of a page.

The **`<soapcall>`** tag contains the call for the method with the following input parameters:

```
<soapCall name="<name>" service="<schema>">
  <param type="<type>" exprIn="<xpath>"/>  
  ...
</soapCall>
```

The name of the service and its implementation schema are entered via the **name** and **service** attributes of the **`<soapcall>`** tag.

The input parameters are described on the **`<param>`** elements under the **`<soapcall>`** tag.

Le type du paramètre doit être spécifié à partir de l&#39;attribut **type**. Les différents types possibles sont les suivants :

* **string** : chaîne de caractères
* **boolean** : booléen
* **byte** : nombre entier 8 bits
* **short** : nombre entier 16 bits
* **long** : nombre entier 32 bits
* **short** : nombre entier 16 bits
* **double** : nombre flottant double précision
* **DOMElement** : noeud de type élément

L&#39;attribut **exprIn** contient l&#39;emplacement de la donnée à passer en paramètre.

**Exemple**:

```
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param type="DOMElement" exprIn="/tmp/entityList"/>         
    <param type="DOMElement" exprIn="/tmp/choiceList"/>         
    <param type="boolean"    exprIn="true"/>       
  </soapCall>
</leave>
```


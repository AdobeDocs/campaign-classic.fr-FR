---
title: Modèle de publication
seo-title: Modèle de publication
description: Modèle de publication
seo-description: null
page-status-flag: never-activated
uuid: 1976f70c-b2d8-44ca-8fc3-6451fb67d18b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 279b0ae6-2578-4f1f-af59-13a1a9c80b32
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Modèle de publication{#publication-templates}

## A propos des modèles de publication {#about-publication-templates}

Le modèle de publication est la fiche d&#39;identité du contenu à publier. Il référence les ressources utilisées dans le processus de publication, à savoir :

* le schéma de données,
* le formulaire de saisie,
* les modèles de transformation pour chaque document de sortie.

## Identification d&#39;un modèle de publication {#identification-of-a-publication-template}

Un modèle de publication est identifié par son nom et son espace de nommage.

La clé d&#39;identification d&#39;une feuille de style est une chaîne construite avec l&#39;espace de nommage et le nom séparés par le caractère &#39;:&#39; (par exemple : **xac:newsletter**).

>[!NOTE]
>
>Dans la pratique, il est recommandé d&#39;utiliser la même clé pour le schéma, le formulaire et le modèle de publication.

## Création et paramétrage du modèle {#creating-and-configuring-the-template}

Les modèles de publication sont stockés par défaut dans le **[!UICONTROL Administration > Configuration > Publication templates]** noeud. Pour créer un modèle, cliquez sur le **[!UICONTROL New]** bouton au-dessus de la liste des modèles.

Pour paramétrer le modèle de publication, indiquez le nom du modèle (c&#39;est-à-dire la clé d&#39;identification composée du nom et de l&#39;espace de nommage), son libellé, le schéma de données et le formulaire de saisie auxquels il est associé.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>Le libellé apparaîtra lors de la création d&#39;un contenu à partir de ce modèle de publication.

The **Check status to validate content generation** option forces a check on the &quot;Validated&quot; status of the content instances to authorize file generation. For more on this, refer to [Publication](#publication).

Un modèle de transformation doit être ajouté pour chaque document de sortie. Vous pouvez créer autant de modèles de transformation que nécessaire.

Le **[!UICONTROL Name of template]** champ est un libellé gratuit qui décrit le type de rendu à la sortie. Pour chaque modèle de transformation, les paramètres de publication sont disponibles dans les onglets.

### Rendu {#rendering}

L’ **[!UICONTROL Rendering]** onglet, choisissez :

* le type de rendu utilisé pour la projection du document de sortie : feuille de style XSL ou template JavaScript,
* le format du document de sortie : HTML, Texte, XML ou RTF,
* le modèle contenant les informations de construction, c&#39;est-à-dire la feuille de style ou le template JavaScript à utiliser.

### Publication {#publication}

Publication involves generating the output document in the form of a file, if the type selected is **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

Les options de publication disponibles sont les suivantes :

* Le jeu de caractères d’encodage du fichier de sortie peut être forcé via le **[!UICONTROL Encoding]** champ. Le jeu de caractères Latin 1 (1252) est utilisé par défaut.
* Cette **[!UICONTROL Multi-file generation]** option active un mode de publication de document spécial. Cette option consiste à renseigner une balise de partitionnement au début de chaque page du document de sortie. La génération du contenu génère un fichier pour chaque balise de partitionnement renseignée. Ce mode est utilisé pour générer des mini-sites à partir d’un bloc de contenu. for more on this, refer to [Multi-file generation](#multi-file-generation).
* Le **[!UICONTROL Location]** champ contient le nom du fichier de sortie. Le nom peut être composé de variables afin de générer un nom de fichier automatique.

   A variable is populated with the following format: **`$(<xpath>)`, where `<xpath>` is the path of a field of the publication template data schema.

   Le nom du fichier peut être composé d&#39;un champ de type date. Pour formater correctement ce champ, vous devez utiliser la fonction **$date-format**, avec comme paramètres le chemin du champ et le format de sortie.

   Par défaut, le format de construction du nom du fichier utilise les variables sur les champs &quot;@name&quot; et &quot;@date&quot; :

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   Le nom du fichier généré sera donc composé comme suit : ct_news12_20110901.htm.

   >[!NOTE]
   >
   >Pour plus d’informations sur la génération de contenu, voir [Création d’une instance](../../delivery/using/using-a-content-template.md#creating-a-content-instance)de contenu.

### Diffusion {#delivery}

Cet onglet permet de sélectionner un modèle de diffusion afin de lancer une diffusion directement sur le contenu. Le contenu de l&#39;email sera automatiquement renseigné en fonction des formats de sortie HTML ou Texte.

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>For an example of delivery creation based on a content, refer to [Delivering a content instance](../../delivery/using/using-a-content-template.md#delivering-a-content-instance).

### Agrégateur {#aggregator}

Un traitement d&#39;agrégation de données à partir d&#39;un script ou d&#39;une liste de requêtes permet d&#39;enrichir le document XML des données du contenu. Le principe est de compléter certaines informations référencées par des liens, ou d&#39;ajouter des éléments provenant de la base de données.

### Génération multi-fichiers {#multi-file-generation}

Pour activer la génération de plusieurs fichiers, sélectionnez l’ **[!UICONTROL Multi-file generation]** option dans le modèle de publication. Cette option vous permet de spécifier des balises de partitionnement dans la feuille de style pour le début de chaque page du document de sortie. La génération du contenu produira un fichier pour chaque balise de partitionnement rencontrée.

La balise de découpe à intégrer dans la feuille de style est la suivante :

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** où **`<name_of_file>`** correspond au nom de fichier de la page à générer.

**Exemple :**Génération de fichiers multiples à l’aide du schéma &quot;cus:book&quot;.

Le principe consiste à générer une page principale énumérant la liste des chapitres, avec possibilité d&#39;afficher le détail du chapitre dans une page externe.

![](assets/d_ncs_content_chunk.png)

La feuille de style (&quot;cus:livre.xsl&quot;) correspondante est la suivante :

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Une deuxième feuille de style (&quot;cus:chapitre.xsl&quot;) est nécessaire pour générer le détail des chapitres :

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

La balise de découpe est renseignée en début de page à inclure dans le fichier à générer.

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

The filename is constructed with the **$(path)** variable containing the publication path and **`<xsl:value-of select="@id" />`**, which matches the identifier of the chapter in the input document.

Le modèle de publication doit être renseigné avec les deux feuilles de style &quot;cus:livre.xsl&quot; et &quot;cus:chapitre.xsl&quot;.

The **[!UICONTROL Multi-file generation]** option must be active on the chapter transformation model:

![](assets/d_ncs_content_chunk2.png)

The **[!UICONTROL Location]** field is not used in the generation of multiple files, but you must still populate this field to avoid an error when publishing.

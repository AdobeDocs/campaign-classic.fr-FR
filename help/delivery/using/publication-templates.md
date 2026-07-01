---
product: campaign
title: Modèle de publication
description: Modèle de publication
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Templates
role: User
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
TQID: https://experienceleague.adobe.com/mU7usRNlg73dYQS1PuorYpp9g4d7bNXAWBtIEE1VULk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 844
ht-degree: 100%

---

# Modèles de publication{#publication-templates}

## À propos des modèles de publication {#about-publication-templates}

Le modèle de publication référence les ressources utilisées dans le processus de publication, à savoir :

* le schéma de données,
* le formulaire de saisie,
* les modèles de transformation pour chaque document de sortie.

## Identification d&#39;un modèle de publication {#identification-of-a-publication-template}

Un modèle de publication est identifié par son nom et son espace de noms.

La clé d’identification d’une feuille de style est une chaîne construite avec l’espace de noms et le nom séparés par le caractère deux-points ; par exemple : **cus:newsletter**.

>[!NOTE]
>
>Dans la pratique, il est recommandé d&#39;utiliser la même clé pour le schéma, le formulaire et le modèle de publication.

## Création et configuration du modèle {#creating-and-configuring-the-template}

Les modèles de publication sont stockés par défaut dans le noeud **[!UICONTROL Administration > Paramétrages > Modèles de publication]**. Pour créer un nouveau modèle, cliquez sur le bouton **[!UICONTROL Nouveau]** situé au-dessus de la liste des modèles.

Pour paramétrer le modèle de publication, indiquez le nom du modèle (c&#39;est-à-dire la clé d&#39;identification composée du nom et de l&#39;espace de noms), son libellé, le schéma de données et le formulaire de saisie auxquels il est associé.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>Le libellé apparaîtra lors de la création d&#39;un contenu à partir de ce modèle de publication.

L’option **Vérifier le statut pour valider la génération du contenu** force la vérification du statut « Validé » des instances de contenu pour autoriser la génération du fichier. Pour plus d’informations, consultez la section [Publication](#publication).

Un modèle de transformation doit être ajouté pour chaque document de sortie.Vous pouvez créer autant de modèles de transformation que nécessaire.

Le champ **[!UICONTROL Nom du modèle]** est un libellé libre qui décrit le type de rendu en sortie.Pour chaque modèle de transformation, les paramètres de publication sont disponibles dans les onglets.

### Rendu {#rendering}

Dans l&#39;onglet **[!UICONTROL Rendu]**, choisissez :

* le type de rendu utilisé pour la projection du document de sortie : feuille de style XSL ou template JavaScript,
* le format du document de sortie : HTML, Texte, XML ou RTF,
* le modèle contenant les informations de construction, c&#39;est-à-dire la feuille de style ou le template JavaScript à utiliser.

### Publication {#publication}

La publication consiste à générer le document de sortie sous la forme d&#39;un fichier. Pour cela, vous devez sélectionner le type **[!UICONTROL Fichier]**.

![](assets/d_ncs_content_model2.png)

Les options de publication disponibles sont les suivantes :

* Il est possible de forcer le jeu de caractères d’encodage du fichier de sortie à partir du champ **[!UICONTROL Codage]**.Le jeu de caractères Latin 1 (1252) est utilisé par défaut.
* L’option **[!UICONTROL Génération multi-fichiers]** active un mode de publication de documents particulier.Cette option consiste à renseigner une balise de partitionnement au début de chaque page du document de sortie.La génération du contenu créera un fichier pour chaque balise de partitionnement renseignée.Ce mode est utilisé pour générer des mini-sites à partir d’un bloc de contenu.Voir à ce propos [Génération multi-fichiers](#multi-file-generation)
* Le champ **[!UICONTROL Localisation]** contient le nom du fichier de sortie.Le nom peut être construit à partir de variables afin de générer un nom de fichier automatique.

  Une variable est renseignée avec le format suivant : **`$(<xpath>)`**, où **`<xpath>`** est le chemin d’un champ du schéma de données du modèle de publication.

  Le nom du fichier peut être composé d&#39;un champ de type date. Pour formater correctement ce champ, vous devez utiliser la fonction **$date-format**, avec comme paramètres le chemin du champ et le format de sortie.

  Par défaut, le format de construction du nom du fichier utilise les variables sur les champs &quot;@name&quot; et &quot;@date&quot; :

  ```xml
  ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
  ```

  Le nom du fichier généré sera donc composé comme suit : ct_news12_20110901.htm.

  >[!NOTE]
  >
  >Pour plus d’informations sur la génération du contenu, consultez la section [Création d’une instance de contenu](using-a-content-template.md#creating-a-content-instance).

### Diffusion {#delivery}

Cet onglet vous permet de sélectionner un scénario afin de lancer une diffusion directement sur le contenu.Le contenu de l’e-mail sera automatiquement renseigné en fonction du format de sortie (HTML ou Texte).

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>Pour découvrir un exemple de création de diffusion à partir dʼun contenu, consultez la section [Diffusion dʼune instance de contenu](using-a-content-template.md#delivering-a-content-instance).

### Agrégateur {#aggregator}

L’agrégation de données à partir d’un script ou d’une liste de requêtes vous permet d’enrichir le document XML avec les données du contenu.L’objectif est de compléter certaines informations référencées par des liens, ou d’ajouter des éléments de la base de données.

### Génération multi-fichiers {#multi-file-generation}

Pour activer la génération multi-fichiers, sélectionnez l’option **[!UICONTROL Génération multi-fichiers]** dans le modèle de publication.Cette option vous permet d’indiquer des balises de partitionnement dans la feuille de style en début de chaque page du document de sortie.La génération du contenu créera un fichier pour chaque balise de partitionnement rencontrée.

La balise de découpe à intégrer dans la feuille de style est la suivante :

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** où **`<name_of_file>`** correspond au nom de fichier de la page à générer.

**Exemple :** génération multi-fichiers à l’aide du schéma « cus:book ».

Le principe consiste à générer une page principale énumérant la liste des chapitres, avec possibilité d&#39;afficher le détail du chapitre dans une page externe.

![](assets/d_ncs_content_chunk.png)

La feuille de style correspondante (« cus:book.xsl ») est la suivante :

```xml
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

Une deuxième feuille de style (« cus:chapter.xsl ») est nécessaire pour générer les détails des chapitres :

```xml
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

```xml
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

Le nom du fichier est construit avec la variable **$(path)** contenant le chemin de publication et **`<xsl:value-of select="@id" />`**, qui correspond à l&#39;identifiant du chapitre dans le document en entrée.

Le modèle de publication doit être renseigné avec les deux feuilles de style « cus:book.xsl » et « cus:chapter.xsl ».

L’option **[!UICONTROL Génération multi-fichiers]** doit être active sur le modèle de transformation des chapitres :

![](assets/d_ncs_content_chunk2.png)

Le champ **[!UICONTROL Localisation]** n&#39;est pas utilisé dans la génération multi-fichiers, vous devez toutefois renseigner ce champ afin d&#39;éviter une erreur lors de la publication.

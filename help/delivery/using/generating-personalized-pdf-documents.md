---
title: Générer des documents PDF personnalisés
seo-title: Générer des documents PDF personnalisés
description: Générer des documents PDF personnalisés
seo-description: null
page-status-flag: never-activated
uuid: d4c27523-bff3-457a-ba60-e2747a2b3166
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 8dfc5e7c-c762-46ba-bbda-a7251354cb47
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Générer des documents PDF personnalisés{#generating-personalized-pdf-documents}

## A propos des documents PDF variables {#about-variable-pdf-documents}

Adobe Campaign permet la génération de documents PDF variables (pièces jointes d&#39;email, diffusion courrier papier) à partir de documents LibreOffice ou Microsoft Word.

Les extensions supportées sont : &quot;.docx&quot;, &quot;.doc&quot;, et &quot;.odt&quot;.

Pour personnaliser vos documents, vous disposez des mêmes fonctionnalités JavaScript que celles disponibles pour la personnalisation des e-mails.

You need to activate the **[!UICONTROL &quot;The content of the file is personalized and converted to PDF during the delivery of each message&quot;]** option. This option is accessible when you attach the file to the delivery email. Pour plus d’informations sur l’association d’un fichier calculé, reportez-vous à la section [Joindre des fichiers](../../delivery/using/attaching-files.md) .

Exemple de personnalisation de l&#39;en-tête d&#39;une facture :

![](assets/s_ncs_pdf_simple.png)

Si vous souhaitez générer des tableaux dynamiques ou inclure des images à partir d&#39;URL, vous devez suivre une procédure particulière.

## Générer des tableaux dynamiques {#generating-dynamic-tables}

La procédure pour générer des tableaux dynamiques est la suivante :

* Créez un tableau de trois lignes, avec autant de colonnes que vous le souhaitez, et paramétrez sa mise en forme (bordures, trame, etc.).
* Positionnez le curseur sur le tableau créé, et cliquez dans le menu **[!UICONTROL Tableau > Propriétés du tableau]**. Depuis l&#39;onglet **[!UICONTROL Tableau]**, saisissez un nom commençant par **NlJsTable**.
* Dans la première cellule de la première ligne, définissez une boucle (&quot;for&quot; par exemple) qui va permettre d&#39;itérer sur les valeurs que vous souhaitez afficher dans votre tableau.
* Insérez, dans chaque cellule de la deuxième ligne du tableau, les scripts retournant les valeurs à afficher.
* Fermez votre boucle dans la troisième et dernière ligne du tableau.

   Exemple de définition d&#39;un tableau dynamique :

   ![](assets/s_ncs_pdf_table.png)

## Insérer des images externes {#inserting-external-images}

L&#39;insertion d&#39;images externes est utile lorsque, par exemple, vous souhaitez personnaliser un document avec une image dont l&#39;URL est renseignée dans un champ du destinataire.

Pour cela, il est nécessaire de paramétrer un bloc de personnalisation puis d&#39;inclure dans le fichier attaché un appel au bloc de personnalisation.

**Exemple : Insertion d&#39;un logo personnalisé en fonction du pays du destinataire**

**Etape n°1 : Création du fichier attaché :**

* Insérez l&#39;appel au bloc de personnalisation : **&lt;%@ include view=&quot;nomdubloc&quot; %>**
* Insérez votre contenu personnalisé ou non dans le corps du fichier

![](assets/s_ncs_open_office_blocdeperso.png)

**Etape n°2 : Création du bloc de personnalisation:**

* Allez dans le menu **[!UICONTROL Ressources > Gestion de campagne > Blocs de personnalisation]** de la console Adobe Campaign.
* Créez un nouveau bloc de personnalisation &quot;Mon Logo&quot; avec pour nom interne &quot;Mon_Logo&quot;.
* Cliquez sur le lien **[!UICONTROL Paramètres avancés...]** et cochez l&#39;option **[!UICONTROL &quot;Le bloc est inclus dans un document attaché&quot;]**. Cette option va permettre de recopier la définition du bloc de personnalisation directement dans le contenu du fichier OpenOffice.

   ![](assets/s_ncs_pdf_bloc_option.png)

   Il est nécessaire de distinguer deux types de déclaration à l&#39;intérieur du bloc de personnalisation :

   * The Adobe Campaign code of the personalization fields for which the &quot;open&quot; and &quot;closed&quot; chevrons must be replaced with escape characters (respectively `&lt;` and `&gt;`).
   * Le code XML OpenOffice qui sera intégralement recopié dans le document OpenOffice.

Dans l&#39;exemple, le bloc de personnalisation est de cette forme :

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

En fonction du pays du destinataire, la personnalisation est bien visible dans le document lié à la diffusion:

![](assets/s_ncs_pdf_result.png)

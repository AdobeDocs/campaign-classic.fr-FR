---
product: campaign
title: Génération de documents PDF personnalisés
description: Découvrez comment générer des documents PDF personnalisés
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Personalization
role: User
hide: true
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
TQID: https://experienceleague.adobe.com/5hETJLlKZ9iWu2k1nW-RMeDlzpSm7wFwfe3QwSEZCa4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 499
ht-degree: 100%

---

# Génération de documents PDF personnalisés{#generating-personalized-pdf-documents}

## À propos des documents PDF variables {#about-variable-pdf-documents}

Adobe Campaign permet la génération de documents PDF variables pour pièces jointes d&#39;email à partir de documents LibreOffice ou Microsoft Word.

Les extensions supportées sont : &quot;.docx&quot;, &quot;.doc&quot;, et &quot;.odt&quot;.

Pour personnaliser vos documents, vous disposez des mêmes fonctionnalités JavaScript que celles disponibles pour la personnalisation des e-mails.

Vous devez activer l’option **[!UICONTROL « Le contenu du fichier est personnalisé et converti en PDF au moment de la diffusion pour chaque message »]**.Cette option est accessible lors de l’ajout du fichier en pièce jointe à l’e-mail de la diffusion.Pour en savoir plus sur l’ajout d’un fichier calculé en pièce jointe, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=fr){target="_blank"}.

Exemple de personnalisation de l&#39;en-tête d&#39;une facture :

![](assets/s_ncs_pdf_simple.png)

Si vous souhaitez générer des tableaux dynamiques ou inclure des images à partir d&#39;URL, vous devez suivre une procédure particulière.

## Génération de tableaux dynamiques {#generating-dynamic-tables}

La procédure pour générer des tableaux dynamiques est la suivante :

* Créez un tableau de trois lignes, avec autant de colonnes que vous le souhaitez, et paramétrez sa mise en page (bordures, trame, etc.).
* Positionnez le curseur sur le tableau créé, et cliquez dans le menu **[!UICONTROL Tableau > Propriétés du tableau]**. Depuis l&#39;onglet **[!UICONTROL Tableau]**, saisissez un nom commençant par **NlJsTable**.
* Dans la première cellule de la première ligne, définissez une boucle (&quot;for&quot; par exemple) qui va permettre d&#39;itérer sur les valeurs que vous souhaitez afficher dans votre tableau.
* Insérez, dans chaque cellule de la deuxième ligne du tableau, les scripts retournant les valeurs à afficher.
* Fermez votre boucle dans la troisième et dernière ligne du tableau.

  Exemple de définition d&#39;un tableau dynamique :

  ![](assets/s_ncs_pdf_table.png)

## Insertion dʼimages externes {#inserting-external-images}

L&#39;insertion d&#39;images externes est utile lorsque, par exemple, vous souhaitez personnaliser un document avec une image dont l&#39;URL est renseignée dans un champ du destinataire.

Pour cela, il est nécessaire de paramétrer un bloc de personnalisation, puis d’inclure dans la pièce jointe un appel au bloc de personnalisation.

**Exemple : insertion dʼun logo personnalisé en fonction du pays du destinataire**

**Étape n°1 : Création de la pièce jointe :**

* Insérez l&#39;appel au bloc de personnalisation : **&lt;%@ include view=&quot;nomdubloc&quot; %>**
* Insérez votre contenu personnalisé ou non dans le corps du fichier

![](assets/s_ncs_open_office_blocdeperso.png)

**Etape n°2 : Création du bloc de personnalisation:**

* Allez dans le menu **[!UICONTROL Ressources > Gestion de campagne > Blocs de personnalisation]** de la console Adobe Campaign.
* Créez un nouveau bloc de personnalisation &quot;Mon Logo&quot; avec pour nom interne &quot;Mon_Logo&quot;.
* Cliquez sur le lien **[!UICONTROL Paramètres avancés…]** et cochez l’option **[!UICONTROL « Le bloc est inclus dans une pièce jointe »]**.Cela vous permet de copier la définition du bloc de personnalisation directement dans le contenu du fichier OpenOffice.

  ![](assets/s_ncs_pdf_bloc_option.png)

  Il est nécessaire de distinguer deux types de déclaration à l&#39;intérieur du bloc de personnalisation :

   * Le code Adobe Campaign des champs de personnalisation pour lequel les chevrons « ouvert » et « fermé » doivent être remplacés par des caractères échappés (respectivement `&lt;` et `&gt;`).
   * Le code XML OpenOffice qui sera intégralement recopié dans le document OpenOffice.

Dans l&#39;exemple, le bloc de personnalisation est de cette forme :

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

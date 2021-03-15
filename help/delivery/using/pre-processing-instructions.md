---
solution: Campaign Classic
product: campaign
title: Instructions de pré-traitement pour les URL trackées
description: Découvrez les instructions de pré-traitement à utiliser pour écrire le script de l’URL d’un email et qu'elle soit toujours trackée.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 8aab4bc23d688aa225cfc636936cf2835840e410
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 65%

---


# Instructions de pré-traitement {#pre-processing-instructions}

Vous pouvez utiliser une syntaxe spécifique dans le contenu de la diffusion pour ajouter des instructions et créer un script pour l’URL du courrier électronique suivi. Les instructions &lt;%@ ne sont pas JavaScript : cette syntaxe est spécifique à Adobe Campaign.

Elles ne s&#39;appliquent que dans le contexte du contenu de la diffusion. C’est la seule méthode pour écrire le script de l’URL d’un email et qu’elle soit encore trackée (en plus des paramètres d’URL). Elles peuvent être vues comme un copié/collé automatique appliqué pendant l’analyse de la diffusion avant la détection des liens à tracker.

Il existe trois types d’instructions :

* **[!DNL include]**: principalement pour adapter certains codes dans des options, des blocs de personnalisation, des fichiers externes ou des pages. [En savoir plus](#include)
* **[!DNL value]**: pour donner accès aux champs de la diffusion, aux variables de diffusion et aux objets personnalisés chargés dans la diffusion. [En savoir plus](#value)
* **[!DNL foreach]**: pour placer en boucle un tableau chargé en tant qu’objet personnalisé. [En savoir plus](#foreach)

Elles peuvent être testées directement à partir de l&#39;assistant de diffusion. Elles s’appliquent dans la prévisualisation du contenu et lorsque vous cliquez sur le bouton de tracking pour afficher la liste des URL.

## [!DNL include] {#include}

Les exemples suivants sont parmi les plus couramment utilisés :

* Inclusion du lien de la page miroir : 

   ```
   <%@ include view="MirrorPage" %>  
   ```

* URL de la page miroir:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* URL de désabonnement d’usine : 

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* Autres exemples :

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   Utilisez le bouton de personnalisation de l’assistant de diffusion pour obtenir la syntaxe correcte.

## [!DNL value] {#value}

Cette instruction donne accès aux paramètres de la diffusion qui sont constants pour tous les destinataires.

Syntaxe :

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

Où :

* **[!DNL object]**: nom de l’objet (exemple : diffusion, fournisseur, etc.).
L&#39;objet peut être :
   * **[!DNL delivery]**: pour la diffusion en cours (voir les détails et les restrictions dans la sous-section ci-dessous).
   * **[!DNL provider]**: pour le fournisseur/routage de diffusion actuel (nms:externalAccount).
   * Objet de script supplémentaire : si un objet est chargé dans le contexte via : **Propriétés** > **Personnalisation** > **Ajouter des objets dans le contexte d’exécution**.
   * Élément de la boucle foreach : voir la section [Foreach](#foreach) ci-dessous.
* **[!DNL xpath]**: xpath du champ.
* **[!DNL index]** (facultatif) : s&#39; **[!DNL object]** il s&#39;agit d&#39;un tableau (pour les objets de script supplémentaires), index d&#39;élément dans le tableau (Débuts à 0).

### [!DNL delivery] objet {#delivery-object}

Pour la personnalisation de l&#39;email, l’objet de diffusion est accessible de deux manières différentes :

* Utilisation de JavaScript :

   ```
   <%= delivery.myField %>`.
   ```

   Dans la diffusion d’objets JavaScript, les champs personnalisés ne sont pas pris en charge. Ils fonctionnent dans la prévisualisation, mais pas dans le MTA parce que celui-ci ne peut accéder qu&#39;au schéma de diffusion d’usine.

* Utilisation d’un prétraitement :

   ```
   <%@ value object="delivery"
   ```


**Attention**

Si vous utilisez les instructions suivantes pour les diffusions envoyées par midsourcing, le champ personnalisé **@myCustomField** doit être ajouté au schéma nms:diffusion sur les plateformes marketing et midsourcing :

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

Pour les variables/paramètres de diffusion, utilisez la syntaxe suivante (à l’aide de l’objet &quot;delivery&quot;) :

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] dans une section Javascript  {#value-in-javascript}

Pour autoriser l&#39;utilisation de la valeur &lt;%@ dans les sections JavaScript, deux objets spéciaux sont remplacés par &lt;% et %> :

```
<%@ value object='startScript' %>
<%@ value object='endScript' %>
```

Par exemple :

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Cette instruction permet une itération sur un tableau d&#39;objets chargés dans la diffusion pour tracker les liens individuels associés aux objets.

Syntaxe :

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

Où :

* **[!DNL object]**: nom de l’objet à partir duquel le début doit être effectué, généralement un objet de script supplémentaire, mais il peut s’agir d’une diffusion.
* **[!DNL xpath]** (facultatif) : xpath de la collection à mettre en boucle. La valeur par défaut est &quot;.&quot;, ce qui signifie que l&#39;objet est le tableau à exécuter en boucle.
* **[!DNL index]** (facultatif) : si xpath n&#39;est pas &quot;&quot;. et l&#39;objet est un tableau lui-même, index d&#39;élément de l&#39;objet (démarre à 0).
* **[!DNL item]** (facultatif) : nom d’un nouvel objet accessible avec  &lt;> Par défaut le nom du lien dans le schéma.

Exemple :

Dans les propriétés/personnalisation de la diffusion, chargez un tableau d’articles et une table de relations entre le destinataire et les articles.

L’affichage de liens vers ces articles peut se faire simplement avec un script JavaScript comme suit :

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Avec cette solution, les liens vers tous les articles sont trackés sans distinction. Vous pouvez déterminer qu’un destinataire a cliqué sur un lien d’article, mais vous ne pouvez pas savoir quel article.

La solution consiste à :

1. Précharger tous les articles possibles dans un tableau de script supplémentaire de la diffusion - articleList[] - ce qui signifie qu’il doit y avoir un nombre fini d’articles possibles.
1. Écrire une fonction JavaScript au début du contenu.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```
1. Afficher l’article en appelant la fonction.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```


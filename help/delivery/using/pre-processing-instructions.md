---
solution: Campaign Classic
product: campaign
title: Instructions de prétraitement pour les URL suivies
description: En savoir plus sur les instructions de prétraitement à utiliser pour script l’URL d’un courrier électronique et pour le suivi.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Instructions de prétraitement {#pre-processing-instructions}

Les instructions &lt;%@ ne sont pas JavaScript, cette syntaxe est propre à Adobe Campaign.

Elles ne s&#39;appliquent que dans le contexte du contenu de la diffusion. Il s’agit du seul moyen de script de l’URL d’un courrier électronique et de le suivre (en plus des paramètres d’URL). Ils peuvent être vus comme une copie/collage automatique appliquée pendant l’analyse de diffusion avant de détecter les liens à suivre.

Il existe trois types d’instructions :

* &quot;**include**&quot; : principalement pour faciliter certains codes dans des options, des blocs de personnalisation, des fichiers externes ou des pages
* &quot;**value**&quot; : pour donner accès aux champs de la diffusion, aux variables de diffusion et aux objets personnalisés chargés dans la diffusion
* &quot;**foreach**&quot; : pour placer en boucle un tableau chargé en tant qu’objet personnalisé.

Ils peuvent être testés directement à partir de l&#39;assistant de diffusion. Elles s’appliquent dans la prévisualisation de contenu et lorsque vous cliquez sur le bouton de suivi pour afficher la liste des URL.

## &lt;>{#<%@-include}

Les exemples suivants sont parmi les plus couramment utilisés :

* Inclusion du lien de la page miroir : `<%@ include view="MirrorPage" %>`
* URL de la page miroir : &quot;Vue en tant que `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* URL de désinscription prête à l&#39;emploi : `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Autres exemples :
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Utilisez le bouton de personnalisation de l’assistant de diffusion pour obtenir la syntaxe correcte.

## &lt;%@ valeur {#<%@-value}

Cette instruction donne accès aux paramètres de la diffusion qui sont constants pour tous les destinataires.

Syntaxe:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Où :

* &quot;object&quot; : nom de l’objet (exemple : diffusion, fournisseur, etc.).
* &quot;xpath&quot; : xpath du champ.
* &quot;index&quot; (facultatif) : si &quot;object&quot; est un tableau (pour les objets de script supplémentaires), index d&#39;élément dans le tableau (Débuts à 0).

L&#39;objet peut être :

* *&quot;diffusion&quot; : pour la diffusion en cours (voir les détails et les restrictions dans la sous-section ci-dessous).
* &quot;provider&quot; : pour le fournisseur/routage de diffusion actuel (nms:externalAccount).
* Un objet de script supplémentaire : si un objet est chargé dans le contexte via : **Propriétés** > **Personnalisation** > **Ajouter des objets dans le contexte d’exécution**.
* Élément de la boucle foreach : voir la section [Foreach](#<%@-foreach) ci-dessous.

### Objet &quot;diffusion&quot; {#delivery-object}

Pour la personnalisation du courrier électronique, l’objet de diffusion est accessible de deux manières :

* Dans JavaScript. Par exemple: `<%= delivery.myField %>`.

   Dans la diffusion d’objets JavaScript, les champs personnalisés ne sont pas pris en charge. Ils travaillent dans la prévisualisation, mais pas dans la MTA parce que la MTA ne peut accéder qu&#39;au schéma de diffusion prêt à l&#39;emploi.

* Par le biais du prétraitement `<%@ value object="delivery"`.

Pour l&#39;instruction `<%@ value object="delivery" xpath="@myCustomField" %>`, il existe une autre limite pour les diffusions envoyées par midsourcing. Le champ personnalisé @myCustomField doit être ajouté au schéma nms:diffusion sur les plateformes marketing et de midsourcing.

>[!NOTE]
>
>Pour les paramètres/variables de diffusion, utilisez la syntaxe suivante (à l’aide de l’objet diffusion) :
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#<%@-value-in-javascript}

Pour autoriser l&#39;utilisation de la valeur &lt;%@ dans les sections de script, deux objets spéciaux sont remplacés par &lt;% et %> :

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

par exemple :

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#<%@-foreach}

Cette instruction permet l&#39;itération sur un tableau d&#39;objets chargés dans la diffusion pour suivre les liens individuels liés aux objets.

Syntaxe:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Où :

* &quot;object&quot; : nom de l’objet à partir duquel le début doit être effectué, généralement un objet de script supplémentaire, mais il peut s’agir d’une diffusion.
* &quot;xpath&quot; (facultatif) : xpath de la collection à mettre en boucle. La valeur par défaut est &quot;.&quot;, ce qui signifie que l&#39;objet est le tableau sur lequel la boucle doit être activée.
* &quot;index&quot; (facultatif) : si xpath n&#39;est pas &quot;&quot;. et object est un tableau lui-même, index d&#39;élément de l&#39;objet (débuts à 0).
* &quot;item&quot; (facultatif) : nom d&#39;un nouvel objet accessible avec la valeur &lt;%@ dans la boucle foreach. Valeur par défaut du nom du lien dans le schéma.

Exemple :

Dans les propriétés/personnalisation de la diffusion, chargez un tableau d’articles et un tableau de relations entre le destinataire et les articles.

L’affichage de liens vers ces articles peut se faire simplement avec un script JavaScript comme suit :

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Avec cette solution, les liens vers tous les articles sont suivis sans distinction. Vous pouvez savoir qu’un destinataire a cliqué sur un lien d’article, mais vous ne pouvez pas savoir quel article.

La solution consiste à :

1. Préchargez tous les articles possibles dans un tableau de script supplémentaire de la diffusion - articleList[] - ce qui signifie qu’il doit y avoir un nombre fini d’articles possibles.
1. Ecrivez une fonction JavaScript au début du contenu.

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
1. Affichez l’article en appelant la fonction.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```


---
solution: Campaign Classic
product: campaign
title: Instructions relatives aux scripts et à l’encodage
description: En savoir plus sur les directives à suivre lors du développement en Adobe Campaign (workflows, JavaScript, JSSP, etc.).
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 64%

---


# Instructions relatives aux scripts et à l’encodage {#scripting-coding-guidelines}

## Scripts

Pour plus d&#39;informations, reportez-vous à la [documentation JSAPI Campaign](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Si vous écrivez un script à l&#39;aide d&#39;un workflow, d&#39;applications web ou de jssp, suivez ces bonnes pratiques :

* Evitez autant que possible d&#39;utiliser des instructions SQL.

* Utilisez des fonctions (instruction prepare) paramétrables au lieu de la concaténation de chaîne.

   Mauvaise pratique :

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
   ```

   Bonne pratique :

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
   ```

   >[!IMPORTANT]
   >
   >sqlSelect ne prend pas en charge cette fonctionnalité, vous devez donc utiliser la fonction de requête de la classe DBEngine :

   ```
   var cnx = application.getConnection()
   var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
   for each(var row in stmt) logInfo(row[0] + " : " + row[1])
   cnx.dispose()
   ```

Pour éviter les injections SQL, les fonctions SQL doivent être ajoutées à la liste autorisée à utiliser dans Adobe Campaign. Une fois ajoutées à la liste autorisée, vos opérateurs peuvent les voir dans l’éditeur d’expression. Consultez à ce sujet [cette page](../../configuration/using/adding-additional-sql-functions.md).

>[!IMPORTANT]
>
>Si vous utilisez une version antérieure à 8140, l&#39;option **XtkPassUnknownSQLFunctionsToRDBMS** peut être définie sur &quot;1&quot;. Si vous souhaitez protéger votre base de données, supprimez cette option (ou définissez-la sur ’0’).

Si vous utilisez des saisies
                    utilisateur pour créer des filtres dans des requêtes ou des instructions SQL, vous devez toujours les placer dans une séquence d&#39;échappement (reportez-vous à la [documentation JSAPI Campaign](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) - Protection des données : fonctions d&#39;échappement). Ces fonctions sont les suivantes :

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## Sécuriser votre nouveau modèle de données

### Base de dossiers

Reportez-vous aux pages suivantes :

* [Propriétés d&#39;accès des dossiers](../../platform/using/access-management.md)
* [Dossier lié](../../configuration/using/configuration.md#linked-folder)

### Droits nommés

En plus du modèle de sécurité basé sur les dossiers, vous pouvez utiliser des droits nommés pour limiter les actions des opérateurs :

* Vous pouvez ajouter des filtres système (sysFilter) pour empêcher la lecture/écriture de vos données (voir [cette page](../../configuration/using/filtering-schemas.md)).

   ```
   <sysFilter name="writeAccess">    
       <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
   </sysFilter>
   ```

* Vous pouvez également protéger certaines actions (méthode SOAP) définies dans des schémas. Il vous suffit de définir l&#39;attribut d&#39;accès avec la valeur correspondante nommée right comme valeur.

   ```
   <method name="grantVIPAccess" access="myNewRole">
       <parameters>
   ...
       </parameters>
   </method>
   ```

   Consultez [cette page](../../configuration/using/implementing-soap-methods.md) pour plus d&#39;informations.

>[!IMPORTANT]
>
>Vous pouvez utiliser des droits nommés dans le nœud command d’un navtree. Il offre une meilleure expérience à l’utilisateur, mais ne fournit aucune protection (utilisez uniquement le côté client pour les masquer/les désactiver). Vous devez utiliser l’attribut access.

### Table d&#39;Overflow

Si vous devez protéger des données confidentielles (partie d’un schéma) en fonction du niveau d’accès des opérateurs, ne les masquez pas dans la définition du formulaire (conditions enabledIf/visibleIf).

L’entité entière est chargée par l’écran. Vous pouvez également les afficher dans la définition de colonne. Pour ce faire, vous devez créer une table d’Overflow. Reportez-vous à [cette page](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## Ajouter des captchas dans les applications web

Il est recommandé d&#39;ajouter un captcha dans les landing pages/pages d&#39;inscription publiques. Il est cependant relativement difficile de le faire dans les pages du DCE (Digital Content Editor). Nous allons vous expliquer dans cette section comment ajouter un captcha v5 ou un reCAPTCHA Google.

La méthode générale pour ajouter un captcha dans le DCE consiste à créer un bloc de personnalisation pour l&#39;inclure facilement dans le contenu de la page. Vous devrez ajouter une activité **Script** et une activité **Test**.

### Bloc de personnalisation

1. Accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Blocs de personnalisation]** et créez un bloc de personnalisation.

1. Utilisez le type de contenu **[!UICONTROL Application web]** et cochez **[!UICONTROL Visible dans les menus de personnalisation]**.

   Pour plus d’informations, consultez [cette page](../../delivery/using/personalization-blocks.md).

   Voici un exemple de **captcha Campaign** :

   ```javascript
   <%
   var captchaID = CaptchaIDGen();
   %>
   <img src="/nms/jsp/captcha.jsp?captchaID=<%=captchaID%>&width=200&height=50&minWordSize=8&maxWordSize=8"/>
   <input id="captchaValue" name="captchaValue" <%= String(ctx.vars.captchaValid) === "false" ? class="ui-state-error" : "" %>>
   <input type="hidden" name="captchaID" value="<%=captchaID%>"/>
   <%
   if( serverForm.isInputErroneous("captchaValue") ) {
   %>
   <script type="text/javascript"> 
   $("#captchaValue").addClass("ui-state-error")
   </script>
   <%
   }
   %>
   ```

   * Les lignes 1 à 6 génèrent toutes les entrées requises.
   * La ligne 7 et les lignes suivantes jusqu&#39;à la dernière gèrent les erreurs.
   * La ligne 4 permet de changer la taille du cadre gris du captcha (width/height) et la longueur du mot
                    généré (minWordSize/maxWordSize).
   * Avant d&#39;utiliser Google reCAPTCHA, vous devez vous enregistrer sur Google et créer un nouveau site reCAPTCHA.

      `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`
   Vous devriez être en mesure de désactiver le bouton de validation, mais comme il n’existe pas de bouton/lien standard, il est préférable de le faire dans le code HTML. Pour savoir comment le faire, consultez [cette page](https://developers.google.com/recaptcha/).

### Mettre à jour votre application web

1. Accédez aux propriétés de votre application Web pour ajouter une variable booléenne nommée **captchaValid**.

   ![](assets/scripting-captcha.png)

1. Entre la dernière page et l&#39;activité **[!UICONTROL Enregistrement]**, ajoutez **[!UICONTROL Script]** et **[!UICONTROL Test]**.

   Branchez la branche **[!UICONTROL True]** à l&#39;**[!UICONTROL Enregistrement]** et l&#39;autre à la page qui aura la capture.

   ![](assets/scripting-captcha2.png)

1. Modifiez la condition de la branche True avec `"[vars/captchaValid]"` égale True.

   ![](assets/scripting-captcha3.png)

1. Modifiez l&#39;activité **[!UICONTROL Script]**. Le contenu dépendra du moteur de capture choisi.

1. Enfin, vous pouvez ajouter votre bloc personnalisé dans la page : voir [cette page](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>Pour l’intégration de reCAPTCHA, vous devez ajouter du code JavaScript côté client dans le code HTML (dans `<head>...</head>`) :
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Campaign captcha

```javascript
var captchaID = request.getParameter("captchaID");
var captchaValue = request.getParameter("captchaValue");
  
if( !CaptchaValidate(captchaID, captchaValue) ) {
  serverForm.logInputError("captchaValue",
                           "The characters you typed for the captcha must match the image ones.",
                           "captchaValue")
  ctx.vars.captchaValid = false
}
else
  ctx.vars.captchaValid = true
```

Ligne 6 : vous pouvez mettre n&#39;importe quel type de message d&#39;erreur.

### Google Recaptcha

Veuillez consulter la [documentation officielle](https://developers.google.com/recaptcha/docs/verify).

```javascript
ctx.vars.captchaValid = false
var gReCaptchaResponse = request.getParameter("g-recaptcha-response");
  
// Call reCaptcha API to validate it
var req = new HttpClientRequest("https://www.google.com/recaptcha/api/siteverify")
req.method = "POST"
req.header["Content-Type"] = "application/x-www-form-urlencoded"
req.body = "secret=YOUR_SECRET_HERE&response=" + encodeURIComponent(gReCaptchaResponse)
req.execute()
var response = req.response
if( response.code == 200 ) {
  captchaRes = JSON.parse(response.body.toString(response.codePage));
  ctx.vars.captchaValid = captchaRes.success
}
  
if( ctx.vars.captchaValid == false ) {
  serverForm.logInputError("reCaptcha",
                           "Please validate the captcha",
                           "reCaptcha")
  logInfo("reCaptcha not validated")
}
```

Pour utiliser JSON.parse, vous devez inclure &quot;shared/json2.js&quot; dans votre webApp :

![](assets/scripting-captcha6.png)

Depuis le build 8797, pour utiliser l’URL de l’API de vérification, vous devez l’ajouter à la liste autorisée dans le fichier serverConf en l’ajoutant dans le nœud urlPermission :

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`

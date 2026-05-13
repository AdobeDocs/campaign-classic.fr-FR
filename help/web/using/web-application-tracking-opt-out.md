---
product: campaign
title: Désinscription (opt-out) du tracking des applications web
description: Désinscription (opt-out) du tracking des applications web
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
TQID: https://experienceleague.adobe.com/-5Bp8qdxH8DTEJ0-NASuorQrjwDMUmvuhBNbW1alqyc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a7760dfc-5c44-4d77-bb68-c50b1e265c93id: b12f6872-9271-4369-85e5-86969a0b99a2
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 719
ht-degree: 59%

---

# Désinscription (opt-out) du tracking des applications web{#web-application-tracking-opt-out}



Adobe Campaign vous permet d’arrêter le suivi des comportements web des utilisateurs finaux qui se sont désinscrits du suivi comportemental via des cookies ou des balises web. Cette fonctionnalité offre la possibilité d’afficher une bannière pour présenter cette option à l’utilisateur final. Vous pouvez ajouter ces bannières dans des applications web ou des pages de destination.

Si un utilisateur final se désinscrit (opt-out) du tracking comportemental via des cookies ou des balises web, ces informations sont transmises au serveur de tracking Adobe Campaign avec les API JavaScript. Veuillez noter que certaines juridictions peuvent exiger que le Client présente aux utilisateurs finaux une option d&#39;opt-in avant qu&#39;une option d&#39;opt-out ne puisse être proposée (ou ont d&#39;autres exigences légales), et il est de la responsabilité du Client de se conformer aux lois applicables.

>[!NOTE]
>
>Lorsque vous créez des scripts, suivez toujours les consignes décrites dans la [Liste de contrôle relative à la sécurité et à la confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#dev).

## Paramétrer la bannière {#configuring-the-banner-}

Pour s&#39;afficher dans des applications Web ou des landing pages, la bannière doit être configurée.

Adobe Campaign s’accompagne d’un exemple de bannière que vous devez adapter à vos besoins. Cette version de bannière s’affiche sous la forme d’un bloc de personnalisation situé dans le dossier du modèle de contenu. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=fr){target="_blank"}.

>[!IMPORTANT]
>
>Pour créer votre propre bannière, vous devez personnaliser la bannière d&#39;usine.

Pour activer la bannière, vous devez configurer les propriétés de l&#39;application web. Pour plus d&#39;informations, consultez la section [Concevoir une application web](designing-a-web-application.md).

Si le tracking web est activé, vous pouvez sélectionner l&#39;une des options suivantes :

* Aucune bannière.
* Configurer la bannière manuellement dans chaque page : cochez cette option et sélectionnez la bannière dans chaque page dans les propriétés de page.

  ![](assets/pageproperties.png)

* Ajouter automatiquement la bannière à toutes les pages : sélectionnez la bannière directement dans les propriétés de l&#39;application Web.

  ![](assets/optoutconfig.png)

>[!NOTE]
>
>Un mode de compatibilité est disponible pour la version 5 de l&#39;application web avec le même comportement.

La bannière par défaut possède la structure suivante :

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

Vous devez remplacer le **Veuillez insérer votre message ici** par le bloc contenant vos informations de tracking. Ce remplacement doit être exécuté dans votre nouveau bloc de personnalisation associé à la bannière d’exclusion.

La bannière est fournie avec un CSS spécifique. Cependant, vous pouvez remplacer les styles lors de la création et de la configuration d’une page web. Pour plus d’informations, consultez [cette page](content-editor-interface.md).

## Définir le cookie de désinscription (opt-out) à l&#39;aide des API {#setting-the-opt-out-cookie-using-api}

Adobe Campaign est fourni avec des API qui permettent de gérer la valeur du cookie et de récupérer les préférences de l&#39;utilisateur.

Le nom du cookie est **acoptout**. Les valeurs courantes sont les suivantes :

* 0 : l&#39;utilisateur a autorisé le tracking web (valeur par défaut).
* 1 : l&#39;utilisateur a interdit le tracking web.
* null : l&#39;utilisateur n&#39;a pas effectué de choix, mais le tracking web est autorisé car il s&#39;agit de la valeur par défaut.

Les API côté client disponibles pour personnaliser la bannière sont les suivantes :

* **NL.ClientWebTracking.allow()** : définit la valeur du cookie d’exclusion pour autoriser le suivi web. Le tracking Web est autorisé par défaut.
* **NL.ClientWebTracking.forbid()** : définit la valeur du cookie d’exclusion sur interdire le suivi web. Le tracking web nécessite l&#39;interdiction d&#39;une entrée utilisateur.
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)** : ferme la bannière de cookie d’exclusion après que l’utilisateur a cliqué sur le bouton Accepter ou Refuser. (pendant la phase de propagation de l’événement de clic)

  bannerDomElt {DOMElement} : élément DOM racine de la bannière du cookie qui doit être supprimé.

* **NL.ClientWebTracking.hasUserPrefs()** : renvoie la valeur true si l’utilisateur a choisi les préférences du tracking web.
* **NL.ClientWebTracking.getUserPrefs()**: renvoie la valeur du cookie d&#39;opt-out qui définit les préférences de l&#39;utilisateur.

Si vous devez écrire du code JSSP, les API côté serveur suivantes sont disponibles :

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)** : génère les balises pour que bannière d&#39;opt-out soit insérée dans la page JSSP.

  **escapeJs{Boolean}** : a la valeur true lorsque les balises générées doivent être placées dans une séquence d’échappement afin d’être utilisées dans le script JavaScript.

  Cette chaîne renvoie le code HTML des balises de la bannière d’opt-out qui doivent être imprimées sur la page.

* **NL.ServerWebTracking._displayOptOutBanner()**

  Renvoie la valeur &quot;true&quot; si la bannière d‘opt-out doit s‘afficher après que l‘administrateur l‘ait sélectionnée.

  Ce code est appelé lorsque l&#39;administrateur a déjà choisi d&#39;utiliser la bannière d&#39;opt-out pour le tracking web.

  La bannière doit s&#39;afficher si l&#39;utilisateur n&#39;a pas encore décidé s&#39;il souhaitait être tracké ou non.

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs) :**

  Rend le balisage de la bannière de désinscription en l’insérant dans la page JSSP. Il est appelé tel quel dans Jssp entre &lt;% %>

  **escapeJs{Boolean}** : a la valeur true lorsque les balises générées doivent être placées dans une séquence d’échappement afin d’être utilisées dans le script JavaScript.

Exemple JSSP :

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```

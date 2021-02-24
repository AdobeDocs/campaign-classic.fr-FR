---
solution: Campaign Classic
product: campaign
title: Détection des URL de suivi
description: En savoir plus sur le modèle recommandé pour effectuer le suivi des URL.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 2%

---


# Détection des URL de suivi

## Exemple de non-détection

`<%= getURL("http://mynewsletter.com") %>` fonctionne et envoie le contenu réel de la page web par courrier électronique aux destinataires. Mais aucun des liens n&#39;est suivi. La raison en est que la MTA s’exécute `"<%=getURL(..."` pour chaque courrier électronique avant de l’envoyer. Il peut être différent pour chaque destinataire, de sorte que Adobe Campaign ne peut pas connaître les URL de suivi et leur attribuer un ID de balise.

Lorsque la page à télécharger est identique pour tous les destinataires, la meilleure pratique consiste à effectuer les opérations suivantes :

`<%@ include url="http://mynewsletter.com" %>`

Dans ce cas, la page est téléchargée pendant l’analyse, avant la détection du suivi. Il permet à Adobe Campaign de découvrir les liens, d’attribuer un ID de balise et de les suivre.

## Modèle recommandé

Après avoir traité les instructions `<%@`, l’URL à suivre possède la syntaxe suivante : `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Tous les autres modèles ne sont pas pris en charge par l&#39;Adobe et doivent être évités afin d&#39;éviter les éventuelles lacunes en matière de sécurité.

## Avertissements sur le modèle http://&lt;%=myURL%>

La syntaxe `<a href="http://<%=myURL%>">` n&#39;est pas sécurisée et n&#39;est pas recommandée car :

* Tidy peut incorrectement corriger certains liens, ce qui peut se produire de manière aléatoire. Le symptôme typique est un morceau de code HTML visible dans les BAT de messagerie mais pas dans la prévisualisation.
* L’échappement de l’URL est problématique, certains caractères de l’URL peuvent poser des problèmes.
* Un paramètre nommé ID ne peut pas entrer en conflit avec un paramètre dans l’URL de redirection.
* L’intérêt du suivi est alors limité aux statistiques de la diffusion, car Adobe Campaign suit indifféremment toutes les valeurs possibles de &quot;myURL&quot;.

Consultez [cette page](https://helpx.adobe.com/fr/campaign/kb/acc-security.html#privacy) pour en savoir plus.


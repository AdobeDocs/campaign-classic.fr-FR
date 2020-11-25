---
solution: Campaign Classic
product: campaign
title: Connexion impossible
description: Connexion impossible
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 2cc4ab52f3cbdd00831d0b5104690b7adf6091ce
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 56%

---


# Connexion impossible{#failure-to-connect}

Les raisons d&#39;un problème de connexion peuvent être multiples et dépendent de divers contextes.

Vous pouvez tester les tests suivants et si l&#39;échec de connexion persiste, contactez l&#39;assistance **** Adobe Campaign.



<table> 
 <thead> 
  <tr> 
   <th>Vérifications<br /> </th> 
   <th>Résolution<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td>Avez-vous accès à internet depuis votre ordinateur ?</td> 
   <td>Vérifiez que vous pouvez vous connecter à des sites sur Internet (par exemple). Si vous ne pouvez pas vous connecter, il s'agit d'un problème sur votre machine : contactez votre administrateur système.</td>
  </tr>
  <tr> 
   <td>Pouvez-vous vous connecter sur le serveur hébergeant Adobe Campaign par un autre service ?</td> 
   <td>Connectez-vous en SSH ou tout autre moyen sur le serveur. En cas d'impossibilité, il y a un problème réseau chez votre hébergeur, contactez leur administrateur réseau.</td>
  </tr>
  <tr> 
   <td>Le serveur Web répond-t-il ?</td> 
   <td>Connect to the Adobe Campaign server access URL using a Web browser: <b>http(s):// &lt;urlserver&gt;</b>. S’il ne répond pas, le serveur web est arrêté sur l’ordinateur. Contactez l’administrateur système de votre hébergeur pour redémarrer le service.</td>
  </tr>
  <tr> 
   <td>L'intégration Adobe Campaign est-elle bien effectuée ?</td> 
   <td>Log on to the: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Le serveur doit renvoyer le type de message suivant :

    &lt;pre>
    &lt;redir status=&#39;OK&#39; date=&#39;AAAA/MM/JJ HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &lt;/pre>
Si vous n’obtenez pas ce résultat, vérifiez dans la configuration de votre serveur Web que l’intégration est bien prise en compte.</td>
</tr>
  <tr> 
   <td>Le module Web Adobe Campaign est-il bien lancé ?</td> 
   <td>Connectez-vous à l’URL suivante : <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>* Si vous obtenez une erreur Java Tomcat :

L&#39;intégration JAVA est-elle correctement effectuée ? Adobe Campaign requiert un JDK SUN pour fonctionner.

It is integrated in the file [path of application]/nl6/customer.sh

* Si vous obtenez une page blanche :

Le module Web d&#39;Adobe Campaign est-il bien démarré ? Vous devez obtenir :

<pre>
nlserver pdumpHH:MM:SS &gt; Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY[...]web@default (27515) - 55.2 Mb[...]
</pre>

* Sinon, relancez-le en utilisant la commande suivante :

<pre>        
nlserver start web
</pre>
</td>
</tr>
  <tr>
  	<td>De manière générale, vérifiez la configuration des zones de sécurité.</td>
  	<td>Pour plus d'informations sur la configuration des zones de sécurité, reportez-vous à [cette section](../../installation/using/configuring-campaign-server.md#definition-security-zones)</td>
  </tr>
 </tbody> 
</table>

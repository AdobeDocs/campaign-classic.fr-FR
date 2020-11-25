---
solution: Campaign Classic
product: campaign
title: Connexion impossible
description: Connexion impossible
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 68fee697b65b2ba69f456803e0a7cebca9be3760
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 40%

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
   <td>Log on to the: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Le serveur doit renvoyer le type de message suivant : &lt;redirecteur status='OK' date='AAAA/MM/JJ HH:MM:SS' build='XXXX' host='&lt;nom d'hôte&gt;' localHost='&lt;serveur&gt;'/&gt; Si vous n'obtenez pas ce résultat, vérifiez la configuration de votre serveur Web qui prend en compte l'intégration.</td>
  </tr>
  <tr> 
   <td>Connect to the following URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
   <td>Si vous obtenez une erreur Java Tomcat, vérifiez si l’intégration JAVA est correctement effectuée. Son intégration se fait dans le fichier [chemin de l'application]/nl6/customer.sh</td>
  </tr>
  <tr> 
   <td>Connect to the following URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
   <td>Si vous obtenez une page vierge, vérifiez si le module Web Adobe Campaign est démarré. La commande nlserver pdump doit renvoyer Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) de DD/MM/YYYY. Sinon, redémarrez le module avec la commande nlserver début web</td>
  </tr>
   <tr>
  	<td>De manière générale, vérifiez la configuration des zones de sécurité.</td>
  	<td>Pour plus d'informations sur la configuration des zones de sécurité, reportez-vous à [cette section](../../installation/using/configuring-campaign-server.md#definition-security-zones)</td>
  </tr>
 </tbody> 
</table>

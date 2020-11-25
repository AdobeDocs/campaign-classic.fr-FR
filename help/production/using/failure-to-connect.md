---
solution: Campaign Classic
product: campaign
title: Connexion impossible
description: Connexion impossible
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: cb6a2247e3b7617511aecf3d2d19985af0216494
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 45%

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
   <td>Connectez-vous à l’URL d’accès au serveur Adobe Campaign à l’aide d’un navigateur Web : **`http(s):// <urlserver>`**. S’il ne répond pas, le serveur web est arrêté sur l’ordinateur. Contactez l’administrateur système de votre hébergeur pour redémarrer le service.</td>
  </tr>
  <tr> 
   <td>L'intégration Adobe Campaign est-elle bien effectuée ?</td> 
   <td>Connectez-vous à : **`http(s)://<urlserver>URL /r/test`**. Le serveur doit renvoyer le type de message suivant :

    &quot;
    &lt;redirecteur status=&#39;OK&#39; date=&#39;AAAA/MM/JJ HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;nom d&#39;hôte>&#39; localHost=&#39;&lt;serveur>&#39;/>
    &quot;
    
    Si vous n&#39;obtenez pas ce résultat, vérifiez dans votre configuration de serveur Web que l&#39;intégration est prise en compte.&lt;/td>
</tr>
  <tr> 
   <td>Le module Web Adobe Campaign est-il bien lancé ?</td> 
   <td>
   Connectez-vous à l’URL suivante : **`http(s)://<URLSERVER>/nl/jsp/logon.jsp`** * Si vous obtenez une erreur Java Tomcat :

    L&#39;intégration JAVA est-elle correctement effectuée ? Adobe Campaign requiert un JDK SUN pour fonctionner.
    
    Il est intégré dans le fichier **`[chemin de l&#39;application]`/nl6/customer.sh**
    
    * Si vous obtenez une page vierge :
    
    Le module Web Adobe Campaign a-t-il démarré ? Vous devez vous procurer :
    
    &quot;
    nlserver
    pdumpHH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) de DD/MM/YYYY
    [..]
    web@default (27515) - 55.2 Mb
    [...]
    &quot;* Si vous ne redémarrez pas, utilisez la commande suivante :&quot;  Web de début de serveur nlserver&quot;&lt;/td>
    
    
    
    
    
    
</tr>
  <tr>
  	<td>De manière générale, vérifiez la configuration des zones de sécurité.</td>
  	<td>Pour plus d'informations sur la configuration des zones de sécurité, reportez-vous à [cette section](../../installation/using/configuring-campaign-server.md#definition-security-zones)</td>
  </tr>
 </tbody> 
</table>

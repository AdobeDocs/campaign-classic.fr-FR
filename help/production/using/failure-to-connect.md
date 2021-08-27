---
product: campaign
title: Connexion impossible
description: Connexion impossible
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 88%

---

# Connexion impossible{#failure-to-connect}

![](../../assets/v7-only.svg)

Les causes des problèmes de connexion peuvent être multiples et dépendent des différents contextes.

Vous pouvez effectuer les tests suivants. Si la connexion échoue toujours, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



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
<td>Connectez-vous à l’URL d’accès au serveur Adobe Campaign à l’aide d’un navigateur web : <b>http(s):// &lt;urlserver&gt;</b>. S’il ne répond pas, le serveur web est arrêté sur l’ordinateur. Contactez l’administrateur système de votre hébergeur pour redémarrer le service.</td>
</tr>
<tr> 
<td>L'intégration Adobe Campaign est-elle bien effectuée ?</td> 
<td>Connectez-vous à l’URL <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Le serveur doit renvoyer le type de message suivant : &lt;redir status='OK' date='YYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;
Si vous n’obtenez pas ce résultat, vérifiez dans la configuration de votre serveur Web que l’intégration est prise en compte.</td>
</tr>
<tr> 
<td>Connectez-vous à l’URL suivante : <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Si vous obtenez une erreur Java Tomcat, vérifiez si l’intégration JAVA est correctement effectuée. Son intégration se fait dans le fichier [chemin de l'application]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Connectez-vous à l'URL suivante : <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Si vous obtenez une page vierge, vérifiez si le module Web Adobe Campaign est démarré. La commande nlserver pdump doit renvoyer Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY. Sinon, redémarrez le module avec la commande nlserver start web</td>
</tr>
<tr>
<td>De manière générale, vérifiez la configuration des zones de sécurité.</td>
<td>Pour plus d’informations sur le paramétrage des zones de sécurité, consultez <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=fr#configuring-campaign-server"/>cette section.</a></td>
</tr>
<tr>
<td>La commande nlserver pdump renvoie <b>Aucune tâche</b></td>
<td>Vous devez redémarrer l’ensemble de l’application Adobe Campaign. Pour ce faire, utilisez la commande suivante : <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>

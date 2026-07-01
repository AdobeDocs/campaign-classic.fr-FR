---
product: campaign
title: Connexion impossible
description: Connexion impossible
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
TQID: https://experienceleague.adobe.com/zQXUUtLQveDPTu8blS48gCzTl8lv09vlJXAtjAjgtW4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 417
ht-degree: 100%

---

# Connexion impossible{#failure-to-connect}



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
<td>Avez-vous accès à internet depuis votre ordinateur ?</td> 
<td>Vérifiez que vous pouvez vous connecter à des sites web sur Internet (par exemple).Si vous ne pouvez pas vous connecter, le problème se produit sur votre ordinateur.Contactez votre administrateur ou administratrice système.</td>
</tr>
<tr> 
<td>Pouvez-vous vous connecter sur le serveur hébergeant Adobe Campaign par un autre service ?</td> 
<td>Connectez-vous au serveur via SSH ou tout autre moyen.Si cela n’est pas possible, votre société hôte rencontre un problème.Contactez son administrateur ou administratrice système.</td>
</tr>
<tr> 
<td>Le serveur Web répond-t-il ?</td> 
<td>Connectez-vous à l’URL d’accès au serveur Adobe Campaign à l’aide d’un navigateur web : <b>http(s):// &lt;urlserver&gt;</b>. S’il ne répond pas, le serveur web est arrêté sur l’ordinateur. Contactez l’équipe d’administration système de votre hébergeur pour redémarrer le service.</td>
</tr>
<tr> 
<td>L'intégration Adobe Campaign est-elle bien effectuée ?</td> 
<td>Connectez-vous à l’URL <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Le serveur doit renvoyer le type de message suivant : &lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;Si vous n’obtenez pas ce résultat, vérifiez dans la configuration de votre serveur web que l’intégration est prise en compte.</td>
</tr>
<tr> 
<td>Connectez-vous à l’URL suivante : <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Si vous obtenez une erreur Java Tomcat, vérifiez si l’intégration JAVA est correctement effectuée. Son intégration se fait dans le fichier [chemin de l'application]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Connectez-vous à l'URL suivante : <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Si vous obtenez une page vierge, vérifiez si le module Web Adobe Campaign est démarré. La commande nlserver pdump doit renvoyer Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY. Sinon, redémarrez le module avec la commande nlserver start web</td>
</tr>
<tr>
<td>De manière générale, vérifiez la configuration des zones de sécurité.</td>
<td>Pour plus d’informations sur le paramétrage des zones de sécurité, consultez <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=fr#configuring-campaign-server"/>cette section.</a></td>
</tr>
<tr>
<td>La commande nlserver pdump renvoie <b>Aucune tâche</b></td>
<td>Vous devez redémarrer l’ensemble de l’application Adobe Campaign. Pour ce faire, utilisez la commande suivante : <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>

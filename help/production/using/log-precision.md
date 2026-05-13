---
product: campaign
title: Précision des logs
description: Précision des logs
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
TQID: https://experienceleague.adobe.com/-AC3ZgKzganqlheg99fMRyJiYNQkHSnIogq5F-Z9xMQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 346
ht-degree: 79%

---

# Précision des logs{#log-precision}



Pour augmenter la précision des logs, vous pouvez appliquer cette procédure à tous les modules Adobe Campaign.

Elle consiste à relancer les processus avec un niveau de logs supérieur.

>[!IMPORTANT]
>
>Cette procédure annule les services en cours sur ce module.

Adobe Campaign peut fonctionner sous deux niveaux de logs :

1. Le mode **Verbose** est le premier niveau après le niveau standard. La commande suivante l&#39;active :

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Vérifiez que lerreur sest bien produite, puis redémarrez le processus normalement :

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Le mode **TraceFilter**, qui permet d&#39;enregistrer le plus grand nombre de logs. Il est activé par la commande suivante :

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Si vous utilisez **tracefilter:&#42;**, tous les types de logs sont activés : ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail.\
   >Les types de logs les plus utiles sont les suivants : **wdbc** (affiche toutes les requêtes SQL), **soap** (affiche tous les appels SOAP), **ldap** (affiche toutes les requêtes LDAP lors de l&#39;authentification), **xtkquery** (affiche la liste de toutes les querydef).\
   >Vous pouvez les utiliser individuellement (**tracefilter:soap,wdbc** par exemple). Vous pouvez aussi tous les activer et choisir d’en exclure certains : **-tracefilter:&#42;,!soap**

   Vérifiez que lerreur sest bien produite, puis redémarrez le processus normalement :

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Les logs de ces commandes sont stockés dans le fichier de log du module.

Voici un exemple spécifique au module Web. Les autres modules fonctionnent comme indiqué ci-dessus.

Avant de lancer cette commande, vérifiez qu&#39;aucun traitement en cours ne peut être impacté :

```
nlserver pdump -who
```

Puis arrêtez et redémarrez le module en mode **TraceFilter:**

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Autre exemple :

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>Le mode **Tracefile** permet d’enregistrer les logs. Dans les exemples ci-dessus, les logs sont enregistrés dans les fichiers **var/`<instance-name>`/mta_debug.log** et **var/default/web_debug.log**.

>[!IMPORTANT]
>
>Sous Windows, n&#39;ajoutez pas l&#39;option LD_PRELOAD. La commande suivante suffit :\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Vérifiez que le problème se reproduit, puis redémarrez le module :

```
nlserver restart web -tomcat -noconsole
```

Toutes les informations sont disponibles dans le fichier **/usr/local/neolane/nl6/var/default/log/web.log**.

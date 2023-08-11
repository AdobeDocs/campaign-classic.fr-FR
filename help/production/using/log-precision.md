---
product: campaign
title: Précision des logs
description: Précision des logs
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '345'
ht-degree: 100%

---

# Précision des logs{#log-precision}



Pour augmenter la précision des logs, vous pouvez appliquer cette procédure à tous les modules Adobe Campaign.

Elle consiste à relancer les processus avec un niveau de logs supérieur.

>[!IMPORTANT]
>
>Cette procédure annule les services en cours sur ce module.

Adobe Campaign peut fonctionner sous deux niveaux de logs :

1. Le mode **Verbose**, premier niveau après le niveau standard. Pour l&#39;activer, la commande est la suivante :

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Vérifiez que l&#39;erreur s&#39;est bien produite, puis relancez le processus normalement :

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Le mode **TraceFilter**, qui permet d&#39;enregistrer le maximum de logs. Pour l&#39;activer, la commande est la suivante :

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Si vous utilisez **tracefilter:&#42;**, tous les types de journaux sont activés : ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail.\
   >Les types de journaux les plus utiles sont les suivants : **wdbc** (affiche toutes les requêtes SQL), **soap** (affiche tous les appels SOAP), **ldap** (affiche toutes les requêtes LDAP lors de l&#39;authentification), **xtkquery** (affiche la liste de toutes les querydef).\
   >Vous pouvez les utiliser individuellement (par exemple : **tracefilter:soap,wdbc**). Vous pouvez aussi tous les activer et choisir d’en exclure certains : **-tracefilter:&#42;,!soap**

   Vérifiez que l&#39;erreur s&#39;est bien produite, puis relancez le processus normalement :

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Les logs de ces commandes sont stockés dans le fichier de log du module.

Voici un exemple spécifique au module Web. Les autres modules fonctionnent comme indiqués ci-dessus.

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
>Sous Windows, vous ne devez pas ajouter l&#39;option LD_PRELOAD. La commande suivante suffit :\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Vérifiez que le problème se reproduit, puis relancez le module :

```
nlserver restart web -tomcat -noconsole
```

Toutes les informations sont disponibles dans le fichier **/usr/local/neolane/nl6/var/default/log/web.log**.

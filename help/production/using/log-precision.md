---
title: Précision des logs
seo-title: Précision des logs
description: Précision des logs
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Précision des logs{#log-precision}

Pour augmenter la précision des logs, vous pouvez appliquer cette procédure à tous les modules Adobe Campaign.

Elle consiste à relancer les processus avec un niveau de logs supérieur.

>[!CAUTION]
>
>Cette procédure annule les services en cours sur ce module.

Adobe Campaign peut fonctionner sous deux niveaux de logs :

1. Le mode **Verbose**, premier niveau après le niveau standard. Pour l&#39;activer, la commande est la suivante :

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Vérifiez que l&#39;erreur s&#39;est bien produite, puis relancez le processus normalement :

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Le mode **TraceFilter**, qui permet d&#39;enregistrer le maximum de logs. Pour l&#39;activer, la commande est la suivante :

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Si vous utilisez **tracefilter:***, tous les types de logs sont activés : ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   Les types de logs les plus utiles sont les suivants : **wdbc** (affiche toutes les requêtes SQL), **soap** (affiche tous les appels SOAP), **ldap** (affiche toutes les requêtes LDAP lors de l&#39;authentification), **xtkquery** (affiche la liste de toutes les querydef).\
   Il est possible de les utiliser unitairement (par exemple : **tracefilter:soap,wdbc**). Vous pouvez aussi tous les activer et choisir d&#39;en exclure certains : **-tracefilter:*,!soap**

   Vérifiez que l&#39;erreur s&#39;est bien produite, puis relancez le processus normalement :

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!CAUTION]
Les logs de ces commandes sont stockés dans le fichier de log du module.

Voici un exemple spécifique au module Web. Les autres modules fonctionnent comme indiqués ci-dessus.

Avant de lancer cette commande, vérifiez qu&#39;aucun processus en cours ne peut être impacté.

```
nlserver pdump -who
```

Puis arrêtez et redémarrez le module en mode **TraceFilter**.

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Autre exemple :

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
Le mode **Suivi des fichiers** vous permet d’enregistrer les journaux. Dans les exemples ci-dessus, les journaux sont enregistrés dans les fichiers **var/`<instance-name>`/mta_debug.log** et **var/default/web_debug.log** .

>[!CAUTION]
Sous Windows, vous ne devez pas ajouter l&#39;option LD_PRELOAD. La commande suivante suffit :\
nlserver web -tomcat -verbose -tracefilter:*

Vérifiez que le problème se reproduit, puis relancez le module :

```
nlserver restart web -tomcat -noconsole
```

All information is available in the file **/usr/local/neolane/nl6/var/default/log/web.log**.

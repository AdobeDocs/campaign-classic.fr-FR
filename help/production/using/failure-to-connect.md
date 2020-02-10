---
title: Connexion impossible
seo-title: Connexion impossible
description: Connexion impossible
seo-description: null
page-status-flag: never-activated
uuid: 5e4cf47d-9699-4b4c-9c45-064fdc17110a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 493067fb-68f1-48b9-afaa-3127a847db83
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 90813bc2913d56136067b9f64c0e934df3f17473

---


# Connexion impossible{#failure-to-connect}

Si vous n&#39;arrivez plus à vous connecter à votre instance Adobe Campaign, les causes peuvent être multiples : de nombreux contextes peuvent poser problème.

De manière générale, vérifiez la configuration des zones de sécurité.

>[!NOTE]
>
>Pour plus d’informations sur le paramétrage des zones de sécurité, consultez [cette section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Vérifiez les informations suivantes :

1. **Vérifications du réseau**

   * Avez-vous accès à internet depuis votre ordinateur ?

      Vérifiez que vous pouvez vous connecter à des sites sur Internet (par exemple). Si vous ne pouvez pas vous connecter, il s&#39;agit d&#39;un problème sur votre machine : contactez votre administrateur système.

   * Pouvez-vous vous connecter sur le serveur hébergeant Adobe Campaign par un autre service ?

      Connectez-vous en SSH ou tout autre moyen sur le serveur. En cas d&#39;impossibilité, il y a un problème réseau chez votre hébergeur, contactez leur administrateur réseau.

1. **Vérifications côté serveur Web** (IIS/apache/etc.)

   * Le serveur Web répond-t-il ?

      Connectez-vous à l’URL d’accès au serveur Adobe Campaign à l’aide d’un navigateur Web : **http(s)://`<urlserver>`**. S’il ne répond pas, le serveur Web est arrêté sur l’ordinateur. Contactez l’administrateur système de votre société hôte pour redémarrer le service.

   * L&#39;intégration Adobe Campaign est-elle bien effectuée ?

      Connectez-vous à : URL **http(s)://`<urlserver>`/r/test** . Le serveur doit renvoyer le type de message suivant :

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      Si vous n’obtenez pas ce résultat, vérifiez dans la configuration de votre serveur Web que l’intégration est bien prise en compte.

1. **Vérifications côté Adobe Campaign**

   * Le module Web Adobe Campaign est-il bien lancé ?

      Connect to the following URL: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Si vous obtenez une erreur Tomcat Java :

         L&#39;intégration JAVA est-elle correctement effectuée ? Adobe Campaign requiert un JDK SUN pour fonctionner.

         Il est intégré dans le fichier **`[path of application]`/nl6/customer.sh **

      * Si vous obtenez une page blanche :

         Le module Web d&#39;Adobe Campaign est-il bien démarré ? Vous devez obtenir :

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * Sinon, relancez-le en utilisant la commande suivante :

         ```
         nlserver start web
         ```
>[!NOTE]
>
>If you obtain a response of the following type when you list the Adobe Campaign modules: **nlserver pdump**
>HH:MM:SS > Serveur d’applications pour Adobe Campaign Classic (version 7.X YY.R XXX@SHA1) de DD/MM/YYYY Aucune tâche Vous devez redémarrer l’ensemble de l’application Adobe Campaign. Pour ce faire, utilisez la commande suivante : **nlserver watchdog -svc -noconsole **

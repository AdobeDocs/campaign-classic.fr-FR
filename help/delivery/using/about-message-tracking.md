---
product: campaign
title: Commencer avec le tracking
description: Découvrez les instructions générales relatives au tracking dans Adobe Campaign.
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 64%

---

# Prise en main du tracking des messages {#get-started-tracking}

>[!IMPORTANT]
>
>Pour obtenir des **conseils généraux sur le tracking** qui s’appliquent à la fois à Campaign Classic v7 et Campaign v8, reportez-vous à la documentation sur le tracking des messages de [Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} :
>
>* [Configuration des liens suivis](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [Configuration des options de tracking d’URL](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [Suivi des liens personnalisés](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [Accéder aux logs de tracking](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [Tracking des tests](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [Rapports de tracking](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**Cette page présente uniquement les fonctionnalités de suivi spécifiques à Campaign Classic v7**, principalement pour les déploiements hybrides et on-premise.

## Fonctionnalités de tracking

### Paramétrage du tracking {#configure-tracking}

Pour les **déploiements hybrides/on-premise** de Campaign Classic v7, vous devez configurer le suivi au niveau de l’instance avant de l’utiliser.

>[!NOTE]
>
>Pour Campaign v8 Managed Cloud Services, la configuration du suivi est effectuée par Adobe.

**Principe de fonctionnement**

Avant d’utiliser le tracking, vous devez d’abord le paramétrer pour votre instance. La configuration doit être effectuée sur le(s) serveur(s) applicatif(s) Adobe Campaign et le(s) serveur(s) web.

Dans Campaign, il existe deux types de tracking :

* **Tracking Web** : ce mode permet de tracker les visites sur les pages de votre site web
* **Suivi des messages** : ce mode permet de suivre les diffusions de messages et le comportement des destinataires

Le mode de tracking est sélectionné lors de l&#39;installation. Pour les installations on-premise, la configuration du suivi doit être définie au niveau de l’instance. [En savoir plus](../../installation/using/deploying-an-instance.md#operating-principle)

**Serveur de tracking**

Pour paramétrer le tracking, votre instance doit être déclarée et enregistrée auprès du ou des serveurs de tracking. Le serveur de tracking est utilisé pour enregistrer et récupérer des informations sur les URL sur lesquelles les destinataires ont cliqué.

Pour les installations on-premise, le serveur de suivi est généralement un serveur web qui exécute l’application web d’Adobe Campaign. L’URL du serveur de suivi doit être définie dans la configuration de votre instance. [En savoir plus](../../installation/using/deploying-an-instance.md#tracking-server)

**Enregistrement du tracking**

Une fois le tracking configuré et les URL renseignées, le serveur de tracking doit être enregistré. L’enregistrement permet à Adobe Campaign d’enregistrer les informations de suivi et de fournir des rapports et des statistiques sur les activités suivies.

Pour les installations on-premise, les informations de tracking sont stockées dans la base de données et récupérées par le biais de workflows techniques. Le workflow technique **Tracking** traite et stocke les données de tracking collectées auprès du serveur de redirection. [En savoir plus](../../installation/using/deploying-an-instance.md#saving-tracking)

### Tracking des applications web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**Le tracking des applications web est spécifique à Campaign Classic v7** et n&#39;est pas disponible dans Campaign v8.

**Tracking d&#39;une application web**

Vous pouvez également tracker et mesurer les visites sur les pages d&#39;application web avec des balises de tracking. Cette fonctionnalité peut être utilisée pour tous les types d&#39;application web, tels que les formulaires et les landing pages. [En savoir plus](../../web/using/tracking-a-web-application.md)

**Désinscription (opt-out) du tracking des applications web**

Le processus d’opt-out du tracking des applications web vous permet d&#39;arrêter le tracking des comportements web des utilisateurs finaux qui se désinscrivent du tracking comportemental. Vous pouvez inclure la possibilité d’afficher une bannière dans des applications web ou des landing pages pour permettre aux utilisateurs de se désinscrire. [En savoir plus](../../web/using/web-application-tracking-opt-out.md)

## Résolution des problèmes liés au tracking {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Les conseils de dépannage suivants s&#39;appliquent aux **déploiements hybrides/on-premise de Campaign Classic v7**. Certaines informations peuvent également s’appliquer aux déploiements On-Premise de Campaign v8. Pour Campaign v8 Managed Cloud Services, contactez votre représentant Adobe pour obtenir de l’aide.

Pour connaître les étapes de dépannage de base du tracking dans Campaign v8, reportez-vous à la [documentation de dépannage du tracking dans Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}.

### Vérifications de base {#basic-checks}

**Vérifiez que le processus trackinglogd est en cours d’exécution**

Ce processus lit la mémoire partagée IIS/serveur web et écrit les logs de redirection.

Vous pouvez y accéder à partir de la page d’accueil en sélectionnant l’onglet Surveillance dans votre instance. Vous pouvez également exécuter la commande suivante sur l’instance : `<user>@<instance>:~$ nlserver pdump`

Si le processus trackinglogd n’apparaît pas dans la liste, lancez-le avec la commande suivante sur l’instance : `<user>@<instance>:~$ nlserver start trackinglogd`

**Vérifiez que le workflow technique Tracking a été exécuté récemment**

Vous pouvez localiser le workflow technique de tracking dans les dossiers Administration > Exploitation > Workflows techniques.

### Dépannage avancé {#advanced-troubleshooting}

+++Le workflow de tracking échoue

>[!NOTE]
>
>Disponible pour Windows uniquement

Le fichier de log de tracking corrompu.../nl6/var/&lt;nom_instance>/redir/log/0x0000 peut arrêter le worklow de tracking. Pour détecter facilement les lignes endommagées et les supprimer afin de reprendre le workflow de tracking, vous pouvez utiliser les commandes ci-dessous.

**Je sais dans quel fichier se trouve la ligne corrompue**

Dans ce cas, des lignes corrompues se trouvent dans le fichier 0x00000000000A0000.log, mais le même processus peut être appliqué à un ensemble de fichiers, un par un.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Vous pouvez ensuite arrêter le workflow de tracking, supprimer la ou les lignes endommagées et le redémarrer.

**Je ne sais pas dans quel fichier se trouve la ligne corrompue**

1. Utilisez la ligne de commande ci-après pour vérifier tous les fichiers de tracking.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. La commande répertorie toutes les lignes corrompues. Par exemple :

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Un retour à la ligne a été ajouté avant l&#39;agent utilisateur pour permettre une meilleure lecture et il ne reflète pas le rendu réel.

1. Exécutez une commande grep pour trouver le fichier correspondant.

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. Recherchez le log défectueux avec le nom de fichier et le numéro de ligne. Par exemple :

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Un retour à la ligne a été ajouté avant l&#39;agent utilisateur pour permettre une meilleure lecture et il ne reflète pas le rendu réel.

Vous pouvez ensuite arrêter le workflow de tracking, supprimer la ou les lignes endommagées et le redémarrer.

+++

+++Échec intermittent des liens de tracking

Lors de la tentative d’accès aux liens de tracking, le message suivant s’affiche :

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. Accédez à l&#39;URL &lt;serveur_redirection>/r/test et vérifiez si le numéro de build et le localhost ont été renvoyés par la requête.

1. Vérifiez la configuration spareServer dans le fichier serverConf.xml pour le serveur de tracking. Cette configuration doit être en mode de redirection.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Vérifiez manuellement si le fichier &lt;deliveryID>.xml existe sur l&#39;ordinateur dans le répertoire .../nl6/var/&lt;nom_instance>/redir/url/&lt;AAAA> (AAAA représente l’année de la diffusion).

1. Vérifiez manuellement si &lt;trackingUrlId> se trouve dans le fichier &lt;deliveryID>.xml.

1. Vérifiez manuellement l’existence de broadlogID dans la diffusion deliveryID associée.

1. Vérifiez les autorisations des fichiers &lt;deliveryID>.xml dans le répertoire.../nl6/var/&lt;nom_instance>/redir/url/year.

   Elles doivent comporter au moins l’autorisation 644 pour qu&#39;Apache puisse lire les URL de tracking pour rediriger le lien demandé.

+++

+++Mise à jour de l’option NmsTracking_Pointer

Procédez comme suit lors de la mise à jour de l&#39;option NmsTracking_Pointer :

1. Arrêtez le workflow de tracking.

1. Arrêtez le service trackinglogd.

1. Mettez à jour l&#39;option NmsTracking_Pointer vers la valeur souhaitée.

1. Redémarrez le service trackinglogd.

1. Redémarrez le workflow de tracking.

+++

+++Le tracking ne fonctionne pas avec certaines messageries web

Vous pouvez personnaliser la formule de suivi des clics et spécifier une formule de tracking Adobe Analytics personnalisée.

Ce type de personnalisation doit être effectué avec prudence afin d’éviter l’ajout de caractères de saut de page supplémentaires. Tous les caractères de saut de page présents en dehors de l’expression Javascript seront également présents dans la formule finale.

Ce type de caractère de saut de ligne supplémentaire dans l&#39;URL de tracking va entraîner un problème dans certaines messageries web (AOL, GMail, etc.).

**Premier exemple :**

* Syntaxe incorrecte

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* Syntaxe correcte

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

Pour comprendre où se trouve le saut de ligne supplémentaire, vous pouvez remplacer l’expression Javascript par une chaîne STRING fixe.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Deuxième exemple**

* Syntaxe incorrecte

  ```
  <%@ include option='NmsTracking_ClickFormula' %>
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* Syntaxe correcte

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

Pour comprendre où se trouve le saut de ligne supplémentaire, vous pouvez remplacer l’expression Javascript par une chaîne STRING fixe.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++La récupération des logs de tracking est trop lente

Lorsque l&#39;instance ne récupère pas directement les logs de tracking mais le fait à partir d&#39;un serveur Adobe Campaign Classic distant, les logs sont récupérés via l&#39;appel SOAP GetTrackingLogs défini dans le schéma remoteTracking.

Une option du fichier serverConf.xml permet de définir le nombre de logs récupérés à la fois par l’intermédiaire de cette méthode : logCountPerRequest.

La valeur par défaut de logCountPerRequest étant 1 000, elle peut s’avérer insuffisante dans certains cas. Les valeurs acceptées doivent être comprises entre 0 et 10 000.

+++

+++Impossible de lier les logs de tracking aux destinataires

Dans Adobe Campaign Classic, un mapping de ciblage est censé être unique en termes de schéma de destinataire par rapport aux schémas de broadlog / trackinglog.

![](assets/tracking-troubleshooting.png)

Il n’est pas possible d’utiliser plusieurs schémas de ciblage avec le même schéma trackinglog, car le workflow de tracking ne pourra pas réconcilier les données avec l’identifiant de ciblage.

Si vous ne souhaitez pas utiliser le mapping de ciblage d&#39;usine avec nms:recipient, nous vous recommandons les approches suivantes :

* Si vous souhaitez utiliser une dimension de ciblage personnalisée, vous devez créer un schéma broadLog/trackingLog personnalisé utilisant nms:broadlog comme modèle (par exemple nms:broadLogRcp, nms:broadLogSvc, etc.).

* Si vous souhaitez utiliser OOB trackingLogRcp/broadLogRcp, la dimension de ciblage doit être nms:recipient et la dimension de filtrage peut être un schéma personnalisé.

+++

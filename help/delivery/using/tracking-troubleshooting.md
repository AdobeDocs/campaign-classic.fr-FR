---
solution: Campaign Classic
product: campaign
title: Dépannage du suivi
description: Cette section présente les questions courantes relatives au suivi de la configuration et de l’implémentation dans Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: efa36dc08ce4dd59805bb9eba63a4249e14609d7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Dépannage du suivi {#tracking-troubleshooting}

Dans cette section, vous trouverez des questions courantes relatives au suivi de la configuration et de l’implémentation dans Adobe Campaign Classic.

## Le processus de suivi échoue {#tracking-workflow-failing}

Mon processus de suivi échoue. Comment puis-je détecter les lignes endommagées dans le fichier de suivi ?

>[!NOTE]
>
>Disponible pour Windows uniquement

Le fichier journal de suivi corrompu.../nl6/var/&lt;nom_instance>/redirecteur/log/0x0000 peut arrêter le processus de suivi. Pour détecter facilement les lignes endommagées et les supprimer pour reprendre le processus de suivi, vous pouvez utiliser les commandes ci-dessous.

### Je sais dans quel fichier se trouve la ligne corrompue

Dans ce cas, des lignes corrompues se trouvent dans le fichier 0x0000000000A0000.log, mais le même processus peut être appliqué à un ensemble de fichiers, un par un.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Vous pouvez ensuite arrêter le processus de suivi, supprimer les lignes endommagées et redémarrer le processus.

### Je ne sais pas dans quel fichier se trouve la ligne corrompue

1. utilisez la ligne de commande suivante pour archiver tous les fichiers de suivi.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. La commande liste toutes les lignes corrompues. par exemple :

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Le retour chariot a été ajouté avant l&#39;agent utilisateur pour permettre une meilleure lecture et ne reflète pas un rendu efficace.

1. Exécutez une commande grep pour rechercher le fichier correspondant.

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. Recherchez le journal défectueux avec le nom de fichier et le numéro de ligne. par exemple :

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Un retour chariot a été ajouté avant User Agent pour permettre une meilleure lecture et ne reflète pas un rendu efficace.

Vous pouvez ensuite arrêter le processus de suivi, supprimer les lignes endommagées et redémarrer le processus.

## Échec intermittent du suivi des liens {#tracking-links-fail-intermittently}

Lors de la tentative d’accès aux liens de suivi, le message suivant s’affiche :

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. Accédez à l&#39;URL &lt;redirection_server>/r/test et vérifiez si le numéro de build et l&#39;hôte local ont été renvoyés par la requête.

1. Recherchez le serveur de suivi dans le fichier serverConf.xml de la configuration spareServer. Cette configuration doit être en mode de redirection.

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

1. Vérifiez manuellement si le fichier &lt;deliveryID>.xml existe sur l&#39;ordinateur dans .../nl6/var/&lt;nom_instance>/redirecteur/url/&lt;AAAA> (AAAA représente l’année de diffusion).

1. Vérifiez manuellement si &lt;trackingUrlId> se trouve dans le fichier &lt;deliveryID>.xml.

1. Vérifiez manuellement l’existence de la variable broadlogID dans la diffusion de la variable deliveryID associée.

1. Vérifiez les autorisations des fichiers &lt;deliveryID>.xml dans .../nl6/var/&lt;nom_instance>/redirecteur/url/year.

   Ils doivent disposer d&#39;au moins 644 autorisations pour qu&#39;Apache puisse lire les url de suivi pour rediriger le lien demandé.

## Mise à jour de l&#39;option NmsTracking_Pointer ? {#updating-option}

Procédez comme suit lors de la mise à jour de l&#39;option NmsTracking_Pointer :

1. Arrêtez le processus de suivi.

1. Arrêtez le service trackinglogd.

1. Mettez à jour l&#39;option NmsTracking_Pointer sur la valeur souhaitée.

1. Redémarrez le service trackinglogd.

1. Redémarrez le processus de suivi.

## Le suivi ne semble pas fonctionner avec certains WebMail {#webmail}

Vous pouvez personnaliser la formule de suivi des clics et spécifier une formule de suivi Adobe Analytics personnalisée.

Ce type de personnalisation doit être effectué avec prudence afin d’éviter d’ajouter des caractères de saut de page supplémentaires. Tous les caractères de saut de page présents en dehors de l’expression javascript seront présents dans la formule finale.

Ce type de caractère de saut de ligne supplémentaire dans l&#39;URL de suivi va conduire à un problème dans certains webMail (AOL, GMail, etc.).

**Premier exemple :**

* Syntaxe incorrecte

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* Syntaxe correcte

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

Pour comprendre où se trouve le saut de ligne supplémentaire, vous pouvez remplacer l’expression javascript par une chaîne CHAÎNE fixe.

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
   <% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* Syntaxe correcte

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

Pour comprendre où se trouve le saut de ligne supplémentaire, vous pouvez remplacer l’expression javascript par une chaîne CHAÎNE fixe.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## La récupération des logs de tracking est trop lente {#slow-retrieval}

Lorsque l&#39;instance ne récupère pas directement des logs de tracking mais à partir d&#39;un serveur Adobe Campaign Classic distant, les journaux sont récupérés via l&#39;appel SOAP GetTrackingLogs défini dans le schéma remoteTracking.

Une option du fichier serverConf.xml permet de définir le nombre de journaux récupérés à la fois par l’intermédiaire de cette méthode : logCountPerRequest.

La valeur par défaut de logCountPerRequest étant 1000, elle peut s’avérer insuffisante dans certains cas. Les valeurs acceptées doivent être comprises entre 0 et 10 000.

## Impossible de lier les logs de tracking aux destinataires {#link-recipients}

À Adobe Campaign Classic, un mapping de ciblage est censé être unique en termes de schéma destinataire par rapport aux schémas de journal en ligne / trackinglog.

![](assets/tracking-troubleshooting.png)

Il n’est pas possible d’utiliser plusieurs schémas de ciblage avec le même schéma de journal de suivi, car le processus de suivi ne pourra pas concilier les données avec l’ID de ciblage.

Si vous ne souhaitez pas utiliser le mapping de ciblage prêt à l&#39;emploi avec nms:destinataire, nous vous recommandons les approches suivantes :

* Si vous souhaitez utiliser la dimension de ciblage personnalisée, vous devez créer un schéma largeLog/trackingLog personnalisé en utilisant nms:broadlog comme modèle (par exemple nms:wideLogRcp, nms:broadLogSvc, etc.).

* Si vous souhaitez utiliser OOB trackingLogRcp/wideLogRcp, la dimension de ciblage doit être nms:destinataire et la dimension de filtrage peut être un schéma personnalisé.

---
solution: Campaign Classic
product: campaign
title: Protocole et paramètres du connecteur SMS
description: En savoir plus sur le connecteur SMS et comment le configurer.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 96ad3208c792efb47097768bc779bec59d9ca313
workflow-type: tm+mt
source-wordcount: '2745'
ht-degree: 0%

---


# Résolution des problèmes SMS {#troubleshooting-sms}

## Conflit entre différents comptes externes {#external-account-conflict}

Si l&#39;instance comporte plusieurs comptes externes SMS, vous devez vérifier que les problèmes ne sont pas causés par un conflit entre comptes externes.

Adobe Campaign traite les comptes externes comme des entités non liées.

Si vous disposez de plusieurs comptes, suivez cette procédure pour isoler le compte externe qui pose problème :

1. Désactivez tous les comptes externes.
1. Activez un compte externe.
1. Essaie de reproduire le problème.
1. Si le problème initial n&#39;apparaît pas toujours, effectuez un nombre raisonnable de tentatives avant de conclure.
1. Si le problème n’apparaît pas avec ce compte unique, désactivez-le et redémarrez l’étape 2 sur le compte suivant.

Une fois que vous avez vérifié chaque compte individuellement, il existe 2 scénarios possibles :

* **Le problème est apparu sur un ou plusieurs comptes.**

   Dans ce cas, vous pouvez appliquer d’autres procédures de dépannage sur chaque compte individuellement. Il est préférable de désactiver d’autres comptes lors du diagnostic d’un compte afin de réduire le trafic réseau et le nombre de journaux.

* **Le problème ne s’affichait pas lorsqu’un seul compte était principal à un moment donné.**

   Vous avez un conflit entre les comptes. Comme nous l&#39;avons déjà mentionné, Adobe Campaign traite les comptes individuellement, mais le fournisseur peut les traiter comme un compte unique.

   * Vous utilisez des combinaisons de nom de connexion/mot de passe différentes entre tous vos comptes.
Vous devrez contacter le fournisseur pour diagnostiquer les conflits potentiels de leur côté.

   * Certains comptes externes partagent la même combinaison de connexion/mot de passe.
Le fournisseur n&#39;a aucun moyen de savoir de quel compte externe provient `BIND PDU`, de sorte qu&#39;il traite toutes les connexions à partir de plusieurs comptes comme une seule connexion. Ils auraient pu rediriger les MO et SR au hasard sur les deux comptes, ce qui aurait posé des problèmes.
Si le fournisseur prend en charge plusieurs codes courts pour la même combinaison de connexion/mot de passe, vous devrez leur demander où placer ce code court dans le `BIND PDU`. Notez que cette information doit être placée dans le `BIND PDU` et non dans `SUBMIT_SM`, puisque le `BIND PDU` est le seul endroit qui permettra d&#39;utiliser correctement les MO de routage.
Consultez la section [Informations de chaque type de PDU](../../delivery/using/sms-protocol.md#information-pdu) ci-dessus pour savoir quel champ est disponible dans `BIND PDU`, en général vous ajoutez le code court dans `address_range`, mais cela nécessite une assistance spéciale de la part du fournisseur. Contactez-les pour savoir comment ils s’attendent à acheminer plusieurs codes courts indépendamment.
Adobe Campaign prend en charge la gestion de plusieurs codes courts sur le même compte externe.

## Problème avec le compte externe en général {#external-account-issues}

* Vérifiez si le connecteur a été modifié récemment et par qui (vérifiez les Comptes externes en tant que groupe).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Recherchez (dans le répertoire /postupgrade) si le système a été mis à niveau et quand
* Déterminez si des paquets affectant SMS ont pu être mis à jour récemment (/var/log/dpkg.log).

## Problème avec le midsourcing (hébergé){#issue-mid-sourcing}

* Si le problème survient sur un environnement de midsourcing, assurez-vous que la diffusion et les journaux étendus sont correctement créés et mis à jour sur le serveur de midsourcing. Si ce n&#39;est pas le cas, ce n&#39;est pas un problème de SMS.

* Si tout fonctionne sur le serveur intermédiaire et que les SMS sont correctement envoyés, mais que l’instance marketing n’est pas correctement mise à jour, un problème de synchronisation intermédiaire peut se produire.

## Problème lors de la connexion au fournisseur {#issue-provider}

* Si `BIND PDU` renvoie un code non nul `command_status`, demandez au fournisseur d’autres informations.

* Vérifiez que le réseau est correctement configuré pour que la connexion TCP puisse être établie avec le fournisseur.

* Demandez au fournisseur de vérifier s’il a correctement ajouté les adresses IP à la liste autorisée de l’instance Adobe Campaign.

* Vérifiez les paramètres **Compte externe**. Demandez au fournisseur la valeur des champs.

* Si la connexion est réussie mais instable, consultez la section [Problème de connexions instables](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Si les problèmes de connexion sont difficiles à diagnostiquer, une capture réseau peut fournir des informations. Assurez-vous que la capture du réseau s&#39;exécute simultanément pendant que le problème s&#39;affiche pour pouvoir être analysé efficacement. Notez également l’heure exacte à laquelle le problème apparaît.

## Problèmes de connexion instable {#issues-unstable-connection}

Une connexion est considérée comme instable si l’une des situations suivantes se produit :

* La connexion dure moins d&#39;une heure. Les connexions d&#39;émetteurs Adobe Campaign Classic constituent une exception en raison du fonctionnement de la MTA Adobe Campaign Classic.

* Le fournisseur envoie `UNBIND PDU`s.

* `enquire_link` expire, soit du côté de l’Adobe Campaign, soit du côté du fournisseur. Dans ce cas, `ENQUIRE_LINK_RESP` peut s’afficher avec un code d’erreur non nul.

* Il y a beaucoup de `BIND PDU`s. Il ne doit pas y en avoir plus pendant une journée, selon le nombre de connexions. Plus d&#39;une PDU BIND par heure doit être alertée.

Comment résoudre les problèmes de stabilité des connexions :

* Les connexions instables sont rarement la cause première, c&#39;est souvent le résultat d&#39;un autre problème qui déclenche une déconnexion. Trouver la cause première est la priorité.

* Activez les traces SMPP détaillées. Vous aurez besoin d&#39;eux pour voir ce qui se passe au redémarrage de la connexion.

* Si le fournisseur envoie `BIND PDU`s, il se peut qu&#39;il y ait un problème. Demandez à votre fournisseur pourquoi `UNBING` est envoyé.

* La capture du réseau est parfois la seule façon de voir comment la connexion est fermée.

* Si le fournisseur ferme les connexions en envoyant un `TCP FIN` ou un `TCP RST packet`, demandez à votre fournisseur de plus amples informations.

* Si le fournisseur ferme la connexion après avoir envoyé une erreur de nettoyage telle que `DELIVER_SM_RESP` avec un code d&#39;erreur, il doit réparer son connecteur sinon il empêchera la transmission d&#39;autres types de messages et déclenchera le ralentissement MTA. Ceci est particulièrement important en mode transcepteur où la fermeture de la connexion a un impact à la fois sur MT et SR.

## Problème lors de l&#39;envoi d&#39;un MT (SMS régulier envoyé à un utilisateur final){#issue-MT}

* Vérifiez que la connexion est stable. Une connexion SMPP doit rester en service pendant au moins une heure en continu, à l&#39;exception des émetteurs de Adobe Campaign Classic. Voir la section [Problème de connexions instables](../../delivery/using/sms-protocol.md#issues-unstable-connection).

* Si le redémarrage de la MTA entraîne l’envoi de MT à nouveau opérationnel pendant une petite période de temps, vous avez probablement un ralentissement dû à une connexion instable. Voir la section [Problème de connexions instables](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Vérifiez que le journal volumineux est présent et que son état est correct avec les dates correctes. Si ce n&#39;est pas le cas, il peut s&#39;agir d&#39;un problème de préparation de diffusion ou de diffusion.

* Vérifiez que la MTA traite réellement le message. Si ce n&#39;est pas le cas, ce pourrait ne pas être un problème de SMS.

* Vérifiez que le connecteur SMS est effectivement lié à l&#39;équipement du fournisseur. Demandez au fournisseur de nous faire part de ses commentaires pour vous assurer que tous les systèmes communiquent correctement. Voir `BIND_TRANSMITTER` et `BIND_TRANSCEIVER PDU`s pour plus d&#39;informations sur le processus de liaison. Vous devrez peut-être activer les traces SMPP pour un dépannage correct.

* Lorsque les traces SMPP sont activées, vérifiez que `SUBMIT_SM PDU` contient les informations appropriées.

* Vérifiez que le fournisseur répond par une valeur `SUBMIT_SM_RESP PDU` avec une valeur &quot;OK&quot; (code 0). Assurez-vous que la PDU arrive avec un délai raisonnable : tout ce qui dure plus d&#39;une seconde doit être discuté avec le fournisseur, il arrive habituellement en moins de 100 ms.

* Si toutes ces étapes fonctionnent, vous pouvez être certain que le problème est du côté fournisseur. Ils devront effectuer le dépannage sur leur plateforme.

* S&#39;il fonctionne mais que le débit est incohérent, essayez d&#39;ajuster la fenêtre d&#39;envoi et d&#39;abaisser le débit MT. Vous devrez travailler avec le fournisseur pour l’ajuster. Adobe Campaign peut envoyer des messages très rapidement afin que des problèmes de performances puissent survenir sur l&#39;équipement du fournisseur.

## Les MT sont dupliquées (le même SMS est envoyé plusieurs fois de suite){#duplicated-MT}

Les duplicata sont souvent causés par des Reprises. Il est normal d&#39;avoir des duplicata lors de la nouvelle tentative de messages, vous devriez plutôt essayer de supprimer la cause première des Reprises.

* Si vous voyez des duplicata envoyés exactement à 60 secondes d&#39;intervalle, c&#39;est probablement un problème du côté fournisseur, ils n&#39;envoient pas un `SUBMIT_SM_RESP` assez rapidement.

* Si vous voyez beaucoup de `BIND/UNBIND`, vous avez une connexion instable. Consultez la section [Problème de connexions instables](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) pour connaître les solutions avant de tenter de résoudre les problèmes de messages de duplicata.

Réduction du nombre de duplicata en cas de nouvelle tentative :

* Baissez la fenêtre d&#39;envoi. La fenêtre d&#39;envoi doit être suffisamment grande pour couvrir la latence `SUBMIT_SM_RESP`. Sa valeur représente le nombre maximal de messages pouvant être dupliqués en cas d&#39;erreur pendant que la fenêtre est pleine.

## Problème lors du traitement de SR (reçus de diffusion) {#issue-process-SR}

* Vous aurez besoin de traces SMPP activées pour effectuer tout type de dépannage SR.

* Vérifiez que le `DELIVER_SM PDU` vient du fournisseur et qu&#39;il est bien formé.

* Vérifiez que Adobe Campaign a répondu avec succès `DELIVER_SM_RESP PDU` en temps opportun. Sur Adobe Campaign Classic, cela garantit que la SR a été insérée dans la table `providerMsgId` pour traitement différé par le processus SMS.

Si l&#39;`DELIVER_SM PDU` n&#39;est pas reconnu, vérifiez ce qui suit :

* Vérifiez l&#39;expression regex associée à l&#39;extraction des identifiants et au traitement des erreurs dans le **Compte externe**. Vous devrez peut-être les valider par rapport au contenu de `DELIVER_SM PDU`.

* Vérifiez que les erreurs sont correctement configurées dans la table `broadLogMsg`.

Si `DELIVER_SM PDU` a été reconnu par le connecteur SMPP étendu de Adobe Campaign Classic mais que le fichier wideLog n&#39;est pas mis à jour correctement, vérifiez le processus de rapprochement des identifiants décrit dans la section [Correspondance des entrées MT, SR et Broadlog](../../delivery/using/sms-protocol.md#matching-mt).

Si vous avez tout corrigé, mais que certains SR non valides figurent toujours dans les tampons du fournisseur, vous pouvez les ignorer en utilisant l’option &quot;Invalid ID accept count&quot; (Nombre d’identifiants non valides reconnus). Il doit être utilisé avec soin et réinitialisé à 0 aussi vite que possible après le nettoyage des tampons.

## Problème lors du traitement de MO (et de la réponse automatique/liste bloquée){#issue-process-MO}

* Activez les traces SMPP pendant les tests. Si vous n&#39;activez pas le protocole TLS, vous devez effectuer une capture réseau lors du dépannage de MO pour vérifier que les PDU contiennent les informations correctes et sont correctement formatées.

* Lors de la capture du trafic réseau ou de l&#39;analyse des traces SMPP, veillez à capturer l&#39;ensemble de la conversation avec le MO et sa réponse MT si une réponse est configurée.

* Si le MO (`DELIVER_SM PDU`) n&#39;apparaît pas dans les traces, le problème est du côté fournisseur. Ils devront effectuer un dépannage sur leur plateforme.

* Si le `DELIVER_SM PDU` apparaît, vérifiez qu’Adobe Campaign l’a reconnu avec un `DELIVER_SM_RESP PDU` (code 0). Ce REEE garantit que toute la logique de traitement a été appliquée par Adobe Campaign (réponse automatique et permission/liste bloquée). Si ce n&#39;est pas le cas, recherchez un message d&#39;erreur dans les journaux de processus SMS.

* Si les réponses automatiques sont activées, vérifiez que `SUBMIT_SM` a été envoyé au fournisseur. Dans le cas contraire, il est garanti de trouver un message d&#39;erreur dans les journaux de processus SMS.

* Si le `SUBMIT_SM MT PDU` contenant la réponse se trouve dans les traces mais que le SMS n&#39;arrive pas au téléphone portable, vous devrez contacter le fournisseur pour obtenir de l&#39;aide sur le dépannage.

## Problème lors de la préparation de la diffusion sans exclure les destinataires mis en quarantaine (mis en quarantaine par la fonction de réponse automatique) {#issue-delivery-preparation}

* Vérifiez que le format du numéro de téléphone est exactement le même dans le tableau de quarantaine et dans le journal des diffusions. Si ce n&#39;est pas le cas, consultez cette [section](../../delivery/using/sms-protocol.md#automatic-reply) si vous rencontrez des problèmes avec le préfixe plus du format de numéro de téléphone international.

* Cochez les codes courts. Des exclusions peuvent se produire si le code court du destinataire est identique à celui défini dans le compte externe ou s’il est vide (vide = tout code court). Si un seul code court est utilisé pour l’ensemble de l’instance Adobe Campaign, il est plus facile de laisser tous les champs **de code court** vides.

## Problèmes de codage {#encoding-issues}

**Étape 1 : Contactez le fournisseur**

Contactez-les et voyez ce qui ne va pas chez eux. Ils devraient pouvoir vous dire si le problème est de leur côté ou de celui de l&#39;Adobe Campaign. Si le problème est en Adobe Campaign, ils devraient être en mesure de vous dire exactement quel champ est incorrect.

**Étape 2 : Savoir ce qu&#39;il y a dans votre message**

Unicode permet de nombreuses variantes pour les caractères identiques et Adobe Campaign ne peut pas les gérer toutes.

La source de problèmes la plus courante est le copier-coller d’un traitement de texte, qui transforme les caractères habituels en versions typographiques correctes : espaces changés en espaces insécables, les guillemets de doublon changés en guillemets d&#39;ouverture et de fermeture, moins les signes changés en différents types de tirets, etc.

Ne copiez pas et ne collez pas votre message lors du test, tapez-le toujours directement dans l&#39;interface.

Avec le format hexadécimal, vous pouvez faire la différence entre des caractères similaires. Un L minuscule, un I majuscule, O, 0, tous les types de guillemets différents, les encodages non latins ou même différents types d&#39;espaces peuvent tous avoir le même aspect ou même ne pas s&#39;afficher du tout.

Pour convertir unicode en hexadécimal, vous pouvez utiliser des outils en ligne tels que le [convertisseur de code Unicode](https://r12a.github.io/app-conversion/) site Web. Saisissez votre texte, assurez-vous qu’il n’existe pas d’informations d’identification personnelle telles que les numéros de téléphone, puis cliquez sur **Convertir**. Les valeurs hexadécimales se trouvent en bas (zone UTF-32).

Lors de l’ouverture de tickets sur les problèmes de codage, que ce soit avec le fournisseur ou le support Adobe Campaign, incluez toujours une version hexadécimale de ce que vous tapez et de ce que vous voyez.

**Étape 3 : Savoir ce que vous devez envoyer**

Déterminez le codage que vous prévoyez d’utiliser et recherchez en ligne sa table de caractères. Vérifiez que les caractères que vous avez l’intention d’envoyer sont réellement disponibles dans la page de codes de cible. Vérifiez que le champ `data_coding` est correct et correspond à ce que vous et le fournisseur attendez.

**Étape 4 : Connaître ce que vous avez effectivement envoyé**

Vous aurez besoin de la sortie de débogage du connecteur pour voir exactement quels octets vous envoyez au fournisseur. Les problèmes de codage apparaissent dans `SUBMIT_SM PDU`s, veillez donc à les capturer. Envoyez des messages très distincts qui sont faciles à trouver dans le journal.

Envoyez différents types de caractères spéciaux lors du test. Par exemple, l’encodage GSM7 comporte des caractères étendus qui sont très distincts dans leur forme hexadécimale, ils sont faciles à repérer puisqu’ils n’apparaissent dans aucun autre encodage.

## Éléments à inclure lors de la communication sur un problème SMS {#element-include}

Chaque fois que vous cherchez de l&#39;aide sur une question de SGS, que ce soit en ouvrant un ticket d&#39;assistance à Adobe Campaign, au fournisseur de SGS, ou tout autre type de communication sur la question, vous devrez inclure les informations suivantes pour vous assurer qu&#39;elle sera correctement qualifiée. Des problèmes bien qualifiés sont essentiels pour résoudre les problèmes plus rapidement.

* **Activez les** messages SMPP détaillés lorsque le problème apparaît. La plupart des problèmes de SMS sont impossibles à résoudre sans cela.

* Si le problème est lié au trafic SMS, contactez d&#39;abord le fournisseur. Leur plate-forme est la mieux adaptée pour un diagnostic efficace des problèmes de trafic SMS en temps réel.

* Inclure une description brève mais factuelle du problème.

* Incluez une description du résultat attendu.

* Inclure les commentaires du fournisseur.

* Incluez les journaux et/ou les captures réseau appropriés. Lorsque vous effectuez des captures, veillez à reproduire le problème pendant la capture.

* Si vous incluez des journaux, des traces ou des captures, indiquez l’emplacement exact dans le fichier lorsque le problème s’affiche.

* Si vous référencez des messages, des PDU ou des journaux, indiquez clairement leur horodatage pour les rendre plus faciles à trouver.

* Essayez de reproduire le problème sur un environnement de test. Si vous n’êtes pas sûr d’un paramètre, essayez-le sur l’environnement de test et vérifiez le résultat avec les traces SMPP. Il est généralement préférable de signaler les problèmes répliqués sur les environnements d&#39;essai que les problèmes directement rapports sur les environnements de production.

* Incluez les modifications ou les ajustements apportés sur la plateforme. Incluez également toute modification que le fournisseur peut avoir apportée de son côté.

### Capture du réseau {#network-capture}

Une capture réseau n&#39;est pas toujours nécessaire, en général les messages SMPP trop détaillés sont suffisants. Voici quelques directives qui vous aideront à déterminer si une capture réseau est nécessaire :

* Problèmes de connexion, mais les messages verbaux n&#39;affichent pas `BIND_RESP PDU`.

* Déconnexions inexpliquées sans message d&#39;erreur, comportement habituel du connecteur lorsqu&#39;il détecte une erreur de protocole de bas niveau.

* Le fournisseur se plaint du processus de déconnexion/déconnexion.

* Problèmes de codage dans les champs facultatifs TLV.

* Le trafic est suspecté d&#39;être mixte entre les différentes connexions.

Dans tous les autres cas, essayez d&#39;abord d&#39;analyser des messages SMPP explicites et demandez une capture réseau uniquement si des informations sont manquantes dans les journaux explicites.

Dans certains cas, la capture du trafic réseau n’est pas nécessaire. Voici les situations les plus courantes :

* TLS activé : Par définition, le trafic TLS est chiffré, de sorte qu’il ne peut pas être capturé.

* Problèmes de performances : Les journaux contiennent toutes les informations nécessaires pour suivre les problèmes de performances.

* Problèmes de minutage (`retry timing`, `enquire_link` période, plafonnement du débit, etc.)

* Analyse et traitement SR : les journaux explicites offrent beaucoup plus de contexte et une meilleure présentation.

* Traitement MO (réponses automatiques, quarantaine).

* Erreurs n’impliquant pas de trafic SMPP réel : Préparation de la diffusion, problèmes d’API du Centre de messages, problèmes de flux de travail, etc.

## Activation des traces SMPP {#enabling-smpp-traces}

Le nouveau connecteur prend en charge la journalisation étendue via les traces : SMPP. Les suivis sont générés dans le journal MTA, et non dans la sortie standard.

**Activation par compte externe (méthode préférée)**

1. Dans le **Compte externe**, cochez **Activer les traces SMPP détaillées dans le fichier journal**.
1. Patientez 10 minutes pour laisser le serveur recharger les comptes externes.

Ça devrait être principal maintenant.

**Activation dans la configuration**

Dans le fichier `config-instance.xml`, définissez les paramètres suivants :

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Vérification du nombre de connexions ouvertes sur un conteneur {#open-connections}

Pour vérifier le nombre de connexions ouvertes sur un conteneur, vous pouvez utiliser la commande suivante :

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Cela liste le nombre de connexions ouvertes pour un port donné. Nous utilisons ici le port 3600.

Le résultat doit être le suivant :

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 ont ouvert des connexions pour le processus sms et 2 par enfant de 5 enfants par mois.

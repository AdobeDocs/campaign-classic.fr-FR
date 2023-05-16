---
product: campaign
title: Résolution des problèmes de SMS
description: En savoir plus sur la résolution des problèmes liés au canal SMS
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: SMS
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 100%

---

# Résolution des problèmes de SMS {#troubleshooting-sms}



## Conflit entre différents comptes externes {#external-account-conflict}

Si l&#39;instance comporte plusieurs comptes externes SMS, vous devez vérifier que les problèmes ne sont pas causés par un conflit entre comptes externes.

Adobe Campaign traite les comptes externes comme des entités non liées.

Si vous disposez de plusieurs comptes, procédez comme suit pour isoler le compte externe qui pose problème :

1. Désactivez tous les comptes externes.
1. Activez un compte externe.
1. Essayez de reproduire le problème.
1. Si le problème initial n&#39;apparaît pas toujours, effectuez un nombre raisonnable de tentatives avant de conclure.
1. Si le problème n&#39;apparaît pas avec ce compte unique, désactivez-le et redémarrez l&#39;étape 2 sur le compte suivant.

Une fois que vous avez vérifié chaque compte individuellement, il existe 2 scénarios possibles :

* **Le problème est apparu sur un ou plusieurs comptes.**

   Dans ce cas, vous pouvez appliquer d&#39;autres procédures de résolution des problèmes individuellement sur chaque compte. Il est préférable de désactiver les autres comptes lors du diagnostic d&#39;un compte afin de réduire le trafic réseau et le nombre de logs.

* **Le problème ne s&#39;affichait pas lorsqu&#39;un seul compte était actif à un moment donné.**

   Vous avez un conflit entre les comptes. Comme nous l&#39;avons déjà mentionné, Adobe Campaign traite les comptes individuellement, mais le fournisseur peut les traiter comme un compte unique.

   * Vous utilisez des combinaisons nom d&#39;utilisateur / mot de passe différentes entre tous vos comptes.
Vous devrez contacter le fournisseur pour qu&#39;il diagnostique les conflits potentiels de son côté.

   * Certains comptes externes partagent la même combinaison nom d&#39;utilisateur / mot de passe.
Le fournisseur n&#39;a aucun moyen de savoir de quel compte externe provient le `BIND PDU`, de sorte qu&#39;il traite toutes les connexions à partir de plusieurs comptes comme une seule. Il se peut qu&#39;il ait redirigé les MO et SR de manière aléatoire sur les deux comptes, ce qui a provoqué des problèmes.
Si le fournisseur prend en charge plusieurs codes courts pour le même nom d&#39;utilisateur / mot de passe, vous devrez leur demander où placer ce numéro court dans le `BIND PDU`. Notez que cette information doit être placée dans le `BIND PDU` et non dans `SUBMIT_SM`, puisque le `BIND PDU` est le seul endroit qui permettra d&#39;utiliser correctement les MO de routage.
Consultez la section [Informations dans chaque type de PDU](sms-protocol.md#information-pdu) ci-dessus pour savoir quel champ est disponible dans le `BIND PDU`, en général vous ajoutez le numéro court dans `address_range`, mais cela nécessite une assistance spéciale de la part du fournisseur. Contactez-le pour savoir comment il s&#39;attend à acheminer de manière indépendante plusieurs numéros courts.
Adobe Campaign prend en charge la gestion de plusieurs numéros courts sur le même compte externe.

## Problème avec un compte externe en général {#external-account-issues}

* Vérifiez si le connecteur a été changé récemment et par qui (vérifiez les comptes externes en tant que groupe).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Recherchez (dans le répertoire /postupgrade) si le système a été mis à niveau et quand.
* Déterminez si des packages affectant les SMS ont pu être mis à jour récemment (/var/log/dpkg.log).

## Problème lié au mid-sourcing (hébergé){#issue-mid-sourcing}

* Si le problème se produit dans un environnement de mid-sourcing, vérifiez que les logs de diffusion et les broadlogs sont correctement créés et mis à jour sur le serveur de mid-sourcing. Si ce n&#39;est pas le cas, il ne s&#39;agit pas d&#39;un problème de SMS.

* Si tout fonctionne sur le serveur de mid-sourcing et que les SMS sont correctement envoyés, mais que l&#39;instance marketing n&#39;est pas correctement mise à jour, il est possible qu&#39;un problème de synchronisation mid-sourcing se produise.

## Problème lors de la connexion au fournisseur {#issue-provider}

* Si le `BIND PDU` renvoie un code non nul `command_status`, demandez d&#39;autres informations au fournisseur.

* Vérifiez que le réseau est correctement configuré pour que la connexion TCP puisse être établie avec le fournisseur.

* Demandez au fournisseur de vérifier s&#39;il a correctement ajouté les adresses IP à la liste autorisée de l&#39;instance Adobe Campaign.

* Vérifiez les paramètres **Compte externe**. Demandez au fournisseur la valeur des champs.

* Si la connexion est réussie mais instable, consultez la section [Problème de connexion instable](troubleshooting-sms.md#issues-unstable-connection).

* Si les problèmes de connexion sont difficiles à diagnostiquer, une capture réseau peut fournir des informations. Assurez-vous que la capture du réseau s&#39;exécute simultanément pendant que le problème s&#39;affiche pour pouvoir être analysé efficacement. Notez également l&#39;heure exacte à laquelle le problème apparaît.

## Problèmes de connexion instable {#issues-unstable-connection}

Une connexion est considérée comme instable si l&#39;une des situations suivantes se produit :

* La connexion dure moins d&#39;une heure. Les connexions d&#39;émetteur Adobe Campaign Classic constituent une exception en raison du fonctionnement du MTA Adobe Campaign Classic.

* Le fournisseur envoie `UNBIND PDU`.

* `enquire_link` expire, soit du côté d&#39;Adobe Campaign, soit du côté du fournisseur. Dans ce cas, `ENQUIRE_LINK_RESP` peut s&#39;afficher avec un code d&#39;erreur non nul.

* Il y a beaucoup de `BIND PDU`.Il ne doit pas y en avoir plus de quelques-uns durant une journée, selon le nombre de connexions. L&#39;apparition de plusieurs PDU BIND par heure doit attirer l&#39;attention.

Comment résoudre les problèmes de stabilité de connexion :

* Les connexions instables sont rarement la cause première, il s&#39;agit souvent du résultat d&#39;un autre problème qui déclenche une déconnexion. Il est prioritaire d&#39;identifier la cause première.

* Activez les traces SMPP de verbose. Vous aurez besoin d&#39;elles pour voir ce qui se passe au redémarrage de la connexion.

* Si le fournisseur envoie `BIND PDU`, il se peut qu&#39;il y ait un problème. Demandez à votre fournisseur pourquoi `UNBING` est envoyé.

* La capture du réseau est parfois la seule façon de voir comment la connexion est fermée.

* Si le fournisseur ferme les connexions en envoyant un paquet `TCP FIN` ou `TCP RST packet`, demandez à votre fournisseur de plus amples informations.

* Si le fournisseur ferme la connexion après avoir envoyé une erreur de nettoyage telle que `DELIVER_SM_RESP` avec un code d&#39;erreur, il doit réparer son connecteur sinon il empêchera la transmission d&#39;autres types de messages et déclenchera le ralentissement du MTA. Ceci est particulièrement important en mode émetteur-récepteur où la fermeture de la connexion a un impact à la fois sur les MT et SR.

## Problème lors de l&#39;envoi d&#39;un MT (SMS régulier envoyé à un utilisateur final){#issue-MT}

* Vérifiez que la connexion est stable. Une connexion SMPP doit durer au moins une heure en continu, sauf pour les émetteurs sur Adobe Campaign Classic. Pour plus d&#39;informations, consultez la section [Problème de connexion instable](sms-protocol.md#issues-unstable-connection).

* Si le redémarrage du MTA entraîne l&#39;envoi de MT à nouveau opérationnel pendant une petite période de temps, vous avez probablement un ralentissement dû à une connexion instable. Pour plus d&#39;informations, consultez la section [Problème de connexions instables](troubleshooting-sms.md#issues-unstable-connection).

* Vérifiez que le broadlog est présent et que son statut est correct avec les dates correctes. Si ce n&#39;est pas le cas, il peut s&#39;agir d&#39;un problème de préparation de diffusion ou de diffusion.

* Vérifiez que le MTA traite réellement le message. Si ce n&#39;est pas le cas, il est possible qu&#39;il ne s&#39;agisse pas d&#39;un problème de SMS.

* Vérifiez que le connecteur SMS est effectivement lié à l&#39;équipement du fournisseur. Demandez au fournisseur de faire part de ses commentaires pour assurer que tous les systèmes communiquent correctement. Pour plus d&#39;informations sur le processus de liaison, consulter `BIND_TRANSMITTER` et `BIND_TRANSCEIVER PDU`. Vous devrez peut-être activer les traces SMPP pour résoudre correctement les problèmes.

* Lorsque les traces SMPP sont activées, vérifiez que `SUBMIT_SM PDU` contient les informations appropriées.

* Vérifiez que le fournisseur répond par une valeur `SUBMIT_SM_RESP PDU` avec une valeur &quot;OK&quot; (code 0). Assurez-vous que le PDU arrive avec un délai raisonnable : tout ce qui dure plus d&#39;une seconde doit faire l&#39;objet d&#39;une discussion avec le fournisseur (il arrive habituellement en moins de 100 ms).

* Si toutes ces étapes fonctionnent, vous pouvez être certain que le problème est du côté fournisseur. Il devra effectuer la résolution des problèmes sur sa plateforme.

* Si cela fonctionne mais que le débit n&#39;est pas constant, essayez d&#39;ajuster la fenêtre d&#39;émission et d&#39;abaisser le débit MT. Vous devrez travailler avec le fournisseur pour l&#39;ajuster. Adobe Campaign peut envoyer des messages très rapidement de sorte que des problèmes de performances peuvent survenir sur l&#39;équipement du fournisseur.

## Les MT sont dupliquées (le même SMS est envoyé plusieurs fois de suite){#duplicated-MT}

Les doublons sont souvent causés par des reprises. Il est normal d&#39;avoir des doublons lors de la nouvelle tentative d&#39;envoi de messages. Il est préférable d&#39;essayer de supprimer la cause première des reprises.

* Si vous voyez des doublons envoyés exactement à 60 secondes d&#39;intervalle, il s&#39;agit probablement d&#39;un problème du côté fournisseur. L&#39;envoi de `SUBMIT_SM_RESP` n&#39;est pas assez rapide.

* Si vous voyez beaucoup de `BIND/UNBIND`, vous avez une connexion instable. Consultez la section [Problème de connexion instable](troubleshooting-sms.md#issues-unstable-connection) pour connaître les solutions avant de tenter de résoudre les problèmes de doublons de messages.

Réduction du nombre de doublons en cas de nouvelle reprise :

* Baissez la fenêtre d&#39;émission. La fenêtre d&#39;émission doit être suffisamment grande pour couvrir la latence `SUBMIT_SM_RESP`. Sa valeur représente le nombre maximum de messages pouvant être dupliqués en cas d&#39;erreur lorsque la fenêtre est pleine.

## Problème lors du traitement des SR (accusés de réception de diffusion) {#issue-process-SR}

* Vous aurez besoin de traces SMPP activées pour tous les types de résolution des problèmes SR.

* Vérifiez que le `DELIVER_SM PDU` vient du fournisseur et qu&#39;il est correctement formé.

* Vérifiez que Adobe Campaign répond avec succès `DELIVER_SM_RESP PDU` dans les délais impartis. Sur Adobe Campaign Classic, cela garantit que le SR a été inséré dans la table `providerMsgId` pour le traitement différé par le processus SMS.

Si le `DELIVER_SM PDU` n&#39;est pas suivi d&#39;un acquittement, vérifiez ce qui suit :

* Vérifiez l&#39;expression regex associée à l&#39;extraction des identifiants et au traitement des erreurs dans le **compte externe**. Vous devrez peut-être les valider par rapport au contenu de `DELIVER_SM PDU`.

* Vérifiez que les erreurs sont correctement configurées dans le tableau `broadLogMsg`.

Si `DELIVER_SM PDU` a été reconnu par le connecteur SMPP étendu Adobe Campaign Classic mais que le broadLog n&#39;est pas mis à jour correctement, vérifiez le processus de réconciliation des identifiants décrit dans la section [Correspondance des entrées MT, SR et Broadlog](sms-protocol.md#matching-mt).

Si vous avez tout corrigé, mais que des SR non valides figurent toujours dans les tampons du fournisseur, vous pouvez les ignorer à l&#39;aide de l&#39;option Nombre d&#39;acquittements d&#39;identifiant invalides. Cette option doit être utilisée avec soin et réinitialisée à 0 aussi vite que possible après le nettoyage des tampons.

## Problème lors du traitement de MO (et de la réponse liste bloquée / auto){#issue-process-MO}

* Activez les traces SMPP pendant les tests. Si vous n&#39;activez pas le protocole TLS, vous devez effectuer une capture réseau lors de la résolution des problèmes de MO pour vérifier que les PDU contiennent les informations correctes et sont correctement formatées.

* Lors de la capture du trafic réseau ou de l&#39;analyse des traces SMPP, veillez à capturer l&#39;ensemble de la conversation avec le MO et sa réponse MT si une réponse est configurée.

* Si le MO (`DELIVER_SM PDU`) n&#39;apparaît pas dans les traces, le problème est du côté fournisseur. Il devra effectuer une résolution des problèmes sur sa plateforme.

* Si le `DELIVER_SM PDU` apparaît, vérifiez qu&#39;Adobe Campaign a confirmé sa réception avec un `DELIVER_SM_RESP PDU` indiquant un succès (code 0). Ce RESP garantit que toute la logique de traitement a été appliquée par Adobe Campaign (réponse automatique et liste autorisée / liste bloquée). Si ce n&#39;est pas le cas, recherchez un message d&#39;erreur dans les logs de processus SMS.

* Si les réponses automatiques sont activées, vérifiez que `SUBMIT_SM` a été envoyé au fournisseur. Si ce n&#39;est pas le cas, il est garanti qu&#39;un message d&#39;erreur se trouvera dans les logs de processus SMS.

* Si le `SUBMIT_SM MT PDU` contenant la réponse se trouve dans les traces mais que le SMS ne parvient pas au téléphone portable, vous devez contacter le fournisseur pour obtenir de l&#39;aide sur la résolution des problèmes.

## Problème lors de la préparation de la diffusion sans exclure les destinataires mis en quarantaine (mis en quarantaine par la fonction de réponse automatique) {#issue-delivery-preparation}

* Vérifiez que le format du numéro de téléphone est exactement le même dans la table de quarantaine et dans le log de diffusion. Si ce n&#39;est pas le cas, consultez cette [section](sms-protocol.md#automatic-reply) si vous rencontrez des problèmes avec le préfixe plus du format de numéro de téléphone international.

* Vérifiez les numéros courts. Des exclusions peuvent se produire si le numéro court du destinataire est identique à celui défini dans le compte externe ou s&#39;il est vide (vide = tout numéro court). Si un seul numéro court est utilisé pour l&#39;ensemble de l&#39;instance Adobe Campaign, il est plus facile de laisser tous les champs de **numéro court** vides.

## Problèmes d&#39;encodage {#encoding-issues}

**Étape 1 : Contacter le fournisseur**

Contactez-le et vérifiez la nature du problème rencontré de son côté. Il devrait pouvoir vous dire si le problème est de son côté ou de celui d&#39;Adobe Campaign. Si le problème concerne Adobe Campaign, il devrait être en mesure de préciser exactement le champ incorrect.

**Étape 2 : Connaître le contenu de votre message**

Unicode permet de nombreuses variantes pour les caractères identiques et Adobe Campaign ne peut pas toutes les gérer.

La source de problèmes la plus courante est le copier-coller d&#39;un traitement de texte, qui transforme les caractères habituels en versions typographiques correctes : espaces changés en espaces insécables, guillemets doubles changés en guillemets ouvrants et fermants, signes moins changés en différents types de tirets, etc.

Ne copiez pas et ne collez pas votre message lors du test, saisissez-le toujours directement dans l&#39;interface.

Avec le format hexadécimal, vous pouvez faire la différence entre des caractères similaires. Un L minuscule, un I majuscule, un O, un 0, les différents types de guillemets, les encodages non latins ou même les différents types d&#39;espaces peuvent tous avoir le même aspect ou ne pas s&#39;afficher du tout.

Pour convertir les codes unicode en hexadécimal, vous pouvez utiliser des outils en ligne tels que le site Web [Convertisseur de code unicode](https://r12a.github.io/app-conversion/). Saisissez votre texte, assurez-vous qu&#39;il n&#39;existe pas d&#39;informations d&#39;identification personnelle telles que des numéros de téléphone, puis cliquez sur **Convertir**. Les valeurs hexadécimales se trouvent en bas (zone UTF-32).

Lors de l&#39;ouverture de tickets concernant les problèmes d&#39;encodage, que ce soit avec le fournisseur ou l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), incluez toujours une version hexadécimale de ce que vous saisissez et de ce que vous voyez.

**Étape 3 : Savoir ce que vous devez envoyer**

Déterminez l&#39;encodage que vous prévoyez d&#39;utiliser et recherchez en ligne son tableau de caractères. Vérifiez que les caractères que vous avez l&#39;intention d&#39;envoyer sont réellement disponibles dans la page de code cible. Vérifiez que le champ `data_coding` est correct et correspond à ce que vous et le fournisseur attendez.

**Étape 4 : Connaître ce que vous avez effectivement envoyé**

Vous aurez besoin du résultat du débogage du connecteur pour voir exactement les octets à envoyer au fournisseur. Les problèmes d&#39;encodage apparaissent dans `SUBMIT_SM PDU`, veillez donc à les capturer. Envoyez des messages très distincts qui sont faciles à trouver dans le log.

Envoyez différents types de caractères spéciaux lors du test. Par exemple, l&#39;encodage GSM7 comporte des caractères étendus qui sont particulièrement distincts dans leur forme hexadécimale. Ils sont faciles à repérer puisqu&#39;ils n&#39;apparaissent dans aucun autre encodage.

## Éléments à inclure lors de la communication sur un problème SMS {#element-include}

Chaque fois que vous cherchez de l&#39;aide sur une question de SMS, que ce soit en ouvrant un ticket d&#39;assistance à Adobe Campaign, au fournisseur de SMS, ou tout autre type de communication sur la question, vous devrez inclure les informations suivantes pour vous assurer qu&#39;elle sera correctement qualifiée. Des problèmes correctement qualifiés sont essentiels pour résoudre les problèmes plus rapidement.

* **Activez les messages SMPP de verbose** lorsque le problème apparaît. La plupart des problèmes de SMS sont impossibles à résoudre sans cela.

* Si le problème est lié au trafic SMS, contactez d&#39;abord le fournisseur. Sa plateforme est la mieux adaptée pour un diagnostic efficace des problèmes de trafic SMS en temps réel.

* Incluez une description brève mais factuelle du problème.

* Incluez une description du résultat attendu.

* Incluez les commentaires du fournisseur.

* Incluez les logs et/ou les captures réseau appropriés. Lorsque vous effectuez des captures, veillez à reproduire le problème pendant ces captures.

* Si vous incluez des logs, des traces ou des captures, indiquez l&#39;emplacement exact dans le fichier lorsque le problème apparaît.

* Si vous référencez des messages, des PDU ou des logs, indiquez clairement la date et l&#39;heure pour les rendre plus faciles à trouver.

* Essayez de reproduire le problème sur un environnement de test. Si vous n&#39;êtes pas sûr d&#39;un paramètre, essayez-le sur l&#39;environnement de test et vérifiez le résultat avec les traces SMPP. Il est généralement préférable de signaler les problèmes reproduits dans les environnements de test que de les signaler directement dans les environnements de production.

* Incluez les modifications ou les ajustements apportés sur la plateforme. Incluez également toute modification que le fournisseur peut avoir apportée de son côté.

### Capture réseau {#network-capture}

Une capture réseau n’est pas toujours nécessaire, en général les messages SMPP en mode verbeux sont suffisants. Voici quelques directives qui vous aideront à déterminer si une capture réseau est nécessaire :

* Problèmes de connexion, mais les messages en mode verbose n&#39;affichent aucun `BIND_RESP PDU`.

* Déconnexions inexpliquées sans message d&#39;erreur, comportement habituel du connecteur lorsqu&#39;il détecte une erreur de protocole de bas niveau.

* Le fournisseur se plaint du processus de déconnexion / déconnexion.

* Problèmes d&#39;encodage dans les champs facultatifs TLV.

* Il est possible qu&#39;il y ait un trafic mixte entre les différentes connexions.

Dans toutes les autres situations, essayez d&#39;abord d&#39;analyser les messages SMPP en mode verbeux et de demander une capture réseau uniquement si des informations manquent dans les logs de mode verbeux.

Dans certains cas, la capture du trafic réseau n&#39;est pas nécessaire. Voici les situations les plus courantes :

* TLS activé : par définition, le trafic TLS est chiffré, et il ne peut pas être capturé.

* Problèmes de performances : les logs contiennent toutes les informations nécessaires pour tracer les problèmes de performance.

* Problèmes de minutage (`retry timing`, `enquire_link` période, limitation du débit, etc.)

* Analyse et traitement SR : les logs explicites offrent beaucoup plus de contexte et une meilleure présentation.

* Traitement MO (réponses automatiques, quarantaine).

* Erreurs n&#39;impliquant pas de trafic SMPP réel : préparation de la diffusion, problèmes d&#39;API du Message Center, problèmes de workflow, etc.

## Activation des traces SMPP {#enabling-smpp-traces}

Le nouveau connecteur prend en charge la connexion étendue via les traces : SMPP. Les traces sont générées dans le log MTA, et non dans la sortie standard.

**Activation par compte externe (méthode préférée)**

1. Dans le **compte externe**, cochez **Activer les traces SMPP en mode verbeux dans le fichier journal**.
1. Patientez 10 minutes pour permettre au serveur de recharger les comptes externes.

Il doit alors être actif.

**Activation dans la configuration**

Dans le fichier `config-instance.xml`, définissez les paramètres suivants :

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Vérification du nombre de connexions ouvertes sur un conteneur {#open-connections}

Pour vérifier le nombre de connexions ouvertes sur un conteneur, vous pouvez utiliser la commande suivante :

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Cela liste le nombre de connexions ouvertes pour un port donné. Nous utilisons ici le port 3600.

Le résultat doit être le suivant :

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 ont ouvert des connexions pour le processus SMS et 2 par enfant MTA avec 5 enfants.

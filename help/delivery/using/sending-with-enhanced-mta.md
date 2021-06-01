---
product: campaign
title: Envoi d'emails avec le MTA amélioré dans Adobe Campaign Classic
description: Découvrez la portée et les spécificités de l'envoi d'emails avec le MTA amélioré d'Adobe Campaign.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1991'
ht-degree: 100%

---

# Envoi d&#39;emails avec le MTA amélioré {#sending-with-enhanced-mta}

Le **MTA amélioré d&#39;Adobe Campaign** (Mail Transfer Agent) fournit une infrastructure d&#39;envoi mise à niveau qui permet d&#39;améliorer les performances en matière de délivrabilité, de réputation, de débit, de reporting, de gestion des rebonds, de montée en charge des adresses IP et de gestion des paramètres de connexion.

Il est implémenté pour améliorer l&#39;évolutivité, augmenter le débit de diffusion et envoyer plus rapidement un plus grand nombre d&#39;emails. Ces améliorations sont possibles grâce à de nouvelles techniques de diffusion adaptatives qui modifient en temps réel les paramètres d’envoi des emails en fonction des retours des fournisseurs d’accès à Internet.

>[!IMPORTANT]
>
>Le MTA amélioré d&#39;Adobe Campaign est uniquement disponible pour les clients Campaign Classic hébergés ou hybrides. Les installations on-premise de Campaign Classic ne peuvent pas être mises à niveau en vue d’utiliser le MTA amélioré.

Si votre instance de Campaign Classic a été provisionnée après le mois de septembre 2018, vous utilisez le MTA amélioré. Pour tous les autres clients Campaign Classic, consultez le [Forum aux questions](#enhanced-mta-faq) ci-dessous.

L’implémentation du MTA amélioré peut avoir un impact sur certaines fonctionnalités Campaign existantes. Voir à ce sujet la section [Spécificités du MTA amélioré](#enhanced-mta-impacts).

>[!NOTE]
>
>Si vous êtes un utilisateur final d’Adobe Campaign et que vous souhaitez déterminer si votre instance a été mise à niveau vers le MTA amélioré, contactez votre administrateur Campaign interne.

## Forum aux questions {#enhanced-mta-faq}

### Utilisation et avantages

**Qu’est-ce que le MTA amélioré ?**

Adobe Campaign peut maintenant être mis à niveau en vue d’utiliser un nouveau MTA (Mail Transfer Agent) qui exécute le MTA d&#39;email commercial de SparkPost appelé **Momentum**.

Momentum offre une technologie MTA innovante et extrêmement performante. Elle comprend une gestion des retours plus intelligente et une fonctionnalité d&#39;optimisation de la délivrabilité automatisée qui aide les expéditeurs à atteindre et à maintenir des taux de remise optimaux aux boîtes de réception.<!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Quels sont les avantages ?**

* Les clients Adobe Campaign qui utilisent le MTA amélioré ont vu une <!--300%-->augmentation importante de la vitesse de débit globale et une <!--90%+-->réduction significative des soft bounces.
* Le MTA amélioré utilise la dernière technologie MTA pour vous offrir des vitesses de débit optimales pour votre diffusion par email.
* En s&#39;adaptant instantanément et automatiquement aux retours qu&#39;il reçoit, il garantit également une diffusion par email plus précise et plus intelligente avec des données de diffusion en temps réel.

**Puis-je utiliser simultanément le MTA natif d&#39;Adobe Campaign et le MTA amélioré ?**

Non. Seul le MTA amélioré peut être utilisé pour vos diffusions par email après la mise à niveau de votre instance.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Mise à niveau vers le MTA amélioré

**Que faut-il faire pour effectuer la mise à niveau vers le MTA amélioré ?**

Si votre instance de Campaign Classic a été provisionnée après le mois de septembre 2018, aucune action n’est requise, car vous utilisez déjà le MTA amélioré.

Pour tous les autres clients hébergés ou partiellement hébergés (hybrides), l’équipe d&#39;Adobe Campaign fixera une date de migration et fournira des détails sur les étapes appropriées nécessaires à la migration.

>[!IMPORTANT]
>
>Le MTA amélioré n’est pas disponible pour les installations on-premise.

**Quel est le processus de mise à niveau de mon instance vers le MTA amélioré ?**

Pour vos instances hébergées, le processus complet nécessite quelques minutes de temps d’arrêt. Adobe surveillera le débit et la délivrabilité des emails jusqu&#39;à 24 heures après la mise à niveau afin d&#39;évaluer les impacts sur vos diffusions par email.

Si des problèmes sont détectés, Adobe peut rapidement et temporairement rétablir votre instance vers le MTA natif d&#39;Adobe Campaign.

Actuellement, le MTA amélioré affecte uniquement le canal email. Vos notifications push et diffusions SMS continueront à utiliser le MTA natif de Campaign et ne seront en aucune façon affectés par la mise à niveau.

**Dois-je suivre à nouveau le processus de rodage des adresses IP après la mise à niveau vers le MTA amélioré ?**

Non. La mise à niveau n’exige pas de basculer vers de nouvelles adresses IP. Vous pouvez donc continuer à utiliser vos adresses IP d&#39;email rodées.

**La mise à niveau vers le MTA amélioré aura-t-elle un impact sur les campagnes ou les diffusions en cours ?**

Toutes les diffusions qui ont été préparées avant la mise à niveau de votre instance en vue d’utiliser le MTA amélioré devront être repréparées afin d’utiliser correctement le nouveau MTA.

Pour les clients qui utilisent la fonctionnalité de messagerie transactionnelle d&#39;Adobe Campaign, tout appel d’API pour déclencher un email sera mis en file d’attente pendant la très courte période de temps d’arrêt de la mise à niveau et sera réessayé une fois la mise à niveau terminée.

## Spécificités du MTA amélioré {#enhanced-mta-impacts}

### En-têtes du MTA amélioré

Les dernières instances de Campaign Classic incluent du code qui ajoute les en-têtes du MTA amélioré requis à chaque message. Si vous utilisez Adobe Campaign 19.1 (build 9032) ou une version ultérieure et que ce n’est pas le cas, vous devez demander à l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) d’ajouter le paramètre &quot;useMomentum=true&quot; à votre configuration d’instance d’exécution (dans le fichier [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)), qui peut être une instance marketing, une [instance de mid-sourcing](../../installation/using/mid-sourcing-server.md) ou une [instance d’exécution de messages transactionnelle](../../message-center/using/configuring-instances.md#execution-instance), selon votre configuration.

Cependant, si vous utilisez une instance plus ancienne qui n’inclut pas ce code, une nouvelle règle de typologie nommée **[!UICONTROL Règle de typologie pour les MTA améliorés]** doit être ajoutée à toutes les typologies existantes de votre instance Campaign.
Cette règle est ajoutée par un package de **[!UICONTROL typologie]** installé dans le cadre de la mise à niveau vers le MTA amélioré.

>[!IMPORTANT]
>
>Si cette règle de typologie apparaît dans vos typologies, ne la supprimez ni ne la modifiez en aucune manière. Dans le cas contraire, vos diffusions par email pourraient être affectées.

Ce package de **[!UICONTROL typologie]** doit être installé sur l’instance marketing d&#39;Adobe Campaign.

Si vous êtes un client hybride, l’équipe d&#39;Adobe Campaign vous fournira des instructions sur la façon d’installer le package de **[!UICONTROL typologie]** sur votre instance marketing dans le cadre de la mise à niveau vers le MTA amélioré. Contactez votre chargé de compte pour obtenir toutes les instructions.

>[!IMPORTANT]
>
>Les instructions fournies par l’équipe d&#39;Adobe Campaign sur la façon d’installer le package de **[!UICONTROL typologie]** doivent être soigneusement suivies. Sinon, vous risquez de rencontrer des problèmes majeurs avec les adresses IP utilisées pour envoyer des emails.

Pour en savoir plus sur les typologies, consultez [cette section](../../campaign/using/about-campaign-typologies.md).

### Nouvelles règles MX

Les règles de débit de diffusion de gestion des MX ne sont plus utilisées. Le MTA amélioré dispose de ses propres règles MX. Il peut ainsi personnaliser le débit par domaine en fonction de votre réputation, basée sur l&#39;historique des emails et les commentaires en temps réel provenant des domaines auxquels vous adressez des emails.

Pour en savoir plus à propos de la configuration des MX, voir [cette section](../../installation/using/email-deliverability.md#mx-configuration).

### Qualification des retours

Les qualifications des retours dans la table **[!UICONTROL Qualification des logs de diffusion]** Campaign ne sont plus utilisées pour les messages d’erreur relatifs aux échecs des diffusions **synchrones**. Le MTA amélioré détermine le type et la qualification de retour, puis renvoie ces informations à Campaign.

>[!NOTE]
>
>Le MTA amélioré qualifie le retour SMTP et envoie cette qualification à Campaign sous la forme d’un code de retour mappé à un motif et à une qualification de retour Campaign.

Pour plus d’informations sur la qualification des retours, consultez [cette section](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Débit des diffusions

Le graphique du débit des diffusions de Campaign n&#39;affiche plus le débit vers vos destinataires d&#39;emails. Il indique maintenant la vitesse de débit pour le relais de vos messages entre Campaign et le MTA amélioré.

Pour plus d’informations sur le débit de diffusion, consultez [cette section](../../reporting/using/global-reports.md#delivery-throughput).

### Période de validité

Le paramètre de la période de validité dans vos diffusions Campaign ne sera utilisé par le MTA amélioré que s’il est défini sur **3,5 jours ou moins**. Si vous définissez une valeur supérieure à 3,5 jours dans Campaign, elle ne sera pas prise en compte.

Par exemple, si la période de validité est définie sur la valeur par défaut de 5 jours dans Campaign, les messages soft bounce seront placés dans la file d’attente de reprise du MTA amélioré et ne feront l’objet d’une reprise que pendant 3,5 jours à compter du moment où ils ont atteint le MTA amélioré. Dans ce cas, la valeur définie dans Campaign ne sera pas utilisée.

Une fois qu’un message figure dans la file d’attente du MTA amélioré depuis 3,5 jours et qu’il n’a pas été diffusé, il expire et son état est mis à jour de **[!UICONTROL Envoi]** à **[!UICONTROL Échec]** dans les logs de diffusion.

Pour plus d’informations sur la période de validité, consultez [cette section](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### Signature DKIM

La signature d’authentification par email DKIM (DomainKeys Identified Mail) est effectuée par l’MTA amélioré. Dans le cadre de la mise à niveau vers le MTA amélioré, la signature DKIM par le MTA natif de Campaign sera désactivée dans la table Gestion des domaines.
Pour en savoir plus sur la signature DKIM, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=fr#authentication).

### Rapports de réussite de diffusion

Dans la vue **[!UICONTROL Résumé]** du [tableau de bord](../../delivery/using/delivery-dashboard.md) d&#39;une diffusion email, le pourcentage **[!UICONTROL Succès]** débute à 100 %, puis diminue progressivement tout au long de la [période de validité](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period) de la diffusion, à mesure que les erreurs soft et hard bounces font l&#39;objet de rapports du MTA amélioré vers Campaign.

En effet, tous les messages s&#39;affichent comme **[!UICONTROL Envoyés]** dans les [logs d&#39;envoi](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) dès qu&#39;ils sont correctement relayés de Campaign vers le MTA amélioré. Ils restent dans cet état à moins ou jusqu’à ce qu’un [bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) pour ce message soit communiqué de nouveau de la MTA améliorée à Campaign.

Lorsque les messages hard bounce sont renvoyés du MTA amélioré, leur état passe de **[!UICONTROL Envoyés]** à **[!UICONTROL En échec]** et le pourcentage **[!UICONTROL Succès]** diminue en conséquence.

Lorsque les messages soft bounce sont renvoyés du MTA amélioré, ils apparaissent toujours comme **[!UICONTROL Envoyés]** et le pourcentage **[!UICONTROL Succès]** n&#39;est pas encore mis à jour. L&#39;envoi des messages soft bounce fait ensuite l&#39;objet de [reprises](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) tout au long de la période de validité de la diffusion :

* Si une reprise est effectuée avec succès avant la fin de la période de validité, l&#39;état du message reste **[!UICONTROL Envoyé]** et le pourcentage **[!UICONTROL Succès]** reste le même.

* Dans le cas contraire, l&#39;état devient **[!UICONTROL En échec]** et le pourcentage **[!UICONTROL Succès]** diminue en conséquence.

Par conséquent, vous devez attendre la fin de la période de validité pour voir le pourcentage **[!UICONTROL Succès]** final et le nombre final de messages réellement **[!UICONTROL Envoyés]** et en **[!UICONTROL En échec]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Service de commentaires par email (bêta) {#email-feedback-service}

Grâce à la fonctionnalité Service de commentaires par email (EFS), l&#39;état de chaque email est signalé avec précision, car les commentaires sont capturés directement depuis le MTA (Message Tranfer Agent) amélioré.

>[!IMPORTANT]
>
>Le service de commentaires par email est actuellement disponible en version bêta.
>
>Si vous souhaitez participer à ce programme Bêta, remplissez [ce formulaire](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) et nous vous recontacterons.

Une fois la diffusion lancée, le pourcentage **[!UICONTROL Succès]** n&#39;est plus modifié lorsque le message est relayé avec succès de Campaign vers le MTA amélioré.

<!--![](assets/efs-sending.png)-->

Les logs de diffusion affichent le statut **[!UICONTROL Pris en compte par le prestataire]** pour chaque adresse ciblée.

<!--![](assets/efs-pending.png)-->

Lorsque le message est effectivement diffusé aux profils ciblés et que ces informations sont renvoyées en temps réel du MTA amélioré, les logs de diffusion affichent l&#39;état **[!UICONTROL Envoyés]** pour chaque adresse ayant reçu le message avec succès. Le pourcentage **[!UICONTROL Succès]** augmente en conséquence lorsqu&#39;une diffusion est effectuée avec succès.

Lorsque des messages hard bounce sont signalés depuis le MTA amélioré, leur statut de log passe de **[!UICONTROL Pris en compte par le prestataire]** à **[!UICONTROL En échec]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Lorsque des messages soft bounce sont signalés depuis le MTA amélioré, leur statut de log reste inchangé (**[!UICONTROL pris en compte par le prestataire]**) : seule la [raison de l’erreur](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) est mise à jour<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. Le pourcentage **[!UICONTROL Succès]** reste inchangé. L&#39;envoi des messages soft bounce fait ensuite l&#39;objet de reprises tout au long de la [période de validité](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period) de la diffusion :

* Si une reprise est effectuée avec succès avant la fin de la période de validité, l’état du message passe à **[!UICONTROL Envoyé]** et le pourcentage **[!UICONTROL Succès]** augmente en conséquence.

* Sinon, l’état devient **[!UICONTROL Échec]**. Le <!--and **[!UICONTROL Bounces + errors]** -->pourcentage **[!UICONTROL Succès]** reste inchangé.

>[!NOTE]
>
>Pour plus d&#39;informations sur les hard et soft bounces, voir [cette section](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Pour plus d&#39;informations sur les reprises après une diffusion temporairement en échec, voir [cette section](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


Les tableaux ci-après présentent les modifications des KPI et de l&#39;état des logs d&#39;envoi ajoutées par la fonctionnalité EFS.

**Avec le service de commentaires par email**

| Étape du processus d’envoi | Résumé des KPI | État des logs d&#39;envoi |
|--- |--- |--- |
| Le message est relayé avec succès de Campaign vers le MTA amélioré | Le pourcentage **[!UICONTROL Succès]** n’est pas affiché (démarre à 0 %) | Pris en compte par le prestataire |
| Les messages hard bounce sont renvoyés du MTA amélioré. | Aucun changement du pourcentage **[!UICONTROL Succès]** | En échec |
| Les messages soft bounce sont renvoyés du MTA amélioré. | Aucun changement du pourcentage **[!UICONTROL Succès]** | Pris en compte par le fournisseur de services |
| Les reprises des messages soft bounce sont effectuées avec succès | Le pourcentage **[!UICONTROL Succès]** augmente en conséquence | Envoyés |
| Échec des reprises des messages soft bounce | Aucun changement du pourcentage **[!UICONTROL Succès]** | En échec |

**Sans le service de commentaires par email**

| Étape du processus d’envoi | Résumé des KPI | État des logs d&#39;envoi |
|--- |--- |--- |
| Le message est relayé avec succès de Campaign vers le MTA amélioré | Le pourcentage **[!UICONTROL Succès]** commence à 100 % | Envoyés |
| Les messages hard bounce sont renvoyés du MTA amélioré. | Le pourcentage **[!UICONTROL Succès]** diminue en conséquence | En échec |
| Les messages soft bounce sont renvoyés du MTA amélioré. | Aucun changement du pourcentage **[!UICONTROL Succès]** | Envoyés |
| Les reprises des messages soft bounce sont effectuées avec succès | Aucun changement du pourcentage **[!UICONTROL Succès]** | Envoyés | Le pourcentage **[!UICONTROL Succès]** augmente en conséquence | Envoyés |
| Échec des reprises des messages soft bounce | Le pourcentage **[!UICONTROL Succès]** diminue en conséquence | En échec |

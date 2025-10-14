---
product: campaign
title: Envoyer avec le MTA amélioré dans Adobe Campaign Classic
description: Découvrez la portée et les spécificités de lʼenvoi dʼe-mails avec le MTA amélioré dʼAdobe Campaign.
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 98%

---

# Envoi d&#39;emails avec le MTA amélioré {#sending-with-enhanced-mta}

Le **MTA amélioré d&#39;Adobe Campaign** (Mail Transfer Agent) fournit une infrastructure d&#39;envoi mise à niveau qui permet d&#39;améliorer les performances en matière de délivrabilité, de réputation, de débit, de reporting, de gestion des rebonds, de montée en charge des adresses IP et de gestion des paramètres de connexion.

Il est implémenté pour améliorer l&#39;évolutivité, augmenter le débit de diffusion et envoyer plus rapidement un plus grand nombre d&#39;emails. Ces améliorations sont possibles grâce à de nouvelles techniques de diffusion adaptatives qui modifient en temps réel les paramètres d’envoi des emails en fonction des retours des fournisseurs d’accès à Internet.

>[!IMPORTANT]
>
>Le MTA amélioré d&#39;Adobe Campaign est uniquement disponible pour les clients Campaign Classic hébergés ou hybrides. Les installations on-premise de Campaign Classic ne peuvent pas être mises à niveau en vue d’utiliser le MTA amélioré.

Si votre instance de Campaign Classic a été provisionnée après le mois de septembre 2018, vous utilisez le MTA amélioré. Pour tous les autres clients Campaign Classic, consultez le [Forum aux questions](#enhanced-mta-faq) ci-dessous.

L’implémentation du MTA amélioré peut avoir un impact sur certaines fonctionnalités Campaign existantes. Voir à ce sujet la section [Spécificités du MTA amélioré](#enhanced-mta-impacts).

>[!NOTE]
>
>Si vous êtes un utilisateur final d’Adobe Campaign et que vous souhaitez déterminer si votre instance a été mise à niveau vers le MTA amélioré, contactez votre administrateur Campaign interne.

## Forum aux questions {#enhanced-mta-faq}

### Utilisation et avantages

**Qu’est-ce que le MTA amélioré ?**

Adobe Campaign peut maintenant être mis à niveau en vue d’utiliser un nouveau MTA (Mail Transfer Agent) qui exécute le MTA d’e-mail commercial de SparkPost appelé **Momentum**.

Momentum offre une technologie MTA innovante et extrêmement performante. Elle comprend une gestion des rebonds plus intelligente et une fonctionnalité d’optimisation de la délivrabilité automatisée qui aide les expéditeurs à atteindre et à maintenir des taux de remise optimaux aux boîtes de réception.<!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**Quels sont les avantages ?**

* Les clients Adobe Campaign qui utilisent le MTA amélioré ont vu une <!--300%-->augmentation importante de la vitesse de débit globale et une <!--90%+-->réduction significative des rebonds temporaires.
* Le MTA amélioré utilise la dernière technologie MTA pour vous offrir des vitesses de débit optimales pour votre diffusion par email.
* En s&#39;adaptant instantanément et automatiquement aux retours qu&#39;il reçoit, il garantit également une diffusion par email plus précise et plus intelligente avec des données de diffusion en temps réel.

**Puis-je utiliser simultanément le MTA natif d&#39;Adobe Campaign et le MTA amélioré ?**

Non. Seul le MTA amélioré peut être utilisé pour vos diffusions par email après la mise à niveau de votre instance.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Mise à niveau vers le MTA amélioré

**Que faut-il faire pour effectuer la mise à niveau vers le MTA amélioré ?**

Si votre instance de Campaign Classic a été provisionnée après le mois de septembre 2018, aucune action n’est requise, car vous utilisez déjà le MTA amélioré.

Pour tous les autres clients hébergés ou partiellement hébergés (hybrides), l’équipe d&#39;Adobe Campaign fixera une date de migration et fournira des détails sur les étapes appropriées nécessaires à la migration.

>[!IMPORTANT]
>
>Le MTA amélioré n’est pas disponible pour les installations on-premise.

**Quel est le processus de mise à niveau de mon instance vers le MTA amélioré ?**

Pour vos instances hébergées, le processus complet nécessite quelques minutes de temps d’arrêt. Adobe surveillera le débit et la délivrabilité des emails jusqu&#39;à 24 heures après la mise à niveau afin d&#39;évaluer les impacts sur vos diffusions par email.

Si des problèmes sont détectés, Adobe peut rapidement et temporairement rétablir votre instance vers le MTA natif d&#39;Adobe Campaign.

Actuellement, le MTA amélioré affecte uniquement le canal email. Vos notifications push et diffusions SMS continueront à utiliser le MTA natif de Campaign et ne seront en aucune façon affectés par la mise à niveau.

**Dois-je suivre à nouveau le processus de rodage des adresses IP après la mise à niveau vers le MTA amélioré ?**

Non. La mise à niveau n’exige pas de basculer vers de nouvelles adresses IP. Vous pouvez donc continuer à utiliser vos adresses IP d&#39;email rodées.

**La mise à niveau vers le MTA amélioré aura-t-elle un impact sur les campagnes ou les diffusions en cours ?**

Pour les clients et clientes qui utilisent la fonctionnalité de messagerie transactionnelle d&#39;Adobe Campaign, tout appel d’API pour déclencher un e-mail sera mis en file d’attente pendant la très courte période de temps d’arrêt de la mise à niveau et sera réessayé une fois la mise à niveau terminée.

## Spécificités du MTA amélioré {#enhanced-mta-impacts}

### Nouvelles règles MX

Les règles de débit de diffusion de gestion des MX ne sont plus utilisées. Le MTA amélioré dispose de ses propres règles MX. Il peut ainsi personnaliser le débit par domaine en fonction de votre réputation, en fonction de l’historique des e-mails et des commentaires en temps réel provenant des domaines auxquels vous adressez des e-mails.

Pour en savoir plus à propos de la configuration des MX, voir [cette section](../../installation/using/email-deliverability.md#mx-configuration).

### Qualification des rebonds

Les qualifications des rebonds dans la table **[!UICONTROL Qualification des logs de diffusion]** Campaign ne sont plus utilisées pour les messages d’erreur relatifs aux échecs des diffusions **synchrones**. Le MTA amélioré détermine le type et la qualification de rebond, puis renvoie ces informations à Campaign.

>[!NOTE]
>
>Le MTA amélioré qualifie le rebond SMTP et envoie cette qualification à Campaign sous la forme d’un code de retour mappé à un motif et à une qualification de rebond Campaign.

Pour plus d’informations sur la qualification des rebonds, consultez [cette section](understanding-delivery-failures.md#bounce-mail-qualification).

### Diffusion

Une diffusion ne peut pas être arrêtée une fois qu’elle a été transférée au MTA amélioré, même si elle apparaît avec le statut **[!UICONTROL Arrêté]** dans Campaign.

### Débit des diffusions

Le graphique du débit des diffusions de Campaign n&#39;affiche plus le débit vers vos destinataires d&#39;emails. Il indique maintenant la vitesse de débit pour le relais de vos messages entre Campaign et le MTA amélioré.

Pour plus d’informations sur le débit de diffusion, consultez [cette section](../../reporting/using/global-reports.md#delivery-throughput).

### Reprises

Les paramètres de reprise lors de la diffusion ne sont pas utilisés par Campaign. Les reprises des soft bounces et l’intervalle qui les sépare sont déterminés par le MTA amélioré en fonction du type et de la gravité des réponses des rebonds provenant du domaine de messagerie du message.

Pour plus d’informations sur les reprises, consultez cette [page](communication-channels.md) sous **Envoi de diffusion** > **Configurer les reprises**.

### Période de validité

Le paramètre de la période de validité dans vos diffusions Campaign ne sera utilisé par le MTA amélioré que s’il est défini sur **3,5 jours ou moins**. Si vous définissez une valeur supérieure à 3,5 jours dans Campaign, elle ne sera pas prise en compte.

Par exemple, si la période de validité est définie sur la valeur par défaut de 5 jours dans Campaign, les messages soft bounce seront placés dans la file d’attente de reprise du MTA amélioré et ne feront l’objet d’une reprise que pendant 3,5 jours à compter du moment où ils ont atteint le MTA amélioré. Dans ce cas, la valeur définie dans Campaign ne sera pas utilisée.

Une fois qu’un message figure dans la file d’attente du MTA amélioré depuis 3,5 jours et qu’il n’a pas été diffusé, il expire et son état est mis à jour de **[!UICONTROL Envoi]** à **[!UICONTROL Échec]** dans les logs de diffusion.

Pour plus d’informations sur la période de validité, consultez cette [page](communication-channels.md) sous **Envoi de diffusion** > **Définir la période de validité**.

### Signature DKIM

La signature d’authentification par email DKIM (DomainKeys Identified Mail) est effectuée par l’MTA amélioré. Dans le cadre de la mise à niveau vers le MTA amélioré, la signature DKIM par le MTA natif de Campaign sera désactivée dans la table Gestion des domaines.
Pour en savoir plus sur la signature DKIM, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=fr#authentication).

### Rapports de réussite de diffusion

Dans la vue **[!UICONTROL Résumé]** du [tableau de bord](delivery-dashboard.md) d’une diffusion par e-mail, le pourcentage **[!UICONTROL Succès]** débute à 100 %, puis diminue progressivement tout au long de la [période de validité](communication-channels.md) de la diffusion, à mesure que les rebonds temporaires et définitifs font l’objet de rapports du MTA amélioré vers Campaign.

En effet, tous les messages s&#39;affichent comme **[!UICONTROL Envoyés]** dans les [logs d&#39;envoi](delivery-dashboard.md#delivery-logs-and-history) dès qu&#39;ils sont correctement relayés de Campaign vers le MTA amélioré. Ils restent dans cet état à moins ou jusqu’à ce qu’un [rebond &#x200B;](understanding-delivery-failures.md#delivery-failure-types-and-reasons) pour ce message soit communiqué de nouveau de la MTA améliorée à Campaign.

Lorsque les messages hard bounce sont renvoyés du MTA amélioré, leur état passe de **[!UICONTROL Envoyés]** à **[!UICONTROL En échec]** et le pourcentage **[!UICONTROL Succès]** diminue en conséquence.

Lorsque les messages soft bounce sont renvoyés du MTA amélioré, ils apparaissent toujours comme **[!UICONTROL Envoyés]** et le pourcentage **[!UICONTROL Succès]** n&#39;est pas encore mis à jour. L&#39;envoi des messages soft bounce fait ensuite l&#39;objet de [reprises](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) tout au long de la période de validité de la diffusion :

* Si une reprise est effectuée avec succès avant la fin de la période de validité, l&#39;état du message reste **[!UICONTROL Envoyé]** et le pourcentage **[!UICONTROL Succès]** reste le même.

* Dans le cas contraire, l&#39;état devient **[!UICONTROL En échec]** et le pourcentage **[!UICONTROL Succès]** diminue en conséquence.

Par conséquent, vous devez attendre la fin de la période de validité pour voir le pourcentage **[!UICONTROL Succès]** final et le nombre final de messages réellement **[!UICONTROL Envoyés]** et en **[!UICONTROL En échec]**.

Le tableau ci-dessous présente les différentes étapes du processus d’envoi avec les KPI et les statuts des envois correspondants.

| Étape du processus d’envoi | Résumé des KPI | État des logs d&#39;envoi |
|--- |--- |--- |
| Le message est relayé avec succès de Campaign vers le MTA amélioré | Le pourcentage **[!UICONTROL Succès]** commence à 100 % | Envoyés |
| Les messages hard bounce sont renvoyés du MTA amélioré. | Le pourcentage **[!UICONTROL Succès]** diminue en conséquence. | En échec |
| Les messages soft bounce sont renvoyés du MTA amélioré. | Aucun changement du pourcentage **[!UICONTROL Succès]**. | Envoyés |
| Les reprises des messages soft bounce sont effectuées avec succès | Aucun changement du pourcentage **[!UICONTROL Succès]**. | Envoyés | Le pourcentage **[!UICONTROL Succès]** augmente en conséquence. | Envoyés |
| Échec des reprises des messages soft bounce | Le pourcentage **[!UICONTROL Succès]** diminue en conséquence. | En échec |


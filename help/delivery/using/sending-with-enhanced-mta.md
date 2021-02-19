---
solution: Campaign Classic
product: campaign
title: Envoi avec la MTA améliorée à Adobe Campaign Classic
description: Découvrez l'étendue et les spécificités de l'envoi de courriels avec l'accord de confidentialité amélioré Adobe Campaign.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 07ed17a093cb6fb2d7aae376325a127c61b1dcc2
workflow-type: tm+mt
source-wordcount: '1427'
ht-degree: 8%

---


# Envoi avec la MTA améliorée {#sending-with-enhanced-mta}

Le **MTA amélioré d&#39;Adobe Campaign** (Agent de transfert de courrier) fournit une infrastructure d&#39;envoi améliorée permettant une meilleure délivrabilité, réputation, débit, rapports, gestion des rebonds, amélioration de l&#39;adresse IP et gestion des paramètres de connexion.

Il est mis en oeuvre pour améliorer l&#39;évolutivité, augmenter le débit des diffusions et aider à envoyer plus de courriers électroniques plus rapidement. Ceci est réalisé avec de nouvelles techniques de diffusion adaptative qui modifient les paramètres d’envoi de courrier électronique en temps réel en fonction des commentaires des Prestataires Internet.

>[!IMPORTANT]
>
>La MTA Adobe Campaign Enhanced est uniquement disponible pour les clients hébergés ou hybrides Campaign Classic. Les installations sur site des Campaign Classic ne peuvent pas être mises à niveau pour utiliser la MTA améliorée.

Si une instance de Campaign Classic a été configurée après septembre 2018, vous utilisez la MTA améliorée. Pour tous les autres clients Campaign Classic, consultez la [Foire aux questions](#enhanced-mta-faq) ci-dessous.

L’implémentation améliorée de la MTA peut avoir un impact sur certaines fonctionnalités Campaign existantes. Pour en savoir plus sur ce sujet, voir les [Spécifications MTA améliorées](#enhanced-mta-impacts).

## Forum aux questions {#enhanced-mta-faq}

### Utilisation et avantages

**Qu’est-ce que l’AMT améliorée ?**

Adobe Campaign peut désormais être mis à niveau pour utiliser un nouveau MTA (Mail Transfer Agent) qui exécute le courrier électronique commercial de SparkPost appelé **Momentum**.

Momentum représente une technologie MTA innovante et hautement performante qui comprend une gestion plus intelligente des rebonds et une capacité d&#39;optimisation automatisée de la délivrabilité qui aide les expéditeurs à atteindre et à maintenir des taux de diffusion optimaux de boîte de réception. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Quels sont les avantages ?**

* Les clients Adobe Campaign utilisant l&#39;AMT amélioré ont vu une <!--300%-->augmentation massive de la vitesse de débit globale et une <!--90%+-->réduction significative des rebonds doux.
* La MTA améliorée utilise la dernière technologie MTA pour vous offrir des vitesses de débit optimales pour votre diffusion de messagerie.
* En s&#39;adaptant instantanément et automatiquement aux commentaires qu&#39;il reçoit, il garantit également une diffusion de courriel plus précise et plus intelligente avec des données de diffusion en temps réel.

**Puis-je utiliser simultanément les MTA natifs Adobe Campaign et les MTA amélioré ?**

Non. Seule la MTA améliorée peut être utilisée pour vos diffusions de messagerie après la mise à niveau de votre instance.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Mise à niveau vers la MTA améliorée

**Que faut-il faire pour effectuer la mise à niveau vers la MTA améliorée ?**

Si une instance de Campaign Classic a été configurée après septembre 2018, aucune action n’est requise, car vous utilisez déjà la MTA améliorée.

Pour tous les autres clients hébergés ou partiellement hébergés (hybrides), l’équipe Adobe Campaign tentera de coordonner une date de migration et fournira des détails sur les étapes appropriées nécessaires à la migration.

>[!IMPORTANT]
>
>La MTA améliorée n’est pas disponible pour les installations sur site.

**Quel est le processus de mise à niveau de mon instance vers la MTA améliorée ?**

Le processus complet pour vos instances hébergées nécessite quelques minutes d’inactivité. Adobe surveillera le débit et la délivrabilité des courriers électroniques jusqu&#39;à 24 heures après la mise à niveau afin d&#39;évaluer tout impact sur vos diffusions de courrier électronique.

Si des problèmes sont détectés, l’Adobe peut rapidement et temporairement rétablir votre instance dans la MTA Adobe Campaign native.

Actuellement, la MTA améliorée affecte uniquement le canal de messagerie. Vos notifications Push et diffusions SMS continueront à utiliser le MTA natif de Campaign et ne seront en aucune façon affectés par la mise à niveau.

**Dois-je recommencer à utiliser le réchauffement d’IP après la mise à niveau vers la MTA améliorée ?**

Non. La mise à niveau n’exige pas de passer à de nouvelles adresses IP. Vous pouvez donc continuer à utiliser vos adresses IP de messagerie réchauffées existantes.

**La mise à niveau vers la MTA améliorée aura-t-elle un impact sur les campagnes ou les diffusions en cours ?**

Toutes les diffusions qui ont été préparées avant la mise à niveau de votre instance pour utiliser la MTA améliorée devront être repréparées pour utiliser correctement la nouvelle MTA.

Pour les clients qui utilisent la fonctionnalité de messagerie transactionnelle Adobe Campaign, tout appel d’API pour déclencher un courrier électronique sera mis en file d’attente pendant la très courte période d’interruption de la mise à niveau et sera tenté une fois la mise à niveau terminée.

## Spécifications MTA améliorées {#enhanced-mta-impacts}

### En-têtes MTA améliorés

Les dernières instances de Campaign Classic incluent du code qui ajoute les en-têtes MTA améliorés requis à chaque message. Si vous utilisez Adobe Campaign 19.1 (build 9032) ou version ultérieure et que ce n’est pas le cas, vous devez ajouter le paramètre &quot;useMomentum=true&quot; à votre configuration d’instance de marketing (dans le fichier [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)).

Cependant, si vous utilisez une instance plus ancienne qui n’inclut pas ce code, une nouvelle règle de typologie nommée **[!UICONTROL Règle de typologie pour les MTA améliorées]** doit être ajoutée à toutes les typologies existantes de votre instance Campaign.
Cette règle est ajoutée par un **[!UICONTROL package de typologie]** installé dans le cadre de la mise à niveau vers la MTA améliorée.

>[!IMPORTANT]
>
>Si cette règle de typologie apparaît dans vos typologies, ne la supprimez ni ne la modifiez en aucune manière. Dans le cas contraire, vos diffusions de messagerie pourraient être affectées.

Ce package **[!UICONTROL Typology]** doit être installé sur l’instance de marketing Adobe Campaign.

Si vous êtes un client hybride, l’équipe Adobe Campaign vous fournira des instructions sur la façon d’installer le package **[!UICONTROL typologie]** sur votre instance marketing dans le cadre de la mise à niveau vers la MTA améliorée. Contactez votre gestionnaire de compte pour obtenir toutes les instructions.

>[!IMPORTANT]
>
>Les instructions fournies par l’équipe Adobe Campaign sur la façon d’installer le package **[!UICONTROL Typology]** doivent être soigneusement suivies. Sinon, vous risquez de rencontrer des problèmes majeurs avec vos adresses IP utilisées pour envoyer des courriers électroniques.

Pour en savoir plus sur les typologies, voir [cette section](../../campaign/using/about-campaign-typologies.md).

### Nouvelles règles MX

Les règles de débit de la diffusion de gestion MX ne sont plus utilisées. La MTA améliorée dispose de ses propres règles MX qui lui permettent de personnaliser votre débit par domaine en fonction de votre propre réputation de courriel historique et des commentaires en temps réel provenant des domaines où vous envoyez des messages électroniques.

Pour en savoir plus à propos de la configuration des MX, voir [cette section](../../installation/using/email-deliverability.md#mx-configuration).

### Qualification de rebond

Les qualifications de rebond dans la table Campaign **[!UICONTROL qualification du journal de Diffusion]** ne sont plus utilisées pour les messages d&#39;erreur de diffusion **synchrone**. Le MTA amélioré détermine le type et la qualification de rebond, puis renvoie ces informations à Campaign.

>[!NOTE]
>
>La MTA améliorée qualifie le rebond SMTP et renvoie cette qualification à Campaign sous la forme d’un code de rebond mappé à un motif de rebond Campaign et à une qualification.

Pour en savoir plus sur la qualification des rebonds, voir [cette section](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### État envoyé avec MTA amélioré

Dans la vue **[!UICONTROL Résumé]** d&#39;une diffusion de courriel [tableau de bord](../../delivery/using/delivery-dashboard.md), le pourcentage **[!UICONTROL Succès]** début à 100 %, puis diminue progressivement tout au long de la diffusion [période de validité](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), lorsque les rebonds soft et hard sont reportés de l&#39;ATM amélioré.

En effet, tous les messages s’affichent sous la forme **[!UICONTROL Envoyé]** dans les journaux [d’envoi](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) dès qu’ils sont correctement relayés de Campaign vers l’AMT amélioré. Ils restent dans ce statut à moins ou jusqu’à ce qu’un [bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) pour ce message soit communiqué de nouveau de la MTA améliorée à Campaign.

Lorsque des messages rebondissants sont signalés à partir de la MTA améliorée, leur état passe de **[!UICONTROL Envoyé]** à **[!UICONTROL Échec]** et le pourcentage **[!UICONTROL Succès]** est diminué en conséquence.

Lorsque les messages rebondissant à l’écran sont renvoyés à partir de la MTA améliorée, ils apparaissent toujours sous la forme **[!UICONTROL Envoyé]** et le pourcentage **[!UICONTROL Succès]** n’est pas encore mis à jour. L&#39;envoi des messages soft bounces est ensuite [réessayé](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) tout au long de la période de validité de la diffusion :

* Si une nouvelle tentative a réussi avant la fin de la période de validité, l’état du message reste **[!UICONTROL Envoyé]** et le pourcentage **[!UICONTROL Succès]** reste inchangé.

* Sinon, l’état devient **[!UICONTROL Échec]** et le pourcentage **[!UICONTROL Succès]** est diminué en conséquence.

Par conséquent, vous devez attendre la fin de la période de validité pour voir le pourcentage final **[!UICONTROL Succès]** et le nombre final de **[!UICONTROL Envoyé]** et **[!UICONTROL Échec]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Débit des diffusions

Le graphique de débit de la Diffusion Campaign n&#39;affiche plus le débit de vos destinataires de messagerie. Ce graphique montre maintenant la vitesse de transmission de vos messages de Campaign vers le MTA amélioré.

Pour plus d&#39;informations sur le débit des diffusions, voir [cette section](../../reporting/using/global-reports.md#delivery-throughput).

### Période de validité

Le paramètre de la période de validité dans vos diffusions Campaign ne sera utilisé par la MTA améliorée que s’il est défini sur **3,5 jours ou moins**. Si vous définissez une valeur supérieure à 3,5 jours à Campaign, elle ne sera pas prise en compte.

Par exemple, si la période de validité est définie sur la valeur par défaut de 5 jours dans Campaign, les messages rebondissants seront placés dans la file d’attente des nouvelles tentatives MTA améliorées et ne seront retentés que pendant 3,5 jours à compter du moment où ce message a atteint la MTA améliorée. Dans ce cas, la valeur définie dans Campaign ne sera pas utilisée.

Une fois qu’un message figure dans la file d’attente du MTA amélioré depuis 3,5 jours et qu’il n’a pas été diffusé, il expire et son état est mis à jour de **[!UICONTROL Envoi]** à **[!UICONTROL Échec]** dans les logs de diffusion.

Pour en savoir plus sur la période de validité, voir [cette section](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### Signature DKIM

La signature de l’authentification par courrier électronique DKIM (DomainKeys Identified Mail) est effectuée par l’AMT améliorée. Dans le cadre de la mise à niveau vers le MTA amélioré, la signature DKIM par le MTA natif de Campaign sera désactivée dans la table Gestion des domaines.
Pour en savoir plus sur DKIM, voir [cette section](../../delivery/using/technical-recommendations.md#dkim).
---
title: Contrôler une diffusion
seo-title: Contrôler une diffusion
description: Contrôler une diffusion
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 537cbdec1ec88da1c759f6ca8eafe383c55a61d3
workflow-type: tm+mt
source-wordcount: '2679'
ht-degree: 96%

---


# Contrôler une diffusion{#monitoring-a-delivery}

Le **tableau de bord des diffusions** est la clé pour suivre les diffusions et les erreurs éventuelles rencontrées lors de l&#39;envoi des messages.

**Rubriques connexes :**

* [Comprendre les diffusions en échec](../../delivery/using/understanding-delivery-failures.md)
* [Comprendre la gestion des quarantaines](../../delivery/using/understanding-quarantine-management.md)
* [Bonnes pratiques de diffusion](https://helpx.adobe.com/fr/campaign/kb/delivery-best-practices.html)
* [Gestion de la délivrabilité](../../delivery/using/about-deliverability.md)

## Tableau de bord de la diffusion {#delivery-dashboard}

Pour consulter les informations relatives à une diffusion, éditez-la, consultez son tableau de bord et cliquez sur les onglets disponibles.

Le contenu de ces onglets n&#39;est plus modifiable lorsque la diffusion a été envoyée.

![](assets/s_ncs_user_del_details.png)

### Synthèse des diffusions (Delivery summary){#delivery-summary}

L&#39;onglet **[!UICONTROL Résumé]** contient les caractéristiques de la diffusion : état de la diffusion, canal utilisé, informations sur l&#39;expéditeur, objet, informations relatives à l&#39;exécution. Voir à ce sujet la section [Nombre de messages envoyés](#number-of-messages-sent).

Le lien **[!UICONTROL Rapports]** permet de consulter un ensemble de rapports relatifs à l&#39;action de diffusion : rapport général d&#39;envoi, rapport détaillé, rapport de diffusion, répartition des messages en échec, taux d&#39;ouverture, clics et transactions, etc. Le contenu de cet onglet est paramétrable en fonction de vos besoins. Reportez-vous à [cette section](../../reporting/using/delivery-reports.md) pour plus d&#39;informations.

### Logs et historique de la diffusion {#delivery-logs-and-history}

L&#39;onglet **[!UICONTROL Diffusion]** propose un historique des occurrences de cette diffusion. Il contient les logs de diffusion, c&#39;est-à-dire la liste des messages envoyés et leur statut. Il permet de visualiser l&#39;état de la diffusion pour chaque destinataire et les messages associés.

Pour une diffusion, vous pouvez afficher par exemple seulement les destinataires pour lesquels l&#39;envoi a échoué ou ceux dont l&#39;adresse est en quarantaine. Pour cela, cliquez sur le bouton **[!UICONTROL Filtres]** et choisissez **[!UICONTROL Par Statut]**. Sélectionnez ensuite le statut dans la liste déroulante affichée au-dessus de la liste.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Les différents statuts sont répertoriés sur [cette page](#delivery-statuses).

>[!NOTE]
>
>Le lien **[!UICONTROL Afficher la page miroir de ce message...]** permet de visualiser, dans une nouvelle fenêtre, la page miroir du contenu de la diffusion sélectionnée dans la liste. La page miroir n&#39;est disponible que pour les diffusions pour lesquelles un contenu HTML a été défini. Voir à ce sujet la section [Générer la page miroir](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### Tracking    {#tracking-logs}

L&#39;onglet **[!UICONTROL Tracking]** liste l&#39;historique du tracking pour cette diffusion. Cet onglet affiche les informations de tracking sur les messages envoyés, soit toutes les URL qui ont fait l&#39;objet d&#39;un tracking par Adobe Campaign. Les informations de tracking sont mises à jour toutes les heures.

>[!NOTE]
>
>Si le tracking n&#39;est pas activé pour une diffusion, cet onglet n&#39;est pas affiché.

Le paramétrage du tracking est effectué dans l&#39;assistant de diffusion, à l&#39;étape concernée. Voir à ce sujet la section [Comment configurer des liens trackés](../../delivery/using/how-to-configure-tracked-links.md). 

Les données de **[!UICONTROL tracking]** sont interprétées dans les rapports de diffusion. Voir [cette section](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Suivi de la diffusion {#delivery-audit-}

L&#39;onglet **[!UICONTROL Suivi]** contient le journal de la diffusion et tous les messages relatifs aux bons à tirer (BAT). Le bouton **[!UICONTROL Actualiser]** permet de mettre à jour les informations. Le bouton **[!UICONTROL Filtres]** permet d&#39;appliquer un filtre sur les données.

Des icônes spécifiques permettent de repérer les erreurs ou avertissements. Voir la section [Analyser la diffusion](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Le sous-onglet **[!UICONTROL Bons à tirer]** vous permet de voir la liste des BAT qui ont été envoyés.

![](assets/s_ncs_user_delivery_log_tab.png)

Vous pouvez modifier les informations affichées dans cette fenêtre (ainsi que celles des onglets **[!UICONTROL Diffusion]** et **[!UICONTROL Tracking]**) en sélectionnant les colonnes à afficher. Pour cela, cliquez sur l&#39;icône **[!UICONTROL Configurer la liste]**, située en bas à droite. La configuration de l&#39;affichage des listes est présentée dans [cette section](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Synchronisation du tableau de bord des diffusions {#delivery-dashboard-synchronization}

Dans le tableau de bord des diffusions, vous souhaitez vérifier les messages traités et les logs de diffusion pour vous assurer que la diffusion a bien été envoyée.

Certains indicateurs ou statuts peuvent être incorrects ou ne pas être à jour. Ce problème peut être résolu à l&#39;aide des solutions suivantes :

* Si le statut de votre diffusion est incorrect, vérifiez que toutes les validations nécessaires ont été effectuées pour celle-ci ou que les workflows **[!UICONTROL operationMgt]** et **[!UICONTROL deliveryMgt]** s&#39;exécutent sans erreur. La diffusion peut aussi utiliser une affinité qui n&#39;est pas configurée sur l&#39;instance d&#39;envoi.
* Si les indicateurs de diffusion sont toujours à zéro et que vous utilisez une configuration en mid-sourcing, vérifiez le workflow technique **[!UICONTROL Mid-sourcing (compteurs des diffusions)]**. Lancez-le si son statut n&#39;est pas **[!UICONTROL Démarré]**. Vous pouvez ensuite essayer de recalculer les indicateurs en procédant comme suit : cliquez avec le bouton droit sur la diffusion en question dans l&#39;explorateur Adobe Campaign et sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Recalculer les indicateurs d&#39;envoi et de tracking]**. Pour plus d&#39;informations sur les indicateurs de tracking, voir cette [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* Si le compteur de diffusions ne correspond pas à votre diffusion, essayez de recalculer les indicateurs en procédant comme suit : cliquez avec le bouton droit sur la diffusion en question dans l&#39;explorateur Adobe Campaign et sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Recalculer les indicateurs d&#39;envoi et de tracking]** pour effectuer une nouvelle synchronisation. Pour plus d&#39;informations sur les indicateurs de tracking, référez-vous à cette [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* Si votre compteur de diffusions n&#39;est pas à jour pour les déploiements Mid-sourcing, vérifiez que le workflow technique **[!UICONTROL Mid-sourcing (compteurs des diffusions)]** est en cours d&#39;exécution. Pour plus d&#39;informations à ce sujet, voir cette [page](../../installation/using/mid-sourcing-deployment.md).

Vous pouvez également effectuer un tracking de vos diffusions à l&#39;aide de différents rapports dans le tableau de bord des diffusions. Voir à ce sujet cette [section](../../reporting/using/delivery-reports.md).

## Problèmes de performance {#performance-issues}

### Liste de contrôle {#checklist-}

En cas de mauvaises performances des diffusions, vous pouvez vérifier les points suivants :

* **Taille de la diffusion** : l&#39;envoi de diffusions volumineuses peut prendre plus de temps. Les fils du MTA sont configurés pour gérer une taille de batch par défaut, qui convient à la plupart des instances, mais qui doit être vérifiée lorsque les diffusions sont constamment lentes.
* **Cible de la diffusion** : les performances d&#39;une diffusion peuvent être impactées par les soft bounces, qui sont traités en fonction de la configuration des reprises. Plus le nombre des erreurs est élevé, plus les reprises sont nécessaires.
* **Charge globale de la plateforme** : lorsque plusieurs diffusions volumineuses sont envoyées, la plateforme globale peut être impactée. Vous pouvez également vérifier la réputation IP et les problèmes de délivrabilité. Voir à ce sujet le [guide de bonnes pratiques de délivrabilité](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) d&#39;Adobe Campaign et [cette page](../../delivery/using/about-deliverability.md).

La maintenance de la plateforme et de la base de données peut également impacter les performances d&#39;envoi des diffusions. Voir à ce sujet [cette page](../../production/using/database-performances.md).

### Diffusions lentes {#slow-deliveries}

Après avoir cliqué sur le bouton **[!UICONTROL Envoyer]**, votre diffusion semble prendre plus de temps que d&#39;habitude. Cela peut être dû à différents éléments :

* Certains fournisseurs de messagerie ont peut-être ajouté vos adresses IP à une liste bloquée. Dans ce cas, vérifiez vos journaux et consultez [cette section](../../delivery/using/about-deliverability.md).
* Votre diffusion peut être trop volumineuse pour être traitée rapidement. Cela peut être le cas lorsque la taille de la diffusion dépasse 60 Ko ou que la personnalisation JavaScript est importante. Pour obtenir des instructions relatives au contenu, consultez [Bonnes pratiques de diffusion](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/deliveryBestPractices.html) d&#39;Adobe Campaign.
* Le MTA Adobe Campaign a peut-être été soumis à une limitation. Celle-ci est due aux éléments suivants :

   * Messages mis en attente (message **[!UICONTROL Quotas atteints]**) : les quotas déclarés par les règles MX déclaratives définies dans Campaign ont été atteints. Pour plus d&#39;informations sur ce message, consultez [cette page](https://helpx.adobe.com/fr/campaign/kb/acc-deliverability-faq.html#FAQ). Pour en savoir plus sur les règles MX, reportez-vous à [cette page](../../delivery/using/technical-recommendations.md#mx-rules).
   * Messages pended (**[!UICONTROL dynamic flow control]** message): Campaign MTA has encountered errors when trying to deliver messages for a given ISP which causes a slowdown to avoid too big of an error density and thus facing potential block list.

* Un problème lié au système peut empêcher les serveurs d&#39;interagir ensemble : l&#39;ensemble du processus d&#39;envoi peut être ainsi ralenti. Vérifiez que les serveurs ne présentent aucun problème de mémoire ou de ressource qui peut impacter Campaign dans le processus de récupération des données de personnalisation par exemple.

### Bonnes pratiques relatives aux performances {#best-practices-performance}

* Ne gardez pas les diffusions en échec sur l&#39;instance, car cela conserve les tables temporaires et a un impact sur les performances.

* Supprimez les diffusions devenues inutiles.

* Les destinataires inactifs au cours des 12 derniers mois doivent être supprimés de la base de données pour maintenir la qualité des adresses.

* N&#39;essayez pas de planifier des diffusions volumineuses ensemble. 5 à 10 minutes sont nécessaires pour répartir la charge uniformément sur le système. Coordonnez la planification des diffusions avec les autres membres de votre équipe afin d&#39;optimiser les performances. Lorsque le serveur marketing gère simultanément trop de tâches différentes, cela peut diminuer les performances.

* Maintenez la taille des emails au plus petit volume possible. La taille maximale recommandée pour un email est d&#39;environ 35 Ko. La taille d&#39;un diffusion par email génère un certain volume dans les serveurs d&#39;envoi.

* Les diffusions volumineuses, notamment celles adressées à plus d&#39;un million de destinataires, ont besoin d&#39;espace dans les files d&#39;attente d&#39;envoi. Il ne s&#39;agit pas seulement d&#39;un problème de serveur. En effet, la combinaison de dizaines d&#39;autres diffusions volumineuses et simultanées peut introduire un délai d&#39;envoi.

* La personnalisation des emails extrait des informations de la base de données pour chaque destinataire. Si les éléments de personnalisation sont nombreux, la quantité de données nécessaire pour préparer la diffusion augmente.

* Indexez les adresses. Pour optimiser les performances des requêtes SQL utilisées dans l&#39;application, un index peut être déclaré à partir de l&#39;élément principal du schéma de données.

>[!NOTE]
>
>Les FAI peuvent désactiver les adresses suite à une période d&#39;inactivité. Les messages rebonds sont envoyés aux expéditeurs pour les informer de ce nouveau statut.

## Statuts de diffusion {#delivery-statuses}

Lors de l&#39;envoi d&#39;une diffusion, les statuts suivants peuvent s&#39;afficher dans le tableau de bord des diffusions :

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Définition et solution<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Non applicable<br /> </td> 
   <td> La diffusion a été prise en compte par le serveur (MTA), mais ce dernier ne l'a pas traitée.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignoré<br /> </td> 
   <td> La diffusion n'a pas été envoyée au destinataire en raison d'une erreur avec son adresse. Il a été ajouté à une liste bloquée, mis en quarantaine, non fourni ou à un duplicata. <br /> </td> 
  </tr> 
  <tr> 
   <td> Envoyés<br /> </td> 
   <td> La diffusion a été correctement transmise au fournisseur de messagerie (mais le destinataire ne l'a pas nécessairement reçu).<br /> </td> 
  </tr> 
  <tr> 
   <td> En échec<br /> </td> 
   <td> La diffusion n'a pas pu atteindre le destinataire en raison d'une adresse invalide ou d'une boîte de réception pleine par exemple. La raison peut être également un problème lié aux blocs de personnalisation. Ils peuvent générer des erreurs lorsque les schémas ne correspondent pas au mapping de diffusion. Voir la section <a href="#failed-status" target="_blank">Statut En échec</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Pris en compte par le fournisseur de services<br /> </td> 
   <td> Le fournisseur de services SMS a reçu la diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> Reçu sur le mobile<br /> </td> 
   <td> Le destinataire a reçu le SMS sur son appareil mobile.<br /> </td> 
  </tr> 
  <tr> 
   <td> En attente<br /> </td> 
   <td> La diffusion est prête à être envoyée. Elle sera traitée par le serveur de diffusion (MTA). Voir la section <a href="#pending-status" target="_blank">Statut En attente</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Diffusion annulée<br /> </td> 
   <td> La diffusion a été annulée par un opérateur.<br /> </td> 
  </tr> 
  <tr> 
   <td> Préparé<br /> </td> 
   <td> Statut intermédiaire utilisé uniquement pour les connecteurs externes tels que le canal mobile. Il succède à l'état 'En attente' et c'est le connecteur externe qui déterminera le statut suivant.<br /> </td> 
  </tr> 
  <tr> 
   <td> Transmis au prestataire<br /> </td> 
   <td> La diffusion a été envoyée au fournisseur de services SMS qui ne l'a pas encore reçue.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Pour apprendre à optimiser la délivrabilité de vos emails Adobe Campaign, consultez le [guide de bonnes pratiques de délivrabilité](https://docs.adobe.com/content/help/fr-FR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) d&#39;Adobe Campaign ainsi que [cette page](../../delivery/using/about-deliverability.md).

### Statut En attente {#pending-status}

Après avoir validé votre diffusion, vous pouvez constater que son statut est **[!UICONTROL En attente]**.Ce statut signifie que le processus d&#39;exécution attend la disponibilité de certaines ressources.

Le statut **[!UICONTROL En attente]** peut d&#39;abord signifier que votre diffusion a été planifiée et qu&#39;elle est en attente jusqu&#39;à la date spécifiée. Voir à ce sujet la section [Planifier la diffusion](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Si votre diffusion n&#39;est pas envoyée et reste dans un état **[!UICONTROL En attente]**, la raison peut en être la suivante :

* Le Message Transfert Agent (MTA) qui exécute les modules et les processus sur le serveur de diffusion et qui gère l&#39;envoi des emails peut ne pas avoir été lancé ou doit être redémarré. Pour le vérifier, puis au besoin le lancer, les étapes sont les suivantes :

   * Vérifiez que vos modules `mta@<instance>` sont bien lancés sur vos serveurs MTA.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * Si le MTA n&#39;est pas listé, démarrez-le à l&#39;aide de la commande suivante :

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Remplacez `<INSTANCENAME>` par le nom de votre instance (production, développement, etc.). Le nom de l&#39;instance est identifié via les fichiers de configuration : `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* La diffusion peut utiliser une affinité qui n&#39;a pas été configurée sur le serveur d&#39;envoi. Dans ce cas, vérifiez la configuration de la gestion du trafic (affinité IP) et utilisez le champ **[!UICONTROL Gestion des affinités avec les adresses IP]** pour lier les diffusions au MTA qui gère l&#39;affinité. Voir à ce propos [cette section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* Lorsque la préparation de la diffusion est en attente, cela peut indiquer que trop de campagnes sont en cours d&#39;exécution, ce qui a bloqué la mise à jour de l&#39;état de la diffusion. Pour résoudre ce problème, accédez à **[!UICONTROL Options]** et augmentez la valeur de l&#39;option **[!UICONTROL NmsOperation_LimitConcurrency]** (la valeur par défaut est 10). N&#39;exécutez pas un nombre de campagnes plus élevé que la valeur affectée à cette option spécifique.

### Statut En échec {#failed-status}

Si l&#39;état d&#39;une diffusion par email est **[!UICONTROL En échec]**, la raison peut être un problème lié aux blocs de personnalisation. Dans une diffusion, les blocs de personnalisation peuvent générer des erreurs lorsque les schémas ne correspondent pas au mapping de diffusion, par exemple.

Les logs de diffusion sont la clé pour apprendre pourquoi une diffusion a échoué. Voici les erreurs possibles que vous pouvez détecter dans les logs de diffusion :

* Si les messages des destinataires échouent avec une erreur &quot;Inaccessible&quot; et le message : **Erreur lors de la compilation du script &#39;content htmlContent&#39; ligne X :`[table]`n&#39;est pas définie. JavaScript : erreur lors de l&#39;évaluation du script &#39;content htmlContent**, le problème est presque toujours dû à une personnalisation du code HTML qui tente d&#39;appeler une table ou un champ non défini ou mappé dans le ciblage amont ou dans le mapping cible de la diffusion.

   Pour corriger ce problème, le workflow et le contenu de la diffusion doivent être examinés afin de déterminer précisément quelle personnalisation tente d&#39;appeler la table en question et si la table peut être mappée ou non. À partir de là, supprimer l&#39;appel à cette table dans le code HTML ou résoudre le mapping sur la diffusion peut permettre de résoudre le problème.

* Dans un modèle de déploiement en mid-sourcing, le message suivant peut apparaître dans les logs de diffusion : **Erreur lors de l&#39;appel de la méthode &#39;AppendDeliveryPart&#39; sur le serveur de mid-sourcing : &#39;Erreur de communication avec le serveur : veuillez vérifier que celui-ci est correctement configuré. Code HTTP 408 &#39;Service momentanément indisponible&#39;**.

   La cause de cette erreur est liée à des problèmes de performance. Elle indique que l&#39;instance marketing a passé trop de temps à créer des données avant de les envoyer au serveur de mid-sourcing.

   Pour la corriger, il est recommandé d&#39;effectuer un nettoyage et une réindexation de la base de données. Pour plus d&#39;informations sur la maintenance de la base de données, consultez [cette section](../../production/using/recommendations.md).

   Vous devez également redémarrer tous les workflows avec une activité planifiée et tous ceux dans un état en échec. Consultez [cette section](../../workflow/using/scheduler.md).

* Lorsqu&#39;une diffusion est en échec, le message d&#39;erreur suivant peut apparaître dans les logs de diffusion : **DLV-XXXX Le nombre de messages préparés (123) est supérieur au nombre de messages à envoyer (111). Veuillez contacter le support.**

   En règle générale, cette erreur signifie qu&#39;un champ ou un bloc de personnalisation dans l&#39;email possède plusieurs valeurs pour le destinataire. Un bloc de personnalisation est utilisé et il récupère plusieurs enregistrements pour un destinataire spécifique.

   Pour la corriger, vérifiez les données de personnalisation utilisées, puis contrôlez la cible des destinataires qui possèdent plusieurs entrées pour l&#39;un de ces champs. Vous pouvez également utiliser une activité de **[!UICONTROL Déduplication]** dans le workflow de ciblage avant l&#39;activité de diffusion pour vérifier qu&#39;il n&#39;existe qu&#39;un seul champ de personnalisation à la fois. Pour plus d&#39;informations sur la déduplication, consultez [cette page](../../workflow/using/deduplication.md).

* Certaines diffusions peuvent échouer avec une erreur &quot;Inatteignable&quot; indiquant : &quot;Réception d&#39;un email de rebond (la règle &#39;Auto_replies&#39; s&#39;est appliquée à ce rebond). Cela signifie que la diffusion a réussi mais qu&#39;Adobe Campaign a reçu une réponse automatique du destinataire (par exemple, une réponse &quot;Out of office&quot;) qui correspond aux règles d&#39;un email de rebond &#39;Auto_replies&#39;. L&#39;email de réponse automatique est ignoré par Adobe Campaign et l&#39;adresse du destinataire ne sera pas mise en quarantaine.

**Rubriques connexes :**

* [Logs et historique de la diffusion](#delivery-logs-and-history)
* [Comprendre les diffusions en échec](../../delivery/using/understanding-delivery-failures.md)
* [Types de diffusion en échec et raisons](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## nombre d&#39;envois {#number-of-messages-sent}

Vous pouvez accéder aux diffusions à partir de la liste des diffusions accessible depuis le nœud **[!UICONTROL Gestion de campagne > Diffusions]** de l&#39;arborescence.

Par défaut, la liste des diffusions affiche les noms et états des diffusions créées dans le nœud sélectionné. Elle affiche également le nombre de messages à envoyer, traités et envoyés avec succès.

* Le nombre de **[!UICONTROL messages à envoyer]** correspond au nombre de destinataires ciblés après analyse de la diffusion et avant envoi.
* Le nombre de messages de la colonne **[!UICONTROL succès]** correspond au nombre de messages émis par le serveur et bien reçus par le destinataire.
* Le nombre de messages **[!UICONTROL traités]** correspond au nombre de messages reçus avec succès auquel s’ajoute le nombre de messages en erreur.

Le tableau de bord de la diffusion permet de suivre le nombre de messages envoyés.

>[!NOTE]
>
>Pour les diffusions volumineuses, il peut être utile d&#39;actualiser ces valeurs. Pour cela, sélectionnez la diffusion visée et cliquez avec le bouton droit de la souris. Choisissez **[!UICONTROL Action > Recalculer les indicateurs de diffusion et de tracking...]** et renseignez les étapes de l&#39;assistant pour mettre à jour les informations.

## Diffusions planifiées {#scheduled-deliveries-}

Si des diffusions ne s&#39;exécutent pas exactement à la date planifiée, c&#39;est peut-être en raison d&#39;une différence de fuseau horaire entre les serveurs. L&#39;instance de mid-sourcing et celle de production peuvent se trouver dans des fuseaux horaires différents.

Par exemple, si l&#39;instance de mid-sourcing se trouve dans le fuseau horaire de Brisbane et que l&#39;instance de production figure dans le fuseau horaire de Darwin, les deux fuseaux horaires sont espacés d&#39;une demi-heure. Dans le journal d&#39;audit, vous verrez clairement que si la diffusion est planifiée pour la production à 11h56, la même diffusion sera planifiée pour le mid-sourcing à 12h26, ce qui représente une différence d&#39;une demi-heure.

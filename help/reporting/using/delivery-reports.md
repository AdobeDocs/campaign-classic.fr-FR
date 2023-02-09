---
product: campaign
title: Rapports sur les diffusions
description: Rapports sur les diffusions
feature: Reporting
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: 64d97c7879320296a5f8efc5bb5bc2bea8663c08
workflow-type: tm+mt
source-wordcount: '1636'
ht-degree: 100%

---

# Rapports sur les diffusions {#delivery-reports}

![](../../assets/common.svg)

Vous pouvez suivre l&#39;exécution des diffusions à l&#39;aide de différents rapports, accessibles depuis la vue d&#39;ensemble des diffusions. Pour les afficher, respectez les étapes suivantes :

1. Allez dans l’onglet **[!UICONTROL Campagnes]** et cliquez sur le lien **[!UICONTROL Diffusion]** pour afficher la liste des diffusions.
1. Cliquez sur le nom de la diffusion visée pour afficher son détail.

   ![](assets/s_ncs_user_detailled_report.png)

1. Sélectionnez l&#39;onglet **[!UICONTROL Résumé]** et cliquez sur le lien **[!UICONTROL Rapports]** pour accéder aux rapports propres à la diffusion.

   ![](assets/s_ncs_user_detailled_report2.png)

   Par défaut, les rapports disponibles sont les suivants :

   * **[!UICONTROL Débit de diffusion ]**: voir [Débit des diffusions](../../reporting/using/global-reports.md#delivery-throughput).
   * **[!UICONTROL Partage vers les réseaux sociaux]** : voir [Partage vers les réseaux sociaux](../../reporting/using/global-reports.md#sharing-to-social-networks).
   * **[!UICONTROL Statistiques des activités de partage]** : voir [Statistiques des activités de partage](../../reporting/using/global-reports.md#statistics-on-sharing-activities).
   * **[!UICONTROL Position des clics]** : voir [Position des clics](#hot-clicks).
   * **[!UICONTROL Statistiques de tracking]** : voir [Statistiques de tracking](#tracking-statistics).
   * **[!UICONTROL URL et flux de clics]** : voir [URL et flux de clics](#urls-and-click-streams).
   * **[!UICONTROL Indicateurs de tracking]** : voir [Indicateurs de tracking](#tracking-indicators).
   * **[!UICONTROL Echecs et retours]** : [Echecs et retours](../../reporting/using/global-reports.md#non-deliverables-and-bounces).
   * **[!UICONTROL Activités utilisateurs]** : voir [Activités utilisateurs](../../reporting/using/global-reports.md#user-activities).
   * **[!UICONTROL Synthèse des diffusions]** : voir [Synthèse des diffusions](#delivery-summary).
   * **[!UICONTROL Suivi des abonnements]** : voir [Suivi des abonnements](../../reporting/using/global-reports.md#subscription-tracking).
   * **[!UICONTROL Statistiques de diffusion]** : voir [Statistiques de diffusion](../../reporting/using/global-reports.md#delivery-statistics).
   * **[!UICONTROL Répartition des ouvertures]** : voir [Répartition des ouvertures](../../reporting/using/global-reports.md#breakdown-of-opens).

## Indicateurs de tracking {#tracking-indicators}

Ce rapport regroupe les indicateurs clés qui permettent de suivre le comportement des destinataires à la réception de la diffusion. Il donne accès aux statistiques d&#39;envoi, de réception, aux taux d&#39;ouverture et de clic, aux flux de clics générés, au web tracking et aux partages vers les réseaux sociaux.

>[!NOTE]
>
>Les valeurs calculées à partir d’ouvertures de messages sont toujours des estimations en raison notamment de la marge d’erreur liée aux emails au format texte. Les indicateurs **[!UICONTROL Ouvertures distinctes / Somme des ouvertures sur la population atteinte]** prennent en compte cette marge d’erreur. Pour plus d’informations sur le tracking des ouvertures, consultez la section [Tracking des ouvertures](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Statistiques de diffusion]**

* **[!UICONTROL Message à diffuser]** : Nombre total de messages à diffuser après l&#39;analyse de la diffusion.
* **[!UICONTROL Succès]** : Nombre de messages traités avec succès.

**[!UICONTROL 2. Statistiques de réception]**

>[!NOTE]
>
>Les pourcentages associés sont calculés par rapport au nombre de messages transmis avec succès.

* **[!UICONTROL Ouvertures distinctes pour la population atteinte]** : estimation du nombre de destinataires ciblés ayant ouvert un message au moins une fois. Les clics sur les URL trackées sont pris en compte, car il faut ouvrir les e-mails pour cliquer sur un lien.
* **[!UICONTROL Somme des ouvertures sur la population atteinte]** : Estimation du nombre total d&#39;ouvertures effectuées par des destinataires ciblés.
* **[!UICONTROL Clics sur le lien d&#39;opt-out]** : Nombre de clics effectués sur le lien d&#39;opt-out.
* **[!UICONTROL Clics sur le lien de la page miroir]** : Nombre de clics effectués sur le lien de la page miroir. Pour être comptabilisé, le lien doit être défini comme tel dans l&#39;assistant de diffusion (URL trackées). Reportez-vous à cette [page](../../delivery/using/about-delivery-monitoring.md).
* **[!UICONTROL Estimation des transferts]** : Estimation du nombre d&#39;emails transférés par les destinataires cibles de la diffusion à d&#39;autres personnes. Cette valeur est calculée en effectuant la différence entre le nombre de personnes distinctes et le nombre de destinataires distincts ayant cliqué au moins une fois dans le mail.

   >[!NOTE]
   >
   >Pour plus d’informations sur la distinction personnes / destinataires ciblés, consultez la section [Distinction personnes / destinataires ciblés](../../reporting/using/indicator-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Taux d&#39;ouverture et de clic]**

Ce tableau de valeurs présente la répartition, par domaine Internet, des envois, des ouvertures, des clics et de la réactivité brute. Les indicateurs utilisés sont les suivants :

* **[!UICONTROL Envois]** : Nombre total de messages envoyés sur ce domaine.
* **[!UICONTROL Plaintes]** : Nombre de messages, sur ce domaine, qui ont été signalés par le destinataire comme indésirables. Le taux est calculé par rapport au nombre total de messages envoyés sur ce domaine.
* **[!UICONTROL Ouvertures]** : Nombre de destinataires ciblés distincts, sur ce domaine, ayant ouvert au moins une fois un même message. Le taux est calculé par rapport au nombre total de messages envoyés sur ce domaine.
* **[!UICONTROL Clics]** : Nombre de destinataires ciblés distincts ayant cliqué au moins une fois dans une même diffusion. Le taux est calculé par rapport au nombre total de messages envoyés sur ce domaine.
* **[!UICONTROL Réactivité brute]** : Pourcentage du nombre de destinataires ayant cliqué au moins une fois dans une même diffusion par rapport au nombre de destinataires ayant ouvert au moins une fois une même diffusion.

>[!NOTE]
>
>Les noms de domaine qui apparaissent dans ce rapport sont définis dans l&#39;énumération utilisée au niveau des cubes. Pour modifier, ajouter ou supprimer des domaines par défaut, éditez l&#39;énumération **[!UICONTROL Domaines]**, et modifiez les valeurs et les alias. Voir à ce sujet [cette section](../../platform/using/managing-enumerations.md). La catégorie **[!UICONTROL Autres]** regroupe les noms de domaine qui n&#39;appartiennent à aucune valeur de l&#39;énumération.

**[!UICONTROL 4. Flux de clics générés]**

>[!NOTE]
>
>Les pourcentages associés sont calculés par rapport au nombre de messages transmis avec succès.

* **[!UICONTROL Clics distincts sur la population atteinte]** : Nombre de personnes distinctes ayant cliqué au moins une fois dans une même diffusion.
* **[!UICONTROL Clics cumulés]** : Nombre total de clics effectués par des destinataires ciblés, hors liens de désinscription et pages miroir.
* **[!UICONTROL Clics des destinataires]** : Nombre de destinataires ciblés distincts ayant cliqué au moins une fois dans une même diffusion.
* **[!UICONTROL Réactivité estimée des destinataires]** : Ratio du nombre de destinataires ayant cliqué au moins une fois dans une même diffusion par rapport à l&#39;estimation du nombre de destinataires ayant ouvert au moins une fois une même diffusion. Ne tient pas compte des clics sur le lien d&#39;opt-out et la page miroir.

**[!UICONTROL 5. Tracking web]**

* **[!UICONTROL Pages visitées]** : Nombre de pages web visitées suite à la réception d&#39;un message.
* **[!UICONTROL Transactions]** : Nombre d&#39;achats suite à la réception d&#39;un message.
* **[!UICONTROL Montant total]** : Montant total des achats suite à la réception d&#39;un message.
* **[!UICONTROL Montant moyen des transactions]** : Moyenne du prix des achats effectués par les destinataires distincts de la diffusion.
* **[!UICONTROL Articles]** : Nombre d&#39;articles achetés par les destinataires de la diffusion.
* **[!UICONTROL Nombre moyen d&#39;articles par transaction]** : Moyenne du nombre d&#39;article par achat effectué par les destinataires distincts.
* **[!UICONTROL Montant moyen par message]** : Moyenne du montant des achats générés, par message.

   >[!NOTE]
   >
   >Pour qu&#39;une page visitée, une transaction, un montant ou un article soit comptabilisé, une balise de webtracking doit être insérée sur la page web correspondante. Le paramétrage du webtracking est présenté dans [cette section](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Partage vers email et réseaux sociaux]**

Cette section indique le nombre de messages partagés sur chaque réseau social. Voir à ce sujet la section [Partage vers les réseaux](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URL et flux de clics {#urls-and-click-streams}

Ce rapport présente la liste des pages visitées suite au lancement d&#39;une diffusion.

![](assets/s_ncs_user_url_report.png)

Vous pouvez paramétrer le contenu de ce rapport en sélectionnant : le palmarès à afficher, le périmètre de la vue (depuis le lancement de l&#39;action, sur les six premières heures suivant le lancement, etc.) et le mode d&#39;affichage des données (par libellé, par URL, par catégorie). Cliquez sur le bouton **[!UICONTROL Actualiser]** pour valider votre choix.

Dans la section supérieure du rapport, les taux suivants sont affichés :

* **[!UICONTROL Réactivité]** : Ratio du nombre de destinataires ciblés ayant cliqué au moins une fois dans une même diffusion par rapport à l&#39;estimation du nombre de destinataires ciblés ayant ouvert au moins une fois une même diffusion. Ne tient pas compte des clics sur le lien d&#39;opt-out et la page miroir.

   >[!NOTE]
   >
   >Pour plus d’informations sur le tracking des ouvertures, consultez la section [Tracking des ouvertures](../../reporting/using/indicator-calculation.md#tracking-opens-).

* **[!UICONTROL Clics distincts]** : Nombre de personnes distinctes ayant cliqué au moins une fois (hors lien de désinscription et page miroir) dans une même diffusion. Le taux affiché est calculé par rapport au nombre de messages transmis avec succès.
* **[!UICONTROL Clics cumulés]** : Nombre total de clics effectués par des destinataires ciblés (hors lien de désinscription et page miroir). Le taux affiché est calculé par rapport au nombre de messages transmis avec succès.

**[!UICONTROL Moyenne plateforme]** : Ce taux moyen, affiché sous chaque taux (réactivité, clics distincts, et clics cumulés), est calculé sur les diffusions envoyées sur les six derniers mois. Seules les diffusions de même typologie et envoyées sur le même canal sont prises en compte. Les BATs sont exclus.

Le tableau central propose les informations suivantes :

* **[!UICONTROL Clics]** : Nombre de clics cumulés, par lien.
* **[!UICONTROL Clics (en %)]** : Répartition du nombre de clics, par lien, par rapport au nombre total de clics cumulés.

**[!UICONTROL Répartition des clics dans le temps]**

Ce graphique présente la répartition des clics cumulés, par jour.

## Synthèse des diffusions {#delivery-summary}

Ce rapport présente l&#39;ensemble des informations principales relatives à la diffusion.

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Une population cible]**

Cette section comporte deux indicateurs :

* **[!UICONTROL Population initiale]** : Nombre total de destinataires auxquels la diffusion est destinée.
* **[!UICONTROL Messages rejetés par règle]** : nombre d&#39;adresses ignorées pendant l&#39;analyse lors de l&#39;application des règles de typologie : adresse manquante, mise en quarantaine, ajoutée à la liste bloquée, etc. Pour plus d’informations sur les règles de typologie, consultez cette [page](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

**[!UICONTROL Causes d&#39;exclusion]**

Le graphique central présente la répartition, par règle, des messages rejetés lors de l&#39;analyse.

**[!UICONTROL Statistiques de diffusion]**

Cette section comporte les indicateurs suivants :

* **[!UICONTROL Message à diffuser]** : Nombre total de messages à diffuser après l&#39;analyse des diffusions.
* **[!UICONTROL Succès]** : Nombre de messages traités avec succès. Le taux associé est le ratio avec le nombre de messages à diffuser.
* **[!UICONTROL Erreurs]** : Nombre total d&#39;erreurs cumulées lors des diffusions et du traitement automatique des retours. Le taux associé est le ratio avec le nombre de messages à diffuser.
* **[!UICONTROL Mises en quarantaine]** : Nombre d&#39;adresses mises en quarantaine à la suite d&#39;un échec (utilisateur inconnu, domaine invalide). Le taux associé est le ratio avec le nombre de messages à diffuser.

## Hot clicks {#hot-clicks}

Ce rapport présente le contenu du message (HTML et/ou texte) avec, sur chaque lien, le pourcentage de clics sur ce lien. Les liens situés dans les blocs de personnalisation, le lien de désinscription, le lien vers la page miroir et les liens des offres sont comptabilisés dans le total des clics cumulés mais ne sont pas affichés dans le rapport.

>[!NOTE]
>
>Si votre diffusion contient des offres (Interaction), un encadré apparaît dans la partie supérieure du rapport affichant le pourcentage de clics sur les offres.

![](assets/s_ncs_user_clic_report.png)

## Statistiques de tracking {#tracking-statistics}

Ce rapport présente les statistiques sur les taux d&#39;ouverture, clics et transactions.

![](assets/s_ncs_user_stat_report.png)

Il vous permet de suivre l&#39;impact marketing de la diffusion. Vous pouvez paramétrer l&#39;affichage des valeurs en sélectionnant le périmètre de la vue (vue sur 1 heure, 3 heures, 24 heures, etc.). Cliquez sur le bouton **[!UICONTROL Actualiser]** pour valider votre choix.

Ce rapport se présente sous la forme d&#39;un tableau de valeur et d&#39;un diagramme de Pareto permettant de mesurer le temps mis pour que la diffusion atteigne son efficacité maximum. Les indicateurs utilisés sont les suivants :

* **[!UICONTROL Ouvertures]** : estimation du temps mis pour atteindre un pourcentage du nombre total de messages ouverts. Les emails au format texte ne sont pas comptabilisés. Pour plus d’informations sur le tracking des ouvertures, consultez la section [Tracking des ouvertures](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clics]** : Estimation du temps mis pour atteindre un pourcentage du nombre total de clics enregistrés. Les clics sur le lien d&#39;opt-out et la page miroir ne sont pas pris en compte.
* **[!UICONTROL Transactions]** : temps mis pour atteindre un pourcentage du nombre total de transactions suite à la réception d&#39;un message. Pour qu&#39;une transaction soit comptabilisée, une balise de webtracking de type transaction doit être insérée sur la page web correspondante. Le paramétrage du webtracking est présenté dans [cette section](../../configuration/using/about-web-tracking.md).

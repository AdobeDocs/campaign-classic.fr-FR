---
product: campaign
title: Calcul des indicateurs
description: Calcul des indicateurs
feature: Reporting
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '3021'
ht-degree: 100%

---

# Calcul des indicateurs {#indicator-calculation}

![](../../assets/common.svg)

## Activités utilisateurs {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Ouvertures (Opens)<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Somme de tous les @totalClicks dont la clé primaire de l'url est égale à 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Somme de tous les @totalClicks dont le type de l'url est égal à "Clic email".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Somme de tous les @totalClicks dont le type de l'url est égal à "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Ce rapport se base sur la table **[!UICONTROL Tracking consolidé]** (nms:trackingStats). Cette table d&#39;agrégats est utilisée pour des raisons de performance lors de l&#39;affichage des rapports, à la place de la table **[!UICONTROL Logs de tracking des destinaires]** (nms:trackingLogRcp) et n&#39;est pas calculée en temps réel. La table est générée quelques minutes après la récupération des logs de tracking. Si les indicateurs sont à jour, les résultats seront les mêmes que pour les indicateurs du rapport **Indicateurs de tracking**. L&#39;indicateur @totalclicks correspond à la somme des clics sur une période de 5 minutes.

## Échecs et bounces {#non-deliverables-and-bounces-1}

**Ventilation par type d&#39;erreur**

Ce rapport se base sur la table **[!UICONTROL Statistiques d&#39;envoi et de tracking]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nombre total de messages traités<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> Somme de tous les messages pour lesquels le statut est égal à "Préparé", "Envoyé" ou "En échec".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Utilisateur inconnu<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Utilisateur inconnu". <br /> </td> 
   <td> Count(@status=2 et msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Inatteignable <br /> </td> 
   <td> @Inatteignable<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Inatteignable". <br /> </td> 
   <td> Count(@status=2 et msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejetés<br /> </td> 
   <td> @refused<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Refusé". <br /> </td> 
   <td> Count(@status=2 et msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Domaine invalide<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Domaine invalide". <br /> </td> 
   <td> Count(@status=2 et msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Compte désactivé<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Compte désactivé".<br /> </td> 
   <td> Count(@status=2 et msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boîte pleine<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Boîte pleine". <br /> </td> 
   <td> Count(@status=2 et msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Erreurs<br /> </td> 
   <td> @valeur<br /> </td> 
   <td> Nombre de messages en échec pour ce type d'erreur.<br /> </td> 
   <td> Count(@status=2 et msg/@failureReason="Valeur du type d'erreur")<br /> </td> 
  </tr> 
  <tr> 
   <td> Contribution<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage du nombre de messages en erreur de ce type par rapport au nombre total de messages en erreur.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Répartition<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage du nombre de messages en erreur de ce type par rapport au nombre total de messages traités.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Ventilation par domaine**

La seconde partie du rapport présente la répartition des messages en échec, non pas par type d&#39;erreur, mais par domaine Internet. La formule associée à l&#39;indicateur **Erreur** (@value) est dans ce cas : Count(@status=2 et @domain=&quot;Valeur du nom de domaine&quot;). C&#39;est-à-dire un comptage de tous les messages dont le statut est en échec sur ce domaine.

## Navigateurs {#browsers-1}

Ce rapport se base sur la table **[!UICONTROL Statistiques Navigateurs internet]** (nms:userAgentsStats).

**Statistiques globales**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visiteurs<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Nombre total de destinataires ciblés, pour ce navigateur, ayant cliqué au moins une fois dans une même diffusion.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Pages vues<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Nombre total de clics sur les liens des diffusions, pour ce navigateur, dans l'ensemble des diffusions.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> Taux d'utilisation<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage des visiteurs, pour ce navigateur, par rapport au nombre total de visiteurs.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistiques par navigateur**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Taux d'utilisation<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Pourcentage du nombre de visiteurs par jour, sur ce navigateur, par rapport au nombre de visiteurs mesuré le jour le plus fréquenté.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taux global<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage des visiteurs, pour cette version, par rapport au nombre total de visiteurs sur l'ensemble des navigateurs.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Taux relatif<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage des visiteurs, pour cette version, par rapport au nombre total de visiteurs sur ce navigateur.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Partage vers les réseaux sociaux {#sharing-to-social-networks-1}

Ce rapport se base sur les tables **[!UICONTROL Diffusion]** (nms:delivery), **[!UICONTROL Tracking consolidé]** (nms:trackingStats), et **[!UICONTROL Tracking Web]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nombre de messages à diffuser<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Nombre total de messages traités lors de l'analyse de la diffusion.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Nombre d'envois réussis<br /> </td> 
   <td> @success<br /> </td> 
   <td> Nombre de messages traités avec succès <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Email<br /> </td> 
   <td> @email<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Partages**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nb. partages<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Nombre total de messages partagés, sur ce réseau social.<br /> </td> 
   <td> Sum(iIf([url/@category]="Valeur du type de réseau social",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Répartition<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Pourcentage du nombre de partages sur ce réseau par rapport au nombre total de partages.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taux de partage<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Nombre de partages sur ce réseau par rapport au nombre de messages à diffuser.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Ouvertures (Opens)**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nb. ouvertures <br /> </td> 
   <td> @open<br /> </td> 
   <td> Nombre total de lignes de tracking dans la table du tracking web.<br /> </td> 
   <td> Count<br /> </td> 
  </tr> 
  <tr> 
   <td> Répartition<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Pourcentage du nombre d'ouvertures, sur ce réseau social, par rapport au nombre total d'ouvertures.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taux d'ouverture<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Nombre d'ouvertures, sur ce réseau social, par rapport au nombre total de messages à diffuser.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiques des activités de partage {#statistics-on-sharing-activities-1}

Ce rapport se base sur les tables **[!UICONTROL Diffusion]** (nms:delivery), **[!UICONTROL Tracking consolidé]** (nms:trackingStats), et **[!UICONTROL Tracking Web]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nouveaux contacts<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> Comptage du nombre de visiteurs liés à un destinataire.<br /> </td> 
   <td> Formule : count(@id)<br /> Filtre : @recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Ouvertures (Opens)<br /> </td> 
   <td> @opened<br /> </td> 
   <td> Comptage de tous les @id dont le type de l'url est égal à "Ouverture".<br /> </td> 
   <td> count(Iif([url/@type]=2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Partages<br /> </td> 
   <td> @shared<br /> </td> 
   <td> Catégorie d'URL incluse dans 'email', 'facebook', 'twitter', 'delicious', 'digg', 'google', 'linkedin'<br /> Comptage de tous les @totalClicks avec une catégorie d'URL égale à "email", "facebook", "twitter", "delicious", "digg", "google" ou "linkedin".<br /> </td> 
   <td> count (Iif([url/@category] IN ('email' , 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Systèmes d’exploitation {#operating-systems-1}

Ce rapport se base sur la table **[!UICONTROL Statistiques Navigateurs internet]** (nms:userAgentsStats).

**Statistiques globales**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visiteurs<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> Moyenne par jour du nombre total de destinataires ciblés, par système d'exploitation, ayant cliqué au moins une fois dans une même diffusion.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Pages vues<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Moyenne par jour du nombre total de clics sur les liens des diffusions, par système d'exploitation, dans l'ensemble des diffusions.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Taux d'utilisation<br /> </td> 
   <td> -<br /> </td> 
   <td> Répartition des visiteurs, par système d'exploitation, par rapport au nombre total de visiteurs.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistiques par système d&#39;exploitation**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Taux d'utilisation<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Pourcentage du nombre de visiteurs par jour, sur ce système d'exploitation, par rapport au nombre de visiteurs mesuré le jour le plus fréquenté.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Taux global<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage des visiteurs, par version, par rapport au nombre total de visiteurs sur l'ensemble des systèmes d'exploitation.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Taux relatif<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage des visiteurs, par version, par rapport au nombre total de visiteurs sur ce système d'exploitation.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracking des abonnements {#subscription-tracking-1}

Ce rapport se base sur la table **[!UICONTROL Services]** (nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Inscrits<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Comptage des inscrits le jour précédent.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Abonnements <br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> comptage des inscriptions (@action = 1) le jour précédent.<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Désinscriptions (Unsubscriptions)<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> comptage des désinscriptions (@action = 0) le jour précédent.<br /> </td> 
   <td> sum(Iif(@action = 0 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolution<br /> </td> 
   <td> -<br /> </td> 
   <td> Nombre de désabonnements soustrait au nombre d'abonnements. Le taux associé est calculé par rapport au nombre total d'abonnés.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%)','')<br /> </td> 
  </tr> 
  <tr> 
   <td> Fidélité<br /> </td> 
   <td> -<br /> </td> 
   <td> Taux de fidélité des abonnés sur la période correspondante.<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Indicateurs de tracking {#tracking-indicators-1}

Ce rapport se base sur les tables **[!UICONTROL Statistiques d&#39;envoi et de tracking]** (nms:deliveryLogStats) et **[!UICONTROL Tracking consolidé]** (nms:trackingStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Messages à diffuser<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Comptage du nombre de broadLogs après l'analyse de la cible.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Succès<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Comptage des messages pour lesquels le champ "adresse de contrôle" est égal à "Non" et dont le statut est égal à "Pris en compte par le prestataire" ou "Envoyé" ou "Reçu sur le mobile".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Ouvertures distinctes sur la population atteinte<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Extrapolation du nombre d'ouvertures distinctes pour l'ensemble des mails à partir du nombre d'ouvertures distinctes pour les mails en format html.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Somme des ouvertures sur la population atteinte<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Extrapolation du nombre total d'ouvertures pour l'ensemble des mails à partir du nombre total d'ouvertures pour les mails en format html.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics sur le lien de désinscription<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Comptage de tous les @id dont la catégorie de l'url est égale à "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics sur le lien de la page miroir<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Comptage de tous les @id dont la catégorie de l'url est égale à "Page miroir".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Estimation des transferts<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Différence entre le nombre de personnes distinctes et le nombre de destinataires distincts ayant cliqué au moins une fois dans le mail.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Envois<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Comptage des messages pour lesquels le champ "adresse de contrôle" est égal à "Non" et dont le statut est égal à "Pris en compte par le prestataire" ou "Envoyé" ou "Reçu sur le mobile".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Plaintes (Complaints)<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> Comptage des messages dont le statut est égal à "En échec" et la raison est égale à "Adresse sur liste bloquée".<br /> </td> 
   <td> Count(@status=2 et msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Ouvertures (Opens)<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Comptage de tous les @broadLog-id dans tous les logs de tracking.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Comptage distinct des @broadLog-id dont le type de l'url égal à "Clic email". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Réactivité brute<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage du nombre de destinataires ayant cliqué au moins une fois dans une même diffusion par rapport au nombre de destinataires ayant ouvert au moins une fois une même diffusion.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics distincts sur la population atteinte<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Comptage de tous les @source-id dont la catégorie de l'url est égale à "Clic email".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics cumulés<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Comptage de tous les @id dont la catégorie de l'url est égale à "Clic email".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics des destinataires<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Comptage distinct des @broadLog-id dont le type de l'url égal à "Clic email".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Réactivité estimée<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio du nombre de destinataires ayant cliqué au moins une fois dans une même diffusion par rapport à l'estimation du nombre de destinataires ayant ouvert au moins une fois une même diffusion.<br /> </td> 
   <td> percent(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Pages visitées<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Comptage de tous les @id dont le type de l'url est égal à "Web" ou "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=4 ou [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Comptage de tous les @id dont le type de l'url est égal à "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Montant total<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Somme des webTrackingLog/@amount pour lesquels le type de l'url est égal à "Transaction". <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Montant moyen des transactions<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio du montant total par rapport au nombre de transactions.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Articles<br /> </td> 
   <td> @article<br /> </td> 
   <td> Somme des webTrackingLog/@article pour lesquels le type de l'url est égal à "Transaction".<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Nombre moyen d'articles par transaction<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio du nombre d'articles par rapport au nombre de transactions.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Montant moyen par message<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio du montant total par rapport au nombre de messages à diffuser.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> Email<br /> </td> 
   <td> @email<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somme de tous les @totalClicks dont la catégorie de l'url est égale à "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL et flux de clics {#urls-and-click-streams-1}

Ce rapport se base sur la table **[!UICONTROL Diffusion]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Réactivité<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Ratio du nombre de destinataires ciblés ayant cliqué au moins une fois dans une même diffusion par rapport à l'estimation du nombre de destinataires ciblés ayant ouvert au moins une fois une même diffusion.<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics distincts<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> Ratio du nombre de personnes distinctes ayant cliqué au moins une fois dans une même diffusion par rapport au nombre de messages transmis avec succès.<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics cumulés<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Ratio du nombre total de clics effectués par des destinataires ciblés par rapport au nombre de messages transmis avec succès.<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Comptage de tous les @totalClicks dont la clé primaire de l'url est différente de 1<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics (en%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Pourcentage du nombre de clics par rapport au nombre total de clics cumulés.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Synthèse des diffusions {#delivery-summary-1}

Ce rapport se base sur la table **[!UICONTROL Diffusion]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Population initiale<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Nombre total de destinataires auxquels la diffusion est destinée.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messages rejetés par règle<br /> </td> 
   <td> @reject<br /> </td> 
   <td> Nombre d'adresses ignorées lors de l'analyse en application des règles de typologie : adresse non renseignée, en quarantaine, sur liste bloquée, etc.<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messages à diffuser<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Nombre total de messages à diffuser après l'analyse des diffusions.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Succès<br /> </td> 
   <td> @success<br /> </td> 
   <td> Nombre de messages traités avec succès.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Erreurs<br /> </td> 
   <td> @error<br /> </td> 
   <td> Nombre total d'erreurs cumulées lors des diffusions et du traitement automatique des retours.<br /> </td> 
   <td> sum([indicators/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> Mises en quarantaine<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Nombre d'adresses mises en quarantaine à la suite d'un échec (utilisateur inconnu, domaine invalide).<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Hot clicks {#hot-clicks-1}

Ce rapport se base sur les tables Diffusion (nms:delivery), et **[!UICONTROL Tracking consolidé]** (nms:trackingStats).

Ce rapport présente le contenu du message (HTML et/ou texte) avec, sur chaque lien, le pourcentage de clics sur ce lien. Les liens situés dans les blocs de personnalisation, le lien de désinscription et le lien vers la page miroir sont comptabilisés dans le total des clics cumulés mais ne sont pas affichés dans le rapport.

## Statistiques de tracking {#tracking-statistics-1}

Ce rapport se base sur la table **[!UICONTROL Diffusion]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Somme de tous les @totalClicks dont le type de l'url est égal à "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Somme de tous les @totalClicks dont le type de l'url est égal à "Clic email".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Ouvertures<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Somme de tous les @totalClicks dont la clé primaire de l'url est égale à 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiques de diffusion {#delivery-statistics-1}

Ce rapport se base sur la table **[!UICONTROL Statistiques d&#39;envoi et de tracking]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Emails traités<br /> </td> 
   <td> @processed<br /> </td> 
   <td> Somme de tous les messages pour lesquels le statut est égal à "Préparé", "Envoyé" ou "En échec".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivrés<br /> </td> 
   <td> @success<br /> </td> 
   <td> Nombre de messages traités avec succès.<br /> </td> 
   <td> indicators/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Hard bounces<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Utilisateur inconnu".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Soft bounces<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Comptage de tous les messages dont le statut est égal à "En échec" et la raison est égale à "Inatteignable", "Boîte pleine", "Domaine invalide", "Compte désactivé", "Non connecté" ou "Refusé"<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> Ouvertures (Opens)<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Comptage de tous les @broadLog-id dans tous les logs de tracking.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clics<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Comptage de tous les @source-id dont la catégorie de l'url est égale à "Clic email". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Désinscriptions (Unsubscriptions)<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Comptage de tous les @id dont la catégorie de l'url est égale à "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Répartition des ouvertures {#breakdown-of-opens-1}

Ce rapport se base sur les tables **Diffusions** (nms:delivery) et **Logs de tracking** (nms:trackingLogRcp).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Libellé</strong> <br /> </th> 
   <th> <strong>Nom du champ</strong> <br /> </th> 
   <th> <strong>Description de l'indicateur</strong> <br /> </th> 
   <th> <strong>Formule de calcul de l'indicateur</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Ouvertures (Opens)<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Somme de tous les @id dont la clé primaire de l'url est égale à 1 (ouverture). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Autres indicateurs {#other-indicators}

L&#39;indicateur **Envoyés** (@sent), accessible à partir du noeud **Diffusions(nms:delivery)>Indicateurs**, correspond au nombre total de SMS envoyés au prestataire. Cet indicateur est utilisé uniquement pour les diffusions SMS et ne doit pas être utilisé pour les autres types de diffusions (ne pas confondre avec les indicateurs **@success** et **@processed**).

## Synchronisation des indicateurs {#indicator-synchronization}

Si vous observez une désynchronisation ou une incohérence de certains indicateurs, sélectionnez la diffusion concernée dans l&#39;explorateur Adobe Campaign, cliquez avec le bouton droit et choisissez **[!UICONTROL Actions > Recalculer les indicateurs de diffusion et de tracking]**. Cliquez sur **[!UICONTROL Suivant]** puis sur **[!UICONTROL Terminer]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Tracking des ouvertures {#tracking-opens-}

Pour qu’Adobe Campaign puisse détecter l’ouverture d’un message, le destinataire doit télécharger les images de l’email. Les emails HTML et Multipart/Alternative incluent en effet une image de 0 pixel permettant, lorsque le destinataire l’affiche, de détecter qu’il a ouvert le message. Les messages au format texte ne contenant aucune image, il est impossible d’en détecter l’ouverture. Les valeurs calculées sur des ouvertures de messages sont donc toujours des estimations, en raison de la marge d’erreur liée à l’affichage des images.

## Distinction personnes / destinataires ciblés {#targeted-persons---recipients}

Adobe Campaign distingue les personnes et les destinataires ciblés dans les statistiques de certains rapports.

Les destinataires ciblés correspondent à tous les destinataires à qui la diffusion a été envoyée.

Le nombre de personnes englobe les destinataires ciblés, auxquels sont ajoutées toutes les personnes à qui l&#39;email a été transféré. A chaque fois qu&#39;une ouverture ou qu&#39;un clic est effectué dans un nouveau navigateur (avec lequel ce message n&#39;avait jamais été ouvert), une nouvelle personne est comptabilisée.

Par exemple, si vous recevez un email (envoyé par Adobe Campaign) au travail et que vous l&#39;ouvrez ou cliquez dedans, vous êtes comptabilisé comme un destinataire ciblé (donc destinataire=1, personne=1). Si vous transférez ce mail à deux amis, le nombre de destinataires ciblés sera toujours de un alors que le nombre de personnes sera de trois. La valeur 3 correspond donc à chaque ouverture/clic dans un nouveau navigateur.

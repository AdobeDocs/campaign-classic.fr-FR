---
title: Surveillance des processus
seo-title: Surveillance des processus
description: Surveillance des processus
seo-description: null
page-status-flag: never-activated
uuid: 9dc1461f-5e95-454d-8df5-19baab85f184
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 968d0ee3-5efc-46d8-b408-b9cce3e730c4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 954018e1016fc924064bd795066f80704499f6a7

---


# Surveillance des processus{#monitoring-processes}

La surveillance du serveur applicatif et du serveur de redirection (**tracking**) peut être manuelle ou automatique.

## Surveillance manuelle {#manual-monitoring}

Go to **[!UICONTROL Monitoring]** and click the **[!UICONTROL Overview]** link to display the Adobe Campaign process monitoring page.

![](assets/d_ncs_monitoring.png)

La page qui s&#39;affiche permet de visualiser l&#39;état de l&#39;instance connectée à savoir :

* les informations relatives à l&#39;instance : version, nom, moteur de base de données, packages installés, indicateurs système du serveur,
* la liste des processus manquants et les informations d&#39;exécution (date de démarrage, PID, etc.),
* une vue des workflows et des diffusions.

D’autres méthodes de surveillance des différents processus de campagne sont présentées dans [cette page](https://helpx.adobe.com/campaign/kb/acc-maintenance.html).

### Journal des logs {#log-journal}

It is possible to display the log journal related to a process. To do this, click on the process, **mta** for example, then click **[!UICONTROL Open the log journal]** .

![](assets/d_ncs_monitoring2.png)

### Indicateurs système {#system-indicators}

La liste des indicateurs système vous permet d&#39;afficher des informations concernant la machine, telles que sa mémoire physique et virtuelle, ses processus actifs et l&#39;espace disque disponible. Les indicateurs sont différents pour les systèmes d’exploitation Linux et Windows. Accédez à la **[!UICONTROL Instance Monitoring]** page et cliquez sur le **[!UICONTROL Display]** lien pour ouvrir la liste des indicateurs.

#### Sous Windows {#in-windows}

* **[!UICONTROL Pending events queued]** : Indicateur spécifique au Centre **de messages**. Pour plus d&#39;informations, consultez [cette section](../../message-center/using/monitoring-thresholds.md).
* **[!UICONTROL Memory]** : informations relatives à la mémoire physique (RAM).

   **[!UICONTROL Current value]** : consommation réelle de mémoire.

   **[!UICONTROL Max Value]** : quantité totale de mémoire installée.

   **[!UICONTROL Available]** : quantité de mémoire disponible.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 80% de la quantité totale.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 90% de la quantité totale.

   Lorsque les **[!UICONTROL Warning]** indicateurs et les **[!UICONTROL Alert]** indicateurs sont affichés, vous pouvez résoudre le problème en ajoutant de la mémoire vive à l’ordinateur sur lequel le serveur Adobe Campaign est installé. Vous pouvez également décider d’installer le serveur Adobe Campaign sur un ordinateur dédié.

* **[!UICONTROL Swap Memory]** : informations relatives à la mémoire virtuelle qui correspond à un fichier d&#39;échange, soit une zone du disque que Windows utilise comme s&#39;il s&#39;agissait de mémoire vive.

   **[!UICONTROL Current value]** : consommation réelle de mémoire.

   **[!UICONTROL Max Value]** : quantité totale de mémoire.

   **[!UICONTROL Available]** : quantité de mémoire disponible.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 80% de la quantité totale.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 90% de la quantité totale.

   Lorsque les indicateurs **[!UICONTROL Warning]** et **[!UICONTROL Alert]** s&#39;affichent, vous pouvez remédier au problème en augmentant la taille du fichier d&#39;échange dans les paramètres avancés de Windows.

* **[!UICONTROL Disk XXX]** : informations concernant les lecteurs de machines.

   **[!UICONTROL Current value]** : espace disque réellement utilisé.

   **[!UICONTROL Max Value]** : capacité totale du disque.

   **[!UICONTROL Available]** : espace disque disponible

   **[!UICONTROL Used]** : pourcentage de disque utilisé.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque l&#39;espace disque disponible atteint les 80% de la capacité totale.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque l&#39;espace disque disponible atteint les 90% de la capacité totale.

* **[!UICONTROL Number of processes too old]** : informations concernant les processus Adobe Campaign actifs depuis plus d’une journée.

   **[!UICONTROL Current value]** : nombre de processus actuellement actifs.

   **[!UICONTROL Max Value]** : nombre maximal de processus autorisés (1).

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque le nombre de processus est à 1.

   Lorsque l&#39; **[!UICONTROL Alert]** indicateur est affiché, il se peut que le processus concerné soit verrouillé par le moteur de base de données SQL ou qu&#39;il soit bloqué dans une boucle infinie. Le processus de **contrôle** fourni par Adobe Campaign redémarre automatiquement tous les processus chaque jour et vous permet de résoudre ce problème. Cependant, vous pouvez aussi arrêter le processus concerné vous-même pour forcer le redémarrage.

#### Sous Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]** : Indicateur spécifique au Centre **de messages**. Pour plus d&#39;informations, consultez [cette section](../../message-center/using/monitoring-thresholds.md).
* **[!UICONTROL Load average (1/5/15 minutes)]** : informations concernant la charge, c&#39;est-à-dire le taux d&#39;utilisation du processeur par les processus exécutés sur l&#39;ordinateur au cours de la dernière minute, cinq minutes ou quinze minutes

   **[!UICONTROL Current value]** : charge réelle de la machine.

   **[!UICONTROL Max value]** : charge maximale d&#39;utilisation du ou des processeurs de la machine.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque la charge atteint 80% de la valeur maximale autorisée au cours de la dernière minute, ou des cinq ou quinze dernières minutes.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque la charge atteint 90% de la valeur maximale autorisée au cours de la dernière minute, ou des cinq ou quinze dernières minutes.

* **[!UICONTROL Memory]** : informations relatives à la mémoire physique (RAM).

   **[!UICONTROL Current value]** : consommation réelle de mémoire.

   **[!UICONTROL Max Value]** : quantité totale de mémoire installée.

   **[!UICONTROL Available]** : quantité de mémoire disponible.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 80% de la quantité totale.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 90% de la quantité totale.

   Lorsque les **[!UICONTROL Warning]** indicateurs et les **[!UICONTROL Alert]** indicateurs sont affichés, vous pouvez résoudre le problème en ajoutant de la mémoire vive à l’ordinateur sur lequel le serveur Adobe Campaign est installé. Vous pouvez également décider d’installer le serveur Adobe Campaign sur un ordinateur dédié.

* **[!UICONTROL Swap Memory]** : informations relatives à la mémoire virtuelle qui correspond à un fichier d&#39;échange, soit une zone du disque que Windows utilise comme s&#39;il s&#39;agissait de mémoire vive.

   **[!UICONTROL Current value]** : consommation réelle de mémoire.

   **[!UICONTROL Max Value]** : quantité totale de mémoire.

   **[!UICONTROL Available]** : quantité de mémoire disponible.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 80% de la quantité totale.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque la consommation de la mémoire atteint les 90% de la quantité totale.

   Lorsque les indicateurs **[!UICONTROL Warning]** et **[!UICONTROL Alert]** s&#39;affichent, vous pouvez remédier au problème en augmentant la taille du fichier d&#39;échange.

* **[!UICONTROL Core Files]** : informations concernant les fichiers générés après le blocage d’un processus Adobe Campaign. Ces fichiers vous permettent de diagnostiquer les raisons du blocage.

   **[!UICONTROL Current Value]** : nombre de fichiers existants.

   **[!UICONTROL Max Value]** : nombre maximal de fichiers autorisés (1).

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque le nombre de fichiers s&#39;approche de 1.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque le nombre de fichiers est à 1.

   Lorsqu&#39;un processus est manquant suite à un crash, il apparaît en rouge dans la liste des processus et est relancé automatiquement par le processus **watchdog** fourni par Adobe Campaign.

* **[!UICONTROL Number of shared memory segments]** : informations concernant les segments de mémoire partagés par tous les processus Adobe Campaign.

   **[!UICONTROL Current value]** : nombre de segments de mémoire actuellement utilisés.

   **[!UICONTROL Max Value]** : nombre maximal de segments de mémoire autorisés (2).

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque le nombre de segments de mémoire atteint 1.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque le nombre de segments de mémoire atteint 2.

* **[!UICONTROL Number of processes too old]** : informations concernant les processus actifs depuis plus d’une journée.

   **[!UICONTROL Current value]** : nombre de processus actuellement actifs.

   **[!UICONTROL Max Value]** : nombre maximal de processus autorisés.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque le nombre de processus est à 80% de la limite autorisée.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque le nombre de processus est à 90% de la limite autorisée.

* **[!UICONTROL File Handles]** : informations relatives aux descripteurs de fichier, soit le nombre de fichiers ouverts par processus.

   **[!UICONTROL Current value]** : nombre actuel de descripteurs de fichier.

   **[!UICONTROL Max Value]** : nombre maximal de descripteurs de fichiers autorisé par le système d&#39;exploitation.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque le nombre de descripteurs de fichiers autorisé atteint le seuil de 80%.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque le nombre de descripteurs de fichiers autorisé atteint le seuil de 90%.

* **[!UICONTROL Processes]** : informations relatives aux processus de la machine.

   **[!UICONTROL Current value]** : nombre de processus actuellement actifs.

   **[!UICONTROL Max Value]** : nombre maximal de processus autorisés.

   **[!UICONTROL Active Processes]** : nombre de processus actifs.

   **[!UICONTROL Inactive Processes]** : nombre de processus inactifs.

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque le nombre de processus autorisé atteint le seuil de 80% de la valeur maximale autorisée.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque le nombre de processus autorisé atteint le seuil de 90% de la valeur maximale autorisée.

* **[!UICONTROL Zombie Processes]** : informations relatives aux processus qui se sont arrêtés, mais qui disposent toujours d&#39;un identifiant de processus (PID) et restent visibles dans la table des processus.

   **[!UICONTROL Current value]** : nombre de processus zombies actuellement actifs.

   **[!UICONTROL Max Value]** : nombre maximal de processus zombies autorisés (2).

   **[!UICONTROL Warning]** : cet indicateur s&#39;affiche lorsque le nombre de processus zombie s&#39;approche de 2.

   **[!UICONTROL Alert]** : cet indicateur s&#39;affiche lorsque le nombre de processus zombie atteint 2.

#### Indicateurs personnalisés {#customized-indicators}

Adobe Campaign vous permet de personnaliser les indicateurs. Pour ce faire :

1. Create a **.sh** file and name it **[!UICONTROL cust_indicators.sh]** .
1. Ajoutez vos indicateurs personnalisés dans ce fichier. Par exemple :

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   or

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. Put the file in the **[!UICONTROL usr/local/neolane/nl6]** folder.

Ce fichier sera appelé par Adobe Campaign.

## Rapports SMTP {#smtp-reports}

Les rapports de monitoring sur les envois SMTP sont intégrés dans la plateforme Adobe Campaign. Ils sont accessibles via la console ou un accès Web.

Ces rapports affichent les statistiques SMTP d&#39;envoi et les erreurs SMTP par domaine.

Pour y accéder, les droits d&#39;Administration doivent être associés à l&#39;opérateur.

Ils sont regroupés dans **Supervision** > &#39;Monitoring SMTP&#39;.

![](assets/smtp_reports_access.png)

>[!CAUTION]
>
>* Les informations liées au Monitoring SMTP ne sont disponibles que si le canal email a été activé.
>* The **[!UICONTROL SMTP sending statistics]** are only offered if the statistics server is started on the instance.
>



### Statistiques SMTP d&#39;envoi {#smtp-sending-statistics}

Le **[!UICONTROL SMTP sending statistics]** rapport vous permet de contrôler l’activité du serveur. Il affiche une synthèse de chacun des enfants mineurs.

![](assets/smtp_stats_report.png)

La liste des indicateurs de ce rapport est proposée sous le graphique.

1. Nombre total de messages envoyés.
1. 
   * Ligne bleue : messages prêts à l&#39;envoi arrivant dans le Shaper, i.e. dernière étape avant l&#39;envoi SMTP (correspond à ce qui entre).

   * Ligne verte : messages envoyés avec succès (correspond à ce qui sort).

   * Ligne rouge : messages abandonnés par le Shaper, rendus au **mta** (correspond à ce qui est rejeté sur cette reprise).
   Ces valeurs sont exprimées en nombre de messages par heure.

1. Représente symboliquement deux files du Shaper :

   * Courbe bleue : la file des messages actifs. Ces messages seront envoyés dès que possible.

   * Courbe kaki : la file &#39;deferred&#39;. Ces messages ne peuvent pas être envoyés dans l&#39;immédiat pour cause de limitation du serveur de statistiques (throttling) ou parce qu&#39;aucune connexion vers la cible n&#39;est disponible. L&#39;envoi de ces messages sera tenté toutes les 5s, 10s, 20s, 40s, ..., 2min, etc., pendant la durée maximum **MaxAgeSec** définie, avant d&#39;être abandonnés.

1. Ce graphique présente un détail des messages abandonnés (courbe rouge sur le 2e graphe) : il montre la part des messages abandonnés sans avoir essayé de les envoyer (en mauve) par rapport aux messages dont l&#39;envoi a échoué (en rouge). Il permet donc de voir la part des messages qui ne passent pas dans le délai imparti à cause de limitations par le serveur de statistiques (throttling) ou à cause de l&#39;indisponibilité de serveurs distants.
1. Connexions SMTP ouvertes ou en cours d&#39;ouverture.
1. Nombre approximatif de **mtachild**.

>[!NOTE]
>
>Ce rapport est relatif à l&#39;état du composant Email Traffic Shaper.

### Erreurs SMTP par domaine {#smtp-errors-per-domain}

Ce rapport permet de visualiser les erreurs d&#39;envoi, par période, réparties par domaine.

>[!NOTE]
>
>Les options **minConnectionsToLog**, **minErrorsToLog** et **minMessagesToLog** du fichier **serverConf.xml** définissent les seuils au-delà desquels les statistiques de connexion sont prises en compte.

![](assets/smtp_error_report.png)

La liste des indicateurs de ce rapport est proposée sous le tableau.

* La colonne **Domaine** contient les noms des domaines vers lesquels les messages sont envoyés (ou le nom du domaine possédant le domaine réel, par exemple yahoo.com pour yahoo.fr),
* La colonne **Cnx** affiche le nombre de connexions SMTP ouvertes pour ce domaine,
* La colonne **Envoyés** correspond au nombre de messages envoyés vers ce domaine,
* La colonne **Volume** affiche le volume de messages pour lesquels un envoi a été tenté vers ce domaine (valeur approximative),
* La colonne **Erreurs** affiche une représentation du volume des erreurs sur ce domaine pour la période,
* La colonne **Dernière réponse** affiche le message de la dernière réponse SMTP reçue pour ce domaine,
* La colonne **Date** affiche la date de la dernière réponse SMTP reçue pour ce domaine.

>[!NOTE]
>
>The values displayed in the **Cnx**, **Sent**, and **Volume** columns are calculated with respect to the period selected in the **[!UICONTROL Period]** field.

Cliquez sur un nom de domaine pour en visualiser les erreurs.

Elles sont classées par PublicId : cet identifiant correspond à une adresse IP partagée par plusieurs mta Adobe Campaign derrière un routeur. Le serveur de statistiques utilise cet identifiant pour mémoriser les statistiques de connexions et d&#39;envois entre ce point de départ et le serveur cible.

![](assets/smtp_error_report_details.png)

Le **[!UICONTROL Owner of domain]** champ vous permet de grouper différents noms de domaine sous la même étiquette. Dans la vue initiale du rapport, tous les noms de domaine MX seront associés à ce propriétaire.

Cliquez sur un identifiant PublicId pour en visualiser le détail.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>Le pourcentage d&#39;erreurs est représenté par deux graphiques. Le premier est une barre de progression horizontale sur fond noir. Le second graphique est chronologique. La période sélectionnée est divisée en douze intervalles de temps, chacun représenté par une barre de progression verticale. Dans les deux représentations, si aucune erreur n&#39;a été détectée, la barre est noire. La couleur de la barre varie en fonction du pourcentage d&#39;erreurs (jaune, puis orange, et enfin rouge). La couleur grise signifie qu&#39;aucun volume de données significatif n&#39;a été remonté. Il est possible d&#39;afficher le pourcentage exact d&#39;erreurs en positionnant le curseur de la souris sur un graphique.

>[!NOTE]
>
>Pour plus d&#39;informations sur les erreurs SMTP et leur gestion dans Adobe Campaign, consultez [cette section](../../installation/using/email-deliverability.md).

## Rapport de billing {#billing-report}

The **[!UICONTROL Billing]** technical workflow sends the system activity report to the &#39;billing&#39; operator by email. Il est déclenché par défaut le 25 de chaque mois.

Ce workflow technique se trouve dans un sous-dossier du nœud suivant : **Administration** > **Production** > **Workflows techniques**.

![](assets/billing.png)

Une fois le workflow démarré tous les 25 du mois, votre opérateur billing reçoit le rapport suivant dans sa boîte.

![](assets/billing_2.png)

Les mesures suivantes sont disponibles pour effectuer le suivi de vos diffusions :

* **[!UICONTROL Start date]** : Date de début de la livraison. Notez qu’il peut être antérieur à la date &quot;du&quot; du rapport.
* **[!UICONTROL Label]** : Étiquette de la diffusion. Deliveries that have less than 100 messages to send are considered too small and thus aggregated by start date, in which case the label displays the number of aggregates, e.g. [Aggregation of 3 small deliveries].
* **[!UICONTROL Total volume]** : Volume total d’octets transférés pour la remise.
* **[!UICONTROL Avg volume]** : Volume moyen d’octets transférés. Il s’agit du résultat de la formule suivante **(volume total / messages)**, qui est la base de calcul de la **[!UICONTROL Multiplier]** mesure.
* **[!UICONTROL Messages]** : Nombre de messages envoyés. Ceci inclut les messages qui ont été envoyés avec succès et les tentatives (après la réception d’un message de rebond du serveur contacté).
* **[!UICONTROL Multiplier (x)]** : La valeur du multiplicateur est déduite du volume moyen des messages.
* **[!UICONTROL Count]** : Résultat de la multiplication des messages et du multiplicateur.

## Surveillance automatique {#automatic-monitoring}

Adobe Campaign propose plusieurs techniques de monitoring automatique. Elles sont présentées ci-dessous.

### La ligne de commande {#command-line}

La commande

**nlserver monitor**

permet de lister un ensemble d&#39;indicateurs sur le système et les modules Adobe Campaign.

Elle génère une sortie au format XML qui peut être traitée facilement.

De plus, cette commande peut être lancée avec le paramètre **-missing** qui liste les processus manquants sur cette instance alors que, selon les fichiers de configuration, ils devraient se trouver en cours d&#39;exécution.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### Les informations publiées par le serveur {#information-published-by-the-server}

#### Le /r/test{#r-test}

La page **http(s)://`<application>`/r/test** est utilisée pour tester le serveur de redirection. Nous vous recommandons d’utiliser la même méthode pour tester les serveurs frontaux utilisés pour le suivi. Cette page peut également être utilisée pour tester un répartiteur de charge.

Elle affiche une ligne au format XML du type :

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**Fréquence** : il s&#39;agit d&#39;un test ne sollicitant pas de charge, il peut donc être lancé très régulièrement (toutes les secondes, par exemple).

#### Le /nl/jsp/ping.jsp{#nl-jsp-ping-jsp}

Cette page **http(s)://`<Application server url>`/nl/jsp/ping.jsp** fonctionne de la même manière que sa contrepartie réseau : il teste une requête complète qui passe par apache/tomcat/module Web/base de données et qui est téléchargée sur le client. Si tout fonctionne correctement, il renvoie &quot;OK&quot;. Nous vous recommandons d&#39;exécuter ce test sur les machines ayant accès aux bases de données (mtas et enquêtes, par exemple).

**Utilisation**: un jeton de session associé à une connexion d’opérateur doit être transmis en tant qu’argument pour se connecter à distance (voir l’astuce de la section Surveillance [automatique via les scripts](#automatic-monitoring-via-adobe-campaign-scripts)Adobe Campaign).

Par exemple :

![](assets/ncs_monitoring_ping.png)

L&#39;opérateur et son login doivent avoir été préalablement configurés dans la console cliente Adobe Campaign avec les droits sur les données de la base.

![](assets/ncs_operators_rights_01.png)

**Fréquence** : il s&#39;agit d&#39;un test sollicitant peu de charge, il peut donc être lancé assez souvent, mais pas plus d&#39;une fois par minute.

#### Le /nl/jsp/monitor.jsp{#nl-jsp-monitor-jsp}

Il s’agit d’un test permettant de vérifier qu’un opérateur peut accéder au serveur Adobe Campaign via une page Web ; la même page Web que celle accessible via les menus de la console client. Vous pouvez appeler cette page à partir de vos outils de surveillance (Tivoli, Nagios, etc.).

![](assets/ncs_monitoring_web.png)

**Utilisation**: un jeton de session associé à une connexion d’opérateur qui vous permet de vous connecter à l’instance doit être utilisé comme argument (voir l’astuce de la section Surveillance [automatique via les scripts](#automatic-monitoring-via-adobe-campaign-scripts)Adobe Campaign).

L&#39;opérateur et son login doivent avoir été préalablement configurés dans la console cliente Adobe Campaign avec les droits et les restrictions sur les données de la base.

**Fréquence** : il s&#39;agit d&#39;un test complet de tout le serveur, il n&#39;a pas à être lancé fréquemment (on peut l&#39;effectuer par exemple toutes les dix minutes).

#### Le /nl/jsp/soaprouter.jsp{#nl-jsp-soaprouter-jsp}

Ce **jsp** représente le point d&#39;entrée des API de l&#39;application Adobe Campaign. Il peut donc servir de monitoring fin de l&#39;application. Il peut également être utilisé pour surveiller les services web Adobe Campaign. Il est utilisé dans nos scripts de surveillance, néanmoins, il est réservé à des utilisateurs experts.

### Surveillance selon les types de déploiements {#monitoring-based-on-deployment-types}

Adobe Campaign permet différentes configurations de déploiement (voir [cette section](../../installation/using/hosting-models.md) à ce sujet). Dans cette section, sont détaillées les différentes techniques de monitoring automatique à appliquer selon le type d&#39;installation dont vous disposez.

<table> 
 <thead> 
  <tr> 
   <th> Type de déploiement </th> 
   <th> Contrôle  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Stand-alone </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> et <span class="uicontrol">/nl/jsp/monitor.jsp</span> sur le serveur Adobe Campaign</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Standard </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> et <span class="uicontrol">/nl/jsp/ping.jsp</span> sur les serveurs frontaux</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> sur le serveur applicatif</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Entreprise </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> et <span class="uicontrol">/nl/jsp/ping.jsp</span> sur les serveurs frontaux</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> et <span class="uicontrol">/nl/jsp/monitor.jsp</span> sur le serveur applicatif</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> sur le serveur applicatif</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Surveillance automatique via les scripts d&#39;Adobe Campaign {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign peut vous fournir un outil de surveillance des instances (netreport) qui permet d&#39;envoyer un rapport par e-mail sur les anomalies détectées.

![](assets/pro_netreport.png)

>[!CAUTION]
>
>Cet outil peut être utilisé pour surveiller votre instance mais il n&#39;est pas pris en charge par Adobe Campaign. Contactez votre administrateur de Campaign pour plus d&#39;informations.

### Eléments requis {#required-elements}

Pour une surveillance automatique, les précautions suivantes sont requises avant installation :

* You must have the **netreport.tgz **(Linux installation) or **netreport.zip** (Windows installation) files,
* il est fortement conseillé de ne pas installer le monitoring sur la machine à surveiller,
* il est indispensable que la machine sur laquelle il sera installé possède un JRE ou un JDK,
* sous Linux, la machine à surveiller doit posséder le package **bc**. Voir à ce sujet [cette section](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages).

### Procédure d&#39;installation {#installation-procedure}

La procédure d&#39;installation est la suivante :

1. Dans la console, créez, si besoin, un nouvel opérateur (l&#39;utilisateur &#39;monitoring&#39; existe déjà), sans lui attribuer de droits.
1. Lancez l&#39;extraction de l&#39;archive.
1. Read the **readme** file.
1. Update the **netconf.xml** configuration file.
1. Mettez à jour le fichier **netreport.bat** (Windows) ou **netreport.sh **(Linux).

### Configuration du fichier netconf.xml {#configuring-the-netconf-xml-file}

Le fichier XML de configuration contient les éléments suivants :

* [Elément &#39;properties&#39;](#properties--element)
* [Elément &#39;instance&#39;](#instance--element)
* [Elément &#39;host&#39;](#host--element)
* [Les sous-éléments](#sub-elements)

Voici un exemple de configuration :

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>Vous pouvez spécifier différentes configurations en ajoutant un suffixe au fichier **netconf.xml** , par exemple **netconf-dev.xml**, **netconf-prod.xml**, etc. Spécifiez ensuite la configuration à utiliser pour exécuter le netreport dans les fichiers **netreport.bat** ou **netreport.sh** en ajoutant **$JAVA_HOME/bin/java netreport dev** ou **@%JAVA_HOME%binjava netreport prod par exemple.**

>[!CAUTION]
>
>Pour que la connexion à l&#39;opérateur **monitoring** fonctionne, la machine sur laquelle le netreport est exécuté doit être dans une zone de sécurité en mode **sessionTokenOnly**. Si aucun masque IP de confiance n&#39;a été défini pour cet opérateur, la zone de sécurité doit être également en mode **allowEmptyPassword** et **allowUserPassword**.

#### Elément &#39;properties&#39;{#properties--element}

Cet élément permet de renseigner le paramétrage des mails, soit :

* **mailServer**: Serveur SMTP utilisé pour envoyer des courriers électroniques (p. ex. : smtp.domain.net).
* **mailFrom**: adresse électronique de l’expéditeur du rapport (p. ex. : monitoring@domain.net).
* **RecipientList**: liste des adresses électroniques des destinataires du contrôle. Les adresses doivent être séparées par des virgules (sans espaces).
* Le mode &quot;**nuit**&quot; (facultatif) permet d’éviter d’envoyer des courriers électroniques entre les heures spécifiées. Les données sont alors consolidées et un courrier électronique concernant l’activité nocturne est envoyé après l’heure de fin (7:00 par défaut).
* Le sous-élément **buildRange** (facultatif) vous permet de spécifier un nombre de versions minimal et maximal. Une erreur sera générée pour toutes les machines dont le numéro de version ne tombe pas dans cette plage

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* Vous pouvez ajouter un sous-élément **`<sla>`** (facultatif) dans l’élément **Propriétés** . Un fichier journal est généré chaque fois que le rapport réseau est exécuté. Le nom du fichier contient le nom de configuration et la date et l’heure, par exemple **dev_06_12_13_16_47_05.tmp**. Le fichier contient les informations suivantes : nom d’instance, nom de l’ordinateur, niveau de gravité, (0 à 3, du moins critique au plus critique), date (format d’horodatage), délai écoulé (en millisecondes) entre la requête et la réponse, service utilisé (http, ncs, ncsex, redirecteur). Ces informations sont séparées par des marques de tabulation et des sauts de ligne à la fin de chaque service.

>[!NOTE]
>
>L’attribut **persistHtmlFile** avec la valeur &quot;true&quot; sur l’ **`<property>`** élément sert à enregistrer le dernier état de surveillance dans le fichier **netreport.md**. Ce fichier est enregistré dans le répertoire d’installation.

#### Elément &#39;instance&#39;{#instance--element}

Cet élément permet de regrouper plusieurs machines (hosts) sous une même instance. Les noms d&#39;instances apparaissent dans la première partie de l&#39;e-mail de monitoring. Vous pouvez cliquer sur le nom d&#39;une instance pour accéder au détail de chacune des machines.

```
instance name="instanceName" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**: nom d’instance qui apparaîtra dans la première partie du courrier électronique.
* **RecipientList** (facultatif) : vous permet d’envoyer par courrier électronique un rapport de surveillance concernant une instance particulière.

#### Elément &#39;host&#39;{#host--element}

Cet élément paramètre la surveillance sur l&#39;host d&#39;un serveur donné, soit :

* **name**: nom de l&#39;ordinateur à surveiller.
* **alias** (facultatif) : nom de l&#39;ordinateur surveillé tel qu&#39;il apparaîtra dans le rapport.
* **sessionToken**: fournit une authentification de connexion via un jeton de session autorisé.

   Pour paramétrer le token de session, sélectionnez l&#39;opérateur **monitoring** dans la console Adobe Campaign. Dans l&#39;onglet **Droit d&#39;accès**, indiquez les adresses IP des machines autorisées à surveiller cette instance. Depuis ces machines, vous pourrez alors vous connecter à la page de monitoring avec l&#39;identifiant **monitoring** sans avoir besoin de spécifier de mot de passe.

   ![](assets/ncs_operators_rights_02.png)

* **CriticalLevel** (facultatif) : permet de trier les erreurs à afficher par niveau de gravité. Les valeurs possibles sont &quot;0&quot; (tous les niveaux affichés), &quot;1&quot; (seules les erreurs graves et élevées sont affichées) et &quot;2&quot; (seules les erreurs critiques sont affichées). Si cet attribut n’est pas fourni, tous les niveaux d’erreur s’affichent.
* **filter** (facultatif) : vous permet d’exclure certaines erreurs de flux de travaux, par exemple **filter=&quot;wkf;wkf1&quot;**. Les libellés de processus doivent être séparés par des points-virgules.

#### Les sous-éléments {#sub-elements}

* **tcp**: vérifie si le serveur est en marche ou en panne. Vous devez saisir un numéro de port.
* **http**: vérifie que le serveur Web existe (le serveur d’applications est opérationnel).
* **ncs**: vérifie les processus sur l’instance saisie dans l’attribut &quot;instance&quot; (erreurs de flux de travail, utilisation de la mémoire, etc.). L’attribut **includered** (obligatoire) vous donne la possibilité d’afficher les processus inactifs (valeurs &quot;true&quot; ou &quot;false&quot;).
* **redirecteur**: vérifie le suivi.

In most cases, only the **ncs** and **redir** sub-elements can be kept.

In any case, certain nodes can be overloaded in the sub-elements (e.g., the node **port=75** to overload the port used for the http, ncs or redir connection):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

Dans les sous-éléments **ncs**, **redirecteur** et **http** , vous pouvez ajouter l’attribut **isSecure (facultatif) pour choisir d’utiliser ou non le protocole https (valeurs &quot;true&quot; ou &quot;false&quot;).** Si cet attribut n’est pas fourni, le protocole http est utilisé.

### Configuration du fichier netreport.bat ou netreport.sh {#configuring-the-netreport-bat-or-netreport-sh--file}

Pour le configurer, éditez ce fichier et indiquez le répertoire dans lequel a été installé la JRE ou le JDK.

### Lancement du monitoring {#launching-monitoring}

Pour lancer la surveillance, exécutez le fichier **netreport.bat** ou **netreport.sh** à intervalles réguliers via un script. Un rapport est envoyé après la première exécution, puis uniquement en cas de changement d’état.

### Test du monitoring {#testing-monitoring}

To test the monitoring, execute the **netreport.bat** or **netreport.sh** file.

An email is sent to the recipients specified in the **recipientList** of the **netconf.xml** file.

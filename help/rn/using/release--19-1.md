---
title: Version 19.1
seo-title: Version 19.1
description: Version 19.1
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ba5496a008a28a29fc8e2032f31355a7c34f3ef8

---


# Version 19.1{#release-19-1}

## Version 19.1.6 - Version 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Cette version est destinée aux installations sur site uniquement. Pour les déploiements hybrides, les instances hébergées continueront à exécuter la version 9032. Ne mettez pas à niveau votre instance marketing vers la version 9035, car elle n’est pas compatible avec la version 9032.

3 octobre 2019

**Améliorations**

* Correction d’un problème lors de l’utilisation de CRM Connector for Salesforce. (NEO-17712)
* Correction d’un problème d’index qui pouvait entraîner des problèmes de performances lors de l’envoi de messages transactionnels.
* Correction d’un problème de performances lors de l’envoi de messages. (NEO-17558)
* Correction d’un problème en raison duquel certains messages ne pouvaient pas être traités par le serveur d’approvisionnement intermédiaire. (NEO-12395)
* Correction d’un problème qui empêchait l’utilisation complète de l’activité de gestion des données SQL (la &quot;gestion des données SQL&quot; nommée right était absente).

## Version 19.1.5 - Version 9033{#release-19-1-5-build-9033}

13 août 2019

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ou contactez le [support technique](https://support.neolane.net/).

**Améliorations**

* Correction d’un problème avec l’instruction SQL &quot;SELECT COUNT&quot; qui était exécutée sur la base de données par défaut plutôt que sur la base de données FDA lors de l’extraction des données dans l’activité de gestion des données.
* Pour améliorer les fonctionnalités de l’infrastructure client, une déclaration proxy SFTP est désormais disponible dans le fichier de configuration du serveur.
* Correction d&#39;un blocage de la console cliente lors de &quot;l&#39;ajout d&#39;une table liée&quot; dans l&#39;activité de workflow Chargement (SGBD) sans nom de table. (NEO-12213)
* Correction d&#39;un problème lié à l&#39;installation du package midEmetter via la ligne de commande.
* Une option d&#39;authentification a été ajoutée pour prendre en charge les identifiants OAuth dans le connecteur AC avec Microsoft Dynamics. (NEO-11982)
* Correction d’un problème avec UUID (Unique Universal Identifier) qui entraînait l’échec de l’activité d’enrichissement avec Hive FDA.

## Version 19.1.4 - Version 9032{#release-19-1-4-build-9032}

**17 décembre 2019**: nouvelle version (9032-9d34fb17e) qui comprend les correctifs suivants :

* Correction d’un problème de suivi sur les canaux de communication suivants : mobile (SMS, MMS), push (iOS, Android) et réseaux sociaux (Facebook, Twitter).
(NEO-19595)

**11 décembre 2019**: nouvelle version (9032-e28b428b7) qui comprend les correctifs suivants :

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ou contactez le [support technique](https://support.neolane.net/).

* Correction d’un problème de performances lors de l’envoi de messages avec une base de données MSSQL. (NEO-17558)

**20 novembre 2019**: nouvelle version (9032-3468c7bb5) qui comprend les correctifs suivants :

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ou contactez le [support technique](https://support.neolane.net/).

* Correction d’un problème de connexion via l’authentification IMS. (NEO-17312)
* Correction d’un problème lors de l’affichage de rapports cumulatifs sur plusieurs remises. (NEO-18165)
* Correction d’un problème susceptible de bloquer ou de provoquer le blocage du serveur Web.

**19 septembre 2019**: nouvelle version (9032-cee805c93) qui comprend les correctifs suivants :

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ou contactez le [support technique](https://support.neolane.net/).

* Correction d’un problème lors de l’utilisation de CRM Connector for Salesforce. (NEO-17712)
* Correction d’un problème d’index qui pouvait entraîner des problèmes de performances lors de l’envoi de messages transactionnels.

**13 août 2019**: version 19.1.4 initiale qui comprend les correctifs suivants :

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ou contactez le [support technique](https://support.neolane.net/).

* Correction d&#39;un problème lié à l&#39;activité du planificateur qui générait des messages d&#39;erreur indésirables lors de la configuration de l&#39;assistant. Annulation de la mise à jour à partir de NEO-11662. (NEO-17097)
* Correction d&#39;une régression causée par NEO-12727 qui entraînait l&#39;arrêt des workflows lorsqu&#39;une activité de test était exécutée deux fois. (NEO-16835)
* Correction d&#39;un problème qui entraînait le renvoi d&#39;un code HTTP erroné (HTTP 200 OK à la place de HTTP 403 Interdit) lorsqu&#39;un jeton de session non valide ou ayant expiré était utilisé dans les appels d&#39;API. (NEO-16826)
* Correction d&#39;un problème lié à la clé DKIM qui n&#39;était plus incorporée dans les emails, ce qui entraînait des problèmes de délivrabilité. (NEO-16804)
* Correction de divers problèmes liés à la planification des workflows. Les workflows devaient être exécutés une fois par jour sans tenir compte de la configuration du planificateur. (NEO-16619, NEO-16426)

## Version 19.1.2 - Version 9029{#release-19-1-2-build-9029}

21 juin 2019

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ou contactez le [support technique](https://support.neolane.net/).

**Améliorations de la sécurité**

* Pour optimiser la sécurité, la bibliothèque Java (Netty) a été mise à jour vers la dernière version (4.1.34). (NEO-12788)

**Améliorations**

* Correction d&#39;une régression liée à la gestion des colonnes sdomain qui empêchait l&#39;envoi d&#39;emails sur certaines configurations.
* Pour améliorer les performances, un attribut _operation=&quot;none&quot; a été ajouté aux appels SOAP de rtEvent afin d&#39;éviter les requêtes &quot;SELECT FOR UPDATE&quot;.
* Correction d’un problème d’affichage du flux de travail avec les transitions sortantes après l’activité de test. (NEO-12727)
* Nous autorisons maintenant la suppression des enregistrements factices créés dans Microsoft Dynamics lors du workflow d&#39;import.
* Améliorations des permissions pour exécuter le package de zone de sécurité lors de l&#39;utilisation d&#39;un compte interne.

## Version 19.1 - Version 9026{#release-19-1-build-9026}

30 mai 2019

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ou contactez le [support technique](https://support.neolane.net/).

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> Fonctionnalités<br /> </th> 
   <th> Description<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Panneau de contrôle<br /> </td> 
   <td> <p>Pour accroître l'efficacité de votre tâche d'administrateur, gérez les paramètres de vos serveurs SFTP en surveillant le stockage, en whitelistant des adresses IP et en installant des clés SSH pour chaque instance. Veuillez noter, qu'à l'heure actuelle, le panneau de configuration est uniquement disponible pour les clients hébergés sur AWS (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">connectez-vous dès aujourd'hui via Experience Cloud</a>).</p> <p>Pour plus d'informations, consultez la <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">documentation détaillée</a> et la <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">vidéo de procédure</a>. </p><p>Remarque : la mise à niveau vers la dernière version de Campaign n’est pas requise pour accéder au Panneau de configuration.</p> </td> 
  </tr> 
    <tr> 
   <td> Suivi<br /> </td> 
   <td> <p>En tant qu'administrateur, augmentez votre productivité en surveillant et en gérant les modifications apportées dans l'instance Adobe Campaign Classic. Le Suivi consigne les actions effectuées sur les schémas sources, les workflows et les options. Vous pouvez déterminer rapidement si un élément a été créé, modifié ou supprimé.</p><p>Pour plus d'informations, consultez la <a href="../../production/using/audit-trail.md">documentation détaillée</a> et visualisez la <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">vidéo pratique</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Barrière de sécurité, robustesse et évolutivité<br /> </td> 
   <td> Nous avons ajouté une série d'améliorations à Campaign Classic. Les améliorations en termes de barrière de sécurité, de robustesse et d'évolutivité sont répertoriées ci-dessous.<br /> </td> 
  </tr> 
  <tr> 
   <td> Mise à jour de la matrice de compatibilité<br /> </td> 
   <td> Avec cette nouvelle version, Adobe Campaign prend maintenant en charge les systèmes de bases de données suivants. Consultez la <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matrice de compatibilité</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* Pour des motifs de sécurité, vous ne pouvez plus insérer de commandes arbitraires lorsque vous utilisez l&#39;option **[!UICONTROL Inclure un pré-traitement du fichier]** dans une activité de workflow **[!UICONTROL Chargement (fichier)]**. Une liste déroulante vous permet dorénavant de sélectionner parmi 3 options : **[!UICONTROL Aucun]**, **[!UICONTROL Décompression]** (zcat) ou **[!UICONTROL Déchiffrer]** (gpg). Le flag de sécurité XtkSecurity_Disable_Preproc a été ajouté. Pour les nouveaux clients, cette option sera définie sur 0, tandis que pour les clients existants, elle sera définie sur 1 par le postupgrade de façon à conserver le comportement précédent. Consultez [cette section](../../workflow/using/data-loading--file-.md).
* Correction d&#39;un problème de visibilité du mot de passe qui se produisait lors du test de la connexion d&#39;un compte externe FDA sans fuseau horaire défini.
* La bibliothèque PDFBox a été supprimée.
* Tomcat a été mis à jour vers la version 7.0.93.
* Correction d&#39;un problème de visibilité du jeton qui se produisait lorsque le jeton de sécurité n&#39;était pas valide.
* Correction d&#39;un problème d&#39;injection XTK potentiel dans le JSP WSDL (schemawsdl.jsp).
* Le stockage des informations de connexion et des mots de passe a été optimisé dans la mémoire et le code source de l&#39;application.
* La restriction d&#39;affichage des PII a été optimisée. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Correction de problèmes d&#39;incohérence dans la gestion des clés secrètes.
* La même erreur générique s&#39;affiche désormais pour les échecs de connexion avec un nom d&#39;utilisateur valide ou non.
* Le nommage des fichiers téléchargés a été amélioré.
* Une nouvelle option XtkSecurity_Disable_GetSetEnv a été ajoutée afin de bloquer l&#39;utilisation des fonctions setEnv et getEnv.
* Les informations sensibles sont désormais masquées dans le suivi de la pile d’applications.

**Améliorations de la sécurité, de la robustesse et de l&#39;évolutivité**

* Optimisation de l&#39;utilisation de la séquence XtkNewId et de sa durée de vie : les tables les plus gourmandes ont été déplacées de la séquence xtkNewId vers les séquences dédiées. [En savoir plus](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA via HTTP v2 : le protocole FDA via HTTP est largement utilisé sur les déploiements hybrides, en particulier pour la préparation des diffusions et la récupération des broadLogs. Sa robustesse a été renforcée de façon à éviter les problèmes réseau et les erreurs possibles lors de la récupération ou de l&#39;envoi de données. Pour cela, les builds aux deux extrémités de la connexion doivent être à jour, sans quoi le protocole antérieur sera encore utilisé.
* Workflow de tracking : la robustesse du workflow de tracking a été améliorée. Plusieurs problèmes liés aux mises à jour/insertions au niveau des logs de tracking et à la personnalisation du tracking d&#39;URL ont été résolus. En outre, le processus de suivi détecte désormais les problèmes du journal de suivi qui peuvent entraîner des erreurs et arrêter le flux de travail. Ces problèmes sont maintenant ignorés et ne sont pas traités.
* Workflow de nettoyage : le workflow de nettoyage a été amélioré de manière à éviter les erreurs et arrêts potentiels. Cela optimise la taille et la performance des bases de données.
* Images incorporées dans les messages transactionnels : nous avons ajouté la prise en charge complète des images incorporées dans les messages transactionnels dans le but d&#39;éviter les possibles blocages ou images manquantes.
* Taille de la base de données - XtkJobLog : un mécanisme de purge a été ajouté à cette table. Cela a un impact positif sur la taille de la base de données.
* Archivage des emails en Cci : les paramètres par défaut de l&#39;archivage des emails en Cci ont été modifiés en vue d&#39;accélérer l&#39;archivage. [En savoir plus](../../installation/using/email-archiving.md#parameters)
* Mise à jour de la structure des bases de données : les demandes SQL générées par l&#39;assistant de mise à jour de la base de données ont été améliorées dans le but d&#39;accélérer l&#39;exécution.
* Barrières de sécurité pour les actions des opérateurs : plusieurs barrières de sécurité ont été mises en place afin d&#39;empêcher les opérateurs de réaliser des actions susceptibles d&#39;impacter l&#39;intégrité de la plate-forme. Les schémas natifs ne peuvent plus être supprimés via l&#39;interface. En outre, le code XML source d&#39;un workflow ne peut plus être édité par les utilisateurs non administrateurs.
* Deux nouvelles options sont disponibles : **XtkSecurity_Restrict_EditXML** (qui vous permet de désactiver l&#39;édition du code XML des diffusions) et **NmsOperation_OperationMgtDebug** (qui vous permet de surveiller l&#39;exécution du workflow technique operationMgt). [En savoir plus](../../installation/using/configuring-campaign-options.md)

**Autres changements**

* Notifications push : nous prenons maintenant en charge l&#39;option Thread Id pour iOS push.
* Amélioration de la gestion des index aux noms longs qui pouvait créer des problèmes lors du postupgrade.
* Désormais, lors de l&#39;analyse d&#39;une diffusion Deco-mail, si le mode de publication est défini sur **[!UICONTROL Aucun]** dans l&#39;assistant de déploiement, une erreur est consignée et l&#39;analyse s&#39;arrête : « Le mode de publication est défini sur Aucun : impossible d&#39;incorporer d&#39;image. Les images ne s&#39;afficheront pas sur le téléphone polyvalent. » (NEO-12208)
* La gestion des broadlogs a fait l&#39;objet d&#39;améliorations en ce qui concerne les messages transactionnels. Lorsque les broadlogs sont synchronisés à partir de l&#39;instance d&#39;exécution vers l&#39;instance de contrôle, le champ @lastModified est mis à jour selon la date courante du système. L&#39;option MC_Update_BlLastModified a été ajoutée pour les instances de contrôle. Vrai signifie que la date courante sera utilisée pour l&#39;instance de contrôle (comportement par défaut). Faux signifie que nous utilisons la date @lastModified du broadlog de l&#39;instance d&#39;exécution. (NEO-12579)
* Des index ont été ajoutés aux tables temporaires de coupons pour optimiser l&#39;envoi des diffusions. (NEO-12437)
* Dans l&#39;intégration Analytics, la récupération des données de segments AAM avec le caractère % est maintenant autorisée. (NEO-12025)
* Suppression de la limite de 10 000 enregistrements dans la carte thermique des workflows afin de résoudre un problème de données manquantes. (NEO-12329)
* Open Office n&#39;est pas pris en charge et a été complètement supprimé de l&#39;application. Si vous l&#39;utilisiez encore, passez à Libre Office, car il cessera de fonctionner à compter de la version 19.1.
* Vous pouvez maintenant limiter l&#39;accès en écriture à l&#39;activité Mise à jour de données au sein du workflow au moyen d&#39;attributs sysfilter. [En savoir plus](../../configuration/using/filtering-schemas.md)

**Correctifs**

* Correction d&#39;un problème qui empêchait le téléchargement du certificat pour les notifications iOS mobile push.
* Correction du problème potentiel de blocages de serveur récurrents pour les notifications push transactionnelles. D&#39;autres problèmes de blocage ont été résolus.
* Correction d&#39;un problème qui entraînait des incohérences au niveau du reporting entre les activités utilisateurs et les rapports de tracking pour l&#39;indicateur d&#39;ouverture des diffusions. (NEO-11742)
* Correction d&#39;une erreur liée à la connexion IMS.
* Correction d&#39;un problème qui pouvait causer l&#39;absence d&#39;images dans une diffusion lors de l&#39;ajout d&#39;une image de la bibliothèque. (NEO-11900)
* Correction d&#39;un problème qui pouvait se produire lors de l&#39;extraction des détails d&#39;une offre dans une diffusion courrier. (NEO-11700)
* Correction d&#39;une erreur qui pouvait altérer la performance des messages transactionnels par SMS. (NEO-9812)
* Correction des blocages de console qui pouvaient se produire lors de l&#39;utilisation de l&#39;option Définie dans un fichier externe pour la cible principale d&#39;une diffusion. (NEO-12349)
* Correction d&#39;un problème lors de l&#39;analyse d&#39;un message qui ciblait des destinataires de domaines japonais (.JP). (NEO-12246)
* Correction d&#39;un problème d&#39;affichage lors de l&#39;utilisation d&#39;une répartition des valeurs avec un lien 1:N. (NEO-12212, NEO-11820)
* Correction d&#39;un problème qui pouvait entraîner des erreurs NmsMxDomain dans les logs MTA à la suite d&#39;un postupgrade. (NEO-12752)
* Correction d&#39;un problème qui survenait lors de l&#39;utilisation de l&#39;option « Conserver toutes les données additionnelles de l&#39;ensemble principal » dans une activité de workflow d&#39;enrichissement. (NEO-13291)
* Correction d&#39;un problème de blocage Tomcat lors de l&#39;envoi de notifications push via HTTP2. (NEO-12701)
* Correction d&#39;un problème avec l&#39;API HTTPRequest qui n&#39;attendait pas la fin de l&#39;ensemble des callbacks. (NEO-12628)
* Correction d&#39;un problème avec le processus de calcul des indicateurs de tracking pour les messages transactionnels. (NEO-12529)
* Correction d&#39;un problème lié à l&#39;utilisation des thèmes dans la gestion des offres. (NEO-11804)
* Correction d&#39;un problème de performances lors de l&#39;envoi de notifications push. (NEO-11787)
* Correction d&#39;un problème lors de la prévisualisation d&#39;un fichier XML ou CSV sortant dans la gestion des offres pour une diffusion courrier. (NEO-11290)
* Correction d&#39;un problème lors de l&#39;installation du package **Gestion des réseaux sociaux**(Social Marketing). (NEO-12081)
* Correction d&#39;un problème qui vous empêchait de supprimer une application web, même si vous disposiez des droits d&#39;accès adaptés. (NEO-12072)
* Correction d&#39;un problème qui pouvait entraîner le remplacement de certaines valeurs lors de l&#39;export d&#39;un objet via XML et de son import ultérieur. L&#39;option XtkExport_IncludeDefaultValues a été ajoutée. Si elle est définie sur Vrai (comportement par défaut), toutes les valeurs sont exportées, alors que si elle est définie sur Faux, les modifications sont remplacées par la valeur par défaut. (NEO-11979)
* Correction d&#39;un problème qui causait l&#39;échec de l&#39;activité de workflow **[!UICONTROL Alerte]** lors de l&#39;ajout d&#39;une activité d&#39;enrichissement après une requête. (NEO-12132)
* Correction d&#39;un problème sur les installations Oracle dans lesquelles les décalages de pipeline (déclencheurs) n&#39;étaient pas récupérés correctement à partir de la base de données, entraînant des doublons. (NEO-12121)
* Correction d&#39;un problème qui pouvait entraîner des problèmes d&#39;affichage dans les tableaux croisés dynamiques lors de l&#39;utilisation de l&#39;intégration Analytics (NEO-12103)
* Correction d&#39;un problème lié au rapport Analyse descriptive. (NEO-11414)
* Correction d&#39;un problème avec les connecteurs CRM qui se produisait lorsque la table distante comprenait un nom de champ avec un caractère de soulignement.
* Correction d&#39;un problème d&#39;affichage des symboles de devise dans les rapports des hypothèses. (NEO-11634)
* Correction d&#39;un problème lié à la redirection et au tracking lors de l&#39;utilisation de certains caractères dans les liens de tracking.
* Correction d&#39;un problème qui empêchait le bon fonctionnement de la prévisualisation de l&#39;offre.
* Correction d&#39;un problème qui faisait que les erreurs soft n&#39;étaient pas supprimées de la table d&#39;adresses.
* Correction d&#39;une erreur JAVA lors de l&#39;utilisation de code-barres.
* Correction d&#39;un problème de traduction dans les applications web (NEO-12460)
* Correction d&#39;un problème avec l&#39;activité de workflow Transfert de fichier s3. (NEO-12473)
* Correction d&#39;un problème avec les champs de date dans les applications web. (NEO-12496)
* Correction d&#39;un problème d&#39;épuisement des ID lors de l&#39;utilisation d&#39;adresses de contrôle dans une diffusion. (NEO-11842)
* Correction d&#39;un problème lié à phantomjs et à la compatibilité avec Debian 9.
* Correction d&#39;une erreur lors de la validation du contenu d&#39;un BAT. (NEO-12725)
* Correction d&#39;un problème avec la fonctionnalité de workflow « Exclure ce sous-ensemble de la population ». (NEO-12441)
* Correction d&#39;un problème avec l&#39;API HTTPRequest-wait qui n&#39;attendait pas la fin de l&#39;ensemble des callbacks. (NEO-12628)
* Correction d&#39;un problème avec la tâche « Mise à jour d&#39;audience partagée » dans une activité de partage. (NEO-11562)
* Correction d&#39;un problème de blocage de serveur web. (NEO-12904)
* Correction d&#39;un problème avec le paramètre Nature dans les modèles transactionnels. (NEO-12334)
* Correction d&#39;un problème de blocage de console lors de l&#39;affichage des URL trackées dans l&#39;éditeur de texte des emails. (NEO-13122)
* Correction d&#39;un problème lié à l&#39;activité de partage de fichiers lors de l&#39;import d&#39;audiences à partir d&#39;Audience Manager. (NEO-11550)
* Correction d&#39;un problème qui entraînait des erreurs dans le rapport Position des clics. (NEO-11459)
* Correction d&#39;un problème avec le rendu des offres. (NEO-11565)
* Correction d&#39;un problème lié à l&#39;activité Mise à jour de liste lors de l&#39;import d&#39;audiences à partir d&#39;Audience Manager. (NEO-11226)
* Correction d&#39;un problème avec l&#39;activité Planning et la configuration du fuseau horaire. (NEO-11662)
* Correction d&#39;un problème qui entraînait l&#39;échec du workflow de tracking en présence d&#39;URL incorrectes.
* Correction d&#39;un problème avec les comptes externes suite à l&#39;import du package d&#39;application mobile.
* Correction d&#39;un problème lors de l&#39;assignation d&#39;un fuseau horaire à un opérateur. (NEO-12464)
* Correction d&#39;un problème qui pouvait entraîner des erreurs dans les logs mtachild. (NEO-11539, NEO-8978)
* Correction d&#39;un problème lors d&#39;un clic sur l&#39;icône Historique dans un rapport enregistré. (NEO-11620)
* Correction d&#39;un problème lors de l&#39;édition d&#39;un tableau croisé dynamique dans un rapport. (NEO-12068)

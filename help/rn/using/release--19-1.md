---
product: campaign
title: Notes de mise à jour de Campaign 19.1
description: Notes de mise à jour de Campaign 19.1
exl-id: 8540b5f0-194b-45f3-b497-5d30efb318b8
source-git-commit: 2a92cfc705e27332cfdf8c7357a6a03c84dc6c9f
workflow-type: tm+mt
source-wordcount: '3303'
ht-degree: 98%

---

# Version 19.1{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) Version 19.1.8 - Build 9039 {#release-19-1-8-build-9039}

__

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n&#39;est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_22 mars 2021_

* Correction d&#39;une régression qui empêchait l&#39;utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453, NEO-31454)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n&#39;est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_16 décembre 2020_

>[!CAUTION]
>
> * Cette version s’accompagne d’un nouveau protocole de connexion : si vous vous connectez à Campaign via le Service d&#39;identités Adobe (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console cliente puissent se connecter après le **30 juin 2021**. [En savoir plus](../../technotes/ims-updates.md)
> * Cette version s&#39;accompagne d&#39;un [correctif de sécurité](https://helpx.adobe.com/fr/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.
> * Si vous utilisez l&#39;intégration Experience Cloud Triggers par le biais de l&#39;authentification oAuth, vous devez passer à Adobe I/O comme décrit [sur cette page](../../integrations/using/configuring-adobe-io.md). L’ancien mode d’authentification oAuth avec Campaign [a été retiré](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) le **18 août 2021**. Les environnements hébergés bénéficient d’une extension jusqu’au **30 novembre 2021**. En tant que client on-premise ou hybride, contactez l’assistance clientèle d’Adobe pour étendre l’assistance jusqu’au 30 novembre 2021. Vous devez fournir [l’AppID de l’application OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) à Adobe.



**Améliorations**

* Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme d&#39;authentification IMS.
* L’authentification de l’intégration des Triggers basée à l&#39;origine sur la configuration de l&#39;authentification oAUTH pour accéder au pipeline a été modifiée et déplacée vers Adobe I/O. [En savoir plus](../../integrations/using/configuring-adobe-io.md)
* Après la fin de la prise en charge du protocole binaire hérité des APN iOS, toutes les instances utilisant ce protocole sont mises à jour vers le protocole HTTP/2 durant la mise à niveau.
* Correction d’un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)
* Correction d&#39;un problème en raison duquel le connecteur SMPP était désactivé après une erreur de connexion, ce qui empêchait l&#39;envoi d&#39;autres diffusions SMS et provoquait des problèmes de performances.
* Correction d’un problème qui affichait des pourcentages incorrects lors de la génération d’un rapport descriptif via une activité de workflow. (NEO-14314)
* Correction d&#39;un problème de préparation de diffusion lorsque l&#39;option **Exclure les adresses en double lors de la diffusion** était désélectionnée. (NEO-13240)
* Correction d&#39;un problème en raison duquel les workflows échouaient lors de l&#39;exécution d&#39;une activité d&#39;**enrichissement**. (NEO-17338)
* Correction d’un problème dans les workflows lors de la récupération d’enregistrements d’une base de données externe et de leur insertion dans la base de données Campaign. (NEO-26359)
* Correction d’un problème de blocage du serveur en empêchant la corruption de la mémoire lors du nettoyage de l’analyseur d’expressions.
* Correction d&#39;un problème en raison duquel la fonction **NoNull** ne fonctionnait pas dans les bases de données Oracle après la mise à niveau vers la version 9032. (NEO-26488)
* Correction d’un problème lors de la modification de la description d’un modèle de campagne qui empêchait l’affichage du bouton **Enregistrer** pendant la copie et le collage de symboles, comme des caractères japonais. (NEO-27071)
* Correction d’un problème qui empêchait l’enregistrement de la description d’une campagne ou d’un modèle de campagne en cliquant en dehors de la fenêtre avant de cliquer sur le bouton **Enregistrer**. (NEO-27449)
* Correction d’un problème au niveau de la configuration du proxy qui empêchait la connexion à Adobe Campaign après la dernière mise à jour de Windows 10. (NEO-27813)
* Correction d’un problème lié à la gestion des lignes vides dans les fichiers de log, en raison duquel le comportement du processus MTA était défaillant et les performances de l&#39;envoi de diffusions diminuaient.

**Évolutions techniques**

Tomcat a été mis à jour de la version 7 (7.0.103) vers la version 8 (8.5.57). Le répertoire `tomcat-7` a été remplacé par un répertoire `tomcat-8`. Sous Windows, _iis_neolane_setup.vbs_ et _apache_neolane.conf_ sont maintenant installés dans le répertoire `conf` (au lieu de `tomcat-7/conf`). Sous Linux, _apache_neolane.conf_ est maintenant installé dans le répertoire `conf`.

Sous Linux, le démarrage du service nlserver utilise désormais une unité systemd au lieu du script /etc/init.d/nlserver6. La migration vers le nouveau schéma de démarrage est effectuée automatiquement lors de l’installation du package 19.1.8. Le serveur /etc/init.d/nlserver6 est encore fourni, mais pour interagir avec le service nlserver (démarrage, redémarrage, arrêt, etc.), nous vous recommandons d’utiliser directement la commande systemctl.

## ![](assets/do-not-localize/red_2.png) Version 19.1.7 - Build 9036 {#release-19-1-7-build-9036}

_15 septembre 2020_

**Améliorations**

* Amélioration de nlsrvmod pour l&#39;utilisation du thread Apache 2.4 afin de corriger les blocages nlsrvmod.
* Correction d&#39;un problème lors de l&#39;utilisation de l&#39;activité de transfert de fichiers avec un compte externe Azure et un chiffrement SSL. La connexion a été effectuée via HTTP au lieu de HTTPS. (NEO-26720)
* Correction d&#39;un problème lié au mécanisme de cache d&#39;URL qui ne récupérait pas le libellé ou la catégorie.
* Correction d&#39;un problème en raison duquel les URL de page miroir étaient incorrectement définies dans les diffusions par email (en raison d&#39;un contrôle incorrect des caractères ASCII). (NEO-26084)
* La liste jarsToSkip de catalina.properties a été mise à jour afin de supprimer la référence à un fichier jar qui n’était plus utilisé (notifications iOS).
* Correction d&#39;un problème de régression qui empêchait la publication après le postupgrade.
* Correction d&#39;un problème de régression lié aux rapports de diffusion d&#39;usine qui s&#39;affichaient tronqués lors de l&#39;export au format PDF. (NEO-25757)
* Correction d&#39;un problème en raison duquel la valeur du paramètre de codage était supprimée lors de la redirection à partir d&#39;une URL de tracking (impact sur les caractères japonais). (NEO-25637)
* Correction d&#39;un problème en raison duquel les liens non signés provenant de domaines personnalisés étaient bloqués au lieu d&#39;être autorisés. (NEO-25210)
* Correction d&#39;une régression qui affectait les champs calculés d&#39;un workflow et provoquait l&#39;échec de ce workflow. (NEO-25194)
* Correction d&#39;un problème de compatibilité avec Microsoft Dynamics (à partir de la version 8.2) qui empêchait l&#39;exécution de certains appels d&#39;API (RetrieveAllEntities). (NEO-24528)
* Correction d&#39;un problème de régression lors de l&#39;utilisation de la fonction ACS Connector qui empêchait la connexion à une instance de Campaign Standard (gestion incorrecte de la connexion FOH/FOH2). (NEO-23433)
* Correction d&#39;un problème de régression concernant la connexion à la base de données qui provoquait le redémarrage constant du serveur web en raison d&#39;un problème de codage de base de données. Ce problème pouvait conduire à une surconsommation. (NEO-23264)
* Correction d&#39;un problème lié au workflow de nettoyage de la base de données qui pouvait échouer en raison d&#39;une source de données non gérée. (NEO-23160, NEO-23364)
* Le workflow de nettoyage purge désormais les listes expirées par lots de 100 plutôt qu&#39;une par une.
* Après le passage au [nouveau mécanisme d’identifiant de séquence](https://helpx.adobe.com/fr/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), toutes les applications web qui mettent à jour la table des destinataires sont republiées pendant le postupgrade.
* Correction d’un problème qui empêchait l’envoi d’emails lorsque du code JavaScript se trouvait en dehors de la balise de contenu HTML. (NEO-18628)
* Correction d’un problème qui empêchait la mise à jour des indicateurs de tracking des messages transactionnels par le workflow de tracking. (NEO-17770)
* Amélioration des performances de l&#39;assistant de mise à jour de la base de données afin de réduire le nombre d&#39;instructions SQL dans le but d&#39;optimiser le temps de réponse.
* Correction d’un problème de blocage de la console qui pouvait se produire lors de la dévérification des URL trackées dans un email, à partir de l’onglet **Contenu texte** en raison d’une variable non initialisée. (NEO-13545)
* Correction d&#39;un problème qui empêchait le téléchargement de fichiers dans une activité de transfert de fichiers à l&#39;aide d&#39;un compte de stockage Azure Blob externe en raison d&#39;une variable non initialisée (m_pCurlReader). (NEO-13717)
* Correction d&#39;un problème de postupgrade qui désactivait Apache et le serveur Web avant la republication de l&#39;application web. (NEO-27155)
* Correction d&#39;une régression en raison de laquelle un fuseau horaire incorrect était sélectionné lors de la définition de l&#39;heure dans une activité de workflow **Planificateur**.

## ![](assets/do-not-localize/red_2.png) Version 19.1.6 - Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Ce build est destiné aux installations on-premise uniquement. Pour les déploiements hybrides, les instances hébergées continueront à exécuter le build 9032. Ne mettez pas à niveau votre instance marketing vers le build 9035, car il n’est pas compatible avec la version 9032.

_3 octobre 2019_

**Améliorations**

* Correction d’un problème lors de l’utilisation du connecteur CRM pour Salesforce. (NEO-17712)
* Correction d’un problème d’index qui pouvait entraîner des problèmes de performances lors de l’envoi de messages transactionnels.
* Correction d’un problème de performances lors de l’envoi de messages. (NEO-17558)
* Correction d’un problème en raison duquel certains messages ne pouvaient pas être traités par le serveur de mid-sourcing. (NEO-12395)
* Correction d’un problème qui empêchait l’utilisation complète de l’activité de gestion des données SQL (le droit nommé « SQL Data Mangement » était absent).

## ![](assets/do-not-localize/red_2.png) Version 19.1.5 - Build 9033{#release-19-1-5-build-9033}

_13 août 2019_

**Améliorations**

* Correction d&#39;un problème lié à l&#39;instruction SQL &#39;SELECT COUNT&#39; qui était exécutée sur la base de données par défaut plutôt que sur la base de données FDA lors de l&#39;extraction de données dans l&#39;activité Data Management.
* Pour améliorer les capacités de l&#39;infrastructure client, une déclaration de proxy SFTP est maintenant disponible dans le fichier de configuration du serveur.
* Correction d’un problème de blocage en raison duquel le champ **Ajouter une table liée** était vide dans l’activité de workflow **Chargement (SGBD)**. (NEO-12213)
* Correction d&#39;un problème lié à l&#39;installation de packages midEmitter via la ligne de commande.
* Une option d&#39;authentification a été ajoutée pour prendre en charge les identifiants OAuth dans le connecteur AC avec Microsoft Dynamics. (NEO-11982)
* Correction d&#39;un problème lié à la gestion de l&#39;UUID (Unique Universal Identifier) en raison duquel les activités de workflow de requête et de chargement des données échouaient avec Hive FDA.
* Correction d’une régression sur Oracle en raison de laquelle certaines fonctions étaient considérées comme non valides après la mise à niveau. (NEO-12759)
* Correction d&#39;une régression qui entraînait le choix d&#39;un fuseau horaire incorrect lors de la définition de l&#39;heure dans une activité de workflow Planificateur.

## ![](assets/do-not-localize/green_2.png) Version 19.1.4 - Build 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>Les versions 19.1.4 [!DNL Gold Standard] sont répertoriées dans cette [page](../../rn/using/gold-standard.md).


## ![](assets/do-not-localize/red_2.png) Version 19.1.2 - Build 9029{#release-19-1-2-build-9029}

_21 juin 2019_

**Améliorations de la sécurité**

* Pour optimiser la sécurité, la bibliothèque Java (Netty) a été mise à jour vers la dernière version (4.1.34). (NEO-12788)

**Améliorations**

* Correction d&#39;une régression liée à la gestion des colonnes sdomain qui empêchait l&#39;envoi d&#39;emails sur certaines configurations.
* Pour améliorer les performances, un attribut _operation=&quot;none&quot; a été ajouté aux appels SOAP de rtEvent afin d&#39;éviter les requêtes &quot;SELECT FOR UPDATE&quot;.
* Correction d&#39;un problème d&#39;affichage de workflow lié aux transitions sortantes après l’activité Test. (NEO-12727)
* Nous autorisons maintenant la suppression des enregistrements factices créés dans Microsoft Dynamics lors du workflow d&#39;import.
* Améliorations des permissions pour exécuter le package de zone de sécurité lors de l&#39;utilisation d&#39;un compte interne.

## ![](assets/do-not-localize/red_2.png) Version 19.1 - Build 9026{#release-19-1-build-9026}

_30 mai 2019_

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
   <td> <p>Pour travailler plus efficacement en tant qu'utilisateur administrateur, gérez les paramètres de vos serveurs SFTP en surveillant le stockage, ajoutez des adresses IP à la liste autorisée et installez des clés SSH pour chaque instance. Veuillez noter qu’à compter d’aujourd’hui le panneau de contrôle n’est disponible que pour les clients hébergés sur AWS (<a href="https://experiencecloud.adobe.com/fr/campaign/controlpanel/">connectez-vous par l’intermédiaire d’Experience Cloud dès aujourd’hui</a>).</p> <p>Pour plus d'informations, consultez la <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr">documentation détaillée</a> et la <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=fr">vidéo de procédure</a>. </p><p>Remarque : Il n'est pas nécessaire d'effectuer une mise à niveau vers le dernier build de Campaign pour accéder au panneau de contrôle.</p> </td> 
  </tr> 
    <tr> 
   <td> Suivi<br /> </td> 
   <td> <p>En tant qu'administrateur, augmentez votre productivité en surveillant et en gérant les modifications apportées dans l'instance Adobe Campaign Classic. Le Suivi consigne les actions effectuées sur les schémas sources, les workflows et les options. Vous pouvez déterminer rapidement si un élément a été créé, modifié ou supprimé.</p><p>Pour plus d'informations, consultez la <a href="../../production/using/audit-trail.md">documentation détaillée</a> et visualisez la <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html?lang=fr">vidéo pratique</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Barrière de sécurité, robustesse et évolutivité<br /> </td> 
   <td> Nous avons ajouté une série d'améliorations à Campaign Classic. Les améliorations en termes de barrière de sécurité, de robustesse et d'évolutivité sont répertoriées ci-dessous.<br /> </td> 
  </tr> 
  <tr> 
   <td> Mise à jour de la matrice de compatibilité<br /> </td> 
   <td> Avec cette nouvelle version, Adobe Campaign prend maintenant en charge les systèmes de bases de données suivants. Consultez la <a href="https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html">Matrice de compatibilité</a>.<br /> 
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
* Les informations sensibles sont désormais masquées dans la trace de la pile d’applications.

**Améliorations de la sécurité, de la robustesse et de l&#39;évolutivité**

* Optimisation de l&#39;utilisation de la séquence XtkNewId et de sa durée de vie : les tables les plus gourmandes ont été déplacées de la séquence xtkNewId vers les séquences dédiées. [En savoir plus](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA via HTTP v2 : le protocole FDA via HTTP est largement utilisé sur les déploiements hybrides, en particulier pour la préparation des diffusions et la récupération des broadLogs. Sa robustesse a été renforcée de façon à éviter les problèmes réseau et les erreurs possibles lors de la récupération ou de l&#39;envoi de données. Pour cela, les builds aux deux extrémités de la connexion doivent être à jour, sans quoi le protocole antérieur sera encore utilisé.
* Workflow de tracking : la robustesse du workflow de tracking a été améliorée. Plusieurs problèmes liés aux mises à jour/insertions au niveau des logs de tracking et à la personnalisation du tracking d&#39;URL ont été résolus. En outre, le workflow de tracking détecte désormais les problèmes du log de tracking qui peuvent entraîner des erreurs et arrêter le workflow. Ces problèmes sont maintenant écartés et ne sont pas traités.
* Workflow de nettoyage : le workflow de nettoyage a été amélioré de manière à éviter les erreurs et arrêts potentiels. Cela optimise la taille et la performance des bases de données.
* Images incorporées dans les messages transactionnels : nous avons ajouté la prise en charge complète des images incorporées dans les messages transactionnels dans le but d&#39;éviter les possibles blocages ou images manquantes.
* Taille de la base de données - XtkJobLog : un mécanisme de purge a été ajouté à cette table. Cela a un impact positif sur la taille de la base de données.
* Archivage des emails en Cci : les paramètres par défaut de l&#39;archivage des emails en Cci ont été modifiés en vue d&#39;accélérer l&#39;archivage. [En savoir plus](../../installation/using/email-archiving.md#parameters)
* Mise à jour de la structure des bases de données : les demandes SQL générées par l&#39;assistant de mise à jour de la base de données ont été améliorées dans le but d&#39;accélérer l&#39;exécution.
* Barrières de sécurité pour les actions des opérateurs : plusieurs barrières de sécurité ont été mises en place afin d&#39;empêcher les opérateurs de réaliser des actions susceptibles d&#39;impacter l&#39;intégrité de la plateforme. Les schémas natifs ne peuvent plus être supprimés via l&#39;interface. En outre, le code XML source d&#39;un workflow ne peut plus être édité par les utilisateurs non administrateurs.
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

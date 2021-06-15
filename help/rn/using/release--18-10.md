---
product: campaign
title: Notes de mise à jour de Campaign 18.10
description: Notes de mise à jour de Campaign 18.10
feature: Vue d’ensemble
role: Business Practitioner
level: Beginner
exl-id: 57996f77-4ac2-402a-95db-b75d4bea4eeb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '2372'
ht-degree: 100%

---

# Version 18.10{#release-18-10}

## Version 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 juillet 2019

**Améliorations**

* Nous autorisons maintenant la suppression des enregistrements factices créés dans Microsoft Dynamics lors du workflow d&#39;import.
* Correction d&#39;un problème lié à l&#39;activité de workflow Collecteur de fichiers qui consignait des erreurs en boucle lorsque l&#39;accès à un fichier était refusé. (NEO-12085)
* Correction d&#39;un problème qui entraînait des incohérences au niveau du reporting entre les activités utilisateurs et les rapports de tracking pour l&#39;indicateur d&#39;ouverture des diffusions. (NEO-11742)
* Améliorations des permissions pour exécuter le package de zone de sécurité lors de l&#39;utilisation d&#39;un compte interne.
* Correction d&#39;un problème qui entraînait des erreurs dans les logs mtachild. (NEO-8978)

## Version 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 avril 2019

**Améliorations**

* Correction d’un problème de blocage SQL qui entraînait l’échec de l’analyse des diffusions en cas d’analyses/d’envois simultanés (quand deux diffusions étaient analysées en même temps). (NEO-13026)
* Suppression de la limite de 10 000 enregistrements dans la carte thermique des workflows afin de résoudre un problème de données manquantes. (NEO-12329)
* Correction d&#39;un problème qui survenait lors de l&#39;utilisation de l&#39;option « Conserver toutes les données additionnelles de l&#39;ensemble principal » dans une activité de workflow d&#39;enrichissement. (NEO-13291)

## Version 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 avril 2019

**Améliorations**

* Correction d’un problème avec le processus de calcul des indicateurs de tracking pour les messages transactionnels. (NEO-12529, NEO-12581)
* Correction d&#39;un problème avec l&#39;API HTTPRequest qui n&#39;attendait pas la fin de l&#39;ensemble des callbacks. (NEO-12628)
* Des index ont été ajoutés aux tables temporaires de coupons pour optimiser l&#39;envoi des diffusions. (NEO-12437)
* Correction d&#39;un problème lors de l&#39;analyse d&#39;un message qui ciblait des destinataires de domaines japonais (.JP). (NEO-12246)
* Dans l&#39;intégration Analytics, la récupération des données de segments AAM avec le caractère % est maintenant autorisée. (NEO-12025)
* Correction d&#39;un problème de blocage Tomcat lors de l&#39;envoi de notifications push via HTTP2. (NEO-12701)

## Version 18.10.3 - Build 8981{#release-18-10-3-build-8981}

29 janvier 2019

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez une [mise à niveau vers le dernier build](../../production/using/build-upgrade.md) ou contactez l&#39;[Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Améliorations**

* Correction d&#39;un problème avec l&#39;activité de workflow Transfert de fichier s3. (NEO-12473)
* Correction d’un problème qui entraînait l’échec du workflow Tracking. (NEO-12520)
* Correction d&#39;une erreur liée à la connexion IMS.
* Correction d’un problème lié à la prévisualisation et à la validation du contenu des messages transactionnels lors de l’utilisation d’un identifiant de l’offre de grande taille.
* Correction d’un problème avec le workflow Mid-sourcing (compteurs des diffusions).
* Correction d’un problème avec la mise à jour de la structure de la base de données qui déposait de nouveaux index sur NmsRecipient.
* Correction des blocages de console qui pouvaient se produire lors de l&#39;utilisation de l&#39;option Définie dans un fichier externe pour la cible principale d&#39;une diffusion. (NEO-12349)
* Correction de plusieurs blocages InMail.
* Correction d’un problème qui se produisait lors de l’utilisation d’une activité de workflow Mise à jour de données pour supprimer des enregistrements stockés dans une base de données FDA Teradata.
* Correction de problèmes d&#39;incohérence dans la gestion des clés secrètes.
* Correction d’un problème avec l’activité Enrichissement lors de la saisie d’un champ comme suit : xml=true et calculated=true.
* Correction d’un problème d’échappement des caractères lors de l’envoi de notifications push sur une application mobile.
* Correction d’un problème qui empêchait le passage de la méthode de synchronisation FDA à SOAP dans un compte externe Mid-sourcing.

## Version 18.10.2 - Build 8978{#release-18-10-2-build-8978}

6 décembre 2018

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez une [mise à niveau vers le dernier build](../../production/using/build-upgrade.md) ou contactez l&#39;[Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Améliorations**

* Correction de divers problèmes lors de l&#39;exécution des workflows utilisant MySQL sur FDA. (NEO-11652)
* Correction d&#39;un problème de performances lors de l&#39;envoi de notifications push. (NEO-11787)
* Correction d&#39;un problème d&#39;épuisement des ID lors de l&#39;utilisation d&#39;adresses de contrôle dans une diffusion. (NEO-11842)
* Correction d&#39;un problème de blocage du client qui pouvait survenir lors de l&#39;utilisation de workflows complexes. (NEO-11847)
* Correction d&#39;un problème d&#39;affichage lors de l&#39;utilisation d&#39;une distribution de valeurs avec un lien 1:N. (NEO-11820)
* Correction d&#39;une erreur Oracle dans la carte thermique des workflows.
* Correction d&#39;un problème de droit lors de l&#39;ajout d&#39;une proposition d&#39;offre dans une activité d&#39;enrichissement.
* Correction d&#39;un problème de connexion à la gestion des données SQL.
* Correction d&#39;un problème avec la génération de noms de tables de workflows temporaires en cas d&#39;ID négatifs.
* Correction d&#39;un problème avec le calcul des durées de workflow dans la carte thermique des workflows.


## Version 18.10 - Build 8977{#release-18-10-build-8977}

5 novembre 2018

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez une [mise à niveau vers le dernier build](../../production/using/build-upgrade.md) ou contactez l&#39;[Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Améliorations des notifications push<br /> </td> 
   <td> Dans Adobe Campaign, un certain nombre d'améliorations ont été apportées aux notifications push :<br /> 
    <ul> 
     <li> <p>Tracking des notifications silencieuses dans iOS </p> </li> 
     <li> <p>Implémentation du retour sur les appels d'enregistrement dans iOS</p> </li> 
     <li> <p>Amélioration de la vitesse de préparation des diffusions iOS</p> </li> 
    </ul> <p>En raison de l'abandon de GCM par Google, le connecteur Android V2 ne permet plus que les connexions au serveur FCM.</p><p>Voir à ce sujet la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentation détaillée</a>. La mise à niveau manuelle vers FCM est présentée dans <a href="https://helpx.adobe.com/fr/campaign/kb/migrate-to-fcm.html">cet article</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> Activité Gestion des données SQL<br /> </td> 
   <td> <p>Une nouvelle activité de workflow de Data Management a été ajoutée. L'activité <strong>Gestion des données SQL</strong> permet d'écrire ou de copier-coller vos propres scripts SQL pour créer et remplir des tables de travail (FDA uniquement). </p> <p>Pour plus d'informations, consultez la <a href="../../workflow/using/sql-data-management.md">documentation détaillée</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Surveillance des workflows<br /> </td> 
   <td> <p>Avec la nouvelle Carte thermique des workflows Campaign d'Adobe, les administrateurs de la plateforme disposent d'une représentation graphique de tous les workflows simultanés, ce qui leur permet de surveiller la charge de l'instance et de planifier les workflows en conséquence.</p> <p>Pour plus d'informations, consultez la <a href="../../workflow/using/heatmap.md">documentation détaillée</a>.</p> <p>Le package Carte thermique des workflows est également disponible sur demande pour les builds antérieurs à 8977 (à compter du build 8700). Pour plus d'informations sur la façon de le demander et de l'installer, consultez <a href="https://helpx.adobe.com/fr/campaign/kb/install-workflow-heatmap-package.html">cette page</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* Correction d&#39;un problème de sécurité qui entraînait des vulnérabilités aux attaques SSRF (Server Side Request Forgery) et aux attaques par déni de service (DoS). (NEO-11453)
* Le contenu (redirection du tracking, pages miroir, questionnaires, etc.) sera désormais servi par Campaign avec l&#39;en-tête X-Robots-Tag: nocache. Cela empêche l&#39;indexation de ce contenu par les moteurs de recherche Internet. (NEO-11101)
* Correction d&#39;un problème d&#39;injection XTK dans l&#39;API d&#39;abonnement (nms:subscription:Unsubscribe et nms:subscription:Subscribe).
* Correction d’un problème d’injection XTK dans l’application web de désabonnement.
* Suppression des mots de passe qui étaient affichés de manière non sécurisée dans certains logs SMS.

**Améliorations**

* Les API de Campaign Classic sont maintenant disponibles dans une [page dédiée](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html). Si vous utilisiez le fichier jsapi.chm, vous devez à présent vous référer à la nouvelle version en ligne.
* PostgreSQL 10, Debian 9 et Teradata 16.20 sont maintenant pris en charge. Consultez la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html).
* Lors de la création d&#39;une connexion SFTP, vous pouvez maintenant utiliser l&#39;authentification par proxy. Pour plus d&#39;informations, consultez la [documentation détaillée](../../installation/using/file-res-management.md) (NEO-9868)
* L&#39;option **Formule de calcul de date** est maintenant disponible dans les propriétés d&#39;une diffusion lors de la création d&#39;une diffusion unique à l&#39;aide du modèle de diffusion courrier. (NEO-9792)
* La gestion des noms de domaine a été améliorée pour le tracking des cookies et les applications web. Pour plus d&#39;informations, consultez la section &#39;Evolutions techniques&#39;.
* L&#39;import des ressources partagées Adobe Marketing Cloud dans une diffusion ou une landing page a été amélioré en termes de sécurité et de performances.
* Une nouvelle case à cocher est disponible dans le compte externe du canal mobile pour activer les traces SMPP détaillées dans le fichier journal, ce qui rend cette sortie directement accessible à partir de l&#39;interface d&#39;Adobe Campaign.
* Dans les broadlogs, il est maintenant possible de faire la distinction entre le nombre maximal de connexions et le nombre maximal de messages par heure. Lorsque les limites sont atteintes, il est alors possible de savoir pourquoi le débit est limité. Auparavant, le même message (&quot;quota atteint&quot;) s&#39;appliquait aux deux cas.
* Vous pouvez maintenant spécifier un script SQL à exécuter lors de l&#39;acquisition d&#39;une connexion à partir du pool. Ce script peut être utilisé pour définir le schéma par défaut. Il sera appliqué après query banding. (NEO-11256)
* Le SDK de Campaign ne stocke plus l&#39;identifiant utilisateur afin de se conformer à la réglementation en matière de PII d&#39;Adobe. Les données sont maintenant stockées sous la forme d&#39;un hachage.
* Lors de l&#39;import d&#39;un fichier XML d&#39;exportation de package, Campaign prend maintenant en charge la présence de nomenclature dans le fichier, même si le codage y est explicitement déclaré.

**Evolutions techniques**

Upgrade du client et du serveur

>[!CAUTION]
>
>Si votre serveur a été mis à jour vers la version 18.10, vous devrez utiliser un client version 18.10 pour pouvoir accéder à votre serveur. Le client version 18.10 pourra se connecter à une version de serveur plus ancienne.

Gestion des noms de domaine

La gestion des noms de domaine a été améliorée pour le tracking des cookies et les applications web.

Désormais, tous les noms de domaine de second niveau de deux lettres sont pris en charge par défaut (par exemple .aa.com). Pour les noms de domaine plus complexes (par exemple, les domaines de second niveau à trois lettres tels que .com.au), vous devez les ajouter à l&#39;option **cookieDomains** de serverConf (sous la balise de redirection). Voici un exemple :

```
<redirection cookiedomain="http://toureiffel.paris">
```

Améliorations des index

Les index sur NmsRecipient ont été repensés. Les performances des requêtes utilisant cette table devraient être améliorées. Si vous avez créé une extension de NmsRecipient, vous souhaiterez peut-être vérifier qu&#39;aucun index ne duplique les nouveaux index (pour limiter l&#39;utilisation de l&#39;espace sur le serveur de base de données). (NEO-8228)

Dans PostgreSql, lors de l&#39;utilisation d&#39;un classement UTF-8, il est maintenant possible de créer des index qui optimiseront les opérations &quot;LIKE &#39;string%&#39;&quot; (ou &quot;commence par&quot;). Si vous effectuez d&#39;autres opérations sur la même colonne (order by ou jointure par exemple), un autre index standard sera requis. Du côté du schéma, cela sera fait en ajoutant indexOption=&quot;searchFromStart&quot; dans la définition d&#39;index (un index varchar_pattern_ops sera créé à la place d&#39;un index btree standard). Par exemple (sur NmsRecipient) :

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

De nouveaux index ont été ajoutés à NmsRtEvent et NmsEventHisto (dans la colonne &quot;Scheduled&quot;), ce qui devrait améliorer le temps d&#39;affichage sur le formulaire correspondant. (NEO-11738)

Ces modifications d&#39;index peuvent entraîner une augmentation du temps nécessaire pour effectuer le post-upgrade.

**Correctifs**

* Correction d&#39;une erreur qui empêchait le téléchargement des fichiers depuis l&#39;activité de workflow **Téléchargement Web**. (NEO-11105)
* Correction d&#39;une erreur qui laissait parfois le workflow **Envoi des indicateurs et des attributs de campagne** dans un statut En échec (NEO-10820).
* Correction d&#39;une erreur qui supprimait la liste des destinataires créée après l&#39;exécution de l&#39;activité Mise à jour de liste dans un workflow. (NEO-11696)
* Correction d&#39;une erreur en raison de laquelle les campagnes étaient affichées un mois à l&#39;avance dans le calendrier de Campaign (sur une instance japonaise). (NEO-11445)
* Correction d&#39;une erreur qui empêchait l&#39;affichage de la configuration d&#39;Analytics dans l&#39;onglet Web Analytics des Propriétés de la diffusion. (NEO-11619)
* Correction d&#39;une erreur qui s&#39;affichait lors de la tentative d&#39;édition et d&#39;enregistrement du formulaire de saisie nms:delivery. (NEO-10973)
* Correction d&#39;une erreur de configuration de compte externe qui se produisait lors de l&#39;exécution d&#39;un workflow contenant une activité Transfert de fichier. (NEO-11012)
* Correction d&#39;une erreur qui renvoyait des lignes vides lors de l&#39;utilisation de la fonction zcat pour charger des fichiers dans l&#39;activité Chargement des données. (NEO-11273)
* Correction d&#39;une erreur qui générait des broadlogs en double lors de l&#39;analyse de la diffusion. (NEO-11360)
* Correction d&#39;une erreur qui entraînait un échec de la diffusion en raison d&#39;une clé de lien étrangère manquante après l&#39;exécution de l&#39;activité Enrichissement dans un workflow. (NEO-11537)
* Correction d&#39;une erreur qui empêchait la désinstallation ou la réparation correcte d&#39;Adobe Campaign lorsque le chemin d&#39;installation incluait des caractères chinois GB18030 spécifiques.
* Correction d&#39;une erreur qui associait certains logs de tracking à une mauvaise diffusion. (NEO-11412)
* Correction d&#39;une erreur en raison de laquelle certaines parties des logs de diffusion conservaient le statut en attente plus longtemps que prévu. (NEO-11336)
* Correction d&#39;une erreur qui se produisait lors de l&#39;édition d&#39;une requête afin d&#39;ajouter un coupon à une diffusion. (NEO-11037)
* Correction d&#39;un problème lié aux rapports en raison duquel les graphiques calculaient toujours la somme des valeurs, quel que soit l&#39;opérateur agrégé sélectionné. (NEO-10913)
* La fonction &quot;request.scheme&quot; étant obsolète, elle a été supprimée de la documentation JSAPI. (NEO-10828)
* Correction d&#39;une erreur qui empêchait certains utilisateurs possédant des configurations de fuseau horaire spécifiques de se connecter à Adobe Campaign. (NEO-10712)
* Correction d&#39;une erreur qui se produisait lors de la configuration d&#39;un compte externe de canal mobile à l&#39;aide du connecteur SMPP générique étendu : si vous aviez spécifié l&#39;utilisation de paramètres différents pour le récepteur, l&#39;émetteur utilisait ces paramètres de manière incorrecte plutôt que ses propres paramètres.
* Correction d&#39;une erreur en raison de laquelle les diffusions planifiées échouaient lors de la définition d&#39;une fréquence pour la règle de pression, car elles étaient constamment recalculées après le premier arbitrage. (NEO-10016)
* Correction d&#39;une erreur qui entraînait le blocage du serveur web IIS lors du processus de recyclage du pool d&#39;applications (dans la bibliothèque nlsrvmod.dll). (NEO-10862)
* Correction d&#39;une erreur qui empêchait la recherche d&#39;un destinataire dans l&#39;écran **Profils et Cibles**. (NEO-8228)
* Correction d&#39;un problème qui entraînait une erreur de timeout lors de l&#39;accès au dossier Historique des événements dans le cas d&#39;un nombre élevé d&#39;enregistrements. (NEO-11738)
* Correction d&#39;une erreur qui entraînait le renvoi erroné des destinataires d&#39;une diffusion LINE comme &quot;Inatteignable&quot;. (NEO-10833)
* Correction d&#39;une erreur lors de l&#39;exécution d&#39;une requête de workflow avec une colonne supplémentaire sur Oracle. (NEO-11615)
* Une amélioration a été apportée pour s&#39;assurer que les connexions fermées ne sont pas conservées trop longtemps dans le pool de connexions. (NEO-11392)
* Correction d&#39;une erreur lors de l&#39;utilisation d&#39;une activité de workflow de ciblage (requête, chargement (SGBD), etc.) connectée via FDA à une table Oracle externe contenant des caractères UTF8 (dans le nom de la table, le nom d&#39;un champ, etc.) et une contrainte de clé primaire avec un nom de contrainte par défaut généré par le système. (NEO-10714)
* Correction d&#39;une erreur qui empêchait la suppression du contenu HTML d&#39;une diffusion. (NEO-11327)
* Correction d&#39;un problème lié à l&#39;aperçu des fichiers XML et CSV dans un courrier après l&#39;exécution d&#39;une campagne. (NEO-11290)
* Correction d&#39;une erreur lors du tri des données dans une activité de workflow Enrichissement. (NEO-11394)
* Correction d&#39;une erreur lors du tri des données dans un rapport personnalisé. (NEO-10896)
* Correction d&#39;un problème qui entraînait des erreurs lors de l&#39;utilisation du paramètre useVault avec Teradata. (NEO-11399)
* Correction d&#39;une erreur qui entraînait le blocage de la console cliente d&#39;Adobe Campaign lors de la suppression de plusieurs lignes de requête. (NEO-10744)
* Correction d&#39;une erreur qui empêchait l&#39;application de règles de pression dans certains cas lors d&#39;une diffusion courrier. (NEO-9004)
* Correction d&#39;une erreur qui se produisait lors de l&#39;utilisation de l&#39;activité de chargement de données pour importer une colonne avec le type de données ‘time’ : le séparateur d&#39;heure était réinitialisé même après sa suppression. (NEO-10743)
* Correction d&#39;une erreur qui empêchait l&#39;affichage du dossier Diffusions depuis la liste de dossiers Exécution dans les propriétés d&#39;une diffusion lors de l&#39;édition d&#39;une diffusion récurrente. (NEO-11094)
* Correction d&#39;une erreur qui empêchait la fenêtre d&#39;affichage de la population d&#39;afficher plus de 200 enregistrements en tant que cible obtenue depuis une activité Requête dans un workflow. (NEO-11195)
* Correction d&#39;une erreur dans Oracle qui empêchait l&#39;exécution d&#39;une requête DELETE lorsque plus de 1 000 éléments étaient sélectionnés. (NEO-11171)
* Correction d&#39;une erreur qui entraînait le codage des URL en tant qu&#39;URL trackées dans les paramètres additionnels d&#39;une diffusion de notification push Android. (NEO-11468)
* Correction d&#39;une erreur de script qui se produisait dans le rapport sur les activités des utilisateurs lors de la définition des paramètres sur ‘Intervalles d’un jour’ et ‘Ouvertures’. (NEO-11655)
* Correction d&#39;une erreur qui se produisait lors de la connexion au serveur de mid-sourcing ou à Message Center via un proxy web authentifié. (NEO-11309)
* Correction d&#39;une erreur Oracle qui se produisait lors de l&#39;enregistrement d&#39;une nouvelle composition de diffusion après la sélection d&#39;un élément d&#39;un schéma spécifique **basé sur une vue SQL**. (NEO-11682)
* Correction d&#39;une erreur qui entraînait la génération de fichiers de rejet comportant des faux positifs lors du traitement d&#39;un fichier zip contenant un fichier .csv via une activité de chargement de fichier utilisant l&#39;option de décompression.
* xtkjoblog est maintenant purgé par le nettoyage.

---
product: campaign
title: Versions de Campaign Classic 2018
description: En savoir plus sur les versions de Campaign Classic 2018
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '5423'
ht-degree: 100%

---

# Versions 2018{#release-2018}



## Version 18.10

### Version 18.10.6 - Build 8985{#release-18-10-6-build-8985}

12 juillet 2019

**Améliorations**

* Nous autorisons maintenant la suppression des enregistrements factices créés dans Microsoft Dynamics lors du workflow d&#39;import.
* Correction d&#39;un problème lié à l&#39;activité de workflow Collecteur de fichiers qui consignait des erreurs en boucle lorsque l&#39;accès à un fichier était refusé. (NEO-12085)
* Correction d&#39;un problème qui entraînait des incohérences au niveau du reporting entre les activités utilisateurs et les rapports de tracking pour l&#39;indicateur d&#39;ouverture des diffusions. (NEO-11742)
* Améliorations des autorisations pour exécuter le package de zone de sécurité lors de l&#39;utilisation d&#39;un compte interne.
* Correction d&#39;un problème qui entraînait des erreurs dans les logs mtachild. (NEO-8978)

### Version 18.10.5 - Build 8984{#release-18-10-5-build-8984}

23 avril 2019

**Améliorations**

* Correction d’un problème de blocage SQL qui entraînait l’échec de l’analyse des diffusions en cas d’analyses/d’envois simultanés (quand deux diffusions étaient analysées en même temps). (NEO-13026)
* Suppression de la limite de 10 000 enregistrements dans la carte thermique des workflows afin de résoudre un problème de données manquantes. (NEO-12329)
* Correction d&#39;un problème qui survenait lors de l&#39;utilisation de l&#39;option « Conserver toutes les données additionnelles de l&#39;ensemble principal » dans une activité de workflow d&#39;enrichissement. (NEO-13291)

### Version 18.10.4 - Build 8983{#release-18-10-4-build-8983}

15 avril 2019

**Améliorations**

* Correction dʼun problème avec le processus de calcul des indicateurs de suivi pour les messages transactionnels. (NEO-12529, NEO-12581)
* Correction d&#39;un problème avec l&#39;API HTTPRequest qui n&#39;attendait pas la fin de l&#39;ensemble des callbacks. (NEO-12628)
* Des index ont été ajoutés aux tables temporaires de coupons pour optimiser l&#39;envoi des diffusions. (NEO-12437)
* Correction d&#39;un problème lors de l&#39;analyse d&#39;un message qui ciblait des destinataires de domaines japonais (.JP). (NEO-12246)
* Dans l&#39;intégration Analytics, la récupération des données de segments AAM avec le caractère % est maintenant autorisée. (NEO-12025)
* Correction d&#39;un problème de blocage Tomcat lors de l&#39;envoi de notifications push via HTTP2. (NEO-12701)

### Version 18.10.3 - Build 8981{#release-18-10-3-build-8981}

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

### Version 18.10.2 - Build 8978{#release-18-10-2-build-8978}

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
* Correction dʼune erreur Oracle dans la carte thermique des workflows.
* Correction d&#39;un problème de droit lors de l&#39;ajout d&#39;une proposition d&#39;offre dans une activité d&#39;enrichissement.
* Correction d&#39;un problème de connexion à la gestion des données SQL.
* Correction d&#39;un problème avec la génération de noms de tables de workflows temporaires en cas d&#39;ID négatifs.
* Correction d&#39;un problème avec le calcul des durées de workflow dans la carte thermique des workflows.


### Version 18.10.1 - Build 8977{#release-18-10-build-8977}

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
   <td> Dans Adobe Campaign, un certain nombre d'améliorations ont été apportées aux notifications push :<br /> 
    <ul> 
     <li> <p>Tracking des notifications silencieuses dans iOS </p> </li> 
     <li> <p>Implémentation du retour sur les appels d'enregistrement dans iOS</p> </li> 
     <li> <p>Amélioration de la vitesse de préparation des diffusions iOS</p> </li> 
    </ul> <p>En raison de l'abandon de GCM par Google, le connecteur Android V2 ne permet plus que les connexions au serveur FCM.</p><p>Pour plus d’informations, consultez la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentation détaillée</a>.</p> </td> 
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

* Les API de Campaign Classic sont maintenant disponibles dans une [page dédiée](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=fr). Si vous utilisiez le fichier jsapi.chm, vous devez à présent vous référer à la nouvelle version en ligne.
* PostgreSQL 10, Debian 9 et Teradata 16.20 sont maintenant pris en charge. Consultez la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html).
* Lors de la création d&#39;une connexion SFTP, vous pouvez maintenant utiliser l&#39;authentification par proxy. Pour plus d&#39;informations, consultez la [documentation détaillée](../../installation/using/file-res-management.md) (NEO-9868)
* L&#39;option **Formule de calcul de date** est maintenant disponible dans les propriétés d&#39;une diffusion lors de la création d&#39;une diffusion unique à l&#39;aide du modèle de diffusion courrier. (NEO-9792)
* La gestion des noms de domaine a été améliorée pour le tracking des cookies et les applications web. Pour plus d&#39;informations, consultez la section &#39;Evolutions techniques&#39;.
* L&#39;import des ressources partagées Adobe Marketing Cloud dans une diffusion ou une landing page a été amélioré en termes de sécurité et de performances.
* Une nouvelle case à cocher est disponible dans le compte externe du canal mobile pour activer les traces SMPP détaillées dans le fichier journal, ce qui rend cette sortie directement accessible à partir de l&#39;interface d&#39;Adobe Campaign.
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
* Correction d&#39;une erreur qui empêchait la désinstallation ou la réparation correcte d&#39;Adobe Campaign lorsque le chemin d&#39;installation incluait des caractères chinois GB18030 spécifiques.
* Correction d&#39;une erreur qui associait certains logs de tracking à une mauvaise diffusion. (NEO-11412)
* Correction d&#39;une erreur en raison de laquelle certaines parties des logs de diffusion conservaient le statut en attente plus longtemps que prévu. (NEO-11336)
* Correction d&#39;une erreur qui se produisait lors de l&#39;édition d&#39;une requête afin d&#39;ajouter un coupon à une diffusion. (NEO-11037)
* Correction d&#39;un problème lié aux rapports en raison duquel les graphiques calculaient toujours la somme des valeurs, quel que soit l&#39;opérateur agrégé sélectionné. (NEO-10913)
* La fonction &quot;request.scheme&quot; étant obsolète, elle a été supprimée de la documentation JSAPI. (NEO-10828)
* Correction d&#39;une erreur qui empêchait certains utilisateurs possédant des configurations de fuseau horaire spécifiques de se connecter à Adobe Campaign. (NEO-10712)
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
* Correction d&#39;une erreur qui entraînait le blocage de la console cliente d&#39;Adobe Campaign lors de la suppression de plusieurs lignes de requête. (NEO-10744)
* Correction d&#39;une erreur qui empêchait l&#39;application de règles de pression dans certains cas lors d&#39;une diffusion courrier. (NEO-9004)
* Correction d&#39;une erreur qui se produisait lors de l&#39;utilisation de l&#39;activité de chargement de données pour importer une colonne avec le type de données ‘time’ : le séparateur d&#39;heure était réinitialisé même après sa suppression. (NEO-10743)
* Correction d&#39;une erreur qui empêchait l&#39;affichage du dossier Diffusions depuis la liste de dossiers Exécution dans les propriétés d&#39;une diffusion lors de l&#39;édition d&#39;une diffusion récurrente. (NEO-11094)
* Correction d&#39;une erreur qui empêchait la fenêtre d&#39;affichage de la population d&#39;afficher plus de 200 enregistrements en tant que cible obtenue depuis une activité Requête dans un workflow. (NEO-11195)
* Correction d&#39;une erreur dans Oracle qui empêchait l&#39;exécution d&#39;une requête DELETE lorsque plus de 1 000 éléments étaient sélectionnés. (NEO-11171)
* Correction d&#39;une erreur qui entraînait le codage des URL en tant qu&#39;URL suivies dans les paramètres additionnels d&#39;une diffusion de notification push Android. (NEO-11468)
* Correction d&#39;une erreur de script qui se produisait dans le rapport sur les activités des utilisateurs lors de la définition des paramètres sur ‘Intervalles d’un jour’ et ‘Ouvertures’. (NEO-11655)
* Correction d&#39;une erreur qui se produisait lors de la connexion au serveur de mid-sourcing ou à Message Center via un proxy web authentifié. (NEO-11309)
* Correction d&#39;une erreur Oracle qui se produisait lors de l&#39;enregistrement d&#39;une nouvelle composition de diffusion après la sélection d&#39;un élément d&#39;un schéma spécifique **basé sur une vue SQL**. (NEO-11682)
* Correction d&#39;une erreur qui entraînait la génération de fichiers de rejet comportant des faux positifs lors du traitement d&#39;un fichier zip contenant un fichier .csv via une activité de chargement de fichier utilisant l&#39;option de décompression.
* xtkjoblog est maintenant purgé par le nettoyage.

## Version 18.6

### Version 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 août 2018

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
   <td> Query banding<br /> </td> 
   <td> <p>Lorsque plusieurs utilisateurs de Campaign se connectent à un même compte externe Teradata FDA, vous pouvez désormais transmettre une Query band (paires clé/valeur) spécifique à chaque utilisateur. Chaque fois qu'un utilisateur de Campaign effectue une requête sur la base de données Teradata, Adobe Campaign peut désormais envoyer des métadonnées associées à l'utilisateur. Ces données, qui consistent en une liste de clés et de valeurs, peuvent ensuite être utilisées par les administrateurs de Teradata à des fins d'audit ou pour gérer les droits d'accès, par exemple.</p><p>Pour plus d’informations, consultez la <a href="../../installation/using/external-accounts.md">documentation détaillée</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Améliorations**

* Les logs d&#39;archivage des emails ont été améliorés, ce qui permet de vérifier plus facilement et plus clairement quels emails ont été diffusés avec succès ou non via l&#39;archivage Cci. (NEO-10675)
* Correction d&#39;une erreur qui entraînait l&#39;affichage des adresses IP des équilibreurs de charge au lieu de celles des clients dans les broadlogs de tracking. (NEO-11295)
* Correction d&#39;une erreur aléatoire qui entraînait le remplacement incorrect des propriétés d&#39;une diffusion. (NEO-11015)
* Correction d&#39;une erreur de syntaxe lors du tri des résultats d&#39;une activité d&#39;enrichissement. (NEO-11394)
* Correction d&#39;une erreur lors de l&#39;utilisation de champs calculés dans une activité de workflow **[!UICONTROL Réponses au questionnaire]**. (NEO-11382)
* Mise à jour de Tomcat pour éviter l&#39;exploitation de vulnérabilités. (NEO-11503)
* Correction d&#39;une erreur liée au codage LATIN1 lors de l&#39;utilisation d&#39;une connexion FDA à une base de données PostgreSQL.(NEO-11299)
* Correction dʼune erreur qui se produisait lors de lʼutilisation de lʼoption de diffusion **[!UICONTROL Préparer les données de personnalisation avec un workflow]**. (NEO-11047)
* Correction d&#39;une erreur de postupgrade qui empêchait l&#39;envoi de SMS lors de l&#39;utilisation d&#39;un connecteur étendu.
* Amélioration de l&#39;import/export de package (ajout de log et de région dans l&#39;interface).
* Correction d&#39;un problème qui affichait des erreurs inutiles dans le log de postupgrade lorsqu&#39;une activité de workflow **[!UICONTROL Réponses au questionnaire]** n&#39;était pas entièrement configurée.

**Evolutions techniques**

Query banding

Une clé spécifique (PROXYUSER ou PROXYROLE) est utilisée pour associer un utilisateur ou un rôle Teradata à un utilisateur Campaign. Une nouvelle autorisation a été ajoutée pour utiliser ce rôle/utilisateur proxy. Vous devez ajouter le droit d&#39;accès GRANT CONNECT THROUGH au compte de base de données (celui défini dans le compte externe Teradata).

Un nouvel onglet a été ajouté dans les comptes externes de Teradata. L’onglet **[!UICONTROL Query banding]** comprend les options suivantes :

* **[!UICONTROL Activer]** : cochez cette case pour activer la fonctionnalité.
* **[!UICONTROL Par défaut]** : saisissez un query banding par défaut qui sera utilisé si un utilisateur n’a aucun query banding associé. Si aucun query banding par défaut n’est défini, les utilisateurs sans query banding associé ne pourront pas utiliser Teradata.
* **[!UICONTROL Utilisateurs]** : pour chaque utilisateur, spécifiez un query banding. Vous pouvez ajouter autant de paires clé/valeur que nécessaire. Par exemple : ’priority=1;workload=high;’

Pour plus d’informations sur query banding, référez-vous à ces articles :

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Version 18.6.1 - Build 8947{#release-18-6-build-8947}

25 juin 2018

>[!CAUTION]
>
>Ce build a été rappelé. Effectuez un [upgrade vers le dernier build](../../production/using/build-upgrade.md) ou contactez le [support technique](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Amélioration de la sécurité<br /> </td> 
   <td> Nous avons ajouté une série d'améliorations de sécurité à Campaign Classic. Les améliorations et les corrections sont répertoriées ci-dessous.<br /> </td> 
  </tr> 
  <tr> 
   <td> Prise en charge de Windows Server 2016<br /> </td> 
   <td> Adobe Campaign est maintenant compatible avec Windows Server 2016. Consultez la <a href="https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html">matrice de comptabilité de Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

decryptString

La fonction **decryptString** est obsolète. Reportez-vous à l’article [Fonctionnalités obsolètes et supprimées](deprecated-features.md).

Pour les nouveaux clients, cette fonction n’est plus utilisée que pour déchiffrer l’ID chiffré du destinataire dans les landing pages. Pour déchiffrer les mots de passe stockés dans un compte externe, utilisez la nouvelle fonction **decryptPassword**.

Pour les clients existants, le comportement de cette fonction reste inchangé, mais nous vous recommandons d’utiliser **decryptPassword** au lieu de **decryptString**. L’option de compatibilité **XtkSecurity_Unsafe_DecryptString** est ajoutée par le postupgrade et activée par défaut, ce qui vous permet de continuer à utiliser la fonction. Si vous souhaitez désactiver **decryptString**, désactivez l’option.

decryptPassword

La fonction **decryptPassword** a été ajoutée. Elle vous permet de déchiffrer un mot de passe stocké dans un compte externe. Reportez-vous à la documentation [JSAPI](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) pour plus d’informations.

API de fichier

Pour les nouvelles installations, l’accès aux dossiers via les API de fichier est limité aux dossiers **var**, **sftp** et temporaires d’Adobe Campaign.

Pour les clients existants, les API de fichier ne peuvent plus accéder au dossier **conf** d’Adobe Campaign. L’option de compatibilité **XtkSecurity_Disable_JSFileSandboxing** est ajoutée par le postupgrade et activée par défaut, ce qui vous permet de maintenir l’accès aux autres dossiers. Si vous souhaitez limiter l’accès aux dossiers **var**, **sftp** et temporaires d’Adobe Campaign, désactivez l’option.

**Correctif**

* Correction d&#39;une erreur qui pouvait altérer la performance des messages transactionnels par SMS. (NEO-9812)

## Version 18.4

### Version 18.4.5 - Build 8937{#release-18-4-5-build-8937}

21 novembre 2018

**Améliorations**

* Correction de divers problèmes lors de l&#39;exécution des workflows utilisant MySQL sur FDA. (NEO-11652)
* Correction d&#39;un problème qui faisait qu&#39;une partie de la population de diffusion restait en état d&#39;attente dans des cas spécifiques. (NEO-11336)
* Correction d&#39;un problème intermittent avec la réponse automatique SMS. (NEO-11811)
* Correction d&#39;un problème d&#39;épuisement des ID lors de l&#39;utilisation d&#39;adresses de contrôle dans une diffusion. (NEO-11842)
* Correction d&#39;une erreur de syntaxe lors du tri dans une activité de workflow d&#39;enrichissement. (NEO-11394)
* Correction d&#39;un problème qui pouvait provoquer le blocage du serveur web lors du redémarrage d&#39;IIS. (NEO-10862)
* Correction d&#39;un problème qui pouvait entraîner l&#39;échec du workflow de tracking après une mise à niveau de build (FDA - SQL). (NEO-11635)
* Correction d&#39;un problème qui pouvait entraîner la perte des données de liste de workflow. (NEO-11696)
* Correction d&#39;un problème de performances lors de l&#39;envoi de notifications push. (NEO-11787)
* Correction d’un problème qui empêchait le bon fonctionnement du tracking web pour les domaines &quot;com.au&quot; (NEO-4385).
* Correction d&#39;un problème de blocage du client qui pouvait survenir lors de l&#39;utilisation de workflows complexes. (NEO-11847)
* Correction d&#39;une erreur Oracle lors de l&#39;enregistrement d&#39;une nouvelle diffusion après avoir sélectionné un élément d&#39;un schéma spécifique (NEO-11682).
* Correction d&#39;un problème lors de l&#39;interrogation d&#39;un champ contenant des caractères avec accents (FDA/Teradata). Le compte externe vous permet désormais de modifier le codage utilisé pour communiquer avec le pilote Teradata. (NEO-11818).
* Correction d&#39;un problème de tracking lors de la transmission d&#39;URL dans des variables supplémentaires dans une notification push qui pouvait entraîner la réception de données mal formatées ou incorrectes par l&#39;application mobile. (NEO-11468, NEO-11960)
* Correction d&#39;un problème d&#39;affichage lors de l&#39;utilisation d&#39;une distribution de valeurs avec un lien 1:N. (NEO-11820)
* Correction d’une erreur qui empêchait le bon fonctionnement du chargement en masse sur Teradata 16.
* Augmentation de la taille du tampon pour l&#39;horodatage sur Teradata afin d&#39;éviter les problèmes de liaison avec le pilote 15.10.
* Amélioration de la gestion des index aux noms longs qui pouvait créer des problèmes lors du postupgrade.
* Amélioration du temps disponible de la mémoire partagée lors du traitement des enfants morts (MTA).
* Correction d’un blocage potentiel dans Apache (tracking).


### Version 18.4.4 - Build 8936{#release-18-4-4-build-8936}

1er août 2018

**Améliorations**

* Les logs d&#39;archivage des emails ont été améliorés, ce qui permet de vérifier plus facilement et plus clairement quels emails ont été diffusés avec succès ou non via l&#39;archivage Cci. (NEO-10675)
* Correction d&#39;une erreur qui entraînait l&#39;affichage des adresses IP des équilibreurs de charge au lieu de celles des clients dans les broadlogs de tracking. (NEO-11295)
* Correction d&#39;une erreur liée au codage LATIN1 lors de l&#39;utilisation d&#39;une connexion FDA à une base de données PostgreSQL.(NEO-11299)
* Correction dʼune erreur qui se produisait lors de lʼutilisation de lʼoption de diffusion **[!UICONTROL Préparer les données de personnalisation avec un workflow]**. (NEO-11047, NEO-11301)
* Correction d&#39;une erreur aléatoire qui entraînait le remplacement incorrect des propriétés d&#39;une diffusion. (NEO-11015)
* Correction d&#39;une erreur lors de l&#39;utilisation de champs calculés dans une activité de workflow **[!UICONTROL Réponses au questionnaire]**. (NEO-11382)
* Correction d’un problème lors de l’utilisation de données stockées en XML dans une activité de workflow **[!UICONTROL Réponses au questionnaire]**. (NEO-10816)
* Correction d’un problème lors de l’upgrade du serveur avec le build 8935.
* Correction d&#39;un problème qui affichait des erreurs inutiles dans le log de postupgrade lorsqu&#39;une activité de workflow **[!UICONTROL Réponses au questionnaire]** n&#39;était pas entièrement configurée.
* FDA Teradata : correction d’un problème lié aux champs et aux index auto-incrémentés dans les tables SQL.

### Version 18.4.3 - Build 8935{#release-18-4-3-build-8935}

22 juin 2018

**Améliorations**

* Correction d’une erreur d’encodage du suivi avec Microsoft Edge et Internet Explorer. (NEO-11257)
* Correction d’une erreur avec la personnalisation du lien de l’image dans les diffusions LINE. (NEO-11077)
* Correction d’une erreur qui empêchait le bon fonctionnement du mécanisme de génération de séquence d’identifiants. (NEO-11115)
* Correction d’une erreur qui empêchait les demandes d’accès à des informations personnelles (RGPD) de fonctionner lors de l’utilisation d’un espace de noms personnalisé avec une clé de réconciliation de type entier. (NEO-11123)
* Correction d’une erreur qui pouvait survenir lors de l’utilisation de l’option **[!UICONTROL Répartition des valeurs]** dans les activités de workflow **[!UICONTROL Requête]**. (NEO-10958)
* Correction d’une erreur lors de la synchronisation des emplacements de l’instance marketing vers l’instance d’interaction. (NEO-11162)
* Amélioration de la gestion des index aux noms longs lors du postupgrade.

### Version 18.4.2 - Build 8932{#release-18-4-2-build-8932}

22 mai 2018

**Améliorations**

* Correction d’une erreur qui empêchait Windows Server d’être mis à jour correctement.
* Correction d’une erreur dans l’activité **[!UICONTROL Résultat du questionnaire]** lors de l’utilisation de données stockées en XML. Le rapport ne s’affichait pas correctement. (NEO-10816)
* Correction d’un problème de performance qui pouvait se produire avec le processus inMail lors de l’utilisation d’un serveur de mails rebonds. (NEO-10641)
* Correction d’un problème de mise à niveau de la base de données qui pouvait survenir lors de la mise à niveau de plus de 1 000 schémas.

### Version 18.4.1 - Build 8931{#release-18-4-build-8931}

24 avril 2018

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
   <td> Règlement général sur la protection des données (RGPD) de l’UE<br /> </td> 
   <td> <p>Le RGPD, qui entrera en vigueur le 25 mai 2018, est la nouvelle loi de l’Union européenne (UE) sur la protection de la vie privée. Il harmonise et modernise les exigences en matière de protection des données. Il s’applique aux clients Adobe Campaign qui détiennent des données pour des titulaires de données résidant dans l’UE.</p> <p>Outre les fonctionnalités de protection des données déjà disponibles dans Adobe Campaign (notamment la gestion du consentement, les paramètres de conservation des données et les rôles utilisateur), nous incluons, en qualité de responsable du traitement des données, d'autres fonctionnalités pour faciliter votre préparation en tant que contrôleur de données à certaines demandes RGPD:</p> 
    <ul> 
     <li> <p>Droit d’accès : permet au titulaire de données de recevoir une copie de ses données personnelles capturées par les contrôleurs de données, notamment les données éventuellement stockées dans Adobe Campaign.</p> </li> 
     <li> <p>Droit de suppression : autorise le titulaire de données à demander la suppression de ses données personnelles capturées par les contrôleurs de données, notamment les données éventuellement stockées dans Adobe Campaign.</p> </li> 
    </ul> Pour plus d'informations, consultez la <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html">documentation détaillée</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Profils actifs<br /> </td> 
   <td> <p>Adobe Campaign fournit désormais la liste des profils actifs, mise à jour tous les mois via un workflow dédié.</p> <p>Pour plus d'informations, consultez la <a href="../../platform/using/about-profiles.md#active-profiles">documentation détaillée</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Amélioration du connecteur push Android<br /> </td> 
   <td> <p>Le connecteur Android a été amélioré afin de prendre en charge un débit supérieur. </p> <p>Pour plus d'informations, consultez la <a href="../../delivery/using/configuring-the-mobile-application.md">documentation détaillée</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* L&#39;extension des entités externes est désormais désactivée pour prévenir les attaques potentielles d&#39;utilisateurs non authentifiés. (NEO-10173)
* Autorisations renforcées pour empêcher les utilisateurs standard de modifier les paramètres de configuration d&#39;instance, tels que les URL d&#39;accès aux applications, la configuration LDAP, etc. (NEO-10171)
* Correction d&#39;un problème qui pouvait révéler des informations sensibles via des traces de pile. Les détails d&#39;erreur sont maintenant consignés en back-end à un emplacement inaccessible à partir du réseau externe. (NEO-10176)
* Autorisations renforcées pour empêcher les utilisateurs standard d&#39;afficher les documents téléchargés et/ou les packages exportés par un administrateur. (NEO-10170)

**Améliorations**

* **Canal LINE - amélioration de l&#39;architecture** : à l&#39;instar de tous les autres canaux d&#39;Adobe Campaign, le canal LINE est désormais pris en charge dans tous les types de déploiement : hébergé, hybride et on-premise.
* **Génération automatique de séquence** : le mécanisme de génération d’identifiants a été amélioré pour augmenter la durée de vie des instances Campaign ayant des volumes d’objets importants.

**Autres changements**

* Un nouveau mode est disponible pour l&#39;import de packages à l&#39;aide d&#39;une ligne de commande. Il permet les dépendances circulaires (non recommandé pour les packages volumineux). Pour plus d&#39;informations, consultez la section Evolutions techniques. (NEO-8979)
* Amélioration des performances pour le chargement de grandes quantités de données dans Teradata et correction d&#39;une erreur qui empêchait l&#39;affichage de la valeur correcte des données traitées dans le log. (NEO-10429)
* L&#39;import d&#39;audiences depuis Audience Manager est désormais possible avec des fichiers partagés. Auparavant, seul le dernier fichier du segment était importé par le workflow technique importSharedAudience. (NEO-10156)
* Sous Windows, le chemin d’installation par défaut du serveur Campaign a changé. Lors du lancement du programme d’installation de la version 64 bits, le chemin d’installation par défaut est désormais **C:\Program Files\Adobe\Adobe Campaign Classic v7\** au lieu de **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* Les règles MX par défaut ont été améliorées pour inclure davantage de domaines et optimiser le débit.
* Application des restrictions d&#39;accès sur l&#39;appel SOAP de l&#39;assistant de déploiement (xtk:serverOptions#SaveOptions).
* La bibliothèque obsolète weka.jar a été supprimée et la bibliothèque OpenSSL a été mise à jour pour optimiser la sécurité.
* Amélioration du workflow technique de facturation pour sécuriser les performances des instances.
* Les administrateurs peuvent à nouveau définir ou réinitialiser le mot de passe des opérateurs. Pour cela, cliquez avec le bouton droit sur un opérateur, sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Réinitialiser le mot de passe]**, puis définissez le nouveau mot de passe de l&#39;opérateur. Nous recommandons aux opérateurs de changer leur mot de passe lors de leur première reconnexion. Pour plus d&#39;informations, consultez la [documentation détaillée](../../production/using/lost-password.md).
* Pour prendre en charge la nouvelle fonctionnalité multi-tenant d&#39;Adobe Target, un nouveau paramètre &quot;at_property&quot; peut maintenant être ajouté aux URL lors de la configuration des options et des comptes externes pour l&#39;intégration avec Target. La valeur à utiliser pour ce paramètre figure dans Adobe Target et sera utilisée par Campaign lors des appels à Target. Pour plus d&#39;informations, consultez la [documentation détaillée](../../integrations/using/inserting-a-dynamic-image.md).
* Vous pouvez maintenant spécifier l&#39;ouverture d&#39;une landing page par défaut lors d&#39;un clic sur une image fournie par Adobe Target. Auparavant, un clic sur cette image affichait l&#39;image par défaut définie lors de la création de l&#39;email. Pour plus d&#39;informations, consultez la [documentation détaillée](../../integrations/using/inserting-a-dynamic-image.md).
* Ajout de la case à cocher **Activer les traces SMPP** dans le compte externe pour forcer la sortie des traces. Pour plus d&#39;informations, consultez la [documentation détaillée](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Evolutions techniques**

queryDef

queryDef a été modifié en ce qui concerne la clause &quot;orderBy&quot;. Avant le changement, la clé primaire de la table interrogée aurait été implicitement ajoutée aux clauses &quot;orderBy&quot;. Sur certains moteurs de base de données (postgresql), il empêche l&#39;utilisation d&#39;index (tous les champs de la clause orderBy doivent être couverts par le même index). Si vous étiez dépendant de ce comportement, vous devrez ajouter explicitement la clé primaire dans votre clause &quot;orderBy&quot;.

Par exemple, si vous avez la requête suivante :

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

elle est implicitement gérée en tant que (avant les modifications de la version 18.4) :

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

Fonction urlEncode

La fonction JavaScript &#39;urlEncode&#39; ne fonctionnait pas correctement pour les caractères non-ASCII. Elle a été corrigée et fonctionne maintenant avec tous les caractères Unicode (y compris les caractères japonais). Si vous dépendiez du comportement de &#39;urlEncode&#39; pour un caractère non-ASCII, vous devez adapter votre code.

Nouveau mode pour l&#39;import de package

Un nouveau mode est disponible pour l&#39;import de packages à l&#39;aide d&#39;une ligne de commande. Il permet les dépendances circulaires (non recommandé pour les packages volumineux). La fonctionnalité existante est conservée. Pour ces packages avec des dépendances circulaires, un nouveau flag **-usejs** a été ajouté à la ligne de commande pour l&#39;import du package. Lorsqu&#39;il est exécuté, il utilise JSEngine comme lorsque l&#39;import est effectué à partir de l&#39;interface.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Correctifs**

* Correction d&#39;une erreur de synchronisation lors de la réplication des logs de diffusion et de tracking d&#39;Adobe Campaign Standard vers Adobe Campaign Classic. (NEO-10023)
* Correction d&#39;une erreur liée à la gestion des tables d&#39;erreurs et de logs dans Teradata lorsqu&#39;un workflow ETL reprenait après l&#39;échec d&#39;une opération de chargement rapide. Les tables d&#39;erreurs et de logs sont désormais supprimées correctement chaque fois que le workflow reprend. (NEO-10672)
* Correction d&#39;une erreur de postupgrade qui permet d&#39;installer automatiquement le package Hive (nécessaire pour Hadoop) si le package FDA est installé. (NEO-10592)
* Correction d&#39;une erreur qui traitait les domaines non valides comme une erreur **Non définie**. (NEO-10248)
* Correction d&#39;une erreur qui entraînait la duplication des logs dans la table deliveryLogStats lors de l&#39;envoi de diffusions push Android. (NEO-10234)
* Correction d’une erreur qui empêchait la lecture de certains formats de code-barres par les lecteurs de code-barres. (NEO-10125)
* Correction d&#39;une erreur liée à la fonction JavaScript &#39;urlEncode&#39; lors de l&#39;utilisation de caractères non-ASCII. Pour plus d&#39;informations, consultez la section Evolutions techniques. (NEO-10123)
* Correction d&#39;une erreur lors de l&#39;exécution d&#39;une requête incluant des fonctions sha256 sur des bases de données Teradata. (NEO-10119)
* Correction des erreurs de mémoire de workflow qui se produisaient dans l&#39;activité SalesForce lors de l&#39;utilisation de tables SalesForce très volumineuses. (NEO-9900)
* Correction d&#39;une erreur liée à l&#39;option **Générer le complémentaire** dans les activités de workflow de ciblage lors de l&#39;utilisation de FDA. (NEO-9878)
* Correction d&#39;une erreur qui empêchait la mise à jour des mesures **Traités** et **Succès** sur l&#39;instance marketing lors de l&#39;utilisation du mid-sourcing. (NEO-9454)
* Correction des règles de non-reproposition d&#39;Interaction lorsque plus de 10 000 offres se trouvent sur la plateforme. (NEO-9352)
* Correction d&#39;une erreur qui empêchait la spécification de la cible d&#39;une diffusion lors de l&#39;utilisation d&#39;un fichier externe XML. (NEO-9312)
* Correction d&#39;un problème pouvant entraîner des erreurs de workflow lors de l&#39;exécution d&#39;une hypothèse sur une offre et de la mise à jour du statut de la proposition. (NEO-9304)
* Correction des erreurs qui se produisaient pendant l&#39;analyse des diffusions lorsque des règles de pression basées sur un attribut du mapping de diffusion Android étaient utilisées. (NEO-9202)
* Correction d&#39;un problème qui entraînait des problèmes de performances lors du tri des colonnes de la liste des destinataires. Pour plus d&#39;informations sur les modifications de queryDef, consultez la section Evolutions techniques ci-dessus. (NEO-9042)
* Correction d&#39;un problème en raison duquel les liens d&#39;un email de validation pointaient vers une URL de connexion incorrecte, en particulier lors de l&#39;utilisation d&#39;un type de connexion Federated ID. (NEO-9011)
* Correction d&#39;une erreur qui entraînait l&#39;affichage de dates erronées dans les sélecteurs de date des rapports pour certains fuseaux horaires. (NEO-9007)
* Correction d&#39;une erreur qui empêchait l&#39;affichage de la cible d&#39;une sortie lors de l&#39;utilisation d&#39;une base de données SQL FDA. (NEO-8924)
* Correction d&#39;une erreur qui empêchait le connecteur MS Dynamics CRM d&#39;extraire des données pour les 7 premiers jours du mois. (NEO-8803)
* Correction d&#39;une erreur liée à l&#39;intégration d&#39;Analytics qui empêchait les utilisateurs d&#39;inclure des caractères internationaux. (NEO-8719)
* Correction d&#39;une erreur qui permettait l&#39;édition de workflows sans les droits adéquats. (NEO-8708)
* Correction d&#39;une erreur liée à FDA via HTTPs lors de l&#39;utilisation de Message Center dans une architecture hybride, entraînant une perte de connexion (timeout). (NEO-8438)
* Correction des erreurs de workflow se produisant dans les activités de requête incrémentale pour les identifiants négatifs. (NEO-8229)
* Correction d&#39;une erreur qui entraînait l&#39;affichage de deux barres de défilement dans certains écrans. (NEO-8208)
* Correction d&#39;une erreur qui entraînait l&#39;affichage d&#39;un message d&#39;erreur lors de l&#39;exécution de l&#39;assistant de mise à jour de la structure de la base de données. Le postupgrade exécute une opération d&#39;attribution de nouveaux noms aux index dont les noms comportent plus de 30 caractères. Pour les tables volumineuses, le remplacement des index prend du temps. (NEO-7983)
* Correction d&#39;une erreur qui entraînait une synchronisation incorrecte des logs de tracking de l&#39;instance d&#39;exécution de Message Center vers l&#39;instance de pilotage. (NEO-7286)
* Correction d&#39;un problème de performance lié à l&#39;activité d&#39;enrichissement des offres. (NEO-7263)
* Correction d&#39;un problème empêchant l&#39;utilisation de la fonction DaysAgo lors de l&#39;interrogation d&#39;une base de données Redshift via FDA. (NEO-7099)
* Correction d&#39;une régression dans Data Management qui empêchait la création d&#39;index sur les activités de workflow de type Enrichissement.
* Correction d&#39;un problème qui se produisait lors de la création de ressources externes avec le titre @id.
* Correction d&#39;un problème qui se produisait lors du téléchargement de fichiers compressés via un serveur FTP ou du téléchargement de fichiers dont le nom comportait des caractères génériques.
* Correction d&#39;un problème lié aux énumérations de type base longues dans les ressources personnalisées externes créées dans Campaign Standard.
* Correction d&#39;un problème qui entraînait l&#39;envoi de SMS même lorsque la connexion avec le fournisseur échouait, entraînant des pertes de SMS.
* Correction d&#39;une erreur qui entraînait le blocage indéfini d&#39;une connexion SMTP.
* Correction d&#39;une erreur liée aux règles de typologie de pression durant la préparation des messages lors de l&#39;utilisation d&#39;un mapping LINE ou lorsque les schémas de filtrage et de ciblage diffèrent.

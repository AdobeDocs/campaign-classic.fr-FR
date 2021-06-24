---
product: campaign
title: Notes de mise à jour de Campaign 20.3
description: Notes de mise à jour de Campaign 20.3
feature: Vue d’ensemble
role: Business Practitioner
level: Beginner
exl-id: e927b7fc-95cd-4e08-bab7-ceeb6e67c265
source-git-commit: c0a3d9217696f5f5622a6af8f64c62b1a9fbce20
workflow-type: tm+mt
source-wordcount: '1955'
ht-degree: 100%

---

# Version 20.3{#release-20-3}

## ![](assets/do-not-localize/red_2.png) Version 20.3.3 - Build 9234 {#release-20-3-3-build-9234}

_11 janvier 2021_

* Correction d’un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)
* Correction d’un problème de régression lié au processus de génération des broadlogs qui entraînait le blocage du processus MTA.

## ![](assets/do-not-localize/red_2.png) Version 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 octobre 2020_

>[!CAUTION]
>
> * Cette version s’accompagne d’un nouveau protocole de connexion : si vous vous connectez à Campaign via Adobe Identity Service (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console client puissent se connecter après le **30 juin 2021**. [En savoir plus](../../technotes/ims-updates.md)
> * Cette version s’accompagne d’un [correctif de sécurité](https://helpx.adobe.com/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.
> * Si vous utilisez l’intégration Experience Cloud Triggers par le biais de l’authentification oAuth, vous devez passer à Adobe I/O comme décrit [sur cette page](../../integrations/using/configuring-adobe-io.md). Le mode d’authentification oAuth hérité avec Campaign sera mis hors service le **30 novembre 2021**.


**Nouveautés**

<table> 
<thead>
<tr> 
<th> <strong>Améliorations des notifications push iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Lors de l’intégration de votre application mobile avec Campaign, vous devez sécuriser vos communications avec le service Apple Push Notification (APN). Vous pouvez utiliser l’authentification par certificat ou par jeton.
</p>
<p>Ces deux modes d’authentification sont maintenant disponibles pour les applications mobiles iOS dans Campaign Classic :
</p>
<ul> 
<li><p>Authentification par jeton (recommandée) : ce mode d'authentification est basé sur un fichier .p8. Il est plus rapide, car chaque demande aux APN contient le jeton. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">En savoir plus</a></p></li>
<li><p>Authentification par certificat : ce mode d'authentification est basé sur un fichier .p12. Pour chaque application, un certificat distinct est requis. Ce certificat est délivré par Apple via votre compte de développeur. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">En savoir plus</a></p></li> 
</ul>
<p>Découvrez comment sélectionner le mode d'authentification dans Campaign dans la <a href="../../delivery/using/configuring-the-mobile-application.md">documentation détaillée</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Améliorations des notifications push Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Les notifications push Android ont été améliorées afin de prendre en charge l’API FCM HTTP v1 pour l’authentification de canal push Android.</a> </p>
<p>Avec la nouvelle version de l'API prise en charge, vous pouvez maintenant envoyer des messages de notification FCM qui proposent des fonctionnalités enrichies de messagerie push. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">En savoir plus</a></p> 
<p>Découvrez comment configurer l’API FCM HTTP v1 pour Android dans Adobe Campaign dans <a href="../../delivery/using/configuring-the-mobile-application-android.md">cette section</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Améliorations de la sécurité**

* Chargement sécurisé des bibliothèques : afin de se protéger des attaques par préchargement de DLL, Campaign charge désormais les DLL Windows uniquement à partir du chemin d’accès de DLL système par défaut Windows lors du chargement du client Campaign (nlclient). [En savoir plus](https://support.microsoft.com/fr-fr/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Correction d’un problème de sécurité afin de renforcer la protection contre les attaques SSRF (Server Side Request Forgery). (NEO-25661)
* Correction d’un problème qui se produisait lors du traitement des demandes d’accès à des informations personnelles RGPD qui empêchait la suppression d’enregistrements des tables personnalisées avec une relation de second niveau avec la table des destinataires. (NEO-25967)
* Correction d’un problème de sécurité lors de l’utilisation des appels d’API effectués par des utilisateurs non-administrateurs lors de la synchronisation de modèles Adobe Experience Manager. (NEO-23487)

**Mises à jour de compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

En savoir plus sur la [Matrice de compatibilité de Campaign](../../rn/using/compatibility-matrix.md).

**Fonctionnalités obsolètes**

Les fonctionnalités suivantes sont obsolètes dans la version 20.3 :

* Le domaine demdex utilisé pour importer et exporter des audiences vers Adobe Experience Cloud est obsolète. Si vous utilisez le domaine demdex pour vos comptes externes d’import/export, vous devez adapter votre mise en œuvre en conséquence. [En savoir plus](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* L’authentification de l’intégration des Triggers basée à l&#39;origine sur la configuration de l&#39;authentification oAUTH pour accéder au pipeline a été modifiée et déplacée vers Adobe I/O. [En savoir plus](../../integrations/using/configuring-adobe-io.md)

En savoir plus dans la page [Fonctionnalités obsolètes et supprimées](../../rn/using/deprecated-features.md).

**Améliorations**

* Plusieurs améliorations ont été apportées à la **console cliente** :
   * Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme dʼauthentification IMS. La mise à niveau du serveur et de la console client est obligatoire pour pouvoir se connecter après le 30 juin 2021.
   * Pour éviter toute incompatibilité avec certaines restrictions de règles GPO de sécurité Internet, l&#39;écran de connexion de la console cliente Campaign a été remplacé par un formulaire Windows standard intégré.
   * Correction d’un problème lors des activités de copie/collage dans un workflow à l’aide de la console cliente 64 bits. (NEO-27635)
   * Dans le menu **À propos**, des informations ont été ajoutées pour faire la différence entre les consoles 64 et 32 bits.
* L&#39;identifiant du workflow s&#39;affiche maintenant dans les logs lors de la reprise d&#39;un workflow, ce qui vous permet de mieux l’identifier.
* Un nouveau cookie permanent a été ajouté : nllastdelid. Ce cookie (autre que UUID230) stockera deliveryId. Lorsque le cookie de session n’est pas présent, les informations de broadlog sont extraites du deliveryId présent dans ce cookie.
Cette modification corrige un problème qui se produisait lorsque la session du navigateur était terminée : le cookie de session contenant deliveryId et broadlogId a été supprimé. Sans deliveryId, les informations de broadlog étaient introuvables et celles de la table de tracking étaient manquantes en cas de tracking permanent (dernière diffusion).
En savoir plus sur les cookies dans [cette section](../../platform/using/privacy-and-recommendations.md#cookies).
* Amélioration des performances de débit des diffusions à volume élevé avec le serveur de délivrabilité en redémarrant le processus MTA avant l&#39;envoi de la diffusion.

**Autres changements**

* Lors de l’utilisation d’un chemin relatif pour le protocole SFTP, les caractères `~/` ne sont plus automatiquement ajoutés. Si nécessaire, vous pouvez ajouter manuellement des caractères `~/` à votre chemin, mais Adobe conseille d’utiliser un **chemin absolu**.
* L&#39;authentification Windows NT a été supprimée des méthodes d&#39;authentification disponibles lors de la configuration d&#39;une nouvelle base de données avec Microsoft SQL Server. [En savoir plus](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Le workflow de nettoyage de la base a été optimisé pour Teradata afin d’améliorer les performances. (NEO-19959)
* Amélioration du message d’erreur affiché lors de l’insertion d’une image à partir d’Adobe Target. Le nom du tenant était vide dans le compte externe.
* Dans les propriétés de la diffusion, l’option **[!UICONTROL Archiver les emails]** a été renommée **[!UICONTROL Email BCC]**.
* Pour améliorer la robustesse, les requêtes selectAll avec des nœuds non valides sont maintenant rejetées. Si vous devez désactiver la vérification et revenir au comportement précédent, vous pouvez définir XtkSecurity_Disable_QueryCheck sur 0.

**Évolutions techniques**

Tomcat a été mis à jour de la version 7 (7.0.103) vers la version 8 (8.5.57).

Le répertoire `tomcat-7` a été remplacé par un répertoire `tomcat-8`.

Sous Windows, _iis_neolane_setup.vbs_ et _apache_neolane.conf_ sont maintenant installés dans le répertoire `conf` (au lieu de `tomcat-7/conf`).

Sous Linux, _apache_neolane.conf_ est maintenant installé dans le répertoire `conf`.

**Correctifs**

* Correction d’un problème qui empêchait le nouveau calcul des statistiques de diffusion.
* Correction d’un problème en raison duquel un message d’erreur s’affichait lors du téléchargement d’un fichier CSV pendant l’utilisation du build 9080 de Campaign Classic connecté à un serveur utilisant un build plus ancien. (NEO-23218)
* Correction d’un problème qui affichait un message d’erreur lors de la configuration de l’assistant Microsoft Dynamics CRM pour un compte externe. Cette erreur était due à un problème de compatibilité avec la dernière version de l&#39;API MS Dynamics CRM. (NEO-24528)
* Correction d’un problème qui empêchait d’exporter des enregistrements de type recherche (c’est-à-dire des données composées d’enregistrements de clé étrangère associés à d’autres tables) de Campaign Classic vers Microsoft Dynamics à l’aide du connecteur CRM. (NEO-23864)
* Correction d’un problème qui empêchait la récupération des données Microsoft Dynamics si l’option **Index automatique** était activée dans le connecteur CRM. (NEO-25981)
* Correction d’un problème lié à l’authentification IMS qui laissait les connexions ouvertes même si elles étaient terminées. Les connexions terminées seront maintenant automatiquement fermées dès leur fin afin d&#39;éviter d&#39;accumuler des connexions et de consommer des ressources système. (NEO-25996)
* Correction d’un problème qui n’affichait aucun message d’erreur lors de l’échec de la synchronisation du contenu Adobe Experience Manager pour une diffusion en raison d’une configuration incorrecte du compte externe (compte ou mot de passe incorrect). Un message s’affiche maintenant en cas d’échec, ce qui permet d’identifier plus facilement le problème. (NEO-25586)
* Correction d’un problème qui se produisait lors de la sélection du type d’opération **Mise à jour** dans l’activité **Mise à jour des données**. Si les données à mettre à jour étaient incorrectes, le workflow était en erreur et échouait. En cas de données incorrectes, le workflow n’échoue pas et les enregistrements sont stockés dans une transition sortante **Rejets**. (NEO-23794)
* Correction d’un problème qui empêchait le fonctionnement des workflows contenant des sous-workflows. (NEO-24036)
* Correction d’un problème lors de la modification de la description d’un modèle de campagne qui empêchait l’affichage du bouton **Enregistrer** pendant la copie et le collage de symboles, comme des caractères japonais. (NEO-27071)
* Correction d’un problème qui empêchait la modification du serveur de tracking dans l’assistant de configuration de l’instance.
* Correction d’un problème qui empêchait l’enregistrement de la description d’une campagne ou d’un modèle de campagne en cliquant en dehors de la fenêtre avant de cliquer sur le bouton **Enregistrer**. (NEO-27449)
* Correction d’un problème qui empêchait le fonctionnement du workflow technique **Nombre de profils de facturation actifs** (billingActiveContactCount). Ce problème peut se produire si une liaison a été effectuée sur un champ calculé dans une extension de schéma. Une grande quantité de données a été créée, ce qui peut entraîner un manque d&#39;espace temporaire dans la base de données. (NEO-24062)
* Correction d’un problème lié à l’activité **Chargement (fichier)** qui empêchait l’import de caractères japonais depuis des fichiers txt et csv s’ils étaient placés à la fin du fichier. (NEO-24957)
* Correction d’un problème en raison duquel les diffusions continues empêchaient le renseignement correct des champs **Début de l’analyse** et **Fin de l’analyse**. (NEO-20755)
* Correction d’un problème en raison duquel un message d’erreur s’affichait lors de la tentative de prévisualisation de messages SMS après une requête sur un autre schéma que **Destinataire** (nms:destinataire). (NEO-27517)
* Correction d’un problème lors de l’utilisation du connecteur Snowflake FDA. Un utilisateur disposant des droits nommés d&#39;accès à Snowflake FDA n&#39;a pas pu exécuter une requête sur un schéma Snowflake. Une erreur de type « Mot de passe introuvable » s&#39;affichait dans les logs. (NEO-23851)
* Correction d’un problème qui se produisait pendant l’utilisation d’un connecteur FDA lorsque le nom du schéma FDA lié était une sous-chaîne d’un nom d’élément du schéma actuel. Ce problème se produisait, par exemple, si le schéma FDA était « cust » et que l’un des éléments du schéma Destinataire était « customer ». Lors de la récupération de la colonne à l’intérieur de l’élément « customer » et de l’ajout d’une colonne à partir du schéma FDA « cust », la valeur de la colonne locale était absente. (NEO-20193)
* Correction d’un problème dans les workflows lors de la récupération d’enregistrements d’une base de données externe et de leur insertion dans la base de données Campaign. (NEO-26359)
* Correction d’un problème dans le workflow technique **Mise à jour du statut des événements** : pour faire correspondre la taille des champs correspondants entrants dans l&#39;activité **Statistiques de diffusion**, la taille de trois champs de destination de l&#39;activité **Mise à jour des stats de diffusion** a été changée de 32 à 64 bits. (NEO-11557) En savoir plus sur le workflow **Mise à jour du statut des événements** dans [cette section](../../workflow/using/about-technical-workflows.md).
* Correction d’un problème dans le rapport **Historique des événements Message Center** qui provoquait des erreurs de script lors de la tentative d’application de filtres et rendait impossible le filtrage selon une période. (NEO-23365)
* Correction d’un problème d’interférence entre les workflows techniques **Traitements sur les opérations** et **Prévisualisation** (prévisionnel). Ce problème se produisait lorsque les diffusions planifiées conservaient le statut « Cible prête » ou « Prêt à être diffusé ». (NEO-20819)
* Correction d’un problème d’analyse XML en raison duquel l’identifiant XML n’était pas présent dans le champ mdata dans xtkOperator. Ce problème entraînait un échec du postupgrade. (NEO-26113)
* Correction d&#39;un problème lors de l&#39;utilisation de l&#39;activité **Transfert de fichier** liée à un compte externe Azure crypté en SSL pour lequel la connexion était établie avec HTTP au lieu de HTTPS. (NEO-26720)
* Correction d’un problème lié à la base de données MSSQL en raison duquel une erreur se produisait avec la procédure up_updatestats pendant le workflow de nettoyage.
* Correction d’un blocage qui se produisait pendant l’arrêt du processus web si les demandes d’interaction étaient toujours en cours de traitement. (NEO-26447)
* Correction d’un problème en raison duquel la fonction **NoNull** d’Oracle DB ne fonctionnait plus après l’upgrade 9032. (NEO-26488)
* Correction d’un problème en raison duquel le workflow de tracking échouait après l’upgrade 9171 si le package LINEV2 était installé sans le package Message Center.
* Correction d’un problème d’évolutivité qui empêchait l’augmentation du pool de connexions au nombre de connexions souhaité, car la chaîne de connexion à la base de données pour l’attribut &#39;APP&#39; finissait par obtenir une valeur non valide. (NEO-25105)
* Correction d’un problème au niveau de la configuration du proxy qui empêchait la connexion à Adobe Campaign après la dernière mise à jour de Windows 10. (NEO-27813)
* Correction d’un problème en raison duquel des URL indésirables étaient visibles dans les emails diffusés après l’import de modèles HTML contenant des liens de tracking. (NEO-25909)
* Correction d’un problème en raison duquel le serveur se bloquait lors de l’affichage des données de la cible à partir d’une activité **Partage** dans un workflow.
* Correction d’un problème de blocage du serveur en empêchant la corruption de la mémoire lors du nettoyage de l’analyseur d’expressions. (NEO-26856)
* Correction d’un problème dans l’activité d’enrichissement en raison duquel les utilisateurs non-administrateurs définissaient des variables de l’instance. (NEO-25653)

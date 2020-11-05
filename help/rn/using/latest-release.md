---
title: Dernière version
description: Dernière version de Campaign Classic Notes
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '1824'
ht-degree: 4%

---


# Dernière version{#latest-release}

Cette page liste de nouvelles fonctionnalités, améliorations et corrections apportées à la **dernière version** du Campaign Classic Release Candidate.

Pour la version Gold Standard Campaign Classic (dernière version GA), [reportez-vous à cette page](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Version 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 octobre 2020_

**Nouveautés**

<table> 
<thead>
<tr> 
<th> <strong>Améliorations des notifications Push iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Lors de l’intégration de votre application mobile à Campaign, vous devez sécuriser votre communication avec le service Apple Push Notification (APN). Vous pouvez utiliser l’authentification par certificat ou par jeton.
</p>
<p>Ces deux modes d’authentification sont désormais disponibles pour les applications mobiles iOS en Campaign Classic :
</p>
<ul> 
<li><p>Authentification basée sur un jeton (recommandé) : ce mode d'authentification est basé sur un fichier .p8. Ce mode d’authentification est plus rapide car chaque requête aux APN contient le jeton. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">En savoir plus</a></p></li>
<li><p>Authentification basée sur un certificat : ce mode d'authentification est basé sur un fichier .p12. Pour chaque application, un certificat distinct est requis. Ce certificat est délivré par Apple via votre compte de développeur. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">En savoir plus</a></p></li> 
</ul>
<p>Découvrez comment sélectionner le mode d'authentification dans Campaign dans la documentation <a href="../../delivery/using/configuring-the-mobile-application.md"></a>détaillée.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Améliorations des notifications Push Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Les notifications Push Android ont été améliorées afin de prendre en charge l’API HTTP v1 de FCM pour l’authentification de canal Push Android. </p>
<p>Avec la nouvelle version d'API prise en charge, vous pouvez désormais envoyer des messages de notification FCM qui offrent des fonctionnalités améliorées de messagerie Push. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">En savoir plus</a></p> 
<p>Découvrez comment configurer l’API FCM HTTP v1 pour Android en Adobe Campaign dans <a href="../../delivery/using/configuring-the-mobile-application-android.md">cette section</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Améliorations de la sécurité**

* Chargement sécurisé des bibliothèques : Afin de protéger des attaques par préchargement de DLL, Campaign charge désormais les DLL Windows uniquement à partir du chemin d’accès de la DLL système par défaut Windows lors du chargement du client Campaign (nlclient). [En savoir plus](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Correction d’un problème de sécurité afin de renforcer la protection contre les attaques SSRF (Server Side Request Forgery). (NEO-25661)
* Correction d’un problème survenant lors du traitement des demandes de confidentialité GDPR qui empêchait la suppression d’enregistrements des tables personnalisées avec une relation de second niveau avec la table du Destinataire. (NEO-25967)
* Correction d’un problème de sécurité à l’aide des appels d’API effectués par des utilisateurs non-administrateurs lors de la synchronisation de modèles Adobe Experience Manager. (NEO-23487)

**Mises à jour de compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Fonctionnalités obsolètes**

Les fonctionnalités suivantes sont obsolètes dans la version 20.3 :

* Le domaine demdex utilisé pour importer et exporter des audiences vers le Adobe Experience Cloud est obsolète. Si vous utilisez le domaine demdex pour vos comptes externes d’importation/exportation, vous devez adapter votre mise en oeuvre en conséquence. [En savoir plus](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Déclenche l&#39;authentification d&#39;intégration basée à l&#39;origine sur la configuration de l&#39;authentification oAUTH pour accéder au pipeline a maintenant été modifiée et déplacée vers les E/S d&#39;Adobe. [En savoir plus](../../integrations/using/configuring-adobe-io.md)

En savoir plus sur la page [Fonctions](../../rn/using/deprecated-features.md)obsolètes et supprimées.

**Améliorations**

* Plusieurs améliorations ont été apportées à la console **** Client :
   * Pour éviter toute incompatibilité avec certaines restrictions des règles d&#39;objet de stratégie de groupe de sécurité Internet, l&#39;écran de connexion de la console cliente Campaign a été remplacé par un formulaire Windows standard intégré.
   * Correction d’un problème en raison duquel les activités de copie/collage dans un flux de travail à l’aide de la console Client 64 bits étaient copiées/collées. (NEO-27635)
   * Dans le menu **À propos** , des informations ont été ajoutées pour distinguer les consoles 64 et 32 bits.
* L&#39;identifiant de flux de travaux s&#39;affiche désormais dans les journaux lors de la reprise d&#39;un flux de travaux, ce qui vous permet de mieux identifier le flux de travaux qui a été repris.
* Un nouveau cookie permanent a été introduit : nllastdelid. Ce cookie (autre que UUID230) stockera l’ID de diffusion. Lorsque le cookie de session n’est pas présent, les informations du journal de diffusion sont extraites du paramètre deliveryId présent dans ce cookie.
Cette modification corrige un problème qui se produisait lorsque la session du navigateur était terminée : le cookie de session contenant deliveryId et broadlogId a été supprimé. Sans deliveryId, les informations du journal large étaient introuvables et les informations de la table de suivi manquaient en cas de suivi permanent (dernière diffusion).
Learn more about cookies in [this section](../../platform/using/privacy-and-recommendations.md#cookies).
* Amélioration des performances de débit de diffusion de volume élevé avec le serveur de délivrabilité en redémarrant le processus MTA avant l&#39;envoi de diffusion.

**Autres changements**

* Lors de l’utilisation d’un chemin relatif pour le protocole SFTP, `~/` les caractères ne sont plus automatiquement ajoutés. Si nécessaire, vous pouvez ajouter `~/` des caractères à votre chemin manuellement, mais l’Adobe recommande d’utiliser un chemin **** absolu.
* L&#39;authentification Windows NT a été supprimée des méthodes d&#39;authentification disponibles lors de la configuration d&#39;une nouvelle base de données avec Microsoft SQL Server. [En savoir plus](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Le processus de nettoyage de la base de données a été optimisé pour Teradata afin d’améliorer les performances. (NEO-19959)
* Amélioration du message d’erreur affiché lors de l’insertion d’une image à partir d’Adobe Target et le nom du client était vide dans le compte externe.
* Dans les propriétés de la diffusion, l’option **[!UICONTROL Archiver les courriers électroniques]** a été renommée **[!UICONTROL Courrier électronique (Cci]**).
* Pour améliorer la robustesse, sélectionnez Toutes les requêtes avec des noeuds non valides sont maintenant rejetées. Si vous devez désactiver la vérification et revenir au comportement précédent, vous pouvez définir XtkSecurity_Disable_QueryCheck sur 0.

**Évolutions techniques**

Tomcat a été mis à jour de la version 7 (7.0.103) à la version 8 (8.5.57).

Le `tomcat-7` répertoire est remplacé par un `tomcat-8` répertoire.

Sous Windows, _is_neolane_setup.vbs_ et _apache_neolane.conf_ sont désormais installés dans le `conf` répertoire (au lieu de `tomcat-7/conf` précédemment).

Sur linux, _apache_neolane.conf_ est maintenant installé dans le `conf` répertoire.

**Correctifs**

* Correction d’un problème en raison duquel les statistiques de diffusion ne pouvaient pas être recalculées.
* Correction d’un problème en raison duquel un message d’erreur s’affichait lors du téléchargement d’un fichier CSV lors de l’utilisation de la version 9080 du Campaign Classic connectée à un serveur à l’aide d’une version plus ancienne. (NEO-23218)
* Correction d’un problème qui pouvait afficher un message d’erreur lors de la configuration de l’assistant Microsoft Dynamics CRM pour un compte externe. Ceci était dû à un problème de compatibilité avec la dernière version de l&#39;API MS Dynamics CRM. (NEO-24528)
* Correction d’un problème qui vous empêchait d’exporter des enregistrements de type recherche (c’est-à-dire des données composées d’enregistrements de clé étrangère connectés à d’autres tables) du Campaign Classic vers Microsoft Dynamics à l’aide du connecteur CRM. (NEO-23864)
* Correction d’un problème qui empêchait la récupération des données Microsoft Dynamics si l’option d’index **** automatique était activée dans le connecteur CRM. (NEO-25981)
* Correction d’un problème d’authentification IMS en raison duquel les connexions pouvaient être ouvertes même si elles étaient terminées. Les connexions terminées seront désormais automatiquement fermées dès qu&#39;elles seront terminées afin d&#39;éviter d&#39;accumuler des connexions et de consommer les ressources du système. (NEO-25996)
* Correction d’un problème qui n’affichait aucun message d’erreur lorsque la synchronisation du contenu Adobe Experience Manager échouait pour une diffusion en raison d’une configuration incorrecte du compte externe (compte ou mot de passe incorrect). Un message s’affiche désormais en cas d’échec, ce qui vous permet d’identifier plus facilement le problème. (NEO-25586)
* Correction d’un problème survenant lors de la sélection du type d’opération **Mettre à jour** dans l’activité de données **** Mettre à jour. Si les données à mettre à jour étaient incorrectes, le flux de travail était en erreur et échouait. En cas de données incorrectes, le flux de travail n’échoue pas et les enregistrements sont stockés dans une transition **Rejette** sortante. (NEO-23794)
* Correction d’un problème en raison duquel les workflows contenant des sous-workflows ne fonctionnaient pas. (NEO-24036)
* Correction d’un problème lors de la modification d’une description de modèle de campagne qui empêchait l’affichage du bouton **Enregistrer** lors du copier-coller de symboles tels que, par exemple, des caractères japonais. (NEO-27071)
* Correction d’un problème qui pouvait vous empêcher de modifier le serveur de suivi dans l’assistant de configuration d’instance.
* Correction d’un problème qui empêchait l’enregistrement de la description d’une campagne ou d’un modèle de campagne en cliquant en dehors de la fenêtre avant de cliquer sur le bouton **Enregistrer** . (NEO-27449)
* Correction d’un problème en raison duquel le flux de travail technique **Nombre de profils** de facturation principaux (billingActiveContactCount) ne fonctionnait pas. Cela peut se produire si un lien a été exécuté sur un champ calculé dans une extension de schéma. Une grande quantité de données a été créée, ce qui pourrait entraîner une pénurie d&#39;espace temporaire dans la base de données. (NEO-24062)
* Correction d’un problème lié à l’activité de chargement des **données (fichier)** , qui pouvait vous empêcher d’importer des caractères japonais à partir de fichiers txt et csv s’ils étaient positionnés à la fin du fichier. (NEO-24957)
* Correction d’un problème en raison duquel les diffusions continues pouvaient empêcher que les champs **Analyse démarrée** et **Analyse terminée** ne soient renseignés correctement. (NEO-20755)
* Correction d’un problème en raison duquel un message d’erreur pouvait s’afficher lors de la tentative de prévisualisation de messages SMS après une requête sur un autre schéma que **Destinataire** (nms:destinataire). (NEO-27517)
* Correction d’un problème lors de l’utilisation du connecteur de FDA de Snowflake. Un utilisateur disposant des droits d&#39;accès de FDA Snowflake n&#39;a pas pu exécuter une requête sur un schéma Snowflake. Une erreur de type &quot;Mot de passe introuvable&quot; s&#39;affichait dans les journaux. (NEO-23851)
* Correction d’un problème survenant lors de l’utilisation d’un connecteur de FDA lorsque le nom du schéma de FDA lié était une sous-chaîne d’un nom d’élément du schéma actuel. Cela se produisait, par exemple, si le schéma de FDA était &quot;cust&quot; et que l’un des éléments du schéma Destinataire était &quot;customer&quot;. Lors de la récupération de la colonne à l’intérieur de l’élément &quot;client&quot; et de l’ajout d’une colonne à partir du schéma de FDA &quot;client&quot;, la valeur de la colonne locale était absente. (NEO-20193)
* Correction d’un problème dans les workflows lors de la récupération d’enregistrements d’une base de données externe et de leur insertion dans la base de données Campaign. (NEO-26359)
* Correction d’un problème dans le processus technique d’état **du événement de** mise à jour : pour correspondre à la taille des champs correspondants entrants dans l&#39;activité des statistiques **de** Diffusion, la taille de trois champs de destination dans l&#39;activité des statistiques **de la diffusion de** mise à jour a été modifiée de 32 à 64 bits. (NEO-11557) En savoir plus sur le processus de **mise à jour de l’état** du événement dans [cette section](../../workflow/using/message-center--execution-.md).
* Correction d’un problème dans le rapport Historique **des Événements du Centre de** messages qui provoquait des erreurs de script lors de la tentative d’application de filtres et rendait impossible le filtrage selon une plage de dates. (NEO-23365)
* Correction d’un problème d’interférence entre les travaux **** Campaign (opérationMgt) et les workflows techniques de **Prévisualisation** (prévision). Cela se produisait lorsque les diffusions planifiées conservaient l’état &quot;Prêt pour la Cible&quot; ou &quot;Prêt pour la livraison&quot;. (NEO-20819)
* Correction d’un problème d’analyse XML en raison duquel l’identifiant XML n’était pas présent dans le champ de données dans xtkOperator. Cela provoquait un échec après la mise à niveau. (NEO-26113)
* Correction d&#39;un problème lors de l&#39;utilisation de l&#39;activité de transfert **de** fichiers liée à un compte externe Azure chiffré dans SSL où la connexion était établie avec HTTP au lieu de HTTPS. (NEO-26720)
* Correction d’un problème de la base de données MSSQL en raison duquel une erreur pouvait se produire avec la procédure up_updatestats pendant le processus de nettoyage.
* Correction d’un blocage survenant pendant l’arrêt du processus Web si les demandes d’interaction étaient toujours en cours de traitement. (NEO-26447)
* Correction d’un problème en raison duquel la fonction **NoNull** dans Oracle DB ne fonctionnait plus après la mise à niveau 9032. (NEO-26488)
* Correction d’un problème en raison duquel le processus de suivi échouait après la mise à niveau 9171 si le package LINEV2 était installé sans le package Message Center.
* Correction d’un problème d’évolutivité qui empêchait l’augmentation du pool de connexions au nombre de connexions souhaité, car la chaîne de connexion à la base de données pour l’attribut &quot;APP&quot; finissait par obtenir une valeur non valide. (NEO-25105)
* Correction d’un problème au niveau de la configuration du proxy qui empêchait la connexion à Adobe Campaign après la dernière mise à jour de Windows 10. (NEO-27813)
* Correction d’un problème en raison duquel les URL indésirables étaient visibles dans les courriers électroniques remis après l’importation de modèles HTML contenant des liens de suivi. (NEO-25909)
* Correction d’un problème en raison duquel le serveur se bloquait lors de l’affichage des données de cible du reste à partir d’une activité **fractionnée** dans un processus.
* Correction d’un problème de blocage du serveur en empêchant la corruption de la mémoire lors du nettoyage de l’analyseur d’expressions. (NEO-26856)
* Correction d’un problème dans l’activité d’enrichissement en raison duquel les utilisateurs non administrateurs définissaient des variables d’instance. (NEO-25653)
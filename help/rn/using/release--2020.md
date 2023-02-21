---
product: campaign
title: Versions 2020
description: En savoir plus sur les versions de Campaign Classic 2020
feature: Overview
role: User
level: Beginner
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '6610'
ht-degree: 100%

---

# Versions 2020{#release-2020}

![](../../assets/v7-only.svg)


## Version 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Version 20.3.3 - Build 9234 {#release-20-3-3-build-9234}

_11 janvier 2021_

* Correction d&#39;un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)
* Correction d’un problème de régression lié au processus de génération des broadlogs qui entraînait le blocage du processus MTA.

### ![](assets/do-not-localize/red_2.png) Version 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_27 octobre 2020_

>[!CAUTION]
>
> * Cette version s’accompagne d’un nouveau protocole de connexion : si vous vous connectez à Campaign via le Service d&#39;identités Adobe (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console cliente puissent se connecter après le **30 juin 2021**. [En savoir plus](../../technotes/using/ims-updates.md)
> * Cette version s&#39;accompagne d&#39;un [correctif de sécurité](https://helpx.adobe.com/fr/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.
> * Si vous utilisez l’intégration Experience Cloud Triggers par le biais de l’authentification oAuth, vous devez passer à Adobe I/O comme décrit [sur cette page](../../integrations/using/configuring-adobe-io.md). Lʼancien mode dʼauthentification oAuth avec Campaign [a été retiré](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=fr) en **septembre 2021**. Les environnements hébergés bénéficient dʼune extension jusquʼau **23 février 2022**. En tant que client on-premise ou hybride, contactez l’assistance clientèle d’Adobe pour étendre l’assistance jusqu’en février 2022. Vous devez fournir [l’AppID de l’application OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) à Adobe.


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
<p>Découvrez comment configurer l’API FCM HTTP v1 pour Android dans Adobe Campaign dans <a href="../../delivery/using/configuring-the-mobile-application-android.md">cette section</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Améliorations de la sécurité**

* Chargement sécurisé des bibliothèques : afin de se protéger des attaques par préchargement de DLL, Campaign charge désormais les DLL Windows uniquement à partir du chemin d’accès de DLL système par défaut Windows lors du chargement du client Campaign (nlclient). [En savoir plus](https://support.microsoft.com/fr-fr/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Correction d’un problème de sécurité afin de renforcer la protection contre les attaques SSRF (Server Side Request Forgery). (NEO-25661)
* Correction d’un problème qui se produisait lors du traitement des demandes d’accès à des informations personnelles RGPD qui empêchait la suppression d’enregistrements des tables personnalisées avec une relation de second niveau avec la table des destinataires. (NEO-25967)
* Correction d’un problème de sécurité lors de l’utilisation des appels d’API effectués par des utilisateurs non-administrateurs lors de la synchronisation de modèles Adobe Experience Manager. (NEO-23487)

**Mises à jour de compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

En savoir plus sur la [Matrice de compatibilité de Campaign](../../rn/using/compatibility-matrix.md).

**Fonctionnalités obsolètes**

Les fonctionnalités suivantes sont obsolètes dans la version 20.3 :

* Le domaine demdex utilisé pour importer et exporter des audiences vers Adobe Experience Cloud est obsolète. Si vous utilisez le domaine demdex pour vos comptes externes d’import/export, vous devez adapter votre mise en œuvre en conséquence. [En savoir plus](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
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

* Lors de l’utilisation d’un chemin relatif pour le protocole SFTP, les caractères `~/` ne sont plus automatiquement ajoutés. Si nécessaire, vous pouvez ajouter manuellement des caractères `~/` à votre chemin, mais Adobe conseille d’utiliser un **chemin absolu**.
* L&#39;authentification Windows NT a été supprimée des méthodes d&#39;authentification disponibles lors de la configuration d&#39;une nouvelle base de données avec Microsoft SQL Server. [En savoir plus](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Le workflow de nettoyage de la base a été optimisé pour Teradata afin d’améliorer les performances. (NEO-19959)
* Amélioration du message d’erreur affiché lors de l’insertion d’une image à partir d’Adobe Target. Le nom du tenant était vide dans le compte externe.
* Dans les propriétés de la diffusion, l’option **[!UICONTROL Archiver les emails]** a été renommée **[!UICONTROL Email BCC]**.
* Pour améliorer la robustesse, les requêtes selectAll avec des nœuds non valides sont maintenant rejetées. Si vous devez désactiver la vérification et revenir au comportement précédent, vous pouvez définir XtkSecurity_Disable_QueryCheck sur 0.
* La prise en charge de la plage d’identifiants négative a été ajoutée pour la séquence nmsBroadlogId. Cette build ajuste la valeur minimale de la séquence nmsBroadlogId afin dʼinclure la plage négative. Si vous disposez dʼun cas d’utilisation strict qui n’autorise pas les identifiants négatifs, ramenez la valeur minimale de la séquence à 1.

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
* Correction d’un problème qui n’affichait aucun message d’erreur lors de l’échec de la synchronisation du contenu Adobe Experience Manager pour une diffusion en raison d’une configuration incorrecte du compte externe (compte ou mot de passe incorrect). Un message s’affiche maintenant en cas d’échec, ce qui permet d’identifier plus facilement le problème. (NEO-25586)
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
* Correction d&#39;un problème lors de l&#39;utilisation de l&#39;activité **Transfert de fichier** liée à un compte externe Azure chiffré en SSL pour lequel la connexion était établie avec HTTP au lieu de HTTPS. (NEO-26720)
* Correction d’un problème lié à la base de données MSSQL en raison duquel une erreur se produisait avec la procédure up_updatestats pendant le workflow de nettoyage.
* Correction d’un blocage qui se produisait pendant l’arrêt du processus web si les demandes d’interaction étaient toujours en cours de traitement. (NEO-26447)
* Correction d’un problème en raison duquel la fonction **NoNull** d’Oracle DB ne fonctionnait plus après l’upgrade 9032. (NEO-26488)
* Correction d’un problème en raison duquel le workflow de tracking échouait après l’upgrade 9171 si le package LINEV2 était installé sans le package Message Center.
* Correction d’un problème d’évolutivité qui empêchait l’augmentation du pool de connexions au nombre de connexions souhaité, car la chaîne de connexion à la base de données pour l’attribut &#39;APP&#39; finissait par obtenir une valeur non valide. (NEO-25105)
* Correction d’un problème au niveau de la configuration du proxy qui empêchait la connexion à Adobe Campaign après la dernière mise à jour de Windows 10. (NEO-27813)
* Correction d’un problème en raison duquel des URL indésirables étaient visibles dans les emails diffusés après l’import de modèles HTML contenant des liens de tracking. (NEO-25909)
* Correction d’un problème en raison duquel le serveur se bloquait lors de l’affichage des données de la cible à partir d’une activité **Partage** dans un workflow.
* Correction d’un problème de blocage du serveur en empêchant la corruption de la mémoire lors du nettoyage de l’analyseur d’expressions. (NEO-26856)
* Correction d’un problème dans l’activité d’enrichissement en raison duquel les utilisateurs non-administrateurs définissaient des variables de l’instance. (NEO-25653)
* Correction d&#39;une régression qui pouvait bloquer l&#39;export des données du workflow vers une base FDA (Teradata, Snowflake).

## Version 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Version 20.2.5 - Build 9188 {#release-20-2-5-build-9188}

_15 avril 2021_

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n&#39;est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_31 mars 2021_

**Améliorations**

* Une amélioration a été apportée pour empêcher les blocages sur les appels SOAP non valides. Cette situation pouvait entraîner l&#39;arrêt du fonctionnement de l&#39;instance lors de l&#39;exécution de requêtes complexes spécifiques. (NEO-28796, NEO-30553)
* Correction d&#39;une régression qui empêchait l&#39;envoi de diffusions SMS avec TLS en raison de la vérification du nom d&#39;hôte. (NEO-29581)
* Correction d&#39;un problème en raison duquel les liens de tracking signés ne fonctionnaient pas sur certains clients de messagerie. (NEO-28414, NEO-29615)
* Correction d&#39;une séquence d&#39;ID de tracking lors de l&#39;utilisation de balises de tracking webApp qui provoquait des conflits avec les ID dupliqués. (NEO-27931)
* Correction d&#39;un problème en raison duquel les workflows en cours d&#39;exécution étaient arrêtés par le redémarrage quotidien du serveur wfserver. (NEO-30047)
* Correction d&#39;un problème de sécurité lors de l&#39;utilisation des appels d&#39;API effectués par des utilisateurs non-administrateurs lors de la synchronisation de modèles Adobe Experience Manager. (NEO-32389, NEO-23487)
* Correction d&#39;un problème en raison duquel la console se bloquait lors de la fermeture d&#39;une boîte de dialogue sur une diffusion créée à partir d&#39;un modèle. (NEO-31547)
* Correction d&#39;un problème qui se produisait lors de la création et de l&#39;enregistrement d&#39;une diffusion dans l&#39;onglet **Ciblage et workflow** d&#39;une campagne : la prévisualisation échouait avec l&#39;erreur suivante.(NEO-29440)
* Correction d&#39;un problème en raison duquel Tomcat 8.5 envoyait des réponses non valides, ce qui provoquait des erreurs dans les logs de messagerie transactionnelle. (NEO-30858)
* Correction d&#39;un problème de régression qui entraînait une corruption de la mémoire dans la gestion des threads externes et avait un impact sur les performances.
* Correction d&#39;un problème en raison duquel le workflow de facturation échouait lors de l&#39;utilisation d&#39;un mapping de ciblage personnalisé. La clé principale du schéma personnalisé est stockée dans la colonne &#39;sourceId&#39; qui n&#39;autorisait que des entiers. Elle autorise désormais des entiers ainsi que des valeurs de chaîne. (NEO-25914, NEO-28146)
* Correction d&#39;une régression qui empêchait l&#39;utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Version 20.2.4 - Build 9187 {#release-20-2-4-build-9187}

_15 avril 2021_

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)
* Correction d&#39;une régression qui empêchait l&#39;utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453, NEO-31454)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n&#39;est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_22 décembre 2020_

>[!CAUTION]
>
> * Cette version s&#39;accompagne d&#39;un nouveau protocole de connexion : si vous vous connectez à Campaign via Adobe IDentity Service (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console client puissent se connecter après le **30 juin 2021**.  [En savoir plus](../../technotes/using/ims-updates.md)
> * Cette version s&#39;accompagne d&#39;un [correctif de sécurité](https://helpx.adobe.com/fr/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.
> * Si vous utilisez l’intégration Experience Cloud Triggers par le biais de l’authentification oAuth, vous devez passer à Adobe I/O comme décrit [sur cette page](../../integrations/using/configuring-adobe-io.md). Lʼancien mode dʼauthentification oAuth avec Campaign [a été retiré](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=fr) en **septembre 2021**. Les environnements hébergés bénéficient dʼune extension jusquʼau **23 février 2022**. En tant que client on-premise ou hybride, contactez l’assistance clientèle d’Adobe pour étendre l’assistance jusqu’en février 2022. Vous devez fournir [l’AppID de l’application OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) à Adobe.


**Améliorations**

* Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme d&#39;authentification IMS.
* L&#39;authentification de l&#39;intégration des Triggers basée à l&#39;origine sur la configuration de l&#39;authentification oAUTH pour accéder au pipeline a été modifiée et déplacée vers Adobe I/O. [En savoir plus](../../integrations/using/configuring-adobe-io.md)
* Après la [fin de la prise en charge du protocole binaire hérité des APN iOS](https://developer.apple.com/news/?id=c88acm2b), toutes les instances utilisant ce protocole sont mises à jour vers le protocole HTTP/2 durant la mise à niveau.
* Correction d&#39;un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)
* Correction d&#39;un problème en raison duquel le connecteur SMPP était désactivé après une erreur de connexion, ce qui empêchait l&#39;envoi d&#39;autres diffusions SMS et provoquait des problèmes de performances. (NEO-28609)
* Correction d&#39;un problème de blocage du serveur en empêchant la corruption de la mémoire lors du nettoyage de l&#39;analyseur d&#39;expressions. (NEO-26856)
* Correction d&#39;un problème en raison duquel le serveur se bloquait lors de l&#39;affichage des données de la cible à partir d&#39;une activité **Partage** dans un workflow.
* Correction d&#39;un problème en raison duquel un message d&#39;erreur s&#39;affichait lors de la tentative de prévisualisation de messages SMS après une requête sur un autre schéma que **Destinataire** (nms:destinataire). (NEO-27517)
* Correction d&#39;un problème en raison duquel lors de l&#39;exécution d&#39;une demande de connexion HTTPS avec le numéro de port explicitement défini dans le nom d&#39;hôte, l&#39;appel échouait avec une erreur de certificat. (NEO-29146)
* Correction d&#39;un problème dans la gestion des threads POSIX qui générait des fichiers de vidage principaux volumineux sur l&#39;instance marketing. (NEO-28117, NEO-29281)
* Correction de problèmes susceptibles de provoquer un blocage du processus web lors de la préparation de diffusions ou avec une prévisualisation de diffusion récurrente. (NEO-27790, NEO-27517)
* Correction d&#39;un problème en raison duquel l&#39;envoi de diffusions ou de BAT échouait lorsqu&#39;il était déclenché par un opérateur non administrateur. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **Nouvelle version d&#39;octobre du Panneau de contrôle** avec configuration de domaine utilisant des CNAME et nouvelles fonctionnalités de surveillance de base de données. [En savoir plus](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=fr).

### ![](assets/do-not-localize/red_2.png) Version 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_11 septembre 2020_

* Correction d&#39;une régression qui entraînait le blocage de la préparation des diffusions en raison d&#39;une seule fonction erronée sur le fragment de diffusion, et conduisait à une surcharge de la mémoire. (NEO-27346)
* Correction d&#39;un problème de postupgrade qui désactivait Apache et le serveur Web avant la republication de l&#39;application web. (NEO-27155)
* Correction dʼune régression relative à la gestion des modèles HTML, en raison de laquelle les URL de suivi devenaient visibles du fait dʼune mauvaise interprétation des onglets. (NEO-25909)
* Correction d&#39;un problème lié au workflow de nettoyage de la base de données qui pouvait échouer en raison d&#39;une source de données non gérée. (NEO-23160, NEO-23364)
* Le workflow de nettoyage purge désormais les listes expirées par lots de 100 plutôt qu&#39;une par une.
* Correction d&#39;une régression qui empêchait de modifier le nom interne d&#39;un compte externe. (NEO-27323)
* Correction d&#39;une régression au cours d&#39;un postupgrade qui provoquait un démarrage incorrect de nlserver (logs d&#39;erreur).
* La gestion des mises à jour pour la mémoire partagée a été améliorée. Les étapes supplémentaires requises dans la version 20.2 ne sont plus nécessaires.

### ![](assets/do-not-localize/red_2.png) Version 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_22 juillet 2020_

* Correction d&#39;un problème qui empêchait le tracking de fonctionner lorsque la fonction de signature était désactivée. (NEO-26411)
* Correction d&#39;un problème en raison duquel les liens non signés provenant de domaines personnalisés étaient bloqués au lieu d&#39;être autorisés. (NEO-25210)
* Correction d&#39;un problème qui empêchait d&#39;ouvrir/de cliquer sur les URL de tracking lors de l&#39;utilisation de certaines anciennes versions d&#39;Outlook. (NEO-25688)
* Correction d&#39;un problème en raison duquel les URL de page miroir étaient incorrectement définies dans les diffusions par email (en raison d&#39;un contrôle incorrect des caractères ASCII). (NEO-26084)
* Correction d&#39;un problème lié à gestion des URL de codage dans le service anti-hameçonnage. (NEO-25283)
* Correction d&#39;un problème qui empêchait le suivi des URL à l&#39;aide de fragments dans les paramètres de personnalisation (balises d&#39;ancrage avec signe dièse) de fonctionner. (NEO-25774)
* Correction d&#39;un problème de suivi lors de l&#39;utilisation de formules de tracking personnalisées spécifiques. (NEO-25277)

* Correction d&#39;un problème qui empêchait le suivi des « clics de notification » de fonctionner (notifications push iOS et Android). (NEO-25965)
* Correction d&#39;une régression qui affectait les champs calculés d&#39;un workflow et provoquait l&#39;échec de ce workflow. (NEO-25194)
* Correction d&#39;une régression qui empêchait le fonctionnement de la création à la volée d&#39;URL de tracking web. (NEO-20999)
* Correction d&#39;un problème de régression lié aux rapports de diffusion d&#39;usine qui s&#39;affichaient tronqués lors de l&#39;export au format PDF. (NEO-25757)
* Correction d&#39;un problème de blocage dans l&#39;assistant de déploiement.
* Correction d&#39;un problème qui empêchait le fonctionnement correct du workflow Notification des offres après un postupgrade.
* Le connecteur HTTP2 iOS a été amélioré (mises à jour tierces et gestion des erreurs). (NEO-25904, NEO-25903)
* La liste jarsToSkip de catalina.properties a été mise à jour afin de supprimer la référence à un fichier jar qui n&#39;était plus utilisé (notifications iOS).
* Correction d&#39;un problème qui bloquait la préparation des diffusions après un postupgrade.
* Après le passage au nouveau mécanisme d’identifiant de séquence, toutes les applications web qui mettent à jour la table des destinataires sont republiées pendant le postupgrade.
* Correction d&#39;une vulnérabilité XSS potentielle dans le contenu d&#39;une diffusion. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Version de juin du nouveau Panneau de contrôle** avec surveillance des profils actifs, audit de délivrabilité des sous-domaines et gestion des clés GPG. [En savoir plus](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=fr).

### ![](assets/do-not-localize/red_2.png) Version 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_lundi 8 juin 2020_

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Prise en charge des émoticônes</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Lors de la conception d'un message dans Campaign, vous pouvez désormais facilement insérer des émoticônes dans le corps du message, à l'aide d'un bouton dédié. Elles peuvent également être ajoutées à l'objet de l'email. Vous pouvez personnaliser la liste des émoticônes disponibles dans l'interface.</p>
    <p>Pour plus d'informations sur l'ajout d'émoticônes, consultez la <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">documentation détaillée</a>. Découvrez comment personnaliser la liste des émoticônes <a href="../../delivery/using/customizing-emoticon-list.md">dans cette section</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connecteur FDA Azure Synapse</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Vous pouvez désormais connecter votre instance Campaign à la base de données externe Azure Synapse. Cette connexion est gérée à l'aide d'un nouveau compte externe.</p>
    <p>Azure Synapse n'est disponible que pour les environnements hybrides et on-premise. Pour plus d'informations, consultez la <a href="../../installation/using/configure-fda-synapse.md">documentation détaillée</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Loi sur la protection de la vie privée en Thaïlande et au Brésil</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La loi thaïlandaise sur la protection des données personnelles (PDPA) est la nouvelle loi sur la protection de la vie privée destinée à harmoniser et moderniser les exigences en matière de protection des données en Thaïlande. </p>
   <p>Au Brésil, la loi générale sur la protection des données (Lei Geral de Proteção de Dados - LGPD) entrera en vigueur début 2021 pour toutes les entreprises qui collectent ou traitent des données personnelles.</p>
   <p>Ces réglementations s'appliquent aux clients Adobe Campaign qui détiennent des données pour des personnes concernées résidant dans ces pays. Outre les fonctionnalités de confidentialité déjà disponibles dans Campaign (notamment la gestion du consentement, les paramètres de conservation des données et les rôles utilisateur), nous profitons de l'occasion pour inclure d'autres fonctionnalités afin de faciliter votre préparation à la réglementation PDPA et LGPD :</p>
   <ul> 
     <li><p>Droit d'accès et droit de suppression : nous tirons parti des capacités qui ont été ajoutées pour le RGPD et le CCPA. <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html">En savoir plus</a></p></li> 
     <li> <p>Lors de la création d'une demande d'accès à des informations personnelles à l'aide de l'interface Campaign ou d'une API, vous sélectionnez maintenant le type de <strong>règlement</strong> : PDPA, LGPD, RGPD, CCPA. <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">En savoir plus</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* La sécurité améliorée du tracking des liens dans les emails est activée par défaut pour tous les clients. Une autre fonctionnalité de sécurité améliorée est disponible. Il est possible de l&#39;activer en contactant l&#39;Assistance clientèle. Pour plus d&#39;informations sur la fonctionnalité et la procédure d&#39;activation pour les clients non hébergés, consultez la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html). (NEO-24232)

* Pour optimiser la sécurité, l&#39;algorithme de hachage MD5 utilisé pour générer des noms de fichier a été renforcé grâce aux fonctions sha256 pour l&#39;envoi de fichiers publics. (NEO-17044)

* Pour renforcer la sécurité contre les attaques XSS, les scripts client sont désactivés lors de l&#39;exécution d&#39;une page miroir. (NEO-17987)

* Correction d&#39;un problème qui empêchait le workflow technique de **nettoyage des demandes d&#39;accès à des informations personnelles** de supprimer les données de réconciliation. (NEO-25168, NEO-21004)

* Correction d&#39;un problème avec l&#39;activité de **transfert de fichier** qui empêchait le fonctionnement de l&#39;authentification par clé SFTP sur Debian 9. (NEO-23183)

**Améliorations de la compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :
* Systèmes d&#39;exploitation : Debian 10
* SGBDR : Oracle 18c et Oracle 19c
* FDA : Azure Synapse Analytics

En savoir plus sur la [Matrice de compatibilité de Campaign](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html).

**Améliorations**

* La messagerie transactionnelle a été améliorée pour offrir une meilleure expérience utilisateur. Vous pouvez désormais dépublier un modèle de message transactionnel, ce qui le supprime des instances d&#39;exécution. [En savoir plus](../../message-center/using/publishing-message-templates.md#template-unpublication).

* De nouvelles options sont disponibles pour définir des limites lors de l&#39;envoi d&#39;emails contenant des images ou des pièces jointes. Ces mécanismes de sécurisation permettent d&#39;éviter des problèmes de performances, ce qui est particulièrement utile pour les messages transactionnels. [En savoir plus](../../installation/using/configuring-campaign-options.md#delivery)

* La nouvelle option **Préparer les fragments de diffusion dans la base de données** permet d&#39;effectuer la préparation de la diffusion directement dans la base de données, ce qui peut accélérer considérablement l&#39;analyse. Cette option n&#39;est proposée que pour des configurations spécifiques. [En savoir plus](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Les performances de l&#39;[activité Connecteur CRM](../../workflow/using/crm-connector.md) pour Microsoft Dynamics ont été améliorées. (NEO-13303, NEO-12710)

* La version de mémoire partagée a été augmentée.

   >[!WARNING]
   >
   >Cette amélioration nécessite une étape supplémentaire suite à la mise à niveau. Consultez la section **Évolutions techniques** ci-dessous.

* Le workflow de nettoyage a été amélioré. Les tables de travail orphelines de tous les workflows supprimés sont désormais automatiquement supprimées par le workflow de nettoyage. [En savoir plus](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Les certificats des applications mobiles iOS utilisant le connecteur HTTP2 iOS sont maintenant validés avant d&#39;envoyer des notifications push, ce qui empêche les échecs de diffusions en raison du dépassement des dates d&#39;expiration de ces certificats.

* La gestion des connexions au proxy HTTP a été améliorée. [En savoir plus](../../installation/using/file-res-management.md).

* Nouvelle option dans les activités de workflow **[!UICONTROL Code JavaScript]** et **[!UICONTROL Code JavaScript avancé]** pour arrêter l&#39;exécution après une limite. La valeur par défaut est de 1 heure. [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Autres changements**

* Les anciens connecteurs SMS sont désormais obsolètes. Consultez la [page Fonctionnalités obsolètes](../../rn/using/deprecated-features.md).

* Vous ne pouvez plus utiliser votre propre compte Litmus pour configurer et utiliser l’Inbox rendering dans Adobe Campaign. [En savoir plus](../../delivery/using/inbox-rendering.md).

* Pour mieux distinguer les vues et les dossiers, la couleur des noms de vues a été changée du bleu foncé au cyan foncé. [En savoir plus](../../platform/using/access-management-folders.md)

* Il est désormais possible de connecter Campaign Classic à des comptes Microsoft Dynamics CRM hébergés au Royaume-Uni, en Inde et au Canada. Ces conditions s&#39;appliquent aux types de déploiement Office 365 et On premise (Dynamics 2015).

* Campaign effectue désormais une vérification TLS pour contrôler que le nom d&#39;hôte du serveur correspond à celui indiqué dans le certificat fourni.

* Le tableau des statistiques de suivi et des diffusions affiche désormais une entrée par diffusion pour le canal SMS, au lieu d&#39;une entrée par destinataire de diffusion.

* Ajout d&#39;un message d&#39;erreur dans le fichier de log pour avertir les utilisateurs que le fichier téléchargé est plus volumineux que l&#39;espace disque.

* Les fonctions suivantes sont désormais disponibles pour le connecteur Snowflake : MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Évolutions techniques**

Cette nouvelle version met à jour la mémoire partagée et nécessite des étapes supplémentaires pour effectuer la mise à niveau. En tant qu&#39;administrateur de Campaign, vous devez supprimer les segments de mémoire. Ces étapes sont obligatoires, car les anciens segments empêcheront le démarrage de nlserver/nlsrvmod.

Sous Windows, un redémarrage du système est nécessaire.

Sous Debian/CentOs, une suppression de mémoire partagée est nécessaire. La procédure est la suivante :

Avant la mise à niveau, vous devez procéder comme suit :

1. Arrêtez le service apache2 (http2 sur CentOS) s&#39;il est en cours d&#39;exécution.
1. Arrêtez le service nlserver (nlserver6 pour les builds plus anciens) s&#39;il est en cours d&#39;exécution.

Après la mise à niveau :

1. Supprimez la mémoire partagée à l&#39;aide de la commande **ipcrm**, si la version est antérieure à la version actuelle.
1. Démarrez le service nlserver s&#39;il était en cours d&#39;exécution.
1. Démarrez le service apache2 s&#39;il était en cours d&#39;exécution.

Les lignes de commande pour Debian sont les suivantes :

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Un exemple pour Linux est disponible dans cette [page](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Correctifs**

* Correction d&#39;une régression mineure dans les logs du workflow de nettoyage.
* Correction d&#39;un problème dans l&#39;activité de workflow **Chargement (SOAP)** lors de l&#39;analyse des fichiers WSDL.
* Correction d&#39;un problème qui entraînait une erreur lors de la mise à niveau de nombreux workflows à l&#39;aide d&#39;une activité **Questionnaire** pour traiter efficacement un grand nombre de workflows.
* Correction d&#39;un problème de connectivité intermittente lors du traitement des messages inMail à l&#39;aide du MTA amélioré. (NEO-20380)
* Correction d&#39;un problème qui empêchait l&#39;affichage correct des pourcentages de positions des clics lorsque les images s&#39;affichaient avec une largeur de 100 % dans le code HTML. (NEO-23203)
* Correction d&#39;un problème qui empêchait l&#39;affichage complet du contenu conditionnel de la diffusion dans le rapport de positions des clics. (NEO-18729)
* Correction d&#39;un problème en raison duquel l&#39;étape de validation de la cible était ignorée lors de la reprise d&#39;un workflow pour envoyer une diffusion récurrente. (NEO-18166)
* Correction d&#39;un problème en raison duquel le bouton **Relancer la préparation des messages** du message ne reprenait pas la diffusion après correction d&#39;une erreur dans le workflow. (NEO-13488)
* Correction d&#39;un problème en raison duquel les diffusions pouvaient échouer en mode mid-sourcing pendant la phase de progression alors que la cible contenait des destinataires avec des formats d&#39;email japonais. (NEO-23846)
* Correction d&#39;un problème de conversion de fuseau horaire avec le Connecteur Snowflake (NEO-20105).
* Correction d&#39;un problème de comptes externes, lié à l&#39;utilisation de FTP sur SSL. (NEO-20498)
* Correction d&#39;un problème qui empêchait l&#39;affichage des images sur les diffusions LINE. (NEO-23207)
* Correction d&#39;un problème qui entraînait une erreur lors de la publication d&#39;une offre. (NEO-23312)
* Correction d&#39;un problème lié aux notifications push en raison duquel les connexions de test fonctionnaient dans les applications mobiles, même si le certificat avait expiré. (NEO-22991)
* Correction d&#39;un problème qui pouvait avoir un impact sur les notifications push lorsqu&#39;elles étaient envoyées à une fréquence élevée. (NEO-20516)
* Correction d&#39;un problème en raison duquel les données de tracking incluaient des doublons même si les logs de tracking n&#39;en contenaient pas. (NEO-20040)
* Correction d&#39;un problème en raison duquel des doublons d&#39;emails transactionnels étaient envoyés après correction d&#39;un échec de communication du serveur de tracking. (NEO-23640)
* Correction d&#39;un problème en raison duquel la valeur du paramètre de codage était supprimée lors de la redirection à partir d&#39;une URL de tracking (impact sur les caractères japonais). (NEO-25637)
* Correction d&#39;un problème en raison duquel une requête ne fonctionnait pas lors de la comparaison de nombres flottants. (NEO-23243)
* Correction d&#39;un problème en raison duquel le contenu de la colonne **Modification par** ne s&#39;affichait pas après le redémarrage d&#39;un workflow. (NEO-23035)
* Correction d&#39;un problème en raison duquel le workflow technique de tracking échouait lors du téléchargement des logs à partir d&#39;un deuxième conteneur. (NEO-23159)
* Correction d&#39;un problème en raison duquel les workflows échouaient lors de l&#39;exécution d&#39;une activité d&#39;**enrichissement**. (NEO-17338)
* Une vérification a été ajoutée au champ **Doublons à conserver** dans l&#39;activité de workflow **Déduplication** afin d&#39;empêcher la saisie de valeurs &quot;null&quot; ou négatives.
* Suppression de l&#39;**assistant Planificateur** des campagnes récurrentes pour éviter de mentionner les heures et les minutes. Seules les dates sont prises en compte.
* Correction d&#39;un problème lié à d&#39;autres champs d&#39;enregistrement lors de la création de diffusions par le biais de l&#39;option **Calculée par un script** dans l&#39;activité de workflow **Script**. (NEO-20609)
* Correction d&#39;un problème qui empêchait la suppression des workflows fantômes dans les tâches de nettoyage de base de données.
* Correction d&#39;un problème en raison duquel le workflow technique de **Facturation (profils actifs)** échouait. (NEO-19777)
* Correction d’un problème de régression lors de l’utilisation de la fonction ACS Connector qui empêchait la connexion à une instance de Campaign Standard (gestion incorrecte de la connexion FOH/FOH2). (NEO-23433)
* Correction d&#39;un problème qui empêchait la création d&#39;une extension de schéma sur une clé primaire avec plusieurs colonnes et une table Hadoop. (NEO-17390)
* Correction d&#39;un problème dans l&#39;activité **Chargement (SOAP)** qui empêchait le chargement de fichiers WSDL à partir d&#39;une URL. (NEO-16924)
* Correction d&#39;un problème qui empêchait l&#39;exécution d&#39;un **Arrêt inconditionnel** à l&#39;aide de la console lors de l&#39;équilibrage de la charge de plusieurs serveurs de workflows actifs. (NEO-19556)
* Correction d&#39;une régression qui entraînait le blocage du workflow de nettoyage.
* Correction d&#39;un problème qui pouvait se produire lors de la publication d&#39;un modèle sur une instance d&#39;exécution.
* Correction d&#39;un problème qui pouvait empêcher l&#39;exécution du workflow technique de collectPrivacyRequests. (NEO-20513, NEO-25169)
* Correction de problèmes qui pouvaient se produire lors dʼune tentative de connexion à Audience Manager après la mise à niveau vers le build 9080. (NEO-20511, NEO-25167)
* Correction de problèmes qui se produisaient lors de l&#39;export de rapports au format PDF ou XLS. (NEO-20982, NEO-23493, NEO-23348)
* Correction d&#39;un problème en raison duquel une diffusion pouvait s&#39;afficher deux fois dans la liste de diffusion après son envoi.
* Correction d&#39;un problème de préparation de diffusion qui pouvait se produire lorsque la configuration de routage était définie pour envoyer la diffusion par mid-sourcing.
* Correction d&#39;un problème en raison duquel un message d&#39;erreur pouvait s&#39;afficher en cas de clic sur un lien d&#39;application web dans un message LINE.
* Correction d&#39;un problème en raison duquel l&#39;historique de l&#39;activité **Requête incrémentale** était supprimé suite à l&#39;exécution du workflow de nettoyage.
* Correction d&#39;un problème lors de la création d&#39;un compte externe de mid-sourcing en raison de l&#39;absence de l&#39;option NmsMidSourcing_LastBroadLog_&lt;InternalName>.
* Correction d&#39;un problème de régression concernant la connexion à la base de données qui provoquait le redémarrage constant du serveur web en raison d&#39;un problème de codage de base de données. Ce problème pouvait conduire à une surconsommation. (NEO-23264)


## Version 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Version 20.1.4 - Build 9126 {#release-20-1-4-build-9126}

_15 avril 2021_

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

_23 décembre 2020_

>[!CAUTION]
>
> * Cette version s’accompagne d’un nouveau protocole de connexion : si vous vous connectez à Campaign via le Service d&#39;identités Adobe (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console cliente puissent se connecter après le **30 juin 2021**. [En savoir plus](../../technotes/using/ims-updates.md)
>
> * Cette version s&#39;accompagne d&#39;un [correctif de sécurité](https://helpx.adobe.com/fr/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.


* Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme dʼauthentification IMS.
* Correction d&#39;un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Version 20.1.3 - Build 9124{#release-20-1-3-build-9124}

_mercredi 6 mai 2020_

* Correction d’un problème avec l’activité de **transfert de fichier** qui empêchait le fonctionnement de l’authentification par clé SFTP sur Debian 9. (NEO-23183)

### ![](assets/do-not-localize/red_2.png) Version 20.1.2 - Build 9123{#release-20-1-2-build-9123}

_13 mars 2020_

* Correction d’une erreur qui empêchait le déploiement de la version sur les serveurs Red Hat 7. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Version 20.1 - Build 9122{#release-20-1-build-9122}

_17 février 2020_

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connecteur Snowflake FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake est un entrepôt de données dans le cloud entièrement géré, conçu pour être évolutif en termes de stockage et de puissance de calcul. Grâce à ce nouveau connecteur, Adobe Campaign peut maintenant exploiter la puissance de Snowflake pour segmenter les mégadonnées (Big Data). Ce connecteur est disponible pour tous les clients, notamment les clients hébergés par Adobe.</p>
    <p>Pour plus d’informations, consultez la <a href="../../installation/using/configure-fda-snowflake.md">documentation détaillée</a> et regardez le <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html?lang=fr">tutoriel vidéo</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Améliorations apportées au connecteur Hadoop FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Le connecteur Hadoop FDA a été amélioré pour prendre en charge Hadoop 3.0 ainsi que Cloudera.</p>
    <p>Pour plus d’informations, consultez la <a href="../../installation/using/configure-fda-hadoop.md">documentation détaillée</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* Amélioration de la sécurité de la configuration des rapports pour protéger les utilisateurs contre le détournement de clic (clickjacking). Cette amélioration s’applique aux nouveaux rapports. Pour les anciens rapports, vous devez les republier pour appliquer les modifications. (NEO-13282)

* Correction d’un petit problème de mémoire dans cryptString. (NEO-20071)

* Amélioration de la fonction monitor JSP pour corriger une divulgation de propriété intellectuelle interne. (NEO-16821)

* Correction d’un problème en raison duquel les informations de traçage de pile pouvaient être affichées pour des utilisateurs non administrateurs. (NEO-12388)

* Amélioration de la gestion des données mises en cache des sessions précédentes. (NEO-17039)

* Correction d’un problème qui empêchait le fichier logins.log d’enregistrer les tentatives de connexion réussies via IMS. (NEO-11004)

**Améliorations**

* iOS 13 est maintenant pris en charge avec le connecteur HTTP2.

* Amélioration de la gestion des quarantaines et du nettoyage des tables utilisées par la fonction de notification push (nms:address et nms:appSubscriptionRcp). Pour iOS (connecteur HTTP2 uniquement), les jetons désactivés sont maintenant gérés de la même manière que pour Android. Le drapeau disable est maintenant défini dans la table NmsAppSubscriptionRcp. [En savoir plus](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Une nouvelle option a été ajoutée dans les activités de workflow **Code JavaScript** et **Code JavaScript avancé** pour définir un délai d’expiration. Cela permet dʼéviter une phase dʼexécution JavaScript trop longue. Une fois le délai d’expiration écoulé, le workflow est arrêté. Le délai d’expiration par défaut est d’une heure. [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md)

* L’analyse de diffusion est désormais arrêtée lorsqu’aucune affinité correspondante n’a été trouvée sur le serveur de mid-sourcing. Le message d’erreur associé est ensuite affiché.

* Le basculement de base de données pour Postgres est maintenant pris en charge : lorsque le serveur de base de données se bloque et redémarre, Campaign se reconnecte désormais automatiquement.

* La vue **Démarrage en attente** a été ajoutée au nœud Administration > Suivi > Statut des workflows. Il est ainsi possible de surveiller tous les workflows de votre instance qui attendent d’être démarrés par le processus **operationMgt**. Cette vue est proposée avec le package des campagnes marketing. [En savoir plus](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Autres changements**

* Sous Linux, le démarrage du service nlserver utilise maintenant une unité systemd au lieu du script /etc/init.d/nlserver6. La migration vers le nouveau schéma de démarrage est effectuée automatiquement lors de l’installation du package 20.1. Le serveur /etc/init.d/nlserver6 est encore fourni, mais pour interagir avec le service nlserver (démarrage, redémarrage, arrêt, etc.), nous vous recommandons d’utiliser directement la commande systemctl.

* Les tables personnalisées les plus consommatrices de données ont été déplacées de la séquence **xtkNewId** vers des séquences dédiées.

* Amélioration des performances des requêtes, qui pourraient être affectées par des connexions inutiles à la base de données.

* Amélioration des performances de l&#39;assistant de mise à jour de la base de données afin de réduire le nombre d&#39;instructions SQL dans le but d&#39;optimiser le temps de réponse.

* La gestion des enregistrements de la base de données a été améliorée.

* La robustesse du pool de connexions a été améliorée, ce qui peut empêcher des échecs de connexion inattendus trop fréquents.

* Les règles de validation des adresses email pour envoyer une adresse en quarantaine en cas d’erreur soft ont été améliorées. [En savoir plus](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Pour Debian, Campaign utilise maintenant les bibliothèques PCRE système lorsqu’elles sont disponibles.

* Campaign permet désormais d’utiliser une bibliothèque système ODBC plus récente.

* Un délai d’expiration a été ajouté à la servlet LINE lors de l’ouverture d’une connexion pour charger une image enrichie. Si le chargement de l’image prend trop de temps, la servlet arrête la connexion pour éviter un goulot d’étranglement.

**Correctifs**

* Correction d’un problème de chiffrement des clés de compte lors de l’utilisation du connecteur Hadoop.

* Correction d’un problème de régression lié à l’implémentation de la certification SSL, en raison duquel la connexion de l’utilisateur échouait sur Windows Server. (NEO-20629)

* Correction d’un problème lié à l’activité de requête incrémentale en cas d’ID de workflow négatifs. (NEO-19779)

* Correction d’un problème de codage lors de l’exécution de requêtes via le connecteur Netezza FDA. (NEO-19594)

* Correction d’un problème qui entraînait une erreur lors de l’utilisation de la méthode POST dans l’activité d’événement de workflow **Téléchargement Web**.

* Correction d’un problème lié à la génération de propositions d’offres. (NEO-18176)

* Correction d’un problème d’affichage du pied de page lors de l’utilisation du modèle de formulaire web d’acquisition.

* Correction d’un problème lors de l’analyse des URL dans le contenu des diffusions au fil de l’eau, qui pouvait entraîner un blocage. (NEO-16910)

* Correction d’un problème en raison duquel les champs **Début** et **Fin** n’étaient pas calculés lors de la création d’une campagne.

* Correction d’un problème lié à l’activité de workflow **Réception de fichier** lors de l’utilisation d’une adresse URL.

* Correction d’un problème lors de la prévisualisation d’une liste importée dans une activité de rapport. (NEO-13119)

* Correction d’un problème qui provoquait l’affichage d’une image obsolète lors de la sélection du bloc de personnalisation **Powered by Campaign** dans l’éditeur d’email.

* La communication réseau entre le client et le serveur a été améliorée.

* Correction d’un problème résultant de la création d’un trop grand nombre de workflows dans la même campagne. Vous ne pouvez maintenant pas en créer plus de 28. Un avertissement s’affiche.

* Correction d’un problème lors de l’utilisation de l’option de réconciliation **Une sélection de colonnes** dans une activité de workflow **Union**.

* Correction d’un problème de blocage de la console qui se produisait lors de l’utilisation d’une liste d’enrichissement endommagée dans un workflow. (NEO-18096)

* Correction de différents problèmes de blocage de la console qui se produisaient dans les workflows (NEO-18010, NEO-18032)

* Correction d’un problème qui autorisait l’exécution d’une activité de workflow **Signal externe** même lorsqu’elle était désactivée. (NEO-17524)

* Correction d’un problème lors de la création d’un nouveau schéma.

* Correction d’un problème de tracking lors de l’envoi de messages SMS. (NEO-19595)

* Correction d’un problème qui affichait un nombre incorrect d’audiences ciblées dans les indicateurs de diffusion.

* Correction d’un problème qui affichait des pourcentages incorrects lors de la génération d’un rapport descriptif via une activité de workflow. (NEO-14314)

* Correction d’un problème en raison duquel le rapport de débit des diffusions affichait des nombres différents selon le paramètre d’affichage de l’heure. (NEO-11783)

* Correction d’un problème qui empêchait la mise à jour des indicateurs de tracking des messages transactionnels par le workflow de tracking. (NEO-17770)

* Correction d’un problème de régression en raison duquel le processus web se bloquait et redémarrait lors de la demande d’une offre via SOAP. (NEO-19482)

* Correction d’un problème qui empêchait le chargement des données vers des ressources publiques si le répertoire de chargement était un emplacement partagé distant. (NEO-19361)

* Correction d’un problème en raison duquel le workflow technique **Import d’audiences depuis Adobe Experience Cloud** échouait constamment. (NEO-18463)

* Correction d’un problème qui empêchait l’envoi des diffusions lors de l’utilisation de modèles importés à partir d’Experience Manager. (NEO-17540)

* Correction d’un problème qui se produisait après un upgrade vers le build 9032 et qui empêchait l’instance de se connecter au serveur FTP à l’aide du protocole SSL. (NEO-20498)

* Correction d’un problème qui se produisait lors de la suppression, de l’insertion ou de la mise à jour d’une grande quantité de données avec l’activité de **mise à jour des données** dans un workflow à l’aide d’un schéma FDA servant de dimension de ciblage. (NEO-13280)

* Correction d&#39;un problème qui empêchait l&#39;envoi d&#39;emails lorsque du code JavaScript se trouvait en dehors de la balise de contenu HTML. (NEO-18628)

* Correction d’un problème qui se produisait lors de l’affichage de la page miroir depuis les logs de diffusion d’un message envoyé. (NEO-17976)

* Correction d’un problème qui empêchait l’affichage du bloc de personnalisation **Lien vers la page miroir** de l’onglet **Contenu texte** après avoir cliqué sur **Importer le HTML** dans une diffusion. (NEO-17568)

* Clarification du message d’erreur affiché après un clic sur un lien vers une page miroir ayant dépassé le délai d’expiration. (NEO-17340)

* Correction d’un problème qui empêchait l’utilisation de certains boutons dans l’écran de création de **répartition des données**.

* Correction d’un problème qui se produisait lors de la planification d’une activité de diffusion dans une instance dont le fuseau horaire était Asie/Calcutta. (NEO-20001)

* Une erreur s’affiche maintenant lorsqu’une diffusion rencontre un problème de configuration de l’affinité.

* Correction d’un problème qui affichait un numéro de balise de version incorrect dans le menu **À propos**.

* Correction d’un problème qui se produisait lors d’une tentative de mise à jour du compte de routage à partir des propriétés de diffusion récurrente dans un workflow. (NEO-18684)

* Correction d’un problème qui se produisait lors de la connexion à l’instance via le module de redirection. Celui-ci empêchait le nettoyage correct de la connexion une fois fermée.

---
product: campaign
title: Version 20.2
description: Version 20.2
feature: Vue d’ensemble
role: Business Practitioner
level: Beginner
exl-id: fcaab1aa-c8f9-4606-b0d8-eb481a38f588
source-git-commit: c0a3d9217696f5f5622a6af8f64c62b1a9fbce20
workflow-type: tm+mt
source-wordcount: '2977'
ht-degree: 100%

---

# Version 20.2{#release-20-2}

## ![](assets/do-not-localize/green_2.png) Version 20.2.5 - Build 9188 {#release-20-2-5-build-9188}

__

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n’est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_31 mars 2021_

**Améliorations**

* Une amélioration a été apportée pour empêcher les blocages sur les appels SOAP non valides. Cette situation pouvait entraîner l’arrêt du fonctionnement de l’instance lors de l’exécution de requêtes complexes spécifiques. (NEO-28796, NEO-30553)
* Correction d’une régression qui empêchait l’envoi de diffusions SMS avec TLS en raison de la vérification du nom d’hôte. (NEO-29581)
* Correction d’un problème en raison duquel les liens de tracking signés ne fonctionnaient pas sur certains clients de messagerie. (NEO-28414, NEO-29615)
* Correction d’une séquence d’ID de tracking lors de l’utilisation de balises de tracking webApp qui provoquait des conflits avec les ID dupliqués. (NEO-27931)
* Correction d’un problème en raison duquel les workflows en cours d’exécution étaient arrêtés par le redémarrage quotidien du serveur wfserver. (NEO-30047)
* Correction d’un problème de sécurité lors de l’utilisation des appels d’API effectués par des utilisateurs non-administrateurs lors de la synchronisation de modèles Adobe Experience Manager. (NEO-32389, NEO-23487)
* Correction d’un problème en raison duquel la console se bloquait lors de la fermeture d’une boîte de dialogue sur une diffusion créée à partir d’un modèle. (NEO-31547)
* Correction d’un problème qui se produisait lors de la création et de l’enregistrement d’une diffusion dans l’onglet **Ciblage et workflow** d’une campagne : la prévisualisation échouait avec l’erreur suivante.(NEO-29440)
* Correction d’un problème en raison duquel Tomcat 8.5 envoyait des réponses non valides, ce qui provoquait des erreurs dans les logs de messagerie transactionnelle. (NEO-30858)
* Correction d’un problème de régression qui entraînait une corruption de la mémoire dans la gestion des threads externes et avait un impact sur les performances.
* Correction d’un problème en raison duquel le workflow de facturation échouait lors de l’utilisation d’un mapping de ciblage personnalisé. La clé principale du schéma personnalisé est stockée dans la colonne &#39;sourceId&#39; qui n’autorisait que des entiers. Elle autorise désormais des entiers ainsi que des valeurs de chaîne. (NEO-25914, NEO-28146)
* Correction d’une régression qui empêchait l’utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453)

## ![](assets/do-not-localize/red_2.png) Version 20.2.4 - Build 9187 {#release-20-2-4-build-9187}

_15 avril 2021_

* Correction d&#39;une régression de la console cliente qui provoquait des messages d&#39;erreur persistants sur l&#39;écran de connexion IMS. (NEO-34821)
* Correction d’une régression qui empêchait l’utilisation de certains composants de la console, tels que le sélecteur de date et la gestion des images dans les diffusions. (NEO-31453, NEO-31454)

**La mise à niveau de la console uniquement est obligatoire. Aucune mise à niveau du serveur n’est requise.**

>[!NOTE]
>
> Connectez-vous à la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) pour télécharger la nouvelle version. Découvrez comment proposer la mise à jour de la console à tous les utilisateurs finaux [sur cette page](../../installation/using/client-console-availability-for-windows.md).

_22 décembre 2020_

>[!CAUTION]
>
> * Cette version s’accompagne d’un nouveau protocole de connexion : si vous vous connectez à Campaign via Adobe Identity Service (IMS), une mise à niveau est obligatoire pour que le serveur Campaign et la console client puissent se connecter après le **30 juin 2021**.  [En savoir plus](../../technotes/ims-updates.md)
> * Cette version s’accompagne d’un [correctif de sécurité](https://helpx.adobe.com/security/products/campaign/apsb21-04.html) : la mise à niveau est obligatoire pour renforcer la sécurité de votre environnement.
> * Si vous utilisez l’intégration Experience Cloud Triggers par le biais de l’authentification oAuth, vous devez passer à Adobe I/O comme décrit [sur cette page](../../integrations/using/configuring-adobe-io.md). Le mode d’authentification oAuth hérité avec Campaign sera mis hors service le **30 novembre 2021**.


**Améliorations**

* Le protocole de connexion a été mis à jour pour suivre le nouveau mécanisme d&#39;authentification IMS.
* L’authentification de l’intégration des Triggers basée à l&#39;origine sur la configuration de l&#39;authentification oAUTH pour accéder au pipeline a été modifiée et déplacée vers Adobe I/O. [En savoir plus](../../integrations/using/configuring-adobe-io.md)
* Après la [fin de la prise en charge du protocole binaire hérité des APN iOS](https://developer.apple.com/news/?id=c88acm2b), toutes les instances utilisant ce protocole sont mises à jour vers le protocole HTTP/2 durant la mise à niveau.
* Correction d’un problème de sécurité afin de renforcer la protection contre les problèmes SSRF (Server Side Request Forgery). (NEO-27777)
* Correction d&#39;un problème en raison duquel le connecteur SMPP était désactivé après une erreur de connexion, ce qui empêchait l&#39;envoi d&#39;autres diffusions SMS et provoquait des problèmes de performances. (NEO-28609)
* Correction d’un problème de blocage du serveur en empêchant la corruption de la mémoire lors du nettoyage de l’analyseur d’expressions. (NEO-26856)
* Correction d’un problème en raison duquel le serveur se bloquait lors de l’affichage des données de la cible à partir d’une activité **Partage** dans un workflow.
* Correction d’un problème en raison duquel un message d’erreur s’affichait lors de la tentative de prévisualisation de messages SMS après une requête sur un autre schéma que **Destinataire** (nms:destinataire). (NEO-27517)
* Correction d&#39;un problème en raison duquel lors de l&#39;exécution d&#39;une demande de connexion HTTPS avec le numéro de port explicitement défini dans le nom d&#39;hôte, l&#39;appel échouait avec une erreur de certificat. (NEO-29146)
* Correction d&#39;un problème dans la gestion des threads POSIX qui générait des fichiers de vidage principaux volumineux sur l&#39;instance marketing. (NEO-28117, NEO-29281)
* Correction de problèmes susceptibles de provoquer un blocage du processus web lors de la préparation de diffusions ou avec une prévisualisation de diffusion récurrente. (NEO-27790, NEO-27517)
* Correction d&#39;un problème en raison duquel l&#39;envoi de diffusions ou de BAT échouait lorsqu&#39;il était déclenché par un opérateur non administrateur. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **Nouvelle version d&#39;octobre du panneau de contrôle** avec configuration de domaine utilisant des CNAME et nouvelles fonctionnalités de surveillance de base de données. [En savoir plus](https://docs.adobe.com/content/help/fr-FR/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/red_2.png) Version 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_11 septembre 2020_

* Correction d’une régression qui entraînait le blocage de la préparation des diffusions en raison d’une seule fonction erronée sur le fragment de diffusion, et conduisait à une surcharge de la mémoire. (NEO-27346)
* Correction d’un problème de postupgrade qui désactivait Apache et le serveur Web avant la republication de l’application web. (NEO-27155)
* Correction d’une régression relative à la gestion des modèles HTML, en raison duquel les URL de tracking devenaient visibles du fait d&#39;une mauvaise interprétation des onglets. (NEO-25909)
* Correction d’un problème lié au workflow de nettoyage de la base de données qui pouvait échouer en raison d’une source de données non gérée. (NEO-23160, NEO-23364)
* Le workflow de nettoyage purge désormais les listes expirées par lots de 100 plutôt qu&#39;une par une.
* Correction d’une régression qui empêchait de modifier le nom interne d’un compte externe. (NEO-27323)
* Correction d’une régression au cours d’un postupgrade qui provoquait un démarrage incorrect de nlserver (logs d’erreur).
* La gestion des mises à jour pour la mémoire partagée a été améliorée. Les étapes supplémentaires requises dans la version 20.2 ne sont plus nécessaires.

## ![](assets/do-not-localize/red_2.png) Version 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_22 juillet 2020_

* Correction d’un problème qui empêchait le tracking de fonctionner lorsque la fonction de signature était désactivée. (NEO-26411)
* Correction d’un problème en raison duquel les liens non signés provenant de domaines personnalisés étaient bloqués au lieu d’être autorisés. (NEO-25210)
* Correction d’un problème qui empêchait d’ouvrir/de cliquer sur les URL de tracking lors de l’utilisation de certaines anciennes versions d’Outlook. (NEO-25688)
* Correction d’un problème en raison duquel les URL de page miroir étaient incorrectement définies dans les diffusions par email (en raison d’un contrôle incorrect des caractères ASCII). (NEO-26084)
* Correction d’un problème lié à gestion des URL de codage dans le service anti-hameçonnage. (NEO-25283)
* Correction d’un problème qui empêchait le suivi des URL à l’aide de fragments dans les paramètres de personnalisation (balises d’ancrage avec signe dièse) de fonctionner. (NEO-25774)
* Correction d’un problème de suivi lors de l’utilisation de formules de tracking personnalisées spécifiques. (NEO-25277)

* Correction d’un problème qui empêchait le suivi des « clics de notification » de fonctionner (notifications push iOS et Android). (NEO-25965)
* Correction d’une régression qui affectait les champs calculés d’un workflow et provoquait l’échec de ce workflow. (NEO-25194)
* Correction d’une régression qui empêchait le fonctionnement de la création à la volée d’URL de tracking web. (NEO-20999)
* Correction d’un problème de régression lié aux rapports de diffusion d’usine qui s’affichaient tronqués lors de l’export au format PDF. (NEO-25757)
* Correction d’un problème de blocage dans l’assistant de déploiement.
* Correction d’un problème qui empêchait le fonctionnement correct du workflow Notification des offres après un postupgrade.
* Le connecteur HTTP2 iOS a été amélioré (mises à jour tierces et gestion des erreurs). (NEO-25904, NEO-25903)
* La liste jarsToSkip de catalina.properties a été mise à jour afin de supprimer la référence à un fichier jar qui n’était plus utilisé (notifications iOS).
* Correction d’un problème qui bloquait la préparation des diffusions après un postupgrade.
* Après le passage au [nouveau mécanisme d’identifiant de séquence](https://helpx.adobe.com/fr/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), toutes les applications web qui mettent à jour la table des destinataires sont republiées pendant le postupgrade.
* Correction d’une vulnérabilité XSS potentielle dans le contenu d’une diffusion. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Nouvelle version de juin du panneau de contrôle** avec surveillance des profils actifs, audit de délivrabilité des sous-domaines et gestion des clés GPG. [En savoir plus](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/red_2.png) Version 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

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
   <td> <p>Lors de la conception d’un message dans Campaign, vous pouvez désormais facilement insérer des émoticônes dans le corps du message, à l’aide d’un bouton dédié. Elles peuvent également être ajoutées à l’objet de l’email. Vous pouvez personnaliser la liste des émoticônes disponibles dans l’interface.</p>
    <p>Pour plus d’informations sur l’ajout d’émoticônes, consultez la <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">documentation détaillée</a>. Découvrez comment personnaliser la liste des émoticônes <a href="../../delivery/using/customizing-emoticon-list.md">dans cette section</a>.</p>
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
   <td> <p>Vous pouvez désormais connecter votre instance Campaign à la base de données externe Azure Synapse. Cette connexion est gérée à l’aide d’un nouveau compte externe.</p>
    <p>Azure Synapse n’est disponible que pour les environnements hybrides et on-premise. Pour plus d’informations, consultez la <a href="../../installation/using/configure-fda-synapse.md">documentation détaillée</a>.</p>
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
   <p>Ces réglementations s’appliquent aux clients Adobe Campaign qui détiennent des données pour des personnes concernées résidant dans ces pays. Outre les fonctionnalités de confidentialité déjà disponibles dans Campaign (notamment la gestion du consentement, les paramètres de conservation des données et les rôles utilisateur), nous profitons de l’occasion pour inclure d’autres fonctionnalités afin de faciliter votre préparation à la réglementation PDPA et LGPD :</p>
   <ul> 
     <li><p>Droit d'accès et droit de suppression : nous tirons parti des capacités qui ont été ajoutées pour le RGPD et le CCPA. <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html">En savoir plus</a></p></li> 
     <li> <p>Lors de la création d’une demande d’accès à des informations personnelles à l’aide de l’interface Campaign ou d’une API, vous sélectionnez maintenant le type de <strong>règlement</strong> : PDPA, LGPD, RGPD, CCPA. <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">En savoir plus</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* La sécurité améliorée du tracking des liens dans les emails est activée par défaut pour tous les clients. Une autre fonctionnalité de sécurité améliorée est disponible. Il est possible de l’activer en contactant l&#39;Assistance clientèle. Pour plus d’informations sur la fonctionnalité et la procédure d’activation pour les clients non hébergés, consultez la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html). (NEO-24232)

* Pour optimiser la sécurité, l’algorithme de hachage MD5 utilisé pour générer des noms de fichier a été renforcé grâce aux fonctions sha256 pour l’envoi de fichiers publics. (NEO-17044)

* Pour renforcer la sécurité contre les attaques XSS, les scripts client sont désactivés lors de l’exécution d’une page miroir. (NEO-17987)

* Correction d’un problème qui empêchait le workflow technique de **nettoyage des demandes d’accès à des informations personnelles** de supprimer les données de réconciliation. (NEO-25168, NEO-21004)

* Correction d’un problème avec l’activité de **transfert de fichier** qui empêchait le fonctionnement de l’authentification par clé SFTP sur Debian 9. (NEO-23183)

**Améliorations de la compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :
* Systèmes d’exploitation : Debian 10
* SGBDR : Oracle 18c et Oracle 19c
* FDA : Azure Synapse Analytics

En savoir plus sur la [Matrice de compatibilité de Campaign](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html).

**Améliorations**

* La messagerie transactionnelle a été améliorée pour offrir une meilleure expérience utilisateur. Vous pouvez désormais dépublier un modèle de message transactionnel, ce qui le supprime des instances d’exécution. [En savoir plus](../../message-center/using/publishing-message-templates.md#template-unpublication).

* De nouvelles options sont disponibles pour définir des limites lors de l’envoi d’emails contenant des images ou des pièces jointes. Ces garde-fous permettent d’éviter des problèmes de performances, ce qui est particulièrement utile pour les messages transactionnels. [En savoir plus](../../installation/using/configuring-campaign-options.md#delivery)

* La nouvelle option **Préparer les fragments de diffusion dans la base de données** permet d’effectuer la préparation de la diffusion directement dans la base de données, ce qui peut accélérer considérablement l’analyse. Cette option n’est proposée que pour des configurations spécifiques. [En savoir plus](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Les performances de l’[activité Connecteur CRM](../../workflow/using/crm-connector.md) pour Microsoft Dynamics ont été améliorées. (NEO-13303, NEO-12710)

* La version de mémoire partagée a été augmentée.

   >[!WARNING]
   >
   >Cette amélioration nécessite une étape supplémentaire suite à la mise à niveau. Consultez la section **Évolutions techniques** ci-dessous.

* Le workflow de nettoyage a été amélioré. Les tables de travail orphelines de tous les workflows supprimés sont désormais automatiquement supprimées par le workflow de nettoyage. [En savoir plus](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Les certificats des applications mobiles iOS utilisant le connecteur HTTP2 iOS sont maintenant validés avant d’envoyer des notifications push, ce qui empêche les échecs de diffusions en raison du dépassement des dates d’expiration de ces certificats.

* La gestion des connexions au proxy HTTP a été améliorée. [En savoir plus](../../installation/using/file-res-management.md).

* Nouvelle option dans les activités de workflow **[!UICONTROL Code JavaScript]** et **[!UICONTROL Code JavaScript avancé]** pour arrêter l’exécution après une limite. La valeur par défaut est de 1 heure. [En savoir plus](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Autres changements**

* Les anciens connecteurs SMS sont désormais obsolètes. Consultez la [page Fonctionnalités obsolètes](../../rn/using/deprecated-features.md).

* Vous ne pouvez plus utiliser votre propre compte Litmus pour configurer et utiliser l’Inbox rendering dans Adobe Campaign. [En savoir plus](../../delivery/using/inbox-rendering.md).

* Pour mieux distinguer les vues et les dossiers, la couleur des noms de vues a été changée du bleu foncé au cyan foncé. [En savoir plus](../../platform/using/access-management-folders.md)

* Il est désormais possible de connecter Campaign Classic à des comptes Microsoft Dynamics CRM hébergés au Royaume-Uni, en Inde et au Canada. Ces conditions s’appliquent aux types de déploiement Office 365 et On premise (Dynamics 2015).

* Campaign effectue désormais une vérification TLS pour contrôler que le nom d’hôte du serveur correspond à celui indiqué dans le certificat fourni.

* Le tableau des statistiques de suivi et des diffusions affiche désormais une entrée par diffusion pour le canal SMS, au lieu d’une entrée par destinataire de diffusion.

* Ajout d’un message d’erreur dans le fichier de log pour avertir les utilisateurs que le fichier téléchargé est plus volumineux que l’espace disque.

* Les fonctions suivantes sont désormais disponibles pour le connecteur Snowflake : MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Évolutions techniques**

Cette nouvelle version met à jour la mémoire partagée et nécessite des étapes supplémentaires pour effectuer la mise à niveau. En tant qu’administrateur de Campaign, vous devez supprimer les segments de mémoire. Ces étapes sont obligatoires, car les anciens segments empêcheront le démarrage de nlserver/nlsrvmod.

Sous Windows, un redémarrage du système est nécessaire.

Sous Debian/CentOs, une suppression de mémoire partagée est nécessaire. La procédure est la suivante :

Avant la mise à niveau, vous devez procéder comme suit :

1. Arrêtez le service apache2 (http2 sur CentOS) s’il est en cours d’exécution.
1. Arrêtez le service nlserver (nlserver6 pour les builds plus anciens) s’il est en cours d’exécution.

Après la mise à niveau :

1. Supprimez la mémoire partagée à l’aide de la commande **ipcrm**, si la version est antérieure à la version actuelle.
1. Démarrez le service nlserver s’il était en cours d’exécution.
1. Démarrez le service apache2 s’il était en cours d’exécution.

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

* Correction d’une régression mineure dans les logs du workflow de nettoyage.
* Correction d’un problème dans l’activité de workflow **Chargement (SOAP)** lors de l’analyse des fichiers WSDL.
* Correction d’un problème qui entraînait une erreur lors de la mise à niveau de nombreux workflows à l’aide d’une activité **Questionnaire** pour traiter efficacement un grand nombre de workflows.
* Correction d’un problème de connectivité intermittente lors du traitement des messages inMail à l’aide du MTA amélioré. (NEO-20380)
* Correction d’un problème qui empêchait l’affichage correct des pourcentages de positions des clics lorsque les images s’affichaient avec une largeur de 100 % dans le code HTML. (NEO-23203)
* Correction d’un problème qui empêchait l’affichage complet du contenu conditionnel de la diffusion dans le rapport de positions des clics. (NEO-18729)
* Correction d’un problème en raison duquel l’étape de validation de la cible était ignorée lors de la reprise d’un workflow pour envoyer une diffusion récurrente. (NEO-18166)
* Correction d’un problème en raison duquel le bouton **Relancer la préparation des messages** du message ne reprenait pas la diffusion après correction d’une erreur dans le workflow. (NEO-13488)
* Correction d’un problème en raison duquel les diffusions pouvaient échouer en mode mid-sourcing pendant la phase de progression alors que la cible contenait des destinataires avec des formats d’email japonais. (NEO-23846)
* Correction d’un problème de conversion de fuseau horaire avec le Connecteur Snowflake (NEO-20105).
* Correction d’un problème de comptes externes, lié à l’utilisation de FTP sur SSL. (NEO-20498)
* Correction d’un problème qui empêchait l’affichage des images sur les diffusions LINE. (NEO-23207)
* Correction d’un problème qui entraînait une erreur lors de la publication d’une offre. (NEO-23312)
* Correction d’un problème lié aux notifications push en raison duquel les connexions de test fonctionnaient dans les applications mobiles, même si le certificat avait expiré. (NEO-22991)
* Correction d’un problème qui pouvait avoir un impact sur les notifications push lorsqu’elles étaient envoyées à une fréquence élevée. (NEO-20516)
* Correction d’un problème en raison duquel les données de tracking incluaient des doublons même si les logs de tracking n’en contenaient pas. (NEO-20040)
* Correction d’un problème en raison duquel des doublons d’emails transactionnels étaient envoyés après correction d’un échec de communication du serveur de tracking. (NEO-23640)
* Correction d’un problème en raison duquel la valeur du paramètre de codage était supprimée lors de la redirection à partir d’une URL de tracking (impact sur les caractères japonais). (NEO-25637)
* Correction d’un problème en raison duquel une requête ne fonctionnait pas lors de la comparaison de nombres flottants. (NEO-23243)
* Correction d’un problème en raison duquel le contenu de la colonne **Modification par** ne s’affichait pas après le redémarrage d’un workflow. (NEO-23035)
* Correction d’un problème en raison duquel le workflow technique de tracking échouait lors du téléchargement des logs à partir d’un deuxième conteneur. (NEO-23159)
* Correction d’un problème en raison duquel les workflows échouaient lors de l’exécution d’une activité d’**enrichissement**. (NEO-17338)
* Une vérification a été ajoutée au champ **Doublons à conserver** dans l’activité de workflow **Déduplication** afin d’empêcher la saisie de valeurs &quot;null&quot; ou négatives.
* Suppression de l’**assistant Planificateur** des campagnes récurrentes pour éviter de mentionner les heures et les minutes. Seules les dates sont prises en compte.
* Correction d’un problème lié à d’autres champs d’enregistrement lors de la création de diffusions par le biais de l’option **Calculée par un script** dans l’activité de workflow **Script**. (NEO-20609)
* Correction d’un problème qui empêchait la suppression des workflows fantômes dans les tâches de nettoyage de base de données.
* Correction d’un problème en raison duquel le workflow technique de **Facturation (profils actifs)** échouait. (NEO-19777)
* Correction d’un problème de régression lors de l’utilisation de la fonction ACS Connector qui empêchait la connexion à une instance de Campaign Standard (gestion incorrecte de la connexion FOH/FOH2). (NEO-23433)
* Correction d’un problème qui empêchait la création d’une extension de schéma sur une clé primaire avec plusieurs colonnes et une table Hadoop. (NEO-17390)
* Correction d’un problème dans l’activité **Chargement (SOAP)** qui empêchait le chargement de fichiers WSDL à partir d’une URL. (NEO-16924)
* Correction d’un problème qui empêchait l’exécution d’un **Arrêt inconditionnel** à l’aide de la console lors de l’équilibrage de la charge de plusieurs serveurs de workflows actifs. (NEO-19556)
* Correction d’une régression qui entraînait le blocage du workflow de nettoyage.
* Correction d’un problème qui pouvait se produire lors de la publication d’un modèle sur une instance d’exécution.
* Correction d’un problème qui pouvait empêcher l’exécution du workflow technique de collectPrivacyRequests. (NEO-20513, NEO-25169)
* Correction de problèmes qui se produisaient lors d’une tentative de connexion à Audience Manager après la mise à niveau vers le build 9080. (NEO-20511, NEO-25167)
* Correction de problèmes qui se produisaient lors de l’export de rapports au format PDF ou XLS. (NEO-20982, NEO-23493, NEO-23348)
* Correction d’un problème en raison duquel une diffusion pouvait s’afficher deux fois dans la liste de diffusion après son envoi.
* Correction d’un problème de préparation de diffusion qui pouvait se produire lorsque la configuration de routage était définie pour envoyer la diffusion par mid-sourcing.
* Correction d’un problème en raison duquel un message d’erreur pouvait s’afficher en cas de clic sur un lien d’application web dans un message LINE.
* Correction d’un problème en raison duquel l’historique de l’activité **Requête incrémentale** était supprimé suite à l’exécution du workflow de nettoyage.
* Correction d’un problème lors de la création d’un compte externe de mid-sourcing en raison de l’absence de l’option NmsMidSourcing_LastBroadLog_&lt;InternalName>.
* Correction d’un problème de régression concernant la connexion à la base de données qui provoquait le redémarrage constant du serveur web en raison d’un problème de codage de base de données. Ce problème pouvait conduire à une surconsommation. (NEO-23264)

---
title: Dernière version
description: Dernière version
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
source-git-commit: f92180f93850d5bc33e74210d17cdd36c0c15e5f
workflow-type: tm+mt
source-wordcount: '2119'
ht-degree: 92%

---


# Dernière version{#latest-release}

![](assets/do-not-localize/cp-icon.png) **Nouvelle version de juin du panneau de contrôle** avec surveillance des profils actifs, audit de délivrabilité des sous-domaines et gestion des clés GPG. [En savoir plus](https://docs.adobe.com/content/help/fr-FR/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) Version 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_11 septembre 2020_

* Correction d’une régression en raison de laquelle la préparation de la diffusion était bloquée en raison d’une seule fonction erronée sur la partie de la diffusion conduisant à une surcharge de mémoire. (NEO-27346)


* Correction d’un problème après la mise à niveau qui désactivait Apache et le serveur Web avant la republication de l’application Web. (NEO-27155)


* Correction d’une régression sur la gestion des modèles HTML en raison de laquelle les URL de suivi devenaient visibles en raison d’une mauvaise interprétation des onglets. (NEO-25909)


* Correction d’un problème lié au processus de nettoyage de la base de données qui pouvait échouer en raison d’une source de données non gérée. (NEO-23160, NEO-23364)
* Le processus de nettoyage purge désormais les listes expirées par lots de 100 au lieu de 1 par un.
* Correction d’une régression qui empêchait de modifier le nom interne d’un compte externe. (NEO-27323)


* Correction d’une régression au cours de la mise à niveau provoquant un début incorrect de nlserver (journaux d’erreurs).
* La gestion des mises à jour pour la mémoire partagée a été améliorée. Les étapes supplémentaires requises dans la version 20.2 ne sont plus nécessaires.

## ![](assets/do-not-localize/orange_2.png) Version 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_7 juillet 2020_

* Correction d’un problème qui empêchait le tracking de fonctionner lorsque la fonction de signature était désactivée. (NEO-26411)
* Correction d’un problème en raison duquel les liens non signés provenant de domaines personnalisés étaient bloqués au lieu d’être autorisés. (NEO-25210)
* Correction d’un problème qui empêchait d’ouvrir/de cliquer sur les URL de tracking lors de l’utilisation de certaines anciennes versions d’Outlook. (NEO-25688)
* Correction d’un problème en raison duquel les URL de page miroir étaient incorrectement définies dans les diffusions email. (NEO-26084)
* Correction d’un problème lié à gestion des URL de codage dans le service anti-hameçonnage. (NEO-25283)
* Correction d’un problème qui empêchait le suivi des URL à l’aide de fragments dans les paramètres de personnalisation (balises d’ancrage avec signe dièse) de fonctionner. (NEO-25774)
* Correction d’un problème de suivi lors de l’utilisation de formules de tracking personnalisées spécifiques. (NEO-25277)


Correction d’un problème qui empêchait le suivi des « clics de notification » de fonctionner (notifications push iOS et Android). (NEO-25965)
* Correction d’une régression qui avait un impact sur les champs calculés dans un workflow. (NEO-25194)
* Correction d’une régression qui empêchait le fonctionnement de la création à la volée d’URL de tracking web. (NEO-20999)
* Correction d’un problème lié aux rapports de diffusion d’usine qui s’affichaient tronqués lors de l’export au format PDF. (NEO-25757)
* Correction d’un problème de blocage dans l’assistant de déploiement.
* Correction d’un problème qui empêchait le fonctionnement correct du workflow Notification des offres après un postupgrade.
* Le connecteur HTTP2 iOS a été amélioré (mises à jour tierces et gestion des erreurs). (NEO-25904, NEO-25903)
* La liste jarsToSkip de catalina.properties a été mise à jour afin de supprimer la référence à un fichier jar qui n’était plus utilisé (notifications iOS).
* Correction d’un problème qui bloquait la préparation des diffusions après un postupgrade.
* Après le passage au [nouveau mécanisme d’identifiant de séquence](https://helpx.adobe.com/fr/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), toutes les applications web qui mettent à jour la table des destinataires sont republiées pendant le postupgrade.
* Correction d’une vulnérabilité XSS potentielle dans le contenu d’une diffusion. (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) Version 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

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
    <p>Azure Synapse n’est disponible que pour les environnements hybrides et on-premise. Pour plus d’informations, consultez la <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">documentation détaillée</a>.</p>
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
   <p>La loi brésilienne Lei Geral de Proteção de Dados (LGPD) entrera en vigueur début 2021 pour toutes les sociétés qui collectent ou traitent des données personnelles au Brésil.</p>
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

* La sécurité améliorée du tracking des liens dans les emails est activée par défaut pour tous les clients. Une autre fonctionnalité de sécurité améliorée est disponible. Il est possible de l’activer en contactant le service Assistance clientèle. Pour plus d’informations sur la fonctionnalité et la procédure d’activation pour les clients non hébergés, consultez la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html). (NEO-24232)

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

* La messagerie transactionnelle a été améliorée pour offrir une meilleure expérience utilisateur. Vous pouvez désormais annuler la publication d’un modèle de message transactionnel, ce qui le supprime des instances d’exécution. [En savoir plus](../../message-center/using/template-unpublication.md).

* De nouvelles options sont disponibles pour définir des limites lors de l’envoi d’emails contenant des images ou des pièces jointes. Ces garde-fous permettent d’éviter des problèmes de performances, ce qui est particulièrement utile pour les messages transactionnels. [En savoir plus](../../installation/using/configuring-campaign-options.md#delivery)

* La nouvelle option **Préparer les fragments de diffusion dans la base de données** permet d’effectuer la préparation de la diffusion directement dans la base de données, ce qui peut accélérer considérablement l’analyse. Cette option n’est proposée que pour des configurations spécifiques. [En savoir plus](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Les performances de l’[activité Connecteur CRM](../../workflow/using/crm-connector.md) pour Microsoft Dynamics ont été améliorées. (NEO-13303, NEO-12710)

* La version de mémoire partagée a été augmentée.

   >[!WARNING]
   >
   >Cette amélioration nécessite une étape supplémentaire suite à la mise à niveau. Consultez la section **Évolutions techniques** ci-dessous.

* Le workflow de nettoyage a été amélioré. Les tables de travail orphelines de tous les workflows supprimés sont désormais automatiquement supprimées par le workflow de nettoyage. [En savoir plus](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Les certificats des applications mobiles iOS utilisant le connecteur HTTP2 iOS sont maintenant validés avant d’envoyer des notifications push, ce qui empêche les échecs de diffusions en raison du dépassement des dates d’expiration de ces certificats.

* La gestion des connexions au proxy HTTP a été améliorée. [En savoir plus](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Autres changements**

* Les anciens connecteurs SMS sont désormais obsolètes. Consultez la [page Fonctionnalités obsolètes](../../rn/using/deprecated-features.md).

* Vous ne pouvez plus utiliser votre propre compte Litmus pour configurer et utiliser l’Inbox rendering dans Adobe Campaign. [En savoir plus](../../delivery/using/inbox-rendering.md).

* Pour mieux distinguer les vues et les dossiers, la couleur des noms de vues a été changée du bleu foncé au cyan foncé. [En savoir plus](../../platform/using/access-management.md#about-views)

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
* Correction d’un problème en raison duquel la valeur du paramètre de codage était supprimée lors de la redirection à partir d’une URL de tracking. (NEO-25637)
* Correction d’un problème en raison duquel une requête ne fonctionnait pas lors de la comparaison de nombres flottants. (NEO-23243)
* Correction d’un problème en raison duquel le contenu de la colonne **Modifié par** ne s’affichait pas après le redémarrage d’un workflow. (NEO-23035)
* Correction d’un problème en raison duquel le workflow technique de tracking échouait lors du téléchargement des logs à partir d’un deuxième conteneur. (NEO-23159)
* Correction d’un problème en raison duquel les workflows échouaient lors de l’exécution d’une activité d’**enrichissement**. (NEO-17338)
* Une vérification a été ajoutée au champ **Doublons à conserver** dans l’activité de workflow **Déduplication** afin d’empêcher la saisie de valeurs &quot;null&quot; ou négatives.
* Suppression de l’**assistant Planificateur** des campagnes récurrentes pour éviter de mentionner les heures et les minutes. Seules les dates sont prises en compte.
* Correction d’un problème lié à d’autres champs d’enregistrement lors de la création de diffusions par le biais de l’option **Calculée par un script** dans l’activité de workflow **Script**. (NEO-20609)
* Correction d’un problème qui empêchait la suppression des workflows fantômes dans les tâches de nettoyage de base de données.
* Correction d’un problème en raison duquel le workflow technique de **Facturation (profils actifs)** échouait. (NEO-19777)
* Correction d’un problème lors du test de la connexion du compte externe acsDefaultAccount. (NEO-23433)
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
* Correction d’un problème qui empêchait Microsoft Dynamics CRM de récupérer toutes les entités. (NEO-24528)
* Correction d’un problème en raison duquel l’historique de l’activité **Requête incrémentale** était supprimé suite à l’exécution du workflow de nettoyage.
* Correction d’un problème lors de la création d’un compte externe de mid-sourcing en raison de l’absence de l’option NmsMidSourcing_LastBroadLog_&lt;InternalName>

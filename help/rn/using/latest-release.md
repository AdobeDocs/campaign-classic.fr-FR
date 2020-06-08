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
source-git-commit: e3e8802aae0d10befcf9eef1ccf720f82c460038
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 15%

---


# Dernière version{#latest-release}

[Upgrade de build](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html) | [Versions du Panneau de contrôle](https://docs.adobe.com/content/help/fr-FR/control-panel/using/release-notes.html) | [Mises à jour de la documentation](../../rn/using/documentation-updates.md) | [Versions précédentes](../../rn/using/release--20-1.md) | [Fonctionnalités obsolètes](../../rn/using/deprecated-features.md)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Disponibilité générale</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Version diffusable</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Plus disponible</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Obsolète</strong></td> 
  </tr> 
   <tr> 
   <td>Dernier build stable disponible. Build validé en production.<br> </td>
   <td>Build validé par Adobe. En attente de vérification de la production.<br> </td>
   <td>Build le plus récent disponible avec correctifs. Mise à jour requise.<br> </td>
   <td>Contient des régressions connues. La mise à jour est obligatoire.<br> </td>
  </tr> 
 </tbody> 
</table>

Le **dernier build stable** est le build 9032 (3a9dc9c). Cliquez [ici](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) Version 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_8 juin 2020_

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Prise en charge des émoticônes</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Lors de la conception d’un message dans Campaign, vous pouvez désormais facilement insérer des émoticônes dans le corps du message, à l’aide d’un bouton dédié. Ils peuvent également être ajoutés à l’objet du courriel. Vous pouvez personnaliser la liste des émoticônes disponibles dans l’interface.</p>
    <p>Pour plus d’informations sur l’ajout d’émoticônes, consultez la documentation <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons"></a>détaillée. Découvrez comment personnaliser la liste émotionnelle <a href="../../delivery/using/customizing-emoticon-list.md">dans cette section</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Connecteur de FDA de synthèse Azure</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Vous pouvez maintenant connecter votre instance Campaign à votre base de données externe Azure Synapse. Cette connexion est gérée via un nouveau compte externe.</p>
    <p>Azure Synapse n'est disponible que pour les environnements hybrides et sur site. Pour plus d’informations, consultez la <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">documentation détaillée</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>La Thaïlande et le Brésil : loi sur la protection de la vie privée</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La loi thaïlandaise sur la protection des données personnelles (PDPA) est la nouvelle loi sur la protection des données personnelles qui harmonise et modernise les exigences de protection des données en Thaïlande. </p>
   <p>La loi brésilienne Lei Geral de Proteção de Dados (LGPD) entrera en vigueur le 16 août pour toutes les sociétés qui collectent ou traitent des données personnelles au Brésil.</p>
   <p>Ces réglementations s’appliquent aux clients Adobe Campaign qui détiennent des données pour les objets de données résidant dans ces pays. En plus des fonctionnalités de confidentialité déjà disponibles à Campaign (notamment la gestion du consentement, les paramètres de rétention des données et les rôles utilisateur), nous saisissons cette opportunité pour inclure des fonctionnalités supplémentaires, afin de faciliter votre préparation à PDPA et LGPD :</p>
   <ul> 
     <li><p>Droit d'accès et droit de suppression : nous tirons parti des capacités qui ont été ajoutées pour le RGPD et le CCPA. <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html">En savoir plus</a></p></li> 
     <li> <p>Lors de la création d’une requête de confidentialité à l’aide de l’interface Campaign ou de l’API, vous sélectionnez maintenant le type de <strong>règlement</strong> : PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">En savoir plus</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* La sécurité améliorée sur le suivi des liens dans les courriers électroniques est activée par défaut pour tous les clients. Une autre fonctionnalité de sécurité améliorée est disponible. Il est possible de l’activer en contactant le service Assistance clientèle. Pour plus d’informations sur la fonctionnalité et la procédure d’activation pour les clients non hébergés, consultez la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html). (NEO-24232)

* Pour optimiser la sécurité, l’algorithme de hachage MD5 utilisé pour générer des noms de fichier a été renforcé par sha256 pour le transfert de fichiers publics. (NEO-17044)

* Pour renforcer la sécurité contre les attaques XSS, les scripts client sont désactivés lors de l’exécution d’une page miroir. (NEO-17987)

* Correction d’un problème qui empêchait le processus technique de nettoyage **des requêtes de** confidentialité de supprimer les données de rapprochement. (NEO-25168, NEO-21004)

* Correction d’un problème avec l’activité de **transfert de fichier** qui empêchait le fonctionnement de l’authentification par clé SFTP sur Debian 9. (NEO-23183)

**Améliorations de la compatibilité**

Les systèmes suivants sont désormais pris en charge avec Campaign :
* Systèmes d’exploitation : Debian 10
* RDBMS : Oracle 18c et Oracle 19c
* FDA : Azure Synapse Analytics

En savoir plus sur la matrice [de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)Campaign.

**Améliorations**

* La messagerie transactionnelle a été améliorée pour une meilleure expérience utilisateur. Vous pouvez désormais annuler la publication d’un modèle de message transactionnel, ce qui le supprime des instances d&#39;exécution. [En savoir plus](../../message-center/using/template-unpublication.md).

* De nouvelles options sont disponibles pour définir des limites lors de l’envoi de courriers électroniques contenant des images ou des pièces jointes. Ces garde-fous peuvent éviter les problèmes de performances, ce qui est particulièrement utile pour les messages transactionnels. [En savoir plus](../../installation/using/configuring-campaign-options.md#delivery)

* La nouvelle option **Préparer les parties de la diffusion dans la base de données** permet d&#39;effectuer la préparation de la diffusion directement dans la base de données, ce qui peut accélérer considérablement l&#39;analyse. Cette option est disponible uniquement pour des configurations spécifiques. [En savoir plus](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Les performances de l&#39;activité [](../../workflow/using/crm-connector.md) CRM Connector pour Microsoft Dynamics ont été améliorées. (NEO-13303, NEO-12710)

* La version de mémoire partagée a été augmentée.

   >[!WARNING]
   >
   >Cette amélioration nécessite une étape supplémentaire après l’exécution de la mise à niveau. Reportez-vous à la section Évolution **** technique ci-dessous.

* Le processus de nettoyage a été amélioré. Les tables de travail orphelines de tous les workflows supprimés sont désormais automatiquement supprimées par le processus de nettoyage. [En savoir plus](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Les certificats pour les applications mobiles iOS avec le connecteur HTTP2 iOS sont maintenant validés avant d’envoyer des notifications Push, ce qui empêche les diffusions d’échouer en raison de certificats expirés.

* La gestion des connexions proxy HTTP a été améliorée. [En savoir plus](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Autres changements**

* Les connecteurs SMS hérités sont désormais obsolètes. Reportez-vous à la page [Fonctions](../../rn/using/deprecated-features.md)obsolètes.

* Vous ne pouvez plus utiliser votre propre compte Litmus pour configurer et utiliser le rendu de boîte de réception en Adobe Campaign. [En savoir plus](../../delivery/using/inbox-rendering.md).

* Pour mieux distinguer les vues des dossiers, la couleur des noms de vue est passée du bleu foncé au cyan foncé. [En savoir plus](../../platform/using/access-management.md#about-views)

* Campaign Classic peut désormais être connecté à des comptes Microsoft Dynamics CRM hébergés dans les régions du Royaume-Uni, de l&#39;Inde et du Canada. Ceci s&#39;applique aux types de déploiement Office 365 et On premise (Dynamics 2015).

* Campaign effectue désormais une vérification TLS pour vérifier que le nom d’hôte du serveur correspond au nom d’hôte dans le certificat fourni.

* Le tableau des statistiques de Diffusion et de suivi affiche désormais une entrée par diffusion pour le canal SMS, au lieu d&#39;une entrée par destinataire de diffusion.

* Ajouté un message d’erreur dans le fichier journal pour avertir les utilisateurs que le fichier téléchargé est plus volumineux que l’espace disque.

* Les fonctions suivantes sont désormais disponibles pour le connecteur Snowflake : MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Evolutions techniques**

Cette nouvelle version met à jour la mémoire partagée et nécessite des étapes supplémentaires pour effectuer la mise à niveau. En tant qu’administrateur Campaign, vous devez supprimer les segments de mémoire. Ces étapes sont obligatoires, car les anciens segments empêcheront le démarrage de nlserver/nlsrvmod.

Sous Windows, un redémarrage du système est nécessaire.

Sur Debian/CentOs, une suppression de mémoire partagée est nécessaire. Voici les étapes :

Avant la mise à niveau, vous devez suivre les étapes suivantes :

1. Arrêtez le service apache2 (http2 sur CentOS) s’il est en cours d’exécution.
1. Arrêtez le service nlserver (nlserver6 pour les versions plus anciennes) s’il est en cours d’exécution.

Après la mise à niveau :

1. Supprimez la mémoire partagée à l’aide de la commande **ipcrm** , si la version est antérieure à la version actuelle.
1. Début du service nlserver s’il était en cours d’exécution.
1. Début du service apache2 s’il était en cours d’exécution.

Voici les lignes de commande pour Debian :

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

Un exemple pour Linux est disponible sur cette [page](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Correctifs**

* Correction d’une régression mineure dans les logs du workflow de nettoyage.
* Correction d’un problème dans l’activité **de chargement des processus (SOAP)** lors de l’analyse des fichiers WSDL.
* Correction d’un problème qui provoquait une erreur lors de la mise à niveau de nombreux workflows à l’aide d’une activité de **Questionnaire** pour traiter efficacement un grand nombre de workflows.
* Correction d’un problème de connectivité intermittente lors du traitement des messages inMail à partir de la MTA améliorée. (NEO-20380)
* Correction d’un problème qui empêchait l’affichage correct des pourcentages de clics chauds lorsque les images s’affichaient avec une largeur de 100 % dans le code HTML. (NEO-23203)
* Correction d’un problème qui empêchait l’affichage complet du contenu conditionnel de la diffusion dans le rapport Clics chauds. (NEO-18729)
* Correction d’un problème en raison duquel l’étape d’approbation de la cible était ignorée lors de la reprise d’un processus pour envoyer une diffusion récurrente. (NEO-18166)
* Correction d’un problème en raison duquel le bouton **Redémarrer la préparation** du message ne reprenait pas la diffusion après correction d’une erreur dans le processus. (NEO-13488)
* Correction d’un problème en raison duquel les diffusions pouvaient échouer en mode midsourcing pendant la phase de progression où la cible incluait des destinataires avec des formats d&#39;un email japonais. (NEO-23846)
* Correction d’un problème de conversion de fuseau horaire avec Snowflake Connector (NEO-20105).
* Correction d’un problème de comptes externes, lié à l’utilisation de FTP sur SSL. (NEO-20498)
* Correction d’un problème en raison duquel les images ne s’affichaient pas dans les diffusions de ligne. (NEO-23207)
* Correction d’un problème qui provoquait une erreur lors de la publication d’une offre. (NEO-23312)
* Correction d’un problème lié aux notifications Push en raison duquel les connexions de test fonctionnaient dans les applications mobiles, même si le certificat avait expiré. (NEO-22991)
* Correction d’un problème qui pouvait affecter les notifications Push lorsqu’elles étaient envoyées à une fréquence élevée. (NEO-20516)
* Correction d’un problème en raison duquel les données de suivi incluaient des duplicata même si les logs de tracking ne le faisaient pas. (NEO-20040)
* Correction d’un problème en raison duquel des courriers électroniques transactionnels de duplicata étaient envoyés après correction d’un échec de communication du serveur de suivi. (NEO-23640)
* Correction d’un problème en raison duquel la valeur du paramètre de codage était supprimée lors de la redirection à partir d’une URL de suivi. (NEO-25637)
* Correction d’un problème en raison duquel une requête ne fonctionnait pas lors de la comparaison de nombres flottants. (NEO-23243)
* Correction d’un problème en raison duquel le contenu **Modifié par** colonne ne s’affichait pas après le redémarrage d’un processus. (NEO-23035)
* Correction d’un problème en raison duquel le processus technique de suivi échouait lors du téléchargement des journaux à partir d’un deuxième conteneur. (NEO-23159)
* Correction d’un problème en raison duquel les workflows échouaient lors de l’exécution d’une **activité d’Enrichissement** . (NEO-17338)
* Une vérification a été ajoutée aux **Doublons pour conserver** le champ dans l’activité de flux de travail de la **Déduplication** afin d’empêcher la saisie de valeurs nulles ou négatives.
* Suppression de l’assistant **** Planificateur des campagnes récurrentes afin d’éviter de mentionner les heures et les minutes. Seules les dates sont prises en compte.
* Correction d’un problème lié à d’autres champs d’enregistrement lors de la création de diffusions par le biais de l’option **Calculé par un script** dans l’activité de processus **Script** . (NEO-20609)
* Correction d’un problème qui empêchait la suppression des workflows fantômes dans les tâches de nettoyage de la base de données.
* Correction d’un problème en raison duquel le processus technique de **facturation (profils actifs)** échouait. (NEO-19777)
* Correction d’un problème lors du test de la connexion du compte externe acsDefaultAccount. (NEO-23433)
* Correction d’un problème qui empêchait la création d’une extension de schéma sur une clé primaire avec plusieurs colonnes avec une table Hadoop. (NEO-17390)
* Correction d’un problème dans l’activité **de chargement (SOAP)** qui empêchait le chargement de fichiers WSDL à partir d’une URL. (NEO-16924)
* Correction d’un problème qui empêchait l’exécution d’une arrêt **** inconditionnel dans la console lorsque plusieurs serveurs de processus actifs étaient équilibrés en charge. (NEO-19556)
* Correction d’une régression qui entraînait le blocage du workflow de nettoyage.
* Correction d’un problème qui pouvait se produire lors de la publication d’un modèle sur une instance d&#39;exécution.
* Correction d’un problème qui pouvait empêcher l’exécution du flux technique de collectePrivacyRequests. (NEO-20513, NEO-25169)
* Correction de problèmes qui pouvaient survenir lors de la tentative de connexion à Audience Manager après la mise à niveau vers la version 9080. (NEO-20511, NEO-25167)
* Correction de problèmes qui pouvaient survenir lors de l’exportation de rapports au format PDF ou XLS. (NÉO-20982, NÉO-23493, NÉO-23348)
* Correction d’un problème en raison duquel une diffusion pouvait s’afficher deux fois dans la liste de diffusion après son envoi.
* Correction d’un problème de préparation de diffusion qui pouvait se produire lorsque la configuration de routage était définie pour envoyer la diffusion par midsourcing.
* Correction d’un problème en raison duquel un message d’erreur pouvait s’afficher lorsque vous cliquiez sur un lien d’application Web dans un message de ligne.
* Correction d’un problème qui empêchait Microsoft Dynamics CRM de récupérer toutes les entités. (NEO-24528)
* Correction d’un problème en raison duquel l’historique des activités de **Requête incrémentale** était supprimé après l’exécution du processus de nettoyage.
* Correction d’un problème lors de la création d’un compte externe de midsourcing en raison duquel l’option NmsMidSourcing_LastBroadLog_&lt;InternalName> manquait.

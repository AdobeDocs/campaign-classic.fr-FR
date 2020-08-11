---
title: Problèmes de performance et de débit
seo-title: Problèmes de performance et de débit
description: Problèmes de performance et de débit
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 99%

---


# Problèmes de performance et de débit{#performance-and-throughput-issues}

>[!NOTE]
>
>Tout d’abord, vous devez vérifier que le dernier build est installé. Vous êtes ainsi assuré d’avoir les derniers correctifs et fonctionnalités. Reportez-vous aux [Notes de mise à jour](../../rn/using/latest-release.md) pour plus d’informations sur le contenu de chaque version.

## Matériel et infrastructure {#hardware-and-infrastructure}

Les instructions générales concernant les exigences matérielles pour Campaign Classic On-premise sont présentées dans cet [article](https://helpx.adobe.com/fr/campaign/kb/hardware-sizing-guide.html).

L’équipe de conseillers peut fournir aux clients de la version hébergée un outil leur permettant de voir facilement combien d’espace est utilisé par différents types de tables dans la base de données ainsi que l’espace utilisé sur le site SFTP. Elle propose en outre des outils de suppression des données inutiles. Contactez les équipes de conseillers ou de support si vous avez besoin d’implémenter cet outil. Voici quelques points importants à vérifier à l’aide de cet outil :

* Un nettoyage est requis si la taille de l’index est supérieure à la taille de la table.
* Vérifiez les tables qui sont remplies au maximum. Si celles-ci sont fréquemment utilisées, alors il est important de les nettoyer.
* Le blocage de la base de données peut empêcher l’envoi des emails.

Adobe Campaign fournit également un [outil](../../production/using/monitoring-processes.md#manual-monitoring) permettant de vérifier l’utilisation du CPU et de la RAM. Utilisez cet outil pour observer certains indicateurs spécifiques tels que : **Memory**, **Swap Memory**, **Disk**, **Active Processes**. Si les valeurs sont trop élevées, vous pouvez essayer de réduire le nombre de workflows ou de les planifier de manière à ce qu’ils démarrent en décalé.

## Performances de la base {#database-performances}

La plupart du temps, les problèmes de performance sont liés à la maintenance de la base de données. Voici les principaux éléments à vérifier :

* Configuration : nous recommandons de vérifier la configuration initiale de la plateforme d’Adobe Campaign et d’effectuer une vérification complète de la configuration matérielle.
* Installation et configuration de la plateforme Adobe Campaign : vérifiez la configuration du réseau et les options de délivrabilité de la plateforme.
* Maintenance de la base de données : assurez-vous que la tâche de nettoyage de la base de données fonctionne correctement et que la maintenance de la base de données est correctement planifiée et exécutée. Vérifiez le nombre et la taille des tables de travail.
* Diagnostic en temps réel : vérifiez les fichiers journaux des processus et de la plateforme, puis suivez l’activité de la base lors de la reproduction du problème.

>[!NOTE]
>
>Voir à ce sujet la section : [Performances de la base](../../production/using/database-performances.md).

## Configuration des applications {#application-configuration}

Voici une liste d’articles relatifs aux bonnes pratiques en matière de configuration des applications :

* Processus et mémoire MTA et MTAChild : le module **mta** distribue les messages à ses modules fils **mtachild**. Chaque **mtachild** prépare les messages, puis demande l’autorisation au serveur de statistiques avant de les envoyer. Consultez cette [page](../../installation/using/email-deliverability.md) pour plus d’informations.
* Configuration de TLS : l’activation globale de TLS n’est pas recommandée, car elle peut réduire le débit. Les paramètres TLS par domaine, gérés par l’équipe de délivrabilité, doivent plutôt être réglés en fonction des besoins. Consultez cette [page](../../installation/using/email-deliverability.md#mx-configuration) pour plus d’informations.
* DKIM : pour assurer le niveau de sécurité du DKIM, la taille minimum de cryptage recommandée est 1024b. Les clés de DKIM ayant une taille inférieure ne seront pas considérées comme valides par la plupart des fournisseurs d’accès. Reportez-vous à cette [page](../../delivery/using/technical-recommendations.md#dkim) et à cette [technote](https://helpx.adobe.com/fr/campaign/kb/domain-name-delegation.html).

## Problèmes de délivrabilité {#deliverability-issues}

Voici une liste des bonnes pratiques et des articles liés à la délivrabilité :

* Réputation IP : si la réputation IP n’est pas assez bonne, il y aura un impact sur la performance. Le module de **Suivi de la délivrabilité** propose divers outils pour suivre les performances de délivrabilité de votre plateforme. Reportez-vous à cette [page](../../delivery/using/monitoring-deliverability.md).
* Préchauffage d’une adresse IP : ce processus est réalisé par l’équipe de délivrabilité. Il s’agit d’augmenter progressivement le nombre d’emails par le biais de nouvelles adresses IP sur une période de quelques semaines.
* Configuration de l’affinité IP : une configuration incorrecte de l’affinité IP peut stopper complètement les emails (nom d’opérateur/affinité incorrect dans la configuration) ou réduire le débit (petit nombre d’IP dans l’affinité). Reportez-vous à cette [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Taille de l’email : la taille de l’email joue un rôle important au niveau du débit. La taille d’e-mail maximale recommandée est de 60 ko. Reportez-vous à cette [page](https://helpx.adobe.com/fr/legal/product-descriptions/campaign.html). Dans le rapport [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput), vérifiez le nombre d’octets transférés par heure.
* Grand nombre de destinataires non valides : lorsque de nombreux destinataires ne sont pas valides, cela peut avoir un impact sur le débit étant donné que le MTA tente de renvoyer les emails aux destinataires non valides. Veuillez vous assurer que votre base de données est bien tenue à jour.
* Niveau de personnalisation : si le statut d’une diffusion reste en « Personnalisation en cours », vérifiez le JavaScript utilisé dans les blocs de personnalisation.

>[!NOTE]
>
>Voir aussi [la section Points](../../delivery/using/deliverability-key-points.md) clés de la délivrabilité.


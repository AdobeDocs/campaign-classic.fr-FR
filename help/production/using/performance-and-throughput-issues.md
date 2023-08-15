---
product: campaign
title: Problèmes de performance et de débit
description: Problèmes de performance et de débit
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 100%

---

# Problèmes de performance et de débit{#performance-and-throughput-issues}



Tout d&#39;abord, vérifiez que vous avez installé la dernière version. Vous disposez ainsi des fonctionnalités et correctifs de bug les plus récents.

Consultez les [Notes de mise à jour](../../rn/using/latest-release.md) pour plus d&#39;informations sur le contenu de chaque version.

## Matériel et infrastructure {#hardware-and-infrastructure}

Les instructions générales concernant les exigences matérielles pour Campaign Classic on-premise sont présentées dans cette [page](https://helpx.adobe.com/fr/campaign/kb/hardware-sizing-guide.html).

L’équipe conseil peut fournir aux clients hébergés un outil qui permet d&#39;afficher facilement l’espace utilisé par divers types de tables dans la base de données ainsi que celui utilisé sur le site SFTP. Elle propose également des outils permettant de nettoyer les données inutiles. Contactez l&#39;[Assistance clientèle d&#39;Adobe ](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) si vous avez besoin que cet outil soit implémenté. Voici quelques éléments importants à vérifier lors de l&#39;utilisation de cet outil :

* Un nettoyage est requis si la taille de l’index est supérieure à la taille de la table.
* Vérifiez les tables qui sont remplies au maximum. Si celles-ci sont fréquemment utilisées, alors il est important de les nettoyer.
* Le blocage de la base de données peut empêcher l’envoi des emails.

Adobe Campaign fournit également un [outil](../../production/using/monitoring-processes.md#manual-monitoring) permettant de vérifier l’utilisation du CPU et de la RAM. Utilisez cet outil pour observer certains indicateurs spécifiques tels que : **Memory**, **Swap Memory**, **Disk**, **Active Processes**. Si les valeurs sont trop élevées, vous pouvez essayer de réduire le nombre de workflows ou de les planifier de manière à ce qu’ils démarrent en décalé.

## Vérification de la base de données {#database-performances}

La plupart du temps, les problèmes de performance sont liés à la maintenance de la base de données. Voici les principaux éléments à vérifier :

* Configuration : nous recommandons de vérifier la configuration initiale de la plateforme d’Adobe Campaign et d’effectuer une vérification complète de la configuration matérielle.
* Installation et configuration de la plateforme Adobe Campaign : vérifiez la configuration du réseau et les options de délivrabilité de la plateforme.
* Maintenance de la base de données : assurez-vous que la tâche de nettoyage de la base de données fonctionne correctement et que la maintenance de la base de données est correctement planifiée et exécutée. Vérifiez le nombre et la taille des tables de travail.
* Diagnostic en temps réel : vérifiez les fichiers journaux des processus et de la plateforme, puis suivez l’activité de la base lors de la reproduction du problème.

>[!NOTE]
>
>Pour plus d&#39;informations, voir à ce sujet la section : [Performances de la base de données](../../production/using/database-performances.md).

## Configuration des applications {#application-configuration}

Voici une liste d’articles relatifs aux bonnes pratiques en matière de configuration des applications :

* Processus et mémoire MTA et MTAChild : le module **mta** distribue les messages à ses modules enfants **mtachild**. Chaque **mtachild** prépare les messages, puis demande l’autorisation au serveur de statistiques avant de les envoyer. Consultez cette [page](../../installation/using/email-deliverability.md) pour plus d’informations.
* Configuration de TLS : l’activation globale de TLS n’est pas recommandée, car elle peut réduire le débit. Les paramètres TLS par domaine, gérés par l’équipe de délivrabilité, doivent plutôt être réglés en fonction des besoins. Consultez cette [page](../../installation/using/email-deliverability.md#mx-configuration) pour plus d’informations.
* DKIM : pour assurer le niveau de sécurité du DKIM, la valeur 1024b est la taille de chiffrement recommandée selon les bonnes pratiques. Les clés DKIM inférieures ne seront pas considérées comme valides par la majorité des fournisseurs d’accès. Reportez-vous à [cette page](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=fr#authentication).

## Problèmes de délivrabilité {#deliverability-issues}

Voici une liste des bonnes pratiques et des articles liés à la délivrabilité :

* Réputation IP : si la réputation IP n’est pas assez bonne, il y aura un impact sur la performance. Le module de **Suivi de la délivrabilité** propose divers outils pour suivre les performances de délivrabilité de votre plateforme. Reportez-vous à cette [page](../../delivery/using/monitoring-deliverability.md).
* Préchauffage d’une adresse IP : ce processus est réalisé par l’équipe de délivrabilité. Il s’agit d’augmenter progressivement le nombre d’emails par le biais de nouvelles adresses IP sur une période de quelques semaines.
* Configuration de l’affinité IP : une configuration incorrecte de l’affinité IP peut stopper complètement les emails (nom d’opérateur/affinité incorrect dans la configuration) ou réduire le débit (petit nombre d’IP dans l’affinité). Reportez-vous à cette [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Taille de l’email : la taille de l’email joue un rôle important au niveau du débit. La taille d’e-mail maximale recommandée est de 60 ko. Reportez-vous à cette [page](https://helpx.adobe.com/fr/legal/product-descriptions/campaign.html). Dans le rapport [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput), vérifiez le nombre d’octets transférés par heure.
* Grand nombre de destinataires non valides : lorsque de nombreux destinataires ne sont pas valides, cela peut avoir un impact sur le débit étant donné que le MTA tente de renvoyer les emails aux destinataires non valides. Veuillez vous assurer que votre base de données est bien tenue à jour.
* Niveau de personnalisation : si le statut d’une diffusion reste en « Personnalisation en cours », vérifiez le JavaScript utilisé dans les blocs de personnalisation.

>[!NOTE]
>
>Voir aussi la section [Delivrabilité](../../delivery/using/about-deliverability.md). Pour un examen plus approfondi de la délivrabilité, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=fr).

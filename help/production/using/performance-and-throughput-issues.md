---
product: campaign
title: Problèmes de performance et de débit
description: Problèmes de performance et de débit
feature: Monitoring
badge-v7-prem: label="On-premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 70%

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

Adobe Campaign fournit également une [outil](../../production/using/monitoring-processes.md#manual-monitoring) pour vérifier l’utilisation du processeur et de la mémoire vive. Utilisez cet outil et observez des indicateurs spécifiques tels que : **Mémoire**, **Swap Memory**, **Disque**, **Processus actifs**. Si les valeurs sont trop élevées, vous pouvez essayer de réduire le nombre de workflows ou de planifier des workflows pour qu&#39;ils démarrent à des moments différents.

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

* Processus et mémoire MTA et MTAChild : le **mta** distribue des messages à ses **mtachild** modules enfants. Chaque **mtachild** prépare les messages avant de demander l’autorisation au serveur de statistiques et de les envoyer. Voir cette [page](../../installation/using/email-deliverability.md) pour plus d’informations.
* Configuration de TLS : l’activation globale de TLS n’est pas recommandée, car elle peut réduire le débit. Au lieu de cela, les paramètres TLS par domaine, gérés par l’équipe de délivrabilité, doivent être réglés en fonction des besoins. Voir cette [page](../../installation/using/email-deliverability.md#mx-configuration) pour plus d’informations.
* DKIM : pour assurer le niveau de sécurité du DKIM, la valeur 1024b est la taille de chiffrement recommandée selon les bonnes pratiques. Les clés DKIM inférieures ne seront pas considérées comme valides par la majorité des fournisseurs d’accès. Reportez-vous à [cette page](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=fr#authentication).

## Problèmes de délivrabilité {#deliverability-issues}

Voici une liste des bonnes pratiques et des articles liés à la délivrabilité :

* Réputation IP : si la réputation IP n’est pas assez bonne, il y aura un impact sur les performances. La variable **Supervision de la délivrabilité** module propose divers outils pour suivre les performances de délivrabilité de votre plateforme. Voir cette [page](../../delivery/using/monitoring-deliverability.md).
* Préchauffage d’une adresse IP : ce processus est réalisé par l’équipe de délivrabilité. Il s’agit d’augmenter progressivement le nombre d’emails par le biais de nouvelles adresses IP sur une période de quelques semaines.
* Configuration de l’affinité IP : une configuration incorrecte de l’affinité IP peut stopper complètement les emails (nom d’opérateur/affinité incorrect dans la configuration) ou réduire le débit (petit nombre d’adresses IP dans l’affinité). Voir cette [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Taille des emails : la taille des emails joue un rôle important dans le débit. La taille maximale recommandée est de 60 Ko. Consultez cette section [page](https://helpx.adobe.com/fr/legal/product-descriptions/campaign.html). Dans le [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput) , vérifiez le nombre d’octets transférés par heure.
* Grand nombre de destinataires non valides : lorsque de nombreux destinataires ne sont pas valides, cela peut avoir un impact sur le débit étant donné que le MTA tente de renvoyer les emails aux destinataires non valides. Veuillez vous assurer que votre base de données est bien tenue à jour.
* Niveau de personnalisation : si le statut d’une diffusion reste en « Personnalisation en cours », vérifiez le JavaScript utilisé dans les blocs de personnalisation.

>[!NOTE]
>
>Voir aussi la section [Delivrabilité](../../delivery/using/about-deliverability.md). Pour un examen plus approfondi de la délivrabilité, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=fr).

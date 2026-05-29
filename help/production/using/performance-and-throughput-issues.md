---
product: campaign
title: Problèmes de performance et de débit
description: Problèmes de performance et de débit
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
TQID: https://experienceleague.adobe.com/THf7A2u5ktNphqdI8K8ePzLNqCdyCmcqWN0OpYJfVh0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 805
ht-degree: 68%

---

# Problèmes de performance et de débit{#performance-and-throughput-issues}

Tout d’abord, vous devez vérifier que la dernière build est installée. Vous disposez ainsi des dernières fonctionnalités et des derniers correctifs.

Consultez les [Notes de mise à jour](../../rn/using/latest-release.md) pour plus d&#39;informations sur le contenu de chaque version.

## Matériel et infrastructure {#hardware-and-infrastructure}

Les instructions générales concernant les exigences matérielles pour Campaign Classic on-premise sont présentées dans cette [page](https://helpx.adobe.com/fr/campaign/kb/hardware-sizing-guide.html).

L’équipe de conseillers peut fournir aux clients hébergés un outil qui vous permet d’afficher facilement la quantité d’espace utilisée par différents types de tables dans la base de données ainsi que l’espace utilisé sur le site SFTP. Il fournit en outre des outils pour vous permettre de nettoyer les données inutiles. Contactez l&#39;[Assistance clientèle d&#39;Adobe ](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) si vous avez besoin que cet outil soit implémenté. Voici quelques éléments importants à vérifier lors de l&#39;utilisation de cet outil :

* Un nettoyage est requis si la taille de l’index est supérieure à la taille de la table.
* Vérifiez les tables qui ont le maximum de ballonnements. Si ces tables sont fréquemment utilisées, elles doivent être aspirées.
* Le blocage de la base de données peut empêcher l’envoi des emails.

Adobe Campaign fournit également un [outil](../../production/using/monitoring-processes.md#manual-monitoring) permettant de vérifier l’utilisation du processeur et de la mémoire vive (RAM). Utilisez cet outil et observez des indicateurs spécifiques tels que : **Mémoire**, **Mémoire d’échange**, **Disque**, **Processus actifs**. Si les valeurs sont trop élevées, vous pouvez essayer de réduire le nombre de workflows ou de les planifier de manière à ce qu’ils démarrent en décalé.

## Vérification de la base de données {#database-performances}

La plupart du temps, les problèmes de performances sont liés à la maintenance de la base de données. Voici les principaux éléments à vérifier :

* Configuration : nous recommandons de vérifier la configuration initiale de la plateforme d’Adobe Campaign et d’effectuer une vérification complète de la configuration matérielle.
* Installation et configuration de la plateforme Adobe Campaign : vérifiez la configuration du réseau et les options de délivrabilité de la plateforme.
* Maintenance de la base de données : assurez-vous que la tâche de nettoyage de la base de données est opérationnelle et que la maintenance de la base de données est correctement planifiée et exécutée. Vérifiez le nombre et la taille des tables de travail.
* Diagnostic en temps réel : vérifiez les fichiers journaux des processus et de la plateforme, puis suivez l’activité de la base lors de la reproduction du problème.

>[!NOTE]
>
>Pour plus d&#39;informations, voir à ce sujet la section : [Performances de la base de données](../../production/using/database-performances.md).

## Configuration des applications {#application-configuration}

Voici une liste d’articles relatifs aux bonnes pratiques en matière de configuration des applications :

* Processus et mémoire MTA et MTAChild : le module **mta** distribue les messages à ses modules enfants **mtachild**. Chaque **mtachild** prépare les messages, puis demande l’autorisation au serveur de statistiques avant de les envoyer. Voir cette [page](../../installation/using/email-deliverability.md) pour plus d’informations.
* Configuration de TLS : l’activation de TLS globalement n’est pas recommandée, car elle peut réduire le débit. Au lieu de cela, les paramètres TLS par domaine, gérés par l’équipe en charge de la délivrabilité, doivent être réglés en fonction des besoins. Voir cette [page](../../installation/using/email-deliverability.md#mx-configuration) pour plus d’informations.

  >[!NOTE]
  >
  >L’engagement de l’équipe chargée de la délivrabilité repose sur un contrat. La clientèle doit contacter son représentant ou sa représentante Adobe pour obtenir des informations relatives à l’engagement en matière de délivrabilité.

* DKIM : pour assurer le niveau de sécurité du DKIM, la valeur 1024b est la taille de chiffrement recommandée selon les bonnes pratiques. Les clés DKIM inférieures ne seront pas considérées comme valides par la majorité des fournisseurs d’accès. Reportez-vous à [cette page](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=fr#authentication).

## Problèmes de délivrabilité {#deliverability-issues}

Voici une liste des bonnes pratiques et des articles liés à la délivrabilité :

* Réputation IP : si la réputation IP n’est pas assez bonne, il y aura un impact sur la performance. Le module de **Suivi de la délivrabilité** propose divers outils pour suivre les performances de délivrabilité de votre plateforme. Voir cette [page](../../delivery/using/about-delivery-monitoring.md#deliverability-monitoring).
* Préchauffage d’une adresse IP : ce processus est effectué par l’équipe en charge de la délivrabilité. Cela implique d’augmenter progressivement le nombre d’e-mails par le biais de nouvelles adresses IP sur une période de quelques semaines.

  >[!NOTE]
  >
  >L’engagement de l’équipe chargée de la délivrabilité repose sur un contrat. La clientèle doit contacter son représentant ou sa représentante Adobe pour obtenir des informations relatives à l’engagement en matière de délivrabilité.

* Configuration de l’affinité IP : une configuration incorrecte de l’affinité IP peut stopper complètement les emails (nom d’opérateur incorrect/affinité incorrecte dans la configuration) ou réduire le débit (petit nombre d’IP dans l’affinité). Voir cette [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Taille de l’e-mail : la taille de l’e-mail joue un rôle important dans le débit. La taille maximale recommandée pour les e-mails est de 60 Ko. Consultez cette [page](https://helpx.adobe.com/fr/legal/product-descriptions/campaign.html). Dans le rapport [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput), vérifiez le nombre d’octets transférés par heure.
* Grand nombre de destinataires non valides : lorsqu’il y a un grand nombre de destinataires non valides, cela peut avoir un impact sur le débit. Le MTA continue à envoyer des e-mails à des destinataires non valides. Assurez-vous que votre base de données est bien gérée.
* Niveau de personnalisation : si le statut d’une diffusion reste en « Personnalisation en cours », vérifiez le JavaScript utilisé dans les blocs de personnalisation.

>[!NOTE]
>
>Voir aussi la section [Delivrabilité](../../delivery/using/about-deliverability.md). Pour un examen plus approfondi de la délivrabilité, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=fr).

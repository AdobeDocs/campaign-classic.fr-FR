---
solution: Campaign Classic
product: campaign
title: Note technique
description: Note technique
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 96%

---

# Mises à jour de la configuration d’Adobe Campaign - Mars 2021 {#acc-config-updates}

Une mise à jour de l’infrastructure et des paramètres doit être régulièrement effectuée avec les derniers builds et correctifs de produits. Ces correctifs sont nécessaires pour assurer la sécurité et la continuité du service. En outre, des mises à niveau seront nécessaires pour s’aligner sur les modifications tierces.

En tant que **client Managed Services ou hébergé**, Adobe vous informera des mises à niveau de build requises à intervalles réguliers. Vous devrez effectuer la mise à niveau conformément aux recommandations afin de garantir sa conformité.

En tant que **client On-premise ou hybride**, vous devez régulièrement mettre à niveau votre implémentation pour l&#39;adapter aux derniers builds publiés.



Pour des raisons de sécurité, vous devez maintenant effectuer la mise à niveau vers l’une des versions répertoriées ci-dessous. Outre la procédure de mise à niveau standard, vous devez effectuer quelques tâches manuelles afin de vous assurer que votre environnement est sécurisé et prêt à recevoir les futures modifications apportées par Adobe ou des systèmes tiers.

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Mises à jour de sécurité {#acc-security-updates}

Les dernières versions de Campaign s’accompagnent d’un correctif de sécurité qui renforce la protection contre les problèmes de type SSRF (Server Side Request Forgery). En savoir plus [sur cette page](https://helpx.adobe.com/fr/security/products/campaign/apsb21-04.html).

**Cela vous concerne-t-il ?**

Si votre environnement utilise un build antérieur à ceux répertoriés ci-dessous, cela vous concerne :

* Gold Standard 11. [En savoir plus](../rn/using/gold-standard.md)
* Campaign Version 21.1.1. [En savoir plus](../rn/using/latest-release.md)
* Campaign Version 20.3.3. [En savoir plus](../rn/using/release--20-3.md)
* Campaign Version 20.2.4. [En savoir plus](../rn/using/release--20-2.md)
* Campaign Version 20.1.4. [En savoir plus](../rn/using/release--20-1.md)
* Campaign Version 19.2.4. [En savoir plus](../rn/using/release--19-2.md)
* Campaign Version 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

Découvrez comment vérifier votre version [dans cette section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Comment effectuer la mise à jour ?**

Vous devez effectuer une mise à niveau vers un build plus récent parmi ceux répertoriés ci-dessus.

* En tant que client hybride, Adobe vous informera des dates de mise à niveau planifiées pour vos instances de mid-sourcing. Adobe vous recommande vivement de mettre également à niveau votre instance marketing.

   Le nouveau build offre une rétrocompatibilité avec la version 17.9 de Campaign Classic. Toutefois, Adobe vous recommande vivement d’effectuer une mise à niveau sur toutes les instances afin de remédier aux vulnérabilités de sécurité.

* En tant que client On-premise, vous êtes invité à mettre à niveau les instances marketing et celles de mid-sourcing vers le build le plus récent.

>[!CAUTION]
>
>Si vous ne pouvez pas effectuer la mise à niveau dans le délai recommandé, **vous devez contacter l’équipe de l’Assistance clientèle d’Adobe pour appliquer à court terme un correctif de sécurité manuel sur vos instances**.


## Mise à jour de la console cliente Campaign {#acc-cc-updates}

Les versions **désormais disponibles** de la console ci-dessous doivent être installées pour résoudre une régression récemment identifiée. Cette régression empêchait l’utilisation de certains composants de la console cliente, tels que le sélecteur de date et la gestion des images dans les diffusions. La **mise à niveau de la console** est obligatoire.

* Dernier build Gold Standard 11 9032@10c2709. [En savoir plus](../rn/using/gold-standard.md)
* Campaign Version 20.1.4. [En savoir plus](../rn/using/release--20-1.md)
* Campaign Version 19.2.4. [En savoir plus](../rn/using/release--19-2.md)
* Campaign Version 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

## Mise à jour d’Adobe Identity Management System (IMS)

Le Services d&#39;identités Adobe ne prendra plus en charge les anciennes versions d’Internet Explorer à compter du **30 juin 2021**. [En savoir plus](https://helpx.adobe.com/fr/x-productkb/global/update-operating-system-and-browser.html).

Une mise à niveau de la console cliente Campaign est nécessaire pour assurer la compatibilité avec Adobe IMS.

**Cela vous concerne-t-il ?**

Si vous vous connectez à Campaign [via un Adobe ID](../integrations/using/about-adobe-id.md), par le biais d’Adobe Identity Management Service (IMS), la mise à niveau vers l’une des nouvelles versions répertoriées ci-dessous est obligatoire :

* Gold Standard 11. [En savoir plus](../rn/using/gold-standard.md)
* Campaign Version 21.1.1. [En savoir plus](../rn/using/latest-release.md)
* Campaign Version 20.3.3. [En savoir plus](../rn/using/release--20-3.md)
* Campaign Version 20.2.4. [En savoir plus](../rn/using/release--20-2.md)
* Campaign Version 20.1.4. [En savoir plus](../rn/using/release--20-1.md)
* Campaign Version 19.2.4. [En savoir plus](../rn/using/release--19-2.md)
* Campaign Version 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

Ces versions s’accompagnent d’un nouveau protocole de connexion : la mise à niveau est obligatoire pour que le serveur Campaign et la console cliente puissent se connecter à Campaign au-delà du **30 juin 2021**.

Découvrez comment vérifier votre version [dans cette section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Comment effectuer la mise à jour ?**

En tant que client hébergé, Adobe collaborera avec vous sous peu afin de mettre à niveau votre ou vos instance(s) vers la nouvelle version.

En tant que client On-premise/hybride, vous devez effectuer la mise à niveau vers l’une des versions les plus récentes pour bénéficier de la nouvelle console cliente et assurer une transition harmonieuse **avant le 30 juin 2021**.

Une fois toutes les instances mises à niveau, la console cliente doit également être mise à niveau vers cette version.

* Découvrez comment accéder à la [distribution logicielle d’Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr).

* [Découvrez comment installer la console cliente de Campaign](../installation/using/installing-the-client-console.md).

## Intégration avec les triggers Experience Cloud  {#acc-triggers-updates}

Le service d’authentification historique oAuth est arrivé en fin de vie Le mode d’authentification de l’intégration des triggers, historiquement basé sur l’authentification oAUTH pour accéder au pipeline, a été remplacé par Adobe I/O. Il prendra fin le **30 novembre 2021**. [En savoir plus](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Cela vous concerne-t-il ?**

Si vos instances s’exécutent sur une **version antérieure à Campaign 19.1.8, 20.2.4 ou Gold Standard 11**, vous utilisez une version plus ancienne de l’intégration Triggers via l’authentification oAuth : **vous devez effectuer la mise à niveau vers une version plus récente et passer à Adobe I/O**.

La mise à niveau vers l’une des nouvelles versions répertoriées ci-dessous est obligatoire :

* Gold Standard 11. [En savoir plus](../rn/using/gold-standard.md)
* Campaign Version 21.1.1. [En savoir plus](../rn/using/latest-release.md)
* Campaign Version 20.2.5. [En savoir plus](../rn/using/release--20-2.md)
* Campaign Version 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

Découvrez comment vérifier votre version [dans cette section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Comment effectuer la mise à jour ?**

Une fois les instances mises à niveau vers une version plus récente, tous les clients doivent suivre la [procédure permettant de passer au nouveau mode d’authentification](../integrations/using/configuring-adobe-io.md). Pour ce faire, vous devez générer le nouveau jeton Adobe I/O et l’utiliser dans l’implémentation.

En outre, pour les environnements hybrides, les clients doivent s&#39;assurer que pipeline est configuré sur l&#39;instance de mid-sourcing. [En savoir plus](../integrations/using/configuring-pipeline.md).

[Découvrez comment migrer vers Adobe I/O](../integrations/using/configuring-adobe-io.md).

## Mises à jour d’APNs   {#acc-apns-updates}

### API du fournisseur APNs basée sur HTTP/2

Depuis le **31 mars 2021**, le service Apple Push Notification (APN) ne prend plus en charge le protocole binaire hérité. [En savoir plus](https://developer.apple.com/news/?id=c88acm2b).

**Cela vous concerne-t-il ?**

Si vos instances s’exécutent sur une **version antérieure à Campaign 21.1** et que vous envoyez des notifications push avec le protocole binaire Apple hérité, vous devez mettre à jour l’API du fournisseur APNs basée sur HTTP/2.

Découvrez comment vérifier votre version [dans cette section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Comment effectuer la mise à jour ?**

En tant que client hébergé, si vous avez effectué la mise à niveau vers le nouveau build, Adobe a déjà mis à jour votre ou vos instance(s) vers l’API basée sur HTTP/2.

En tant que client sur site/hybride, vous devez mettre à jour votre configuration. [Découvrez comment migrer vers HTTP/2](https://helpx.adobe.com/fr/campaign/kb/migrate-to-apns-http2.html)

### Mises à jour du certificat racine d’APNs

Le 29 mars 2021, une mise à jour de l’infrastructure du service de notifications Push Apple (APN) a affecté le canal Adobe Campaign Classic iOS. Une modification de la configuration du système d’exploitation est **obligatoire** pour éviter une panne du canal push d’iOS.

Pour en savoir plus sur les modifications d’APNs, consultez [cette page](https://developer.apple.com/news/?id=7gx0a2lp).

**Cela vous concerne-t-il ?**

Si vous utilisez Campaign pour envoyer des notifications push sur des appareils iOS, cela vous concerne.

**Comment effectuer la mise à jour ?**

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà intégré le nouveau certificat racine à votre environnement.

En tant que client On-premise/hybride, vous devez mettre à jour votre configuration pour garantir une transition harmonieuse **avant le 29 mars 2021**.

[Découvrez comment intégrer le nouveau certificat](ios-certificate-update.md).

## Liens utiles

* [Mise à niveau de votre environnement](../production/using/build-upgrade.md)
* [FAQ sur la mise à niveau du build](../platform/using/faq-build-upgrade.md)
* [Télécharger le build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Mise à disposition de la nouvelle console cliente auprès des utilisateurs](../installation/using/client-console-availability-for-windows.md)

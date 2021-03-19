---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: cac3e22dd9aa8220f6980bef0d57c11d47c91163
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 15%

---


# Mises à jour de la configuration Adobe Campaign - Mars 2021 {#acc-config-updates}

Vous devez mettre à jour votre infrastructure et vos paramètres avec les dernières versions et correctifs de produits. Ces correctifs sont obligatoires pour assurer la continuité de service et la sécurité. En outre, vous devez adapter votre mise en oeuvre pour l’aligner sur les modifications tierces.

En tant que client hébergé, l’Adobe vous informera des mises à niveau de build requises à intervalles réguliers. Vous devez effectuer la mise à niveau conformément aux recommandations pour garantir la conformité.

En tant que client sur site/hybride, pour des raisons de sécurité, vous devez effectuer la mise à niveau vers l’une des versions répertoriées dans cette page. En outre, vous devez effectuer quelques tâches manuelles pour vous assurer que votre environnement est sûr et prêt pour les modifications à venir à partir d&#39;Adobes ou de systèmes tiers.

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez le service à la clientèle [Adobe ](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Mises à jour de sécurité

Les dernières versions de Campaign sont fournies avec un correctif de sécurité qui renforce la protection contre les problèmes de usurpation de requête côté serveur (SSRF). En savoir plus [dans cette page](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**Es-tu affecté ?**

Si votre environnement utilise une version inférieure à celle répertoriée ci-dessous, vous êtes affecté :

* Gold Standard 11. [En savoir plus](../rn/using/gold-standard.md)
* Version Campaign 21.1.1. [En savoir plus](../rn/using/latest-release.md)
* Version Campaign 20.3.3. [En savoir plus](../rn/using/release--20-3.md)
* Version Campaign 20.2.4. [En savoir plus](../rn/using/release--20-2.md)
* Version Campaign 20.1.4. [En savoir plus](../rn/using/release--20-1.md)
* Version Campaign 19.2.4. [En savoir plus](../rn/using/release--19-2.md)
* Version Campaign 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

**Comment mettre à jour ?**

Vous devez effectuer la mise à niveau vers l’une des nouvelles versions répertoriées ci-dessus.

* En tant que client hybride, l’Adobe mettra à niveau l’instance marketing vers la nouvelle version et il est vivement recommandé de mettre à niveau son instance marketing également.

   La nouvelle version est compatible avec au moins la version 17.9 de Campaign Classic, mais pour éviter tout problème de sécurité, Adobe recommande vivement de mettre à niveau toutes les instances vers une nouvelle version. 

* En tant que client sur site, vous êtes invité à mettre à niveau les instances de marketing et de midsourcing vers une version plus récente.

>[!CAUTION]
>
>Si vous ne pouvez pas effectuer la mise à niveau pour le moment, **vous devez contacter l’équipe d’assistance clientèle d’Adobe pour appliquer manuellement un correctif de sécurité à vos instances**.


## Mise à jour de la console client Campaign

La dernière version de Gold Standard 11 corrige une régression qui empêchait l&#39;utilisation de certains composants de la Console de contrôle, tels que le sélecteur de date et la gestion des images dans les diffusions. La mise à niveau de la console est obligatoire.

[En savoir plus](../rn/using/gold-standard.md).

>[!NOTE]
>
>La nouvelle console client pour les autres versions sera bientôt disponible.

## Mise à jour du système IMS (Adobe Identity Management System)

Le service d&#39;identité d&#39;Adobe (IMS) cessera de prendre en charge les anciennes versions d&#39;Internet Explorer à compter du **30 juin 2021**. [En savoir plus](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Campaign Client Console a été mis à jour pour assurer la compatibilité avec l&#39;Adobe IMS.

**Es-tu affecté ?**

Si vous vous connectez à Campaign [via un Adobe ID](../integrations/using/about-adobe-id.md), par le biais d’Adobe Identity Management Service (IMS), la mise à niveau vers l’une des nouvelles versions répertoriées ci-dessous est obligatoire :

* Gold Standard 11. [En savoir plus](../rn/using/gold-standard.md)
* Version Campaign 21.1.1. [En savoir plus](../rn/using/latest-release.md)
* Version Campaign 20.3.3. [En savoir plus](../rn/using/release--20-3.md)
* Version Campaign 20.2.4. [En savoir plus](../rn/using/release--20-2.md)
* Version Campaign 20.1.4. [En savoir plus](../rn/using/release--20-1.md)
* Version Campaign 19.2.4. [En savoir plus](../rn/using/release--19-2.md)
* Version Campaign 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

Ces versions sont accompagnées d’un nouveau protocole de connexion : la mise à niveau est obligatoire pour que le serveur Campaign et Client Console puissent se connecter à Campaign après le **30 juin 2021**.

**Comment mettre à jour ?**

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà mis à niveau votre ou vos instances vers une version plus récente.

En tant que client sur site/hybride, vous devez effectuer la mise à niveau vers l’une des versions les plus récentes pour bénéficier de la nouvelle console client et assurer une transition **transparente avant le 30 juin 2021**.

Une fois toutes les instances mises à niveau, la console client doit également être mise à niveau vers cette version.

* Découvrez comment accéder à la [distribution logicielle d&#39;Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr).

* [Découvrez comment installer la console](../installation/using/installing-the-client-console.md) client Campaign.

## Intégration avec les déclencheurs Experience Cloud

Le service d’authentification Auth hérité a atteint la fin de vie. Déclenche l&#39;authentification d&#39;intégration, basée à l&#39;origine sur la configuration de l&#39;authentification oAUTH pour accéder au pipeline, a été déplacée vers l&#39;Adobe I/O. Il sera retiré le **30 novembre 2021**. [En savoir plus](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Es-tu affecté ?**

Si vos instances s’exécutent sur une version **plus ancienne que Campaign 19.1.8, 20.2.4, Gold Standard 11**, vous utilisez une version plus ancienne de l’intégration Triggers via l’authentification Auth : **vous devez effectuer la mise à niveau vers une version plus récente et passer à Adobe I/O**.

La mise à niveau vers l’une des nouvelles versions répertoriées ci-dessous est obligatoire :

* Gold Standard 11. [En savoir plus](../rn/using/gold-standard.md)
* Version Campaign 21.1.1. [En savoir plus](../rn/using/latest-release.md)
* Version Campaign 20.3.3. [En savoir plus](../rn/using/release--20-3.md)
* Version Campaign 20.2.4. [En savoir plus](../rn/using/release--20-2.md)
* Version Campaign 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

**Comment mettre à jour ?**

Une fois les instances mises à niveau vers une version plus récente, tous les clients doivent suivre la procédure [passer au nouveau mode d&#39;authentification](../integrations/using/configuring-adobe-io.md). Pour ce faire, vous devez générer le nouveau jeton d’Adobe I/O et l’utiliser dans l’implémentation.  

En outre, pour les environnements hybrides, les clients doivent s&#39;assurer que pipeline est configuré sur l&#39;instance de mid-sourcing. [En savoir plus](../integrations/using/configuring-pipeline.md).

[Découvrez comment migrer vers Adobe I/O](../integrations/using/configuring-adobe-io.md).

## Mises à jour des APN

### API du fournisseur APN basé sur HTTP/2

Le service de notifications Push Apple (APN) ne prendra plus en charge le protocole binaire hérité à compter du **31 mars 2021**. [En savoir plus](https://developer.apple.com/news/?id=c88acm2b).

**Est-ce que tu es affecté ?**

Si vos instances s’exécutent sur une version **plus ancienne que Campaign 21.1,** et envoient des notifications Push avec le protocole binaire Apple hérité, vous devez mettre à jour l’API du fournisseur APN basé sur HTTP/2.

**Comment mettre à jour ?**

En tant que client hébergé, aucune action n’est nécessaire : L’Adobe a déjà mis à jour vos instances vers l’API HTTP/2.

En tant que client sur site/hébergé, vous devez mettre à jour votre configuration. [Découvrez comment migrer vers HTTP/2](https://helpx.adobe.com/fr/campaign/kb/migrate-to-apns-http2.html)

### Mises à jour des certificats racine des APN

Le 29 mars 2021, une mise à jour de l’infrastructure du service de notifications Push Apple (APN) aura un impact sur le canal Adobe Campaign Classic iOS. Une modification de la configuration du système d’exploitation est **obligatoire** pour éviter une panne de canal Push iOS.

Pour en savoir plus sur les modifications des APN [dans cette page](https://developer.apple.com/news/?id=7gx0a2lp).

**Es-tu affecté ?**

Si vous utilisez Campaign pour envoyer des notifications Push sur des appareils iOS, vous êtes affecté.

**Comment mettre à jour ?**

En tant que client hébergé, aucune action n’est nécessaire : Adobe a déjà incorporé le nouveau certificat racine à votre environnement.

En tant que client sur site/hybride, vous devez mettre à jour votre configuration pour garantir une transition **transparente avant le 29 mars 2021**.

[Découvrez comment incorporer le nouveau certificat](ios-certificate-update.md).


## Liens utiles

* [Mettre à niveau votre environnement](../production/using/build-upgrade.md)
* [FAQ sur l&#39;upgrade de build](../platform/using/faq-build-upgrade.md)
* [Télécharger la compilation du Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/fr/campaign.html)
* [Mettre la nouvelle console client à la disposition des utilisateurs](../installation/using/client-console-availability-for-windows.md)

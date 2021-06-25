---
product: campaign
title: Mettre à jour votre environnement pour vous connecter à Adobe Campaign avec IMS
description: Campaign - Mises à jour IMS
hide: true
hidefromtoc: true
source-git-commit: 883ac681e0bf0e4ccf916c745924b7340a4d22f9
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 21%

---

# Comment mettre à jour votre environnement pour se connecter à Adobe Campaign avec IMS {#acc-ims-faq}

Le 30 juin 2021, des modifications seront apportées aux fonctionnalités de connexion [Adobe Identity Management System](https://helpx.adobe.com/fr/enterprise/using/identity.html) (IMS) qui pourraient avoir une incidence sur votre capacité à continuer à utiliser Adobe Campaign. Découvrez comment vous assurer que vous continuez à utiliser Adobe Campaign Classic v7 sans interruption.

## Qu&#39;est-ce qui a changé ?

Adobe Identity Management Service (IMS) cessera de prendre en charge les anciennes versions d’Internet Explorer à partir du **30 juin 2021**. [En savoir plus](https://helpx.adobe.com/fr/x-productkb/global/update-operating-system-and-browser.html).

Adobe souhaite conserver la fonctionnalité IMS pour tous les clients au 30 juin 2021. IMS fait partie de la structure de sécurité qui permet aux utilisateurs de se connecter à la console cliente, et donc à Adobe Campaign.

Pour préserver cette fonctionnalité, les clients doivent mettre à jour la console cliente sur l’ordinateur de chaque utilisateur et s’assurer que la dernière mise à jour de votre [version Windows](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), avec **intégré à Internet Explorer 11**, est installée sur l’ordinateur de chaque utilisateur.

## Cela vous concerne-t-il ?

Si vous vous connectez à Campaign [via une Adobe ID](../integrations/using/about-adobe-id.md), par le biais du service Identity Management d’Adobe (IMS), et que vous exécutez une version de Campaign plus ancienne que celles répertoriées ci-dessous, cela vous impacte.

Si vous avez déjà effectué la mise à niveau, mais que vous utilisez une ancienne version de Microsoft Internet Explorer, vous devez effectuer la mise à niveau vers Internet Explorer 11.

## Comment effectuer la mise à jour ?

* En tant que client hébergé, Adobe a déjà mis à niveau votre ou vos instances vers la version la plus récente.

* En tant que client on-premise/hybride, vous devez effectuer une mise à niveau vers l’une des versions les plus récentes répertoriées ci-dessus pour bénéficier de la nouvelle console cliente et assurer une transition transparente **avant le 30 juin 2021**.

   La mise à niveau vers l’une des nouvelles versions répertoriées ci-dessous est obligatoire :

   * Gold Standard 11. [En savoir plus](../rn/using/gold-standard.md)
   * Campaign Version 21.1.3. [En savoir plus](../rn/using/latest-release.md)
   * Campaign Version 20.2.4. [En savoir plus](../rn/using/release--20-2.md)
   * Campaign Version 20.1.4. [En savoir plus](../rn/using/release--20-1.md)
   * Campaign Version 19.2.4. [En savoir plus](../rn/using/release--19-2.md)
   * Campaign Version 19.1.8. [En savoir plus](../rn/using/release--19-1.md)

   Ces versions sont dotées d’un nouveau protocole de connexion. La mise à niveau est obligatoire pour le serveur Campaign et la console cliente : une fois toutes les instances mises à niveau, la console cliente doit également être mise à niveau vers cette version pour pouvoir se connecter à Campaign après le **30 juin 2021**.

De plus, assurez-vous que la dernière mise à jour de votre [version Windows](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), avec **intégré à Internet Explorer 11**, est installée sur l’ordinateur de chaque utilisateur.

## FAQ

**Comment puis-je vérifier la version de Campaign ?**

Découvrez comment vérifier votre version [dans cette section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Comment puis-je vérifier si j’utilise IMS ?**

Pour vérifier le mode de connexion, vous pouvez :

* Lancez la console cliente Campaign et accédez aux paramètres de connexion de votre instance. Si l’option **Se connecter à un Adobe ID** est sélectionnée, vous utilisez Adobe IMS.

   ![](../integrations/using/assets/ims_1.png)

ou

* Lancez la console cliente Campaign et vérifiez votre fenêtre de connexion. Si vous vous connectez à un Adobe ID, comme illustré dans l’écran ci-dessous, vous utilisez IMS.

   ![](../integrations/using/assets/adobeID.png)

**Message d’avertissement de connexion**

Le message d’avertissement suivant s’affiche pour les utilisateurs s’ils doivent mettre à jour leur console cliente ou utiliser une ancienne version de Microsoft Internet Explorer : **Vous devez installer la dernière mise à jour sous Windows et/ou vos applications d’Adobe.**

![](../integrations/using/assets/do-not-localize/errorMsg.png)

Si un tel avertissement s’affiche, assurez-vous d’installer les dernières mises à jour du système d’exploitation que vous utilisez. [En savoir plus](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

**Après le 30 juin 2021**, le message suivant s’affichera et ne pourra plus vous connecter à Adobe Campaign :

![](../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Liens utiles

* [Mise à niveau de votre environnement](../production/using/build-upgrade.md)
* [FAQ sur l’upgrade de build](../platform/using/faq-build-upgrade.md)
* [Mise à disposition de la nouvelle console cliente auprès des utilisateurs](../installation/using/client-console-availability-for-windows.md)
* [Installation de la console cliente Campaign](../installation/using/installing-the-client-console.md)
* [Accès à la distribution logicielle des Adobes](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr)
* [Télécharger le build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
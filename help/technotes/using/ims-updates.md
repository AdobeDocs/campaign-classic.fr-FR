---
product: campaign
title: Note technique - Mise à jour de votre environnement pour vous connecter à Adobe Campaign avec IMS
description: Campaign - Mises à jour d'IMS
feature: Technote, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 100%

---

# Comment mettre à jour votre environnement pour vous connecter à Adobe Campaign avec IMS {#acc-ims-faq}



Le 30 juin 2021, des modifications ont été apportées aux fonctionnalités de connexion d’[Adobe Identity Management System](https://helpx.adobe.com/fr/enterprise/using/identity.html) (IMS) ce qui pourrait avoir une incidence sur votre capacité à continuer à utiliser Adobe Campaign. Découvrez comment vous assurer que vous continuez à utiliser Adobe Campaign Classic v7 sans interruption.

## Qu&#39;est-ce qui a changé ?

Adobe Identity Management Service (IMS) ne prend plus en charge les anciennes versions d’Internet Explorer depuis le **30 juin 2021**. [En savoir plus](https://helpx.adobe.com/fr/x-productkb/global/update-operating-system-and-browser.html).

Adobe souhaite conserver la fonctionnalité IMS pour tous les clients après le 30 juin 2021. IMS fait partie de l&#39;infrastructure de sécurité qui permet aux utilisateurs de se connecter à la console cliente, et donc à Adobe Campaign.

Pour préserver cette fonctionnalité, les clients doivent mettre à jour la console cliente sur l&#39;ordinateur de chaque utilisateur et s&#39;assurer que la dernière mise à jour de votre [version Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), avec **Internet Explorer 11** natif, est installée sur l&#39;ordinateur de chaque utilisateur.

## Cela vous concerne-t-il ?

Si vous vous connectez à Campaign [via un Adobe ID](../../integrations/using/about-adobe-id.md), par le biais d&#39;Adobe Identity Management Service (IMS), et que vous exécutez une version de Campaign plus ancienne que celles répertoriées ci-dessous, ce changement vous concerne.

Si vous avez déjà effectué la mise à niveau, mais que vous utilisez une ancienne version de Microsoft Internet Explorer, vous devez effectuer la mise à niveau vers Internet Explorer 11.

## Comment effectuer la mise à jour ?

* En tant que client hébergé, Adobe a déjà mis à niveau votre ou vos instances vers la version la plus récente.

* En tant que client On-premise/hybride, vous devez effectuer la mise à niveau vers l&#39;une des versions répertoriées ci-dessus pour bénéficier de la nouvelle console cliente et assurer une transition harmonieuse **avant le 30 juin 2021**.

  La mise à niveau vers l’une des nouvelles versions répertoriées ci-dessous est obligatoire :

   * Gold Standard 11. [En savoir plus](../../rn/using/gold-standard.md)
   * Campaign Version 21.1.3. [Apprenez-en davantage](../../rn/using/latest-release.md)
   * Campaign Version 20.2.5.
   * Campaign Version 20.1.4.
   * Campaign Version 19.2.4.

  Ces versions sont dotées d&#39;un nouveau protocole de connexion. La mise à niveau est obligatoire pour le serveur Campaign et la console cliente : une fois toutes les instances mises à niveau, la console cliente doit également être mise à niveau vers cette version pour pouvoir se connecter à Campaign après le **30 juin 2021**.

De plus, assurez-vous que la dernière mise à jour de votre [version de Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), avec **Internet Explorer 11** natif, est installée sur l&#39;ordinateur de chaque utilisateur.

## FAQ

**Comment puis-je vérifier ma version de Campaign ?**

Découvrez comment vérifier votre version [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Comment puis-je vérifier si j&#39;utilise IMS ?**

Pour vérifier le mode de connexion, vous pouvez :

* Lancer la console cliente Campaign et accéder aux paramètres de connexion de votre instance. Si l&#39;option **Se connecter avec un Adobe ID** est sélectionnée, vous utilisez Adobe IMS.

  ![](../../integrations/using/assets/ims_1.png)

ou

* Lancer la console cliente Campaign et vérifier votre fenêtre de connexion. Si vous vous connectez avec un Adobe ID, comme illustré dans l&#39;écran ci-dessous, vous utilisez IMS.

  ![](../../integrations/using/assets/adobeID.png)

**Message d&#39;avertissement de connexion**

Le message d&#39;avertissement suivant s&#39;affiche pour les utilisateurs s&#39;ils doivent mettre à jour leur console cliente ou utiliser une ancienne version de Microsoft Internet Explorer : **Vous devez installer la dernière mise à jour sous Windows et/ou vos applications Adobe.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Si un tel avertissement s&#39;affiche, assurez-vous d&#39;installer les dernières mises à jour du système d&#39;exploitation que vous utilisez. [En savoir plus](https://helpx.adobe.com/fr/x-productkb/global/update-operating-system-and-browser.html)

Si vous n’avez pas mis à jour votre version d’Internet Explorer, le message suivant s’affiche et vous ne pouvez plus vous connecter à Adobe Campaign :

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Liens utiles

* [Mise à niveau de votre environnement](../../production/using/build-upgrade.md)
* [FAQ sur la mise à niveau des builds](../../platform/using/faq-build-upgrade.md)
* [Mise à disposition de la nouvelle console cliente auprès des utilisateurs](../../installation/using/client-console-availability-for-windows.md)
* [Installer la console cliente Campaign](../../installation/using/installing-the-client-console.md)
* [Accéder à la distribution logicielle Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr)
* [Télécharger le build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/fr/campaign.html)

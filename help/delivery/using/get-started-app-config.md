---
title: 'Paramétrage de l''application mobile dans Adobe Campaign '
description: Découvrez comment débuter avec la configuration de l'application mobile
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: ht
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: ht
source-wordcount: '273'
ht-degree: 100%

---


# Prise en main de la configuration de l&#39;application

Vous trouverez dans cette section un exemple de configuration basé sur une société qui vend des forfaits vacances en ligne. Son application mobile (Neotrips) est disponible pour ses clients en deux versions : Neotrips pour Android et Neotrips pour iOS.

Pour envoyer des notifications push dans Adobe Campaign, vous devez effectuer les opérations suivantes :

* Créez un service d&#39;information de type **[!UICONTROL Application mobile]** pour l&#39;application mobile Neotrips. Reportez-vous à [cette section pour iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service) et à [cette section pour Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Ajoutez, à ce service, les versions iOS et Android de l&#39;application.
* Créez une diffusion pour iOS et Android. [Consultez à ce sujet cette page](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Dans l&#39;onglet **[!UICONTROL Abonnements]** du service, vous trouverez la liste de tous les abonnés au service, c&#39;est-à-dire toutes les personnes ayant installé l&#39;application sur leur terminal mobile et accepté de recevoir des notifications.

## Installer le package {#installing-package-ios}

En tant que client hybride/hébergé, contactez l&#39;équipe d&#39;Assistance clientèle d&#39;Adobe pour accéder au canal de notifications push dans Campaign.

En tant que client On-Premise, vous devez effectuer les étapes d&#39;installation suivantes :

1. Accédez à l&#39;assistant d&#39;import de package depuis le menu **[!UICONTROL Outils > Avancé > Import de package...]** de la console cliente Adobe Campaign.

   ![](assets/package_ios.png)

1. Sélectionnez **[!UICONTROL Installer un package standard]**.

1. Dans la liste qui s&#39;affiche, cochez **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Cliquez sur **[!UICONTROL Suivant]** puis **[!UICONTROL Démarrer]** pour commencer l&#39;installation du package.

   Une fois les packages installés, la barre de progression indique **100 %**. De plus, les logs d&#39;installation contiennent le message suivant : **[!UICONTROL L&#39;installation des packages s&#39;est terminée avec succès]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Fermez]** la fenêtre d&#39;installation.

Une fois cette étape effectuée, vous pouvez configurer vos applications Android et iOS.
Reportez-vous aux sections suivantes :

* [Étapes de configuration pour iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Étapes de configuration pour Android](../../delivery/using/configuring-the-mobile-application-android.md)

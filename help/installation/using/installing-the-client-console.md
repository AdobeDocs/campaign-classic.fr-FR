---
title: Installation de la console
seo-title: Installation de la console
description: Installation de la console
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Installation de la console{#installing-the-client-console}

La procédure d&#39;installation de la console Adobe Campaign est décrite ci-dessous.

Avant d&#39;installer la console Adobe Campaign, consultez les prérequis listés dans la [Matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Pour installer la console Adobe Campaign, les étapes sont les suivantes :

1. Ouvrez un navigateur Web et téléchargez la console disponible à l&#39;adresse suivante :

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. Dans la fenêtre d&#39;identification, saisissez votre identifiant (login) et votre mot de passe.

   ![](assets/s_ncs_install_setup_download01.png)

   Au besoin, utilisez ceux du compte interne définis lors de la création de l&#39;instance.

1. Cliquez sur le lien **[!UICONTROL Téléchargement]** proposé dans la page d&#39;installation.
1. Téléchargez et enregistrez le fichier d&#39;installation client.
1. Exécutez le fichier téléchargé sur un poste sous Windows : l&#39;installation démarre. Le chemin d&#39;installation par défaut de la console cliente est **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, où X correspond à 6 ou 7, selon votre version d&#39;Adobe Campaign.
1. Une fois le programme d&#39;installation terminé, lancez la console depuis le menu **[!UICONTROL Démarrer]** de Windows (dans le groupe de programmes **Adobe Campaign**).

>[!NOTE]
>
>On Windows, you can launch the **nlclient.exe** file directly from the `[INSTALL]/bin` directory on a Windows server, where `[INSTALL]` is the access path for the Adobe Campaign installation folder.\
>Pour créer une connexion, reportez-vous à la section [Création d’une instance et connexion](../../installation/using/creating-an-instance-and-logging-on.md).


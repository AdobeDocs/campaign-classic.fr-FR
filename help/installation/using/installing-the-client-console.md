---
solution: Campaign Classic
product: campaign
title: Installation de la console
description: Découvrez comment installer la console cliente
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 92%

---


# Installation de la console cliente Campaign{#installing-the-client-console}

La console cliente Campaign est un client riche qui vous permet de vous connecter à votre ou vos serveur(s) applicatif(s) Campaign.

Avant de commencer, vous devez vérifier la [matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html) Campaign, obtenir l’URL de votre serveur Campaign et les informations d’identification de l’utilisateur.

>[!CAUTION]
>
>La console cliente et le serveur applicatif Campaign doivent s’exécuter sur la même version de produit. Adobe recommande également d’utiliser la même version de produit.

![](assets/do-not-localize/how-to-video.png) Découvrez comment installer et configurer le client Adobe Campaign en [vidéo](#video)

## Téléchargement de la console{#download-the-client-console}

Pour télécharger et installer la console cliente Adobe Campaign, procédez comme suit :

1. Ouvrez un navigateur web et téléchargez la console disponible à l’adresse suivante :

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Dans la fenêtre d’identification, saisissez votre identifiant (login) et votre mot de passe.

   ![](assets/s_ncs_install_setup_download01.png)

   Au besoin, utilisez ceux du compte interne définis lors de la création de l’instance.

1. Cliquez sur le lien **[!UICONTROL Téléchargement]** proposé dans la page d’installation.
1. Téléchargez et enregistrez le fichier d’installation client.
1. Exécutez le fichier téléchargé sur un poste sous Windows : l’installation démarre. Le chemin d’installation par défaut de la console cliente est **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, où X correspond à 6 ou 7, selon votre version d’Adobe Campaign.

>[!NOTE]
>
>Sous Windows, vous pouvez lancer directement le fichier **nlclient.exe** présent dans le répertoire `[INSTALL]/bin` à partir du serveur Windows, où `[INSTALL]` est le chemin d’accès au répertoire d’installation Adobe Campaign.

## Création de la connexion{#create-the-connection}

Une fois la console cliente installée, procédez comme suit pour créer la connexion au serveur applicatif :

1. Démarrez la console à partir du menu **[!UICONTROL Démarrer]** de Windows, dans le groupe de programmes **Adobe Campaign**.

1. Cliquez sur le lien situé dans le coin supérieur droit des champs d’informations d’identification pour accéder à la fenêtre de configuration de la connexion.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Cliquez sur le menu **[!UICONTROL Ajouter > Connexion]** et saisissez le libellé et l’URL du serveur applicatif Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Définissez une connexion vers votre serveur applicatif Adobe Campaign à partir d’une URL. Utilisez soit un DNS ou un alias de la machine, soit votre adresse IP.

   Par exemple, vous pouvez utiliser une URL de type [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Si Adobe IMS est configuré pour votre organisation, cochez l’option **[!UICONTROL Se connecter avec un Adobe ID.]**

1. Cliquez sur **[!UICONTROL OK]** pour enregistrer vos paramètres.

Vous pouvez ajouter autant de connexions que nécessaire pour vous connecter, par exemple, à vos environnements de test, d’évaluation et de production.

>[!NOTE]
>
>Le bouton **[!UICONTROL Ajouter]** permet de créer des **[!UICONTROL dossiers]** dans lesquels vous pourrez classer vos différentes connexions par des opérations de glisser-déposer.

## Connexion à Adobe Campaign

Pour vous connecter à une instance existante, procédez comme suit :

1. Démarrez la console à partir du menu **[!UICONTROL Démarrer]** de Windows, dans le groupe de programmes **Adobe Campaign**.

1. Cliquez sur le lien situé dans le coin supérieur droit des champs d’informations d’identification pour accéder à la fenêtre de configuration de la connexion.

1. Sélectionnez l’instance de Campaign à laquelle vous devez vous connecter.

1. Cliquez sur **[!UICONTROL Ok]**

1. Entrez vos informations de connexion utilisateur et cliquez sur **[!UICONTROL Se connecter]**.

**Rubriques connexes :**

* [Création d’une instance et connexion](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

## Tutoriel vidéo

Cette vidéo explique comment installer et configurer le client Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

D&#39;autres vidéos pratiques des Campaign Classic sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).

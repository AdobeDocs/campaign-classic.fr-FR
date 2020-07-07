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
source-git-commit: 005be008585f75a87fb0029a8a88578cfde5ce51
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 45%

---


# Installing Campaign client console{#installing-the-client-console}

La console Client Campaign est un client riche qui vous permet de vous connecter à vos serveurs d’applications Campaign.

Avant de commencer, vous devez vérifier la matrice [de](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)compatibilité de Campaign, obtenir l’URL de votre serveur Campaign et les informations d’identification de l’utilisateur.

>[!CAUTION]
>
>La console Client Campaign et le serveur d’applications Campaign doivent s’exécuter sur la même version de produit. Adobe recommande également d’utiliser la même version de produit.

## Téléchargement de la console{#download-the-client-console}

Pour télécharger et installer la console client Adobe Campaign, procédez comme suit :

1. Ouvrez un navigateur Web et téléchargez la console à l’adresse suivante :

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. Dans la fenêtre d&#39;identification, saisissez votre identifiant (login) et votre mot de passe.

   ![](assets/s_ncs_install_setup_download01.png)

   Au besoin, utilisez ceux du compte interne définis lors de la création de l&#39;instance.

1. Cliquez sur le lien **[!UICONTROL Téléchargement]** proposé dans la page d&#39;installation.
1. Téléchargez et enregistrez le fichier d&#39;installation client.
1. Exécutez le fichier téléchargé sur un poste sous Windows : l&#39;installation démarre. Le chemin d&#39;installation par défaut de la console cliente est **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, où X correspond à 6 ou 7, selon votre version d&#39;Adobe Campaign.

>[!NOTE]
>
>Sous Windows, vous pouvez lancer directement le fichier **nlclient.exe** présent dans le répertoire `[INSTALL]/bin` à partir du serveur Windows, où `[INSTALL]` est le chemin d’accès au répertoire d’installation Adobe Campaign.

## Créer la connexion{#create-the-connection}

Une fois la console client installée, procédez comme suit pour créer la connexion au serveur d’applications :

1. Début la console à partir du menu **[!UICONTROL Début]** Windows, dans le groupe de programmes **Adobe Campaign** .

1. Cliquez sur le lien situé dans le coin supérieur droit des champs d’informations d’identification pour accéder à la fenêtre de configuration de la connexion.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Cliquez sur le menu **[!UICONTROL Ajouter > Connexion]** et saisissez le libellé et l&#39;URL du serveur applicatif Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Définissez une connexion vers votre serveur applicatif Adobe Campaign à partir d&#39;une URL. Utilisez soit un DNS ou un alias de la machine, soit votre adresse IP.

   Par exemple, vous pouvez utiliser une URL de type [`https://<machine>.<domain>.com`](https://machine).

1. Si Adobe IMS est configuré pour votre organisation, cochez l’option **[!UICONTROL Se connecter avec un Adobe ID.]**

1. Cliquez sur **[!UICONTROL OK]** pour enregistrer vos paramètres.

Vous pouvez ajouter autant de connexions que nécessaire pour vous connecter à vos environnements de test, d’évaluation et de production, par exemple.

>[!NOTE]
>
>Le bouton **[!UICONTROL Ajouter]** permet de créer des **[!UICONTROL dossiers]** dans lesquels vous pourrez classer vos différentes connexions par des opérations de glisser-déplacer.


## Connexion à Campaign

Pour vous connecter à une instance existante, procédez comme suit :

1. Début la console à partir du menu **[!UICONTROL Début]** Windows, dans le groupe de programmes **Adobe Campaign** .

1. Cliquez sur le lien situé dans le coin supérieur droit des champs d’informations d’identification pour accéder à la fenêtre de configuration de la connexion.

1. Sélectionnez l’instance Campaign à laquelle vous devez vous connecter.

1. Cliquez sur **[!UICONTROL Ok]**

1. Entrez vos informations de connexion utilisateur et cliquez sur **[!UICONTROL Connexion.]**

**Rubriques connexes :**

* [Création et connexion à une instance](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matrice de compatibilité](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)
* [Installation et configuration du client](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) Adobe Campaign (vidéo)

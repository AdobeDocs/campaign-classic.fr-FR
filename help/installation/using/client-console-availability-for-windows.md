---
product: campaign
title: Disponibilité de la console cliente pour Windows
description: Disponibilité de la console cliente pour Windows
feature: Installation, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# Disponibilité de la console cliente pour Windows{#client-console-availability-for-windows}



Afin de permettre aux utilisateurs Adobe Campaign de se connecter à l’instance que vous avez créée et paramétrée, ils doivent utiliser la console cliente.

## Mise à disposition de la console client

Lorsque l’ordinateur utilisé pour démarrer un serveur d’application Adobe Campaign (**nlserver web**) reçoit les connexions des utilisateurs à partir de la console client, vous pouvez le configurer afin de mettre à disposition le programme d’installation de la console Adobe Campaign à travers une interface HTML. Chaque fois qu’une nouvelle version de la console client est disponible, les utilisateurs sont invités à la télécharger lors du lancement de leur console client.

Pour ce faire, procédez comme suit :

1. Sélectionnez le package qui contient le programme d’installation de la console.

   Ce fichier s’appelle `setup-client-7.X.XXXX.exe`, où `X` est la sous-version d’Adobe Campaign et `XXXX` est le numéro de la build.

1. Copiez et collez ce package dans le dossier d’installation Adobe Campaign (sur le serveur marketing pour les installations hybrides), sous **/datakit/nl/eng/jsp**.
1. Démarrez le serveur Adobe Campaign.

Les utilisateurs Campaign peuvent alors télécharger le programme d’installation de la console depuis un navigateur web, via l’URL suivante :

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Cette page nécessite un login et un mot de passe définis dans l’application.

Découvrez comment installer la console [dans cette section](../../installation/using/installing-the-client-console.md).

## Proposez aux utilisateurs finaux de mettre à niveau leur console client.

Une fois la console mise à disposition dans le dossier du serveur Campaign, les utilisateurs sont invités à télécharger la dernière version de la console client dans une fenêtre d’invite dédiée. Adobe recommande de ne pas sélectionner l’option **[!UICONTROL Ne plus poser cette question]** pour que tous les utilisateurs soient informés de la disponibilité d’une nouvelle version de la console.

Si vous sélectionnez cette option et choisissez de ne pas télécharger la dernière version, aucun autre utilisateur ne sera informé des nouvelles versions disponibles.

Si vous avez sélectionné cette option, vous pouvez réinitialiser cette invite. Seuls les administrateurs système qui maîtrisent l’édition du Registre Windows doivent apporter ces modifications :

1. Ouvrez l&#39;Editeur du Registre à l&#39;aide de la commande **regedit** dans le menu **[!UICONTROL Démarrer]** > Exécuter.
1. Recherchez le nœud et développez-le.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Supprimez l&#39;entrée **confAdvisedUpgrade** et fermez l&#39;Editeur du Registre.

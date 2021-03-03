---
solution: Campaign Classic
product: campaign
title: Disponibilité de la console cliente pour Windows
description: Disponibilité de la console cliente pour Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 49%

---


# Disponibilité de la console cliente pour Windows{#client-console-availability-for-windows}

Afin de permettre aux utilisateurs Adobe Campaign de se connecter à l&#39;instance que vous avez créée et paramétrée, ils doivent utiliser la console cliente.

## Mise à disposition de la console client

Lorsque la machine utilisée pour lancer un serveur applicatif Adobe Campaign (**nlserver web**) reçoit les connexions des utilisateurs par la console cliente, vous pouvez la configurer afin de mettre à disposition le programme d&#39;installation (setup) du client riche Adobe Campaign à travers une interface HTML. Chaque fois qu’une nouvelle version de la console client est disponible, les utilisateurs sont invités à la télécharger lors du lancement de leur console client.

Pour cela, vous devez :

1. Sélectionnez le package contenant le programme d&#39;installation de la console.

   Ce fichier est appelé `setup-client-7.X.XXXX.exe` pour v7 ou `setup-client-6.X.XXXX.exe` pour v6.1, où `X` correspond à la sous-version d’Adobe Campaign et `XXXX` au numéro de build.

1. Copiez et collez ce package dans le dossier d’installation Adobe Campaign (sur le serveur marketing pour les installations hybrides), sous **/datakit/nl/eng/jsp**.
1. Début du serveur Adobe Campaign.

Les utilisateurs de Campaign peuvent alors télécharger le programme d’installation de la console via un navigateur Web à l’aide de l’URL suivante :

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Cette page nécessite des identifiant/mot de passe définis dans l&#39;application.

Découvrez comment installer la console [dans cette section](../../installation/using/installing-the-client-console.md).

## Proposer aux utilisateurs finaux de mettre à niveau leur console client

Une fois la console disponible dans le dossier du serveur Campaign, les utilisateurs sont invités à télécharger la dernière version de la console client dans une fenêtre d’invite dédiée. L&#39;Adobe recommande de ne pas sélectionner l&#39;option **[!UICONTROL Ne plus poser cette question]** pour s&#39;assurer que tous les utilisateurs sont avertis lorsqu&#39;une nouvelle version de la console est disponible.

Si vous sélectionnez cette option et choisissez de ne pas télécharger la dernière version, aucun autre utilisateur ne sera informé des nouvelles versions disponibles.

Au cas où l’option était sélectionnée, vous pouvez réinitialiser cette invite. Seuls les administrateurs système à l&#39;aise avec la modification du registre Windows doivent effectuer les modifications suivantes :

1. Ouvrez l&#39;Editeur du Registre à l&#39;aide de la commande **regedit** dans le menu **[!UICONTROL Démarrer]** > Exécuter.
1. Recherchez le nœud et développez-le.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Supprimez l&#39;entrée **confAdvisedUpgrade** et fermez l&#39;Editeur du Registre.


---
title: Disponibilité de la console client pour Windows
seo-title: Disponibilité de la console client pour Windows
description: Disponibilité de la console client pour Windows
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Disponibilité de la console client pour Windows{#client-console-availability-for-windows}

Afin de permettre aux utilisateurs Adobe Campaign de se connecter à l&#39;instance que vous avez créée et paramétrée, ils doivent utiliser la console cliente.

Lorsque la machine utilisée pour lancer un serveur applicatif Adobe Campaign (**nlserver web**) reçoit les connexions des utilisateurs par la console cliente, vous pouvez la configurer afin de mettre à disposition le programme d&#39;installation (setup) du client riche Adobe Campaign à travers une interface HTML.

Pour cela, vous devez :

1. Récupérer le package qui contient le programme d&#39;installation des consoles.

   Ce fichier est appelé `setup-client-7.X.XXXX.exe` pour v7 ou `setup-client-6.X.XXXX.exe` pour v6.1, où `X` correspond à la sous-version d’Adobe Campaign et `XXXX` au numéro de version.

1. Copy and paste this package into the Adobe Campaign installation folder, under **/datakit/nl/eng/jsp**.
1. Démarrer le serveur Adobe Campaign.

Les utilisateurs finaux peuvent alors télécharger le programme d&#39;installation de la console depuis un navigateur Web, via l&#39;URL suivante :

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Cette page nécessite des identifiant/mot de passe définis dans l&#39;application.

Pour télécharger et installer la console, voir [Installation de la console](../../installation/using/installing-the-client-console.md)client.

Dès qu&#39;une nouvelle version de la console cliente est disponible, vous êtes invité à la télécharger.

>[!NOTE]
>
>Dans l&#39;invite qui apparaît, Adobe recommande de conserver l&#39;option **[!UICONTROL Ne plus poser cette question]** non sélectionnée pour que tous les utilisateurs soient informés de la disponibilité d&#39;une nouvelle version de la console.\
>Si vous sélectionnez cette option et choisissez de ne pas télécharger la dernière version, aucun autre utilisateur ne sera informé des nouvelles versions disponibles.

Pour réinitialiser cette invite, procédez comme suit (seuls les administrateurs système qui maîtrisent l&#39;édition de la base du registre doivent apporter ces modifications) :

1. Ouvrez l&#39;Editeur du Registre à l&#39;aide de la commande **regedit** dans le menu **[!UICONTROL Démarrer]** > Exécuter.
1. Recherchez le noeud et développez-le.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Supprimez l&#39;entrée **confAdvisedUpgrade** et fermez l&#39;Editeur du Registre.


---
title: Utiliser le serveur SFTP
description: Découvrez les bonnes pratiques et la résolution des problèmes liés au serveur SFTP.
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
translation-type: ht
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: ht
source-wordcount: '1003'
ht-degree: 100%

---


# Bonnes pratiques et résolution des problèmes liés au serveur SFTP {#sftp-server-usage}

## Bonnes pratiques d&#39;utilisation du serveur SFTP {#sftp-server-best-practices}

Lors de la gestion de fichiers et de données à des fins d&#39;ETL, les fichiers sont stockés sur un serveur SFTP hébergé fourni par Adobe. Ce serveur SFTP est conçu pour être un espace de stockage temporaire pour lequel vous pouvez contrôler la conservation et la suppression des fichiers.

Lorsqu&#39;il n&#39;est pas correctement utilisé ou surveillé, cet espace peut rapidement remplir l&#39;espace physique disponible sur le serveur et entraîner la troncature des fichiers lors des téléchargements suivants. Lorsque l&#39;espace est saturé, une purge automatique peut être déclenchée et effacer les fichiers plus anciens de l&#39;espace de stockage SFTP.

Pour éviter ces problèmes, Adobe recommande de suivre les bonnes pratiques ci-après.

>[!NOTE]
>
>Si votre instance est hébergée sur AWS, vous pouvez surveiller le stockage de votre serveur SFTP au moyen du [Panneau de configuration](https://docs.adobe.com/content/help/fr-FR/control-panel/using/sftp-management/sftp-storage-management.html) Campaign Classic.
>
>Pour vérifier si votre instance est hébergée sur AWS, suivez les étapes présentées dans [cette section](https://docs.adobe.com/content/help/fr-FR/control-panel/using/faq.html#ims-org-id) .

* La taille du serveur varie en fonction de votre licence. Dans tous les cas, conservez le minimum de données possible et uniquement pendant le temps nécessaire (15 jours est la durée maximale).
* Utilisez l’authentification par clé plutôt que par mot de passe pour éviter l’expiration du mot de passe (la période de validité des mots de passe est de 90 jours). De plus, l’authentification par clé permet de générer plusieurs clés, par exemple lors de la gestion de plusieurs entités. À l’inverse, l’authentification par mot de passe nécessite le partage du mot de passe avec toutes les entités que vous gérez.

   Le format de clé pris en charge est SSH-2 RSA 2048. Les clés peuvent être générées avec des outils tels que PyTTY (Windows) ou ssh-keygen (Unix). Vous devrez fournir la clé publique à l’équipe de support Adobe via un [ticket de support](https://support.neolane.net) pour qu’elle soit téléchargée sur le serveur Campaign.

* Utilisez des workflows pour supprimer correctement les données (gérez la conservation depuis les workflows utilisant les données).
* Utilisez des batchs dans les téléchargements SFTP ainsi que dans les workflows.
* Gérez les erreurs/exceptions.
* Connectez-vous de temps à autre au SFTP afin de vérifier directement ce qui s’y trouve.
* Gardez à l’esprit que la gestion des disques SFTP relève principalement de votre responsabilité.
* Par défaut, tous les dossiers que vous créez sont en lecture/écriture pour votre identifiant uniquement. Lorsque vous créez des dossiers auxquels Campaign doit accéder, veillez à les configurer avec des droits en lecture/écriture pour l&#39;ensemble du groupe. Sinon, les workflows peuvent ne pas pouvoir créer/supprimer des fichiers, car ils sont exécutés sous un identifiant différent au sein du même groupe pour des raisons de sécurité.
* Les adresses IP publiques à partir desquelles vous tentez d&#39;établir la connexion SFTP doivent être ajoutées à la liste autorisée sur l&#39;instance Campaign. Vous pouvez ajouter des adresses IP à la liste autorisée par le biais d&#39;un [ticket de support](https://support.neolane.net).

>[!CAUTION]
>
>Si vous utilisez votre propre serveur SFTP, suivez autant que possible les recommandations mentionnées ci-dessus.

## Problèmes de connexion liés au serveur SFTP hébergé par Adobe {#sftp-server-troubleshooting}

La section ci-après indique les informations à vérifier et à fournir à l’équipe de support Adobe via un [ticket de support](https://support.neolane.net) lorsque vous rencontrez des problèmes liés aux serveurs SFTP hébergés Adobe.

1. Vérifiez que votre instance est en cours d’exécution. Pour cela, ouvrez votre navigateur, puis effectuez un appel **[!UICONTROL GET]** sur le point d’entrée **[!UICONTROL /r/test]** de l’instance :

   ```
   https://instanceUrl/r/test
   ```

   Si l&#39;instance est en cours d&#39;exécution, vous devez obtenir ce type de réponse :

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   Dans tous les cas, indiquez la réponse de la commande dans le ticket de support.

1. Vérifiez si le port 22 sortant est ouvert sur le site à partir duquel vous essayez d&#39;initialiser la connexion SFTP. Pour cela, utilisez la commande suivante :

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >L&#39;outil Netcat permet de gérer facilement les connexions réseau sous différents systèmes d&#39;exploitation (voir [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Si le port n’est pas ouvert, veillez à ouvrir les connexions sortantes de votre côté, puis réessayez. Si vous rencontrez toujours des problèmes de connexion, indiquez la sortie de la commande à l’équipe de support Adobe.

1. Vérifiez que l&#39;adresse IP publique à partir de laquelle vous essayez d&#39;établir la connexion SFTP est celle que vous avez fournie au support Adobe pour la liste autorisée.
1. Si vous utilisez une authentification par mot de passe, votre mot de passe peut avoir expiré (les mots de passe ont une période de validité de 90 jours). Nous vous recommandons donc vivement d’utiliser une authentification par clé (voir [Bonnes pratiques d&#39;utilisation du serveur SFTP](#sftp-server-best-practices)).
1. Si vous utilisez une authentification par clé, vérifiez que la clé que vous utilisez est la même que celle fournie pour la prise en charge de la configuration de l’instance.
1. Si vous utilisez FileZilla ou un outil FTP équivalent, fournissez les détails des logs de connexion dans le ticket de support.

## Erreur « Impossible de résoudre le nom d’hôte »

Cette section fournit des informations sur les vérifications et les actions à effectuer lors de l’affichage de l’erreur « Impossible de résoudre le nom d’hôte » après la connexion de Campaign Classic au serveur FTP.

Le journal des workflows affiche les logs suivants :

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Cette erreur se produit lorsque vous tentez de connecter le serveur FTP à partir d’un workflow et de télécharger les fichiers à partir du serveur, alors que vous pouvez toujours vous connecter via FTP à l’aide de FileZilla ou WinSCP.

Cette erreur indique que le nom de domaine du serveur FTP n&#39;a pas pu être résolu correctement. Pour résoudre le problème, procédez comme suit :

1. Résolution des problèmes de **configuration du serveur DNS** :

   1. Vérifiez si le nom du serveur a été ajouté au serveur DNS local.
   1. Si oui, exécutez la commande suivante sur le serveur Adobe Campaign pour obtenir l’adresse IP :

      `nslookup <server domain name>`

      Cela confirme que le serveur FTP fonctionne et est accessible à partir du serveur applicatif Adobe Campaign.

1. Résolution des problèmes liés aux **logs de session** :

   1. Dans le workflow, double-cliquez sur l&#39;activité [Transfert de fichier](../../workflow/using/file-transfer.md).
   1. Accédez à l’onglet **[!UICONTROL Transfert de fichier]**, puis cliquez sur **[!UICONTROL Paramètres avancés]**.
   1. Cochez l’option **[!UICONTROL Afficher les logs de la session]**.

      ![](assets/sftp-error-display-logs.png)

   1. Accédez au workflow Audit et vérifiez si les logs affichent l’erreur « Impossible de résoudre le nom d’hôte ».

1. Si le serveur SFTP est hébergé par Adobe, vérifiez si l&#39;adresse IP est ajoutée à la liste autorisée en contactant l&#39;Assistance clientèle.

   Sinon, validez :

   * Le mot de passe ne contient pas le caractère « @ ». La connexion a échoué si le mot de passe contient le caractère « @ ».
   * Il n’existe aucun problème de pare-feu qui peut gêner la communication entre le serveur applicatif Adobe Campaign et le serveur SFTP.
   * Exécutez les commandes tracert et telnet du serveur de campagne vers le serveur sftp pour vérifier s’il y a des problèmes de connexion.
   * Il n&#39;y a pas de problème de protocole de communication.
   * Le port est ouvert.

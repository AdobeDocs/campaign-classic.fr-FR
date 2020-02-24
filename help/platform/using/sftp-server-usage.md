---
title: Utilisation du serveur SFTP
seo-title: Utilisation du serveur SFTP
description: Utilisation du serveur SFTP
seo-description: null
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1e8492d8e91d679ac13da875974e27d0f7791dc3

---


# Utilisation du serveur SFTP{#sftp-server-usage}

## Bonnes pratiques d&#39;utilisation du serveur SFTP {#sftp-server-best-practices}

Lors de la gestion de fichiers et de données à des fins d&#39;ETL, les fichiers sont stockés sur un serveur SFTP hébergé fourni par Adobe. Ce serveur SFTP est conçu pour être un espace de stockage temporaire pour lequel vous pouvez contrôler la conservation et la suppression des fichiers.

Lorsqu&#39;il n&#39;est pas correctement utilisé ou surveillé, cet espace peut rapidement remplir l&#39;espace physique disponible sur le serveur et entraîner la troncature des fichiers lors des téléchargements suivants. Lorsque l&#39;espace est saturé, une purge automatique peut être déclenchée et effacer les fichiers plus anciens de l&#39;espace de stockage SFTP.

Pour éviter de tels problèmes, Adobe recommande de suivre les bonnes pratiques ci-dessous.

>[!NOTE]
>
>Si votre instance est hébergée sur AWS, vous pouvez surveiller le stockage de votre serveur SFTP au moyen du [Panneau de configuration](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html) Campaign Classic.
>
>Pour vérifier si votre instance est hébergée sur AWS, suivez les étapes présentées dans [cette section](https://docs.adobe.com/content/help/en/control-panel/using/faq.html#ims-org-id) .

* La taille du serveur varie en fonction de votre licence. Dans tous les cas, conservez le minimum de données possible et uniquement pendant le temps nécessaire (15 jours est la durée maximale).
* Utilisez l’authentification par clé plutôt que par mot de passe pour éviter l’expiration du mot de passe (la période de validité des mots de passe est de 90 jours). De plus, l’authentification par clé permet de générer plusieurs clés, par exemple lors de la gestion de plusieurs entités. À l’inverse, l’authentification par mot de passe nécessite le partage du mot de passe avec toutes les entités que vous gérez.

   Le format de clé pris en charge est SSH-2 RSA 2048. Les clés peuvent être générées avec des outils tels que PyTTY (Windows) ou ssh-keygen (Unix). Vous devrez fournir la clé publique à l’équipe de support Adobe via un [ticket de support](https://support.neolane.net) pour qu’elle soit téléchargée sur le serveur Campaign.

* Utilisez des workflows pour supprimer correctement les données (gérez la conservation depuis les workflows utilisant les données).
* Utilisez des batchs dans les téléchargements SFTP ainsi que dans les workflows.
* Gérez les erreurs/exceptions.
* Connectez-vous de temps à autre au SFTP afin de vérifier directement ce qui s&#39;y trouve.
* Gardez à l&#39;esprit que la gestion des disques SFTP relève principalement de votre responsabilité.
* Par défaut, tous les dossiers que vous créez sont en lecture/écriture pour votre identifiant uniquement. Lorsque vous créez des dossiers auxquels Campaign doit accéder, veillez à les configurer avec des droits en lecture/écriture pour l&#39;ensemble du groupe. Sinon, les workflows peuvent ne pas pouvoir créer/supprimer des fichiers, car ils sont exécutés sous un identifiant différent au sein du même groupe pour des raisons de sécurité.
* Les adresses IP publiques à partir desquelles vous essayez d&#39;initier la connexion SFTP doivent être whitelistées sur l&#39;instance Campaign. Le whitelistage des adresses IP peut être demandé via un [ticket de support](https://support.neolane.net).

>[!CAUTION]
>
>Si vous utilisez votre propre serveur SFTP, suivez autant que possible les recommandations mentionnées ci-dessus.

## Résolution des problèmes liés au serveur SFTP {#sftp-server-troubleshooting}

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

1. Vérifiez que l’adresse IP publique à partir de laquelle vous essayez d’établir la connexion SFTP est celle que vous avez fournie au support Adobe pour le whitelistage.
1. Si vous utilisez une authentification par mot de passe, votre mot de passe peut avoir expiré (les mots de passe ont une période de validité de 90 jours). Nous vous recommandons donc vivement d’utiliser une authentification par clé (voir les bonnes pratiques [du serveur](#sftp-server-best-practices)SFTP).
1. Si vous utilisez une authentification par clé, vérifiez que la clé que vous utilisez est la même que celle fournie pour la prise en charge de la configuration de l’instance.
1. Si vous utilisez FileZilla ou un outil FTP équivalent, fournissez les détails des logs de connexion dans le ticket de support.


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
translation-type: tm+mt
source-git-commit: ebec481d5a018d06e47c782627e9a9064cb0dd64
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 77%

---


# Bonnes pratiques et résolution des problèmes liés au serveur SFTP {#sftp-server-usage}

## Recommandations globales du serveur SFTP {#global-recommendations}

Lors de la gestion de fichiers et de données à des fins d’ETL, ces fichiers sont stockés sur un serveur SFTP hébergé, fourni par Adobe. Veillez à suivre les recommandations ci-dessous lors de l’utilisation de serveurs SFTP.

* Utilisez l’authentification par clé plutôt que par mot de passe pour éviter l’expiration du mot de passe (la période de validité des mots de passe est de 90 jours). De plus, l’authentification par clé permet de générer plusieurs clés, par exemple lors de la gestion de plusieurs entités. À l’inverse, l’authentification par mot de passe nécessite le partage du mot de passe avec toutes les entités que vous gérez.

   Le format de clé pris en charge est SSH-2 RSA 2048. Keys can be generated with tools like PyTTY (Windows), or ssh-keygen (Unix).You will have to provide the public key to Adobe Support team via [Adobe Customer Care](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) to have it uploaded on the Campaign server.

* Utilisez des batchs dans les téléchargements SFTP ainsi que dans les workflows.

* Gérez les erreurs/exceptions.

* Par défaut, tous les dossiers que vous créez sont en lecture/écriture pour votre identifiant uniquement. Lorsque vous créez des dossiers auxquels Campaign doit accéder, veillez à les configurer avec des droits en lecture/écriture pour l&#39;ensemble du groupe. Sinon, les workflows peuvent ne pas pouvoir créer/supprimer des fichiers, car ils sont exécutés sous un identifiant différent au sein du même groupe pour des raisons de sécurité.

* Les adresses IP publiques à partir desquelles vous tentez d&#39;établir la connexion SFTP doivent être ajoutées à la liste autorisée sur l&#39;instance Campaign. L’Ajoute des adresses IP à la liste autorisée peut être demandée par l’intermédiaire du service à la clientèle [](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Adobe.

## Meilleures pratiques d’utilisation des bases de données {#sftp-server-best-practices}

Les serveurs SFTP sont conçus pour être des espaces d’enregistrement temporaires sur lesquels vous pouvez contrôler la rétention et la suppression des fichiers.

Lorsqu’ils ne sont pas correctement utilisés ou surveillés, ces espaces peuvent rapidement remplir l’espace physique disponible sur le serveur et entraîner la troncation des fichiers lors des téléchargements suivants. Une fois l’espace saturé, la purge automatique peut déclencher et effacer les fichiers les plus anciens de l’enregistrement SFTP.

Pour éviter ces problèmes, Adobe recommande de suivre les bonnes pratiques ci-après.

>[!NOTE]
>
>Si votre instance est hébergée sur AWS, vous pouvez surveiller le stockage de votre serveur SFTP au moyen du [Panneau de configuration](https://docs.adobe.com/content/help/fr-FR/control-panel/using/sftp-management/sftp-storage-management.html) Campaign Classic.
>
>Pour vérifier si votre instance est hébergée sur AWS, suivez les étapes présentées dans [cette section](https://docs.adobe.com/content/help/fr-FR/control-panel/using/faq.html#ims-org-id) .

* La taille du serveur varie en fonction de votre licence. Dans tous les cas, conservez le minimum de données possible et uniquement pendant le temps nécessaire (15 jours est la durée maximale).

* Utilisez des workflows pour supprimer correctement les données (gérez la conservation depuis les workflows utilisant les données).

* Connectez-vous de temps à autre au SFTP afin de vérifier directement ce qui s’y trouve.

* Gardez à l’esprit que la gestion des disques SFTP relève principalement de votre responsabilité.

## External SFTP server usage {#external-SFTP-server}

Si vous utilisez votre propre serveur SFTP, veillez à suivre autant que possible les recommandations ci-dessus.

En outre, lors de la spécification en Campaign Classic d’un chemin d’accès à un serveur SFTP externe, la syntaxe du chemin d’accès diffère selon le système d’exploitation du serveur SFTP :

* Si votre serveur SFTP se trouve sous **Windows**, utilisez toujours un chemin relatif.
* Si votre serveur STP est sur **Linux**, utilisez toujours un chemin relatif à la maison (commençant par &quot;~/&quot;) ou un chemin absolu (commençant par &quot;/&quot;).

## Problèmes de connexion liés au serveur SFTP hébergé par Adobe {#sftp-server-troubleshooting}

The section below lists the information to check and provide to the Adobe Support team via [Adobe Customer Care](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) when encountering connection issues with Adobe hosted SFTP servers.

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

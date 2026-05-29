---
product: campaign
title: Utilisation du serveur SFTP
description: Découvrez les bonnes pratiques et la résolution des problèmes liés au serveur SFTP.
feature: Troubleshooting
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
TQID: https://experienceleague.adobe.com/RrVBjDmV2i349u1NCfjtDApsuAIEOVwbxalPKnKETI4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
feature_v2: id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1178
ht-degree: 84%

---

# Bonnes pratiques et résolution des problèmes liés au serveur SFTP {#sftp-server-usage}

## Recommandations globales relatives au serveur SFTP {#global-recommendations}

Lors de la gestion de fichiers et de données à des fins d’ETL, ces fichiers sont stockés sur un serveur SFTP hébergé, fourni par Adobe. Veillez à suivre les recommandations ci-dessous lors de l’utilisation de serveurs SFTP.

* Utilisez l’authentification par clé plutôt que l’authentification par mot de passe, afin d’éviter l’expiration du mot de passe (les mots de passe ont une période de validité de 90 jours). De plus, l’authentification par clé permet de générer plusieurs clés, par exemple lors de la gestion de plusieurs entités. Au contraire, l’authentification par mot de passe nécessite de partager le mot de passe avec toutes les entités que vous gérez.

  Le format de clé pris en charge est SSH-2 RSA 2048. L’outil de génération de clés SSH est PuTTYgen pour Windows et ssh-keygen pour Linux. Vous pouvez charger des clés SSH publiques via le panneau de contrôle de Campaign. [En savoir plus](https://experienceleague.adobe.com/fr/docs/control-panel/using/sftp-management/key-management){target="_blank"}

* Utilisez des batchs dans les téléchargements SFTP ainsi que dans les workflows.

* Gérez les erreurs/exceptions.

* Par défaut, tous les dossiers que vous créez sont en mode lecture/écriture pour votre identifiant uniquement. Lors de la création de dossiers auxquels Campaign doit accéder, veillez à les configurer avec des droits en lecture/écriture pour l&#39;ensemble du groupe. Dans le cas contraire, il se peut que les workflows ne puissent pas créer/supprimer de fichiers, car ils sont exécutés avec un identifiant différent au sein du même groupe, et ce pour des raisons de sécurité.

* Les adresses IP publiques à partir desquelles vous tentez d&#39;établir la connexion SFTP doivent être ajoutées à la liste autorisée sur l&#39;instance Campaign. Les adresses IP publiques peuvent être ajoutées via le panneau de contrôle. [En savoir plus](https://experienceleague.adobe.com/fr/docs/control-panel/using/sftp-management/ip-range-allow-listing){target="_blank"}

## Bonnes pratiques d’utilisation du stockage SFTP {#sftp-server-best-practices}

Les serveurs SFTP sont conçus en tant qu’espaces de stockage temporaire sur lequel vous pouvez contrôler la conservation et la suppression des fichiers.

Lorsqu’ils ne sont pas correctement utilisés ou surveillés, ces espaces peuvent rapidement remplir l’espace physique disponible sur le serveur et entraîner la troncation des fichiers lors des téléchargements suivants. Dans les serveurs SFTP hébergés par Adobe, les fichiers sont compressés si le stockage SFTP atteint un seuil de 80 %. Le processus est automatique et déclenché par le système de surveillance Adobe.

Pour éviter ces problèmes, Adobe recommande de suivre les bonnes pratiques ci-dessous.

>[!NOTE]
>
>* Vous pouvez surveiller le stockage de votre serveur SFTP avec le [Panneau de contrôle](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html?lang=fr){target="_blank"} de Campaign Classic.
>
>* Le Panneau de contrôle est accessible à tous les utilisateurs administrateurs. Les étapes permettant d&#39;octroyer un accès administrateur à un utilisateur sont présentées sur [cette page](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=fr#discover-control-panel){target="_blank"}.
>
>* Notez que votre instance doit être mise à niveau avec la [dernière build GA](../../rn/using/rn-overview.md). Découvrez comment vérifier votre version dans [cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version){target="_blank"}.

* Les fonctionnalités de taille du serveur varient en fonction de votre licence. Dans tous les cas, conservez les données minimales possibles et ne conservez les données que le temps nécessaire (15 jours est le délai maximum).

* Utilisez des workflows pour supprimer correctement les données (gérez la conservation depuis les workflows utilisant les données).

* Connectez-vous de temps à autre au SFTP afin de vérifier directement ce qui s’y trouve.

* Gardez à l’esprit que la gestion des disques SFTP relève principalement de votre responsabilité.

## Utilisation d’un serveur SFTP externe {#external-SFTP-server}

Si vous utilisez votre propre serveur SFTP, suivez autant que possible les recommandations mentionnées ci-dessus.

En outre, lors de la spécification dans Campaign Classic d’un chemin d’accès à un serveur SFTP externe, la syntaxe du chemin d’accès diffère selon le système d’exploitation du serveur SFTP :

* Si votre serveur SFTP est sous **Windows**, utilisez toujours un chemin relatif.
* Si votre serveur STP est sous **Linux**, utilisez toujours un chemin relatif au répertoire de base (commençant par &quot;~/&quot;) ou un chemin absolu (commençant par &quot;/&quot;).

## Problèmes de connexion liés au serveur SFTP hébergé par Adobe {#sftp-server-troubleshooting}

La section ci-après indique les informations à vérifier et à fournir à l’équipe de support d’Adobe via l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"} lorsque vous rencontrez des problèmes liés aux serveurs SFTP hébergés d’Adobe.

1. Vérifiez que votre instance est en cours d’exécution. Pour cela, ouvrez votre navigateur, puis effectuez un appel **[!UICONTROL GET]** sur le point d’entrée **[!UICONTROL /r/test]** de l’instance :

   ```xml
   https://instanceUrl/r/test
   ```

   Si l&#39;instance est en cours d&#39;exécution, vous devez obtenir ce type de réponse :

   ```xml
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
   ```

   Dans tous les cas, indiquez la réponse de la commande dans le ticket de support.

1. Vérifiez si le port de sortie 22 est ouvert sur le site à partir duquel vous essayez d’initier la connexion SFTP. Pour cela, utilisez la commande suivante :

   ```xml
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   Si le port n&#39;est pas ouvert, veillez à ouvrir les connexions sortantes de votre côté, puis réessayez. Si vous rencontrez toujours des problèmes de connexion, partagez la sortie de la commande avec l’équipe de l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

1. Vérifiez que l&#39;adresse IP publique à partir de laquelle vous essayez d&#39;établir la connexion SFTP est celle que vous avez fournie au support Adobe pour la liste autorisée.
1. Si vous utilisez une authentification par mot de passe, votre mot de passe peut avoir expiré (les mots de passe ont une période de validité de 90 jours). Nous vous recommandons donc vivement d’utiliser une authentification par clé (voir [Bonnes pratiques d&#39;utilisation du serveur SFTP](#sftp-server-best-practices)).
1. Si vous utilisez une authentification par clé, vérifiez que la clé que vous utilisez est la même que celle fournie à l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour la configuration de l’instance.
1. Si vous utilisez FileZilla ou un outil FTP équivalent, fournissez les détails des logs de connexion dans le ticket de support.

## Erreur « Impossible de résoudre le nom d’hôte »

Cette section fournit des informations sur les vérifications et les actions à effectuer lors de l’affichage de l’erreur « Impossible de résoudre le nom d’hôte » après la connexion de Campaign Classic au serveur FTP.

Le journal des workflows affiche les logs suivants :

```xml
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
   1. Si oui, exécutez la commande suivante sur le serveur Adobe Campaign pour obtenir l’adresse IP :

      `nslookup <server domain name>`

      Cela confirme que le serveur FTP fonctionne et est accessible à partir du serveur applicatif Adobe Campaign.

1. Résolution des problèmes liés aux **logs de session** :

   1. Dans le workflow, double-cliquez sur l&#39;activité [Transfert de fichier](https://experienceleague.adobe.com/fr/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=fr){target="_blank"}.
   1. Accédez à l’onglet **[!UICONTROL Transfert de fichier]**, puis cliquez sur **[!UICONTROL Paramètres avancés]**.
   1. Cochez l’option **[!UICONTROL Afficher les logs de la session]**.

      ![](assets/sftp-error-display-logs.png)

   1. Accédez au workflow Audit et vérifiez si les logs affichent l’erreur « Impossible de résoudre le nom d’hôte ».

1. Si le serveur SFTP est hébergé par Adobe, vérifiez si l&#39;adresse IP est ajoutée à la liste autorisée en contactant l&#39;Assistance clientèle.

   Sinon, validez les éléments suivants :

   * Le mot de passe ne contient pas le caractère `@`. La connexion échoue si le mot de passe contient le caractère `@`.
   * Il n’existe aucun problème de pare-feu qui peut gêner la communication entre le serveur applicatif Adobe Campaign et le serveur SFTP.
   * Exécutez les commandes tracert et telnet du serveur de campagne vers le serveur sftp pour vérifier s’il y a des problèmes de connexion.
   * Il n&#39;y a pas de problème de protocole de communication.
   * Le port est ouvert.

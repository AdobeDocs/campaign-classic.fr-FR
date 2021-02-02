---
solution: Campaign Classic
product: campaign
title: Compresser ou crypter un fichier
description: Découvrez comment compresser ou chiffrer un fichier en Campaign Classic avant de le traiter.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 93%

---


# Compresser ou chiffrer un fichier {#zipping-or-encrypting-a-file}

Adobe Campaign permet d&#39;exporter des fichiers compressés ou chiffrés. Lors de la définition d&#39;un export par le biais d&#39;une activité **[!UICONTROL Extraction (fichier)]**, vous pouvez définir une étape de post-traitement pour le compresser ou le chiffrer.

Pour ce faire :

1. Installez une paire de clés GPG pour votre instance à l’aide du [panneau de contrôle](https://docs.adobe.com/content/help/fr-FR/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >Le panneau de contrôle est disponible pour tous les clients hébergés sur AWS (à l’exception de ceux qui hébergent leurs instances marketing on-premise).

1. Si votre installation d’Adobe Campaign est hébergée par Adobe, contactez le [service à la clientèle de l’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour que les utilitaires nécessaires soient installés sur le serveur.
1. S&#39;il s&#39;agit d&#39;une installation on-premise, installez l&#39;utilitaire que vous souhaitez utiliser (GPG ou GZIP, par exemple) ainsi que les clés (clé de cryptage) nécessaires sur le serveur applicatif.

Vous pouvez ensuite utiliser des commandes ou du code dans l’onglet **[!UICONTROL Script]** de l’activité ou dans une activité **[!UICONTROL Code JavaScript]**. Le cas pratique ci-dessous présente un exemple.

**Rubriques connexes :**

* [Décompresser ou décrypter un fichier avant traitement](../../platform/using/unzip-decrypt.md)
* [Activité Extraction (fichier)](../../workflow/using/extraction--file-.md).

## Cas pratique : cryptage et export de données à l’aide d’une clé installée sur le panneau de contrôle {#use-case-gpg-encrypt}

Dans ce cas pratique, nous allons créer un workflow pour crypter et exporter des données à l’aide d’une clé installée sur le panneau de contrôle.

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](#video)

Les étapes pour traiter ce cas pratique sont les suivantes :

1. Générez une paire de clés GPG (publique/privée) à l’aide d’un utilitaire GPG, puis installez la clé publique sur le panneau de contrôle. Les étapes détaillées sont disponibles dans la [documentation du panneau de contrôle](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. Dans Campaign Classic, créez un workflow pour exporter les données et les crypter à l’aide de la clé privée installée à l’aide du panneau de contrôle. Pour ce faire, nous allons créer un workflow comme suit :

   ![](assets/gpg-workflow-encrypt.png)

   * Activité **[!UICONTROL Requête]** : dans cet exemple, nous voulons exécuter une requête pour cibler les données de la base de données que nous voulons exporter.
   * Activité **[!UICONTROL Extraction (fichier)]** : extrait les données dans un fichier.
   * Activité **[!UICONTROL Code JavaScript]** : crypte les données à extraire.
   * Activité **[!UICONTROL Transfert de fichier]** : envoie les données à une source externe (dans cet exemple, un serveur SFTP).

1. Configurez l’activité **[!UICONTROL Requête]** pour qu’elle cible les données de votre choix dans la base de données. Voir à ce propos [cette section](../../workflow/using/query.md).

1. Ouvrez l’activité **[!UICONTROL Extraction (fichier)]** puis configurez-la selon vos besoins. Les concepts généraux de configuration de l’activité sont présentés dans [cette section](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Ouvrez l’activité **[!UICONTROL Code JavaScript]**, puis copiez-collez la commande ci-dessous pour crypter les données à extraire.

   >[!IMPORTANT]
   >
   >Veillez à remplacer la valeur d’**empreinte** de la commande par l&#39;empreinte de la clé publique installée sur le panneau de Contrôle.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Ouvrez l’activité **[!UICONTROL Transfert de fichier]**, puis spécifiez le serveur SFTP auquel vous souhaitez envoyer le fichier. Les concepts généraux de configuration de l’activité sont présentés dans [cette section](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Vous pouvez maintenant exécuter le workflow. Une fois exécuté, les données ciblées par la requête sont exportées vers le serveur SFTP dans un fichier .gpg crypté.

## Tutoriel vidéo {#video}

Cette vidéo montre comment utiliser une clé GPG pour crypter des données. Elle est également disponible dans

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

D’autres vidéos pratiques sur Campaign Classic sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).

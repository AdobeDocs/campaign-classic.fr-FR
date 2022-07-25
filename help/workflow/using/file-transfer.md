---
product: campaign
title: Envoi de fichier
description: En savoir plus sur l’activité de workflow d’envoi de fichier
feature: Workflows, Data Management
exl-id: 8025d207-3bc0-400f-b6a4-a72765e5a9d2
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '652'
ht-degree: 100%

---

# Envoi de fichier{#file-transfer}

![](../../assets/v7-only.svg)

L&#39;activité **Transfert de fichier** permet de recevoir ou d&#39;envoyer des fichiers, de tester la présence de fichiers ou de répertorier les fichiers sur un serveur. Le protocole utilisé est le suivant : stockage Blob Azure, S3 (Amazon Simple Storage Service), FTP ou SFTP.
Avec la connexion SFTP, S3, ou stockage Blob Azure, vous pouvez également importer des données de segments vers Adobe Campaign avec la plateforme de données clientes en temps réel d&#39;Adobe. Voir à ce propos cette [documentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=fr).

>[!NOTE]
>
>Les bonnes pratiques et la résolution des problèmes liées à l&#39;utilisation du serveur SFTP sont présentées [dans cette page](../../platform/using/sftp-server-usage.md).

## Propriétés {#properties}

Utilisez la liste déroulante du champ **[!UICONTROL Action]** pour sélectionner l&#39;action de l&#39;activité.

![](assets/file_transfert_action.png)

Le paramétrage dépend de l&#39;action sélectionnée.

1. **Réception de fichier**

   Pour recevoir des fichiers stockés sur un serveur distant, sélectionnez l&#39;option **[!UICONTROL Réception de fichier]** dans le champ **[!UICONTROL Action]**. Vous devez en indiquer l&#39;URL dans le champ correspondant.

   ![](assets/file_transfert_edit.png)

   Cochez **[!UICONTROL Utiliser un compte externe]** pour sélectionner un compte à partir du nœud de stockage Blob Azure, S3, FTP ou SFTP configuré dans le nœud **[!UICONTROL Administration > Plateforme > Comptes externes]** de l&#39;arborescence. Indiquez ensuite le répertoire sur le serveur contenant le ou les fichiers à télécharger.

   ![](assets/file_transfert_edit_external.png)

1. **Envoi de fichier**

   Pour envoyer un fichier sur un serveur, sélectionnez l&#39;option **[!UICONTROL Envoi de fichier]** dans le champ **[!UICONTROL Action]**. Vous devez indiquer le serveur cible dans la section **[!UICONTROL Serveur distant]** de l&#39;éditeur. Les paramètres sont les mêmes que pour la réception de fichiers. Voir ci-dessus.

   Le fichier source peut être issu de l&#39;activité précédente : dans ce cas, l&#39;option **[!UICONTROL Utiliser le fichier généré par l&#39;activité précédente]** doit être cochée.

   ![](assets/file_transfert_edit_send.png)

   Il peut également s&#39;agir d&#39;un ou plusieurs autres fichiers. Pour les choisir, décochez l&#39;option et cliquez sur le bouton **[!UICONTROL Ajouter]**. Indiquez le chemin d&#39;accès au fichier à envoyer. Pour ajouter un autre fichier, cliquez de nouveau sur le bouton **[!UICONTROL Ajouter]**. Les fichiers sont alors répartis dans des onglets.

   ![](assets/file_transfert_source.png)

   Utilisez les flèches pour modifier l&#39;ordre des onglets. Il correspond à l&#39;ordre d&#39;envoi des fichiers au serveur.

   L&#39;option **[!UICONTROL Garder un historique des fichiers envoyés]** permet de conserver une trace des envois effectués. Cet historique est accessible dans le répertoire.

1. **Test d&#39;existence de fichier**

   Pour tester l&#39;existence d&#39;un fichier, sélectionnez l&#39;option **[!UICONTROL Test d&#39;existence de fichier]** dans le champ **[!UICONTROL Action]**. Le paramétrage du serveur distant est le même que pour la réception de fichiers. Pour plus d&#39;informations, reportez-vous à cette [section](#properties).

   ![](assets/file_transfert_edit_test.png)

1. **Listage des fichiers**

   Pour lister les fichiers, sélectionnez l&#39;option **[!UICONTROL Listage de fichiers]** dans le champ **[!UICONTROL Action]**. Le paramétrage du serveur distant est le même que pour la réception de fichiers. Pour plus d&#39;informations, reportez-vous à cette [section](#properties).

   L’option **[!UICONTROL Lister tous les fichiers]**, disponible lors de la sélection de l’action **[!UICONTROL Listage de fichiers]** permet de répertorier tous les fichiers présents sur le serveur dans la variable d’événement **vars.filenames**. Les noms des fichiers y sont séparés par les caractères `\n`.

Pour toutes les actions de transfert de fichiers, deux options peuvent être sélectionnées :

* L’option **[!UICONTROL Traiter l’absence de fichier]** ajoute une transition qui sera activée en cas d’absence de fichier dans le répertoire spécifié.
* L’option **[!UICONTROL Traiter les erreurs]** est présentée dans la section [Traiter les erreurs](monitoring-workflow-execution.md#processing-errors).

Le lien **[!UICONTROL Paramètres avancés...]** permet d&#39;accéder aux options suivantes :

![](assets/file_transfert_advanced.png)

* **[!UICONTROL Effacer les fichiers source après leur transfert]**.

   Efface les fichiers sur le serveur distant. Si vous ne cochez pas cette option, veillez à surveiller manuellement la taille du contenu archivé dans le répertoire SFTP.

* **[!UICONTROL Utiliser SSL]**

   Permet d&#39;utiliser une connexion sécurisée via le protocole SSL lors des transferts de fichier.

* **[!UICONTROL Afficher les logs de la session]**

   Permet de récupérer les logs du stockage Blob Azure, S3, du transfert FTP ou SFTP et de les inclure dans les logs de workflow.

* **[!UICONTROL Désactiver le mode passif]**.

   Permet d&#39;indiquer le port de connexion à utiliser pour le transfert des données.

Le lien **[!UICONTROL Paramètres d’historisation des fichiers...]** permet d’accéder aux options présentées dans la section [Téléchargement Web](web-download.md) (étape **[!UICONTROL Historisation des fichiers]**).

## Paramètres d&#39;entrée {#input-parameters}

* filename

   Nom complet du fichier envoyé.

## Paramètres de sortie {#output-parameters}

* filename

   Nom complet du fichier reçu lorsque l&#39;option **[!UICONTROL Utiliser le fichier généré par l&#39;activité précédente]** est sélectionnée.

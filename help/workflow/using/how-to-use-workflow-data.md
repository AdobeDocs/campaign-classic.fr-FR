---
title: Utiliser les données d'un workflow
seo-title: Utiliser les données d'un workflow
description: Utiliser les données d'un workflow
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Utiliser les données d&#39;un workflow{#how-to-use-workflow-data}

## Mettre à jour la base de données {#updating-the-database}

Toutes les données collectées peuvent être utilisées pour mettre à jour la base de données, ou dans des diffusions. Par exemple, vous pouvez enrichir les possibilités de personnalisation du contenu des messages (inclure le nombre de contrats dans le message, indiquer le panier moyen pour l&#39;année écoulée, etc) ou affiner le ciblage des populations (adresser un message aux co-titulaires d&#39;un contrat, cibler les 1000 meilleurs acheteurs abonnés aux services en ligne, etc.). Ces données peuvent également être exportées ou archivées dans une liste.

### Listes et mises à jour directes {#lists-and-direct-updates}

Les données de la base Adobe Campaign et les listes existantes peuvent être mises à jour via deux activités dédiées :

* L&#39;activité **[!UICONTROL Mise à jour de liste]** permet de stocker les tables de travail dans une liste de données.

   Vous pouvez sélectionner une liste existante ou la créer. Dans ce cas, le nom et éventuellement le dossier d&#39;enregistrement sont calculés.

   ![](assets/s_user_create_list.png)

   Reportez-vous à la mise à jour [de la](../../workflow/using/list-update.md)liste.

* L&#39;activité **[!UICONTROL Mise à jour de données]** permet de mettre à jour en masse les champs de la base de données.

   For more on this, refer to [Update data](../../workflow/using/update-data.md).

### Gérer les abonnements/désabonnements {#subscription-unsubscription-management}

To find out about subscribing and unsubscribing recipients to an information service via a workflow, refer to [Subscription Services](../../workflow/using/subscription-services.md).

## Envoyer via un workflow {#sending-via-a-workflow}

### Activité Diffusion {#delivery-activity}

The delivery activity is detailed in [Delivery](../../workflow/using/delivery.md).

### Enrichir et cibler les diffusions {#enriching-and-targeting-deliveries}

Les diffusions peuvent exploiter les données issues des workflows pour personnaliser le contenu ou dans le cadre de la sélection de la population cible.

Par exemple, dans le cadre d&#39;une diffusion courrier, vous pouvez inclure dans le fichier d&#39;extraction les données additionnelles issues des manipulations de données réalisées dans le workflow :

![](assets/s_advuser_add_data_postal_mail.png)

En complément des champs de personnalisation habituels, vous pouvez ajouter dans le contenu des diffusions des champs de personnalisation issus des étapes du workflow. En effet, les données additionnelles définies dans les activités du workflow peuvent être conservées et sont ensuite rendues accessibles dans l&#39;assistant de diffusion, comme dans l&#39;exemple ci-dessous pour définir le nom du fichier de sortie dans le cadre d&#39;une diffusion courrier :

![](assets/s_advuser_using_additional_data.png)

The data contained in the workflow table is identified by its name: it is always made up of the **targetData** link. For more on this, refer to [Target data](../../workflow/using/executing-a-workflow.md#target-data).

Dans le cadre d&#39;une diffusion par email, les champs de personnalisation peuvent également utiliser les données issues de l&#39;extension de la cible réalisée dans les étapes du workflow de ciblage, comme dans l&#39;exemple ci-dessous :

![](assets/s_advuser_add_data_email.png)

Si un code segment est indiqué dans une activité de ciblage, il est ajouté dans une colonne spécifique de la table du workflow et il sera proposé parmi les champs de personnalisation. Pour afficher tous les champs de personnalisation, cliquez sur le lien **[!UICONTROL Extension de la cible > Autre...]** accessible à partir du bouton de personnalisation.

![](assets/s_advuser_segment_code_select.png)

## export des données {#exporting-data}

### Compresser ou chiffrer un fichier {#zipping-or-encrypting-a-file}

Adobe Campaign permet d&#39;exporter des fichiers compressés ou chiffrés. Lors de la définition d&#39;un export par le biais d&#39;une activité **[!UICONTROL Extraction (fichier)]**, vous pouvez définir une étape de post-traitement pour le compresser ou le chiffrer.

Pour ce faire :

* Si votre installation d&#39;Adobe Campaign est hébergée par Adobe : envoyez une demande à l&#39;[assistance technique](https://support.neolane.net) afin que les utilitaires nécessaires soient installés sur le serveur.
* S&#39;il s&#39;agit d&#39;une installation on-premise : installez l&#39;utilitaire que vous souhaitez utiliser (GPG ou GZIP, par exemple) ainsi que les clés (clé de chiffrement) nécessaires sur le serveur applicatif.

Vous pouvez ensuite utiliser des commandes ou du code, par exemple :

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

Lors de l’importation d’un fichier, vous pouvez également le décompresser ou le déchiffrer. See [Unzipping or decrypting a file before processing](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing).

---
product: campaign
title: Chargement (fichier)
description: En savoir plus sur l’activité de workflow de chargement (fichier)
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows, Data Management Activity
exl-id: a380e486-a40c-4bf6-b7f4-7dcd76c34085
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 100%

---

# Chargement (fichier){#data-loading-file}



## Utilisation {#use}

L’activité **[!UICONTROL Chargement (fichier)]** vous permet d’accéder directement à une source de données externes et de l’utiliser dans Adobe Campaign. En effet, toutes les données requises pour les opérations de ciblage ne se trouvent pas toujours dans la base de données Adobe Campaign : elles peuvent provenir de fichiers externes.

Le fichier à charger peut être spécifié par la transition ou calculé lors de l&#39;exécution de cette activité. Il peut s&#39;agir par exemple de la liste des 10 produits favoris d&#39;un client dont les actes d&#39;achats sont gérés dans une base externe.

La section supérieure de la fenêtre de configuration de cette activité permet de définir le format du fichier. Pour cela, utilisez un fichier d&#39;exemple au même format que celui à importer. Ce fichier peut être stocké en local ou sur le serveur.

>[!CAUTION]
>
>Seuls les fichiers à structure &quot;plate&quot; sont pris en charge (ex : CSV, TXT, etc.). L&#39;utilisation du format XML est déconseillée.

![](assets/s_advuser_wf_etl_file.png)

Vous pouvez définir un pré-traitement à exécuter lors de l’import du fichier, par exemple pour ne pas avoir à décompresser le fichier sur le serveur (et donc réserver de la place pour le fichier décompressé), mais que la décompression soit incluse dans le traitement du fichier. Sélectionnez l’option **[!UICONTROL Inclure un pré-traitement du fichier]** et choisissez l’une des 3 options : **[!UICONTROL Aucun]**, **[!UICONTROL Décompression]** (zcat) ou **[!UICONTROL Déchiffrer]** (gpg).

![](assets/preprocessing-dataloading.png)

Pour plus d’informations à ce sujet, consultez cette section : [Compresser ou chiffrer un fichier avant traitement](../../platform/using/unzip-decrypt.md).

## Définir le format du fichier {#defining-the-file-format}

Lorsque vous chargez un fichier, le format des colonnes est automatiquement détecté avec des paramètres par défaut pour chaque type de données. Vous pouvez modifier ces paramètres par défaut afin de spécifier des traitements particulier à appliquer à vos données, notamment en cas d&#39;erreur ou de valeur vide.

Pour cela, sélectionnez **[!UICONTROL Cliquez ici pour changer le format du fichier]** dans la fenêtre principale de l&#39;activité de **[!UICONTROL Chargement (fichier)]**. La fenêtre de détail du format s&#39;ouvre alors.

![](assets/file_loading_columns_format.png)

Vous pouvez alors modifier le formatage général du fichier ainsi que le formatage de chaque colonne.

Le formatage général du fichier permet de définir la manière dont seront reconnues les colonnes (encodage du fichier, séparateurs utilisés, etc.)

Le formatage des colonnes permet de définir le traitement des valeurs de chaque colonne :

* **[!UICONTROL Ignorer la colonne]** : permet de ne pas traiter cette colonne lors du chargement des données.
* **[!UICONTROL Type de données]** : permet de spécifier le type de données attendu dans la colonne.
* **[!UICONTROL Utilisation des NULL]** : permet d&#39;indiquer comment gérer les valeurs vides.

   * **[!UICONTROL Défaut Adobe Campaign]** : génère une erreur pour les champs numériques uniquement, sinon insère la valeur NULL.
   * **[!UICONTROL Valeur vide autorisée]** : autorise les valeurs vides. La valeur NULL est alors insérée.
   * **[!UICONTROL Toujours renseignée]** : génère une erreur en cas de valeur vide.

* **[!UICONTROL Longueur]** : permet de spécifier le nombre maximal de caractères pour les données de type **chaîne**.
* **[!UICONTROL Format]** : permet de définir le format des heures et des dates.
* **[!UICONTROL Mise en forme]** : permet de définir si un traitement au niveau de la casse doit être appliqué sur une **chaîne**.

   * **[!UICONTROL Aucune]** : la chaîne importée n&#39;est pas modifiée.
   * **[!UICONTROL Première lettre en majuscule]** : la première lettre de chaque mot de la chaîne est passée en majuscule.
   * **[!UICONTROL Majuscules]** : tous les caractères de la chaîne sont passés en majuscule.
   * **[!UICONTROL Minuscules]** : tous les caractères de la chaîne sont passés en minuscule.

* **[!UICONTROL Traitements des espaces]** : permet d&#39;indiquer si certains espaces doivent être ignorés dans une chaîne. La valeur **[!UICONTROL Ignorer les espaces]** permet uniquement d&#39;ignorer les espaces en début et en fin de chaîne.
* **[!UICONTROL Traitements d&#39;erreur]** : permet de définir le comportement en cas d&#39;erreur.

   * **[!UICONTROL Ignorer la valeur]** : la valeur est ignorée. Un avertissement est généré dans le journal d&#39;exécution du workflow.
   * **[!UICONTROL Rejeter la ligne]** : la ligne entière n&#39;est pas traitée.
   * **[!UICONTROL Utiliser une valeur par défaut en cas d&#39;erreur]** : remplace la valeur causant l&#39;erreur par une valeur par défaut, définie dans le champ **[!UICONTROL Valeur par défaut]**.
   * **[!UICONTROL Rejeter la ligne en cas d&#39;absence de recodification]** : la ligne entière n&#39;est pas traitée sauf si une correspondance a été définie pour la valeur en erreur (voir option **[!UICONTROL Correspondance]** ci-dessous).
   * **[!UICONTROL Utiliser une valeur par défaut en cas d&#39;absence de recodification]** : remplace la valeur causant l&#39;erreur par une valeur par défaut, définie dans le champ **[!UICONTROL Valeur par défaut]**, sauf si une correspondance a été définie pour la valeur en erreur (voir option **[!UICONTROL Correspondance]** ci-dessous).

* **[!UICONTROL Valeur par défaut]** : permet de spécifier la valeur par défaut en fonction du choix concernant le traitement des erreurs.
* **[!UICONTROL Correspondance]** : ce champ est disponible uniquement dans le paramétrage du détail d&#39;une colonne (accessible via un double-clic ou via les options sur la droite de la liste des colonnes). Il permet de transformer certaines valeurs lors de l&#39;import. Par exemple, vous pouvez transformer &quot;trois&quot; en &quot;3&quot;.

## Exemple : collecter des données et les charger dans la base {#example--collecting-data-and-loading-it-in-the-database}

L&#39;exemple suivant permet de collecter tous les jours un fichier sur le serveur, en charger le contenu, puis mettre à jour les données de la base en fonction des informations qu&#39;il contient. Le fichier à collecter contient les informations relatives aux clients d&#39;un magasin qui peuvent avoir effectué des achats (inférieurs ou supérieurs à 3000 euros), demandé le remboursement d&#39;un achat, ou être venu en boutique sans effectuer d&#39;achat. Selon ces informations, les traitements appliqués à leur profil en base seront différents.

![](assets/s_advuser_load_file_sample_0.png)

1. Le collecteur de fichier est utilisé pour récupérer les fichiers stockés dans un répertoire, selon la fréquence indiquée.

   L&#39;onglet **[!UICONTROL Répertoire]** contient les informations relatives au(x) fichier(s) à récupérer. Dans notre exemple, tous les fichiers au format texte, dont le nom contient le mot &#39;clients&#39; et stockés dans le répertoire tmp/Adobe/Data/files du serveur seront récupérés.

   L’utilisation du **[!UICONTROL Collecteur de fichiers]** est détaillée dans la section [Collecteur de fichiers](file-collector.md).

   ![](assets/s_advuser_load_file_sample_1.png)

   L&#39;onglet **[!UICONTROL Planning]** permet de planifier l&#39;exécution du collecteur, c&#39;est-à-dire d&#39;indiquer à quelle fréquence la présence de ces fichiers sera vérifiée.

   Ici, nous choisirons de déclencher le collecteur tous les jours ouvrés à 21 heures.

   ![](assets/s_advuser_load_file_sample_2.png)

   Pour cela, cliquez sur le bouton **[!UICONTROL Changer...]** situé dans la section inférieure droite de l&#39;éditeur et paramétrez le planning.

   Pour plus d&#39;informations, consultez la section [Planificateur](scheduler.md).

1. Paramétrez ensuite l&#39;activité de chargement de fichier afin d&#39;indiquer comment le ou les fichiers collectés doivent être lus. Sélectionnez pour cela un fichier exemple dont la structure est la même que les fichiers à charger.

   ![](assets/s_advuser_load_file_sample_3.png)

   Ici, le fichier contient cinq colonnes :

   * la première colonne contient un code correspondant à l&#39;événement : achat (d&#39;un montant supérieur ou inférieur à 3000 euros), sans achat ou retour d&#39;un ou plusieurs articles.
   * les quatre colonnes suivantes contiennent le prénom, le nom, l&#39;email et le numéro de compte du client.

   Le paramétrage du format du fichier à charger correspond à celui défini lors d&#39;un import de données dans Adobe Campaign. Voir à ce sujet cette [section](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Dans l&#39;activité de partage, indiquez les sous-ensembles à créer, en fonction de la valeur de la colonne **Evénement**.

   Le fonctionnement de l&#39;activité de partage est présenté dans cette section.

   ![](assets/s_advuser_load_file_sample_4.png)

   Pour chaque sous-ensemble, indiquez une des valeurs de la colonne **Evénement**.

   ![](assets/s_advuser_load_file_sample_5.png)

   Ainsi, l&#39;activité de **[!UICONTROL Partage]** contiendra les informations suivantes :

   ![](assets/s_advuser_load_file_sample_6.png)

1. Indiquez ensuite les traitements à effectuer pour chaque type de population. Dans notre exemple, nous allons mettre à jour les données de la base. Pour cela, positionnez une activité **[!UICONTROL Mise à jour de données]** à l&#39;extrémité de chaque transition sortante de l&#39;activité de **[!UICONTROL Partage]**.

   L&#39;activité de **[!UICONTROL Mise à jour de données]** est présentée dans la section [Mise à jour de données](update-data.md).

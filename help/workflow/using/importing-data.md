---
title: Importer des données
description: Découvrez comment importer des données dans Adobe Campaign Classic
page-status-flag: never-activated
uuid: c8cf2bf1-f7a5-4de4-9e53-a961c9e5beca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: e53af1c2-b50c-4a8c-b5b8-f23a85bd3211
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e16d4de068f8cb1e61069aa53626f7bf7021466

---


# Importer des données{#importing-data}

## Comment collecter des données {#how-to-collect-data}

### Utiliser les données d&#39;une liste : Lecture de Liste {#using-data-from-a-list--read-list}

Les données traitées dans un workflow peuvent provenir de listes dont les données ont été préparées et structurées au préalable.

Ces listes peuvent avoir été constituées directement dans Adobe Campaign ou importées via l&#39;option **[!UICONTROL Importer une liste]**. Pour plus d&#39;informations sur cette option, consultez cette [page](../../platform/using/generic-imports-and-exports.md).

For more on using the read list activity in a workflow, refer to [Read list](../../workflow/using/read-list.md).

### Charger des données depuis un fichier {#loading-data-from-a-file}

Les données traitées dans un workflow peuvent êtes extraites d&#39;un fichier structuré pour qu&#39;il puisse être importé dans Adobe Campaign.

A description of the loading data activity can be found in the [Data loading (file)](../../workflow/using/data-loading--file-.md) section.

Voici un exemple de fichier structuré à importer :

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

### Décompresser ou déchiffrer un fichier avant traitement {#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign permet d&#39;importer des fichiers compressés ou chiffrés. Avant qu&#39;un fichier ne puisse être lu dans une activité **[!UICONTROL Chargement (fichier)]**, vous pouvez définir une étape de prétraitement pour le décompresser ou le déchiffrer.

Pour ce faire :

* Si votre installation d&#39;Adobe Campaign est hébergée par Adobe : envoyez une demande à l&#39;[assistance technique](https://support.neolane.net) afin que les utilitaires nécessaires soient installés sur le serveur.
* S&#39;il s&#39;agit d&#39;une installation on-premise : installez l&#39;utilitaire que vous souhaitez utiliser (GPG ou GZIP, par exemple) ainsi que les clés (clé de chiffrement) nécessaires sur le serveur applicatif.

1. Ajoutez et configurez une activité **[!UICONTROL Transfert de fichier]** dans le workflow.
1. Ajoutez une activité **[!UICONTROL Chargement (fichier)]** et définissez le format de fichier.
1. Cochez l&#39;option **[!UICONTROL Inclure un pré-traitement du fichier]**.
1. Spécifiez la commande de prétraitement que vous souhaitez appliquer. Par exemple, pour déchiffrer un fichier à l&#39;aide de PGP :

   ```
   <path-to_pgp_if-not_global_or_server/>pgp.exe --decrypt --input nl6/var/vp/import/filename.pgp --passphrase "your password" --recipient recipient @email.com --verbose --output nl6/var/vp/import/filename
   ```

1. Ajoutez d&#39;autres activités pour gérer les données provenant du fichier.
1. Enregistrez et exécutez le workflow.

Lors de l’exportation d’un fichier, vous pouvez également le compresser ou le chiffrer. See [Zipping or encrypting a file](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Bonnes pratiques relatives à l’import de données {#best-practices-when-importing-data}

Pour garantir la cohérence des données au sein de la base de données et éviter les erreurs fréquentes lors de la mise à jour de la base de données ou de l&#39;export de données, faites preuve de précaution et suivez les quelques règles simples détaillées ci-dessous.

### Utiliser les modèles d&#39;import  {#using-import-templates}

La plupart des workflows d&#39;import doivent contenir les activités suivantes : **[!UICONTROL Chargement (fichier)]**, **[!UICONTROL Enrichissement]**, **[!UICONTROL Partage]**, **[!UICONTROL Déduplication]**, **[!UICONTROL Mise à jour de données]**.

L&#39;utilisation de modèles d&#39;import facilite la préparation d&#39;imports similaires et garantit la cohérence des données au sein de la base de données. Découvrez comment créer des modèles de processus dans la section Modèles [de](../../workflow/using/building-a-workflow.md#workflow-templates) processus.

Pour de nombreux projets, les imports sont construits sans activité de **[!UICONTROL Déduplication]** car les fichiers utilisés n&#39;ont pas de doublon. Des doublons apparaissent parfois suite à l&#39;import d&#39;autres fichiers. La déduplication est alors difficile. C&#39;est pourquoi l&#39;ajout d&#39;une étape de déduplication est une précaution utile pour tous les workflows d&#39;import.

Ne partez pas de l&#39;hypothèse selon laquelle les données entrantes sont cohérentes et justes ou que le département informatique ou le responsable Adobe Campaign s&#39;en occupera. Gardez la normalisation des données à l&#39;esprit tout au long du projet. Veillez à dédupliquer, à réconcilier et à maintenir la cohérence des données lors des imports.

Un exemple de modèle d’importation est disponible dans la section [Configuration d’une importation](#setting-up-a-recurring-import) périodique.

### Utiliser des formats de fichiers plats  {#using-flat-file-formats}

Le format le plus efficace pour les imports est le fichier plat. Les fichiers plats peuvent être importés en masse au niveau de la base de données.

Par exemple :

* Séparateur : onglet ou point virgule
* Première ligne avec en-têtes
* Pas de délimiteur de chaîne
* Format de date : AAAA/MM/JJ HH:mm:SS

Adobe Campaign ne peut pas importer de fichiers XML via les activités d&#39;import de fichier standard. Les fichiers XML peuvent être importés à l&#39;aide de JavaScript, mais uniquement en petits volumes : moins de 10K enregistrements par fichier.

### Utiliser la compression et le cryptage {#using-compression-and-encryption}

Lorsque cela est possible, utilisez des fichiers compressés pour les imports et les exports.

Sous Linux, il est possible de décompresser un fichier et de l&#39;importer en même temps à l&#39;aide d&#39;une ligne de commande. Par exemple :

```
zcat nl6/var/vp/import/filename.gz
```

Il est également de bonne pratique de crypter les fichiers envoyés via le réseau s&#39;il n&#39;est pas sécurisé. Pour cela, vous pouvez utiliser GPG.

### Charger des données en mode batch depuis des fichiers {#loading-data-in-batch-from-files}

Le chargement des données en mode batch depuis un fichier est plus efficace que le chargement ligne par ligne et en temps réel (via un service web, par exemple).

Les imports à l&#39;aide de Services web ne sont pas efficients. Il est recommandé d&#39;utiliser des fichiers dans la mesure du possible.

L&#39;appel aux services web externes pour enrichir des profils en temps réel engendre des problèmes de performance et des fuites mémoire, car il opère au niveau ligne.

Pour importer des données, il vaut mieux procéder en mode batch via un workflow plutôt qu&#39;en temps réel à l&#39;aide d&#39;une application web ou d&#39;un service web.

### Utiliser la gestion des données {#using-data-management}

Le chargement en mode itératif (ligne par ligne) à l&#39;aide de JavaScript doit être limité aux faibles volumes.

Pour plus d&#39;efficacité, toujours utiliser l&#39;activité **[!UICONTROL Chargement (fichier)]** dans les workflows de gestion des données.

### Importer en mode Delta {#importing-in-delta-mode}

Les imports standard doivent être effectués en mode delta. Cela signifie qu&#39;au lieu d&#39;envoyer le tableau entier à chaque fois, seules les données modifiées ou nouvelles sont envoyée à Adobe Campaign.

Les imports complets sont réservés au chargement initial.

Les données doivent être importées à l&#39;aide de la gestion des données et non de JavaScript.

### Maintenir la cohérence  {#maintaining-consistency}

Pour maintenir la cohérence des données dans la base de données Adobe Campaign, veuillez appliquer les principes suivants :

* Si les données importées correspondent à une table de référence dans Adobe Campaign, elles doivent être réconciliées avec ce tableau dans le workflow. Les enregistrements sans correspondance doivent être rejetés.
* Assurez-vous que les données importées soient toujours **« normalisées »** (email, numéro de téléphone, adresse postale) et que cette normalisation soit fiable et ne risque pas de changer pas au fil des années. Si ce n&#39;est pas le cas, des doublons risquent d&#39;apparaître dans la base de données, et dans la mesure où Adobe Campaign ne fournit pas d&#39;outils de « correspondance approximative », leur suppression sera très difficile.
* Les données transactionnelles doivent être dotées d&#39;une clé de réconciliation et être réconciliées avec les données existantes afin d&#39;éviter la création de doublons.
* **Les fichiers liés doivent être importés dans l&#39;ordre**.

   Si l&#39;import est composé de fichiers multiples et interdépendants, le workflow doit vérifier que les fichiers sont importés dans l&#39;ordre. Si un fichier échoue, les autres fichiers ne sont pas importés.

* **Dédupliquez**, réconciliez et maintenez la cohérence lorsque vous importez des données.

## Configurer un import récurrent {#setting-up-a-recurring-import}

L&#39;utilisation d&#39;un modèle d&#39;import est une bonne pratique si vous devez importer régulièrement des fichiers de structure identique.

Cet exemple montre comment pré-paramétrer un workflow qui pourra être réutilisé pour importer des profils en provenance d&#39;un CRM dans la base de données Adobe Campaign. Pour plus d&#39;informations sur tous les paramétrages possibles pour chaque activité, reportez-vous à cette [section](../../workflow/using/about-activities.md).

1. Créez un nouveau modèle de workflow à partir de **[!UICONTROL Ressources > Modèles > Modèles de workflow]**.
1. Ajoutez les activités suivantes :

   * **[!UICONTROL Chargement (fichier)]** : définissez la structure attendue du fichier contenant les données à importer.
   * **[!UICONTROL Enrichissement]** : réconciliez les données importées avec les données se trouvant dans la base de données.
   * **[!UICONTROL Partage]** : créez des filtres pour traiter les enregistrements différemment selon qu&#39;ils aient pu ou non être réconciliés.
   * **[!UICONTROL Déduplication]** : dédupliquez les données du fichier entrant avant son import dans la base de données.
   * **[!UICONTROL Mise à jour de données]** : mettez la base de données à jour avec les profils importés.
   ![](assets/import_template_example0.png)

1. Configurez l&#39;activité **[!UICONTROL Chargement (fichier)]** :

   * Définissez la structure attendue en téléchargeant un fichier exemple. Le fichier exemple ne doit contenir que quelques lignes mais toutes les colonnes nécessaires pour l&#39;import. Vérifiez et éditez le format du fichier pour vous assurer que le type de chaque colonne est paramétré correctement : texte, date, nombre entier, etc.
Par exemple :

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * Dans la section **[!UICONTROL Nom du fichier à charger]**, sélectionnez **[!UICONTROL Télécharger un fichier présent sur le poste local]** et laissez le champ vide. A chaque fois qu&#39;un nouveau workflow sera créé à partir de ce modèle, vous pourrez préciser ici le fichier souhaité (tant qu&#39;il correspond à la structure définie).

      Toutes les options sont utilisables, mais il faut modifier le modèle en conséquence. Par exemple, en sélectionnant **[!UICONTROL Spécifié par la transition]**, vous pouvez ajouter une activité **[!UICONTROL Transfert de fichier]** devant pour récupérer le fichier à importer à partir d&#39;un serveur FTP/SFTP. Avec la connexion S3 ou SFTP, vous pouvez également importer des données de segments dans Adobe Campaign avec la plate-forme de données clientes en temps réel d’Adobe. For more on this, refer to this [documentation](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).

      ![](assets/import_template_example1.png)

1. Configurez l&#39;activité **[!UICONTROL Enrichissement]**. Dans ce contexte, le but de cette activité est d&#39;identifier les données entrantes.

   * Dans l&#39;onglet **[!UICONTROL Enrichissement]**, sélectionnez **[!UICONTROL Ajouter des données]** et définissez un lien entre les données importées et la dimension de ciblage des destinataires. Dans cet exemple, le champ personnalisé **Identifiant dans le CRM** permet de créer la condition de jointure. Utilisez le champ ou la combinaison de champs nécessaire tant que l&#39;identification des enregistrements uniques reste possible.
   * Dans l&#39;onglet **[!UICONTROL Réconciliation]**, laissez l&#39;option **[!UICONTROL Identifier le document de ciblage à partir des données de travail]** décochée.
   ![](assets/import_template_example2.png)

1. Configurez l&#39;activité de **[!UICONTROL Partage]** pour récupérer les destinataires réconciliés dans une transition, et les destinataires qui n&#39;ont pas pu être réconciliés mais qui disposent de suffisamment de données dans une autre transition.

   La transition des destinataires réconciliés peut alors être utilisée pour mettre à jour la base de données. La transition des destinataires inconnus peut servir à créer de nouvelles entrées de destinataires dans la base de données si un ensemble d&#39;informations minimum est disponible dans le fichier.

   Les destinataires ne pouvant pas être réconciliés et ne disposant pas de suffisamment de données sont sélectionnés dans une transition sortante complémentaire et peuvent être exportés dans un fichier séparé ou tout simplement ignorés.

   * Dans l&#39;onglet **[!UICONTROL Général]** de l&#39;activité, sélectionnez **[!UICONTROL Utiliser les données additionnelles uniquement]** comme paramètre de filtrage et vérifiez que la **[!UICONTROL Dimension de ciblage]** est paramétrée automatiquement sur **[!UICONTROL Enrichissement]**.

      Cochez l&#39;option **[!UICONTROL Générer le complémentaire]** pour voir si des enregistrements n&#39;ont pas pu être intégrés dans la base de données. Le cas échéant, vous pourrez alors appliquer d&#39;autres traitements aux données complémentaires : export de fichier, mise à jour de liste, etc.

   * Dans le premier sous-ensemble de l&#39;onglet **[!UICONTROL Sous-ensembles]**, ajoutez une condition de filtrage sur la population entrante pour sélectionner uniquement les enregistrements pour lesquels la clé primaire du destinataire est différente de 0. De cette manière les données du fichier réconciliées avec les destinataires de la base de données sont sélectionnées dans ce sous-ensemble.

      ![](assets/import_template_example3.png)

   * Ajoutez un second sous-ensemble pour sélectionner les enregistrements non réconciliés disposant de suffisamment de données pour être intégrés dans la base de données. Par exemple : adresse email, prénom et nom de famille.

      Les sous-ensembles sont traités dans l&#39;ordre dans lequel ils ont été créés, ce qui veut dire que lorsque ce second sous-ensemble est traité, tous les enregistrements qui existent déjà dans la base de données sont déjà sélectionnés dans le premier sous-ensemble.

      ![](assets/import_template_example3_2.png)

   * Tous les enregistrement qui ne sont pas sélectionnés dans les deux premiers sous-ensembles sont sélectionnés dans le **[!UICONTROL Complémentaire]**.

1. Configurez l&#39;activité **[!UICONTROL Mise à jour de données]** située après la première transition sortante de l&#39;activité **[!UICONTROL Partage]** paramétrée précédemment.

   * Sélectionnez **[!UICONTROL Mise à jour]** comme **[!UICONTROL Type d&#39;opération]**, puisque la transition entrante contient uniquement des destinataires déjà présents dans la base de données.
   * Dans la section **[!UICONTROL Identification des enregistrements]**, sélectionnez **[!UICONTROL En utilisant des clés de réconciliation]** et définissez une clé entre la dimension de ciblage et le lien créé dans l&#39;**[!UICONTROL Enrichissement]**. Dans cet exemple, le champ personnalisé **Identifiant dans le CRM** est utilisé.
   * Dans la section **[!UICONTROL Champs à mettre à jour]**, indiquez les champs de la dimension des destinataires à mettre à jour avec la valeur de la colonne correspondante du fichier. Si les noms des colonnes du fichier sont identiques ou presque identiques aux noms des champs de la dimension des destinataires, utilisez le bouton baguette magique pour réconcilier les différents champs automatiquement.

      ![](assets/import_template_example6.png)

1. Configurez l&#39;activité **[!UICONTROL Déduplication]** située après la transition contenant les destinataires non réconciliés :

   * Sélectionnez **[!UICONTROL Editer la configuration]** et paramétrez la dimension de ciblage sur le schéma temporaire généré à partir de l&#39;activité **[!UICONTROL Enrichissement]** du workflow.

      ![](assets/import_template_example4.png)

   * Dans cet exemple, le champ email est utilisé pour trouver les profils uniques. Vous pouvez utiliser n&#39;importe quel champ dont vous êtes sûr qu&#39;il est rempli et qu&#39;il fait partie d&#39;une combinaison unique.
   * Dans l&#39;écran **[!UICONTROL Méthode de déduplication]**, sélectionnez **[!UICONTROL Paramètres avancés]** et cochez l&#39;option **[!UICONTROL Désactiver le filtrage automatique des enregistrements d&#39;identifiant 0]** pour veiller à ce que les enregistrements dont la clé primaire est égale à 0 (normalement, tous les enregistrements de cette transition) sont exclus.
   ![](assets/import_template_example7.png)

1. Configurez l&#39;activité **[!UICONTROL Mise à jour de données]** située après l&#39;activité **[!UICONTROL Déduplication]** paramétrée précédemment.

   * Sélectionnez **[!UICONTROL Insertion]** comme **[!UICONTROL Type d&#39;opération]** comme la transition entrante contient uniquement des destinataires non présents dans la base de données.
   * Dans la section **[!UICONTROL Identification des enregistrements]**, sélectionnez **[!UICONTROL En utilisant directement la dimension de ciblage]** et choisissez la dimension **[!UICONTROL Destinataires]**.
   * Dans la section **[!UICONTROL Champs à mettre à jour]**, indiquez les champs de la dimension des destinataires à mettre à jour avec la valeur de la colonne correspondante du fichier. Si les noms des colonnes du fichier sont identiques ou presque identiques aux noms des champs de la dimension des destinataires, utilisez le bouton baguette magique pour réconcilier les différents champs automatiquement.

      ![](assets/import_template_example8.png)

1. Après la troisième transition de l&#39;activité **[!UICONTROL Partage]**, ajoutez une activité **[!UICONTROL Extraction (fichier)]** et une activité **[!UICONTROL Transfert de fichier]** si vous souhaitez conserver une trace des données non intégrées dans la base de données. Paramétrez ces activités afin d&#39;exporter la colonne dont vous avez besoin et de transférer le fichier sur un serveur FTP ou SFTP, où vous pourrez le récupérer.
1. Ajoutez une activité **[!UICONTROL Fin]** et enregistrez le modèle de workflow.

Le modèle est à présent utilisable et disponible pour chaque nouveau workflow. Il suffira alors de spécifier le fichier contenant les données à importer dans l&#39;activité **[!UICONTROL Chargement (fichier)]**.

![](assets/import_template_example9.png)


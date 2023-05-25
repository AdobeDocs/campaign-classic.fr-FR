---
product: campaign
title: Bonnes pratiques en matière d'import et d'export
description: En savoir plus sur les bonnes pratiques à suivre lors de l'import ou de l'export de données
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '523'
ht-degree: 100%

---

# Bonnes pratiques en matière d&#39;import et d&#39;export {#import-export-best-practices}



Pour garantir la cohérence des données au sein de la base de données et éviter les erreurs fréquentes lors de la mise à jour de la base de données ou de l&#39;export de données, faites preuve de précaution et suivez les quelques règles simples détaillées ci-dessous.

## Utilisation de modèles de workflow {#using-import-templates}

La plupart des workflows servant à importer des données doivent contenir les activités suivantes : **[!UICONTROL Chargement du fichier]**, **[!UICONTROL Réconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Déduplication]**, **[!UICONTROL Mise à jour de données]**.

L&#39;utilisation de modèles de workflow facilite la préparation d&#39;imports similaires et garantit la cohérence des données au sein de la base de données.

Pour de nombreux projets, les imports sont construits sans activité de **[!UICONTROL Déduplication]** car les fichiers utilisés n&#39;ont pas de doublon. Des doublons apparaissent parfois suite à l&#39;import d&#39;autres fichiers. La déduplication est alors difficile. C&#39;est pourquoi l&#39;ajout d&#39;une étape de déduplication est une précaution utile pour tous les workflows d&#39;import.

Ne partez pas de l&#39;hypothèse selon laquelle les données entrantes sont cohérentes et justes ou que le département informatique ou le responsable Adobe Campaign s&#39;en occupera. Gardez la normalisation des données à l&#39;esprit tout au long du projet. Veillez à dédupliquer, à réconcilier et à maintenir la cohérence des données lors des imports.

Un exemple de modèle de workflow générique conçu pour importer des données est disponible dans la section [Exemple : modèle de workflow pour importer des données](../../platform/using/creating-import-export-templates.md).

## Utiliser des formats de fichier plat {#using-flat-file-formats}

Le format le plus efficace pour les imports est le fichier plat. Les fichiers plats peuvent être importés en masse au niveau de la base de données.

Par exemple :

* Séparateur : onglet ou point virgule
* Première ligne avec en-têtes
* Pas de délimiteur de chaîne
* Format de date : AAAA/JJ HH:mm:SS

Voici un exemple de fichier à importer :

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Utiliser la compression {#using-compression}

Lorsque cela est possible, utilisez des fichiers compressés pour les imports et les exports. GZIP est pris en charge par défaut. Vous pouvez ajouter une étape de pré-traitement lors de l&#39;import des fichiers ou de post-traitement lors de l&#39;extraction des données dans les activités de workflow **[!UICONTROL Chargement de fichier]** et **[!UICONTROL Extraction de fichier]**.

**Rubriques connexes :**

* [Activité Chargement (fichier)](../../workflow/using/data-loading--file-.md)
* [Activité Extraction des données (fichier)](../../workflow/using/extraction--file-.md)

## Importer en mode Delta {#importing-in-delta-mode}

Les imports standard doivent être effectués en mode delta. Cela signifie qu’au lieu d’envoyer le tableau entier à chaque fois, seules les données modifiées ou nouvelles sont envoyée à Adobe Campaign.

Les imports complets sont réservés au chargement initial.

## Conserver la cohérence {#maintaining-consistency}

Pour maintenir la cohérence des données dans la base de données Adobe Campaign, veuillez appliquer les principes suivants :

* Si les données importées correspondent à une table de référence dans Adobe Campaign, elles doivent être réconciliées avec ce tableau dans le workflow. Les enregistrements sans correspondance doivent être rejetés.
* Assurez-vous que les données importées soient toujours **« normalisées »** (email, numéro de téléphone, adresse postale) et que cette normalisation soit fiable et ne risque pas de changer pas au fil des années. Si ce n’est pas le cas, des doublons risquent d’apparaître dans la base de données, et dans la mesure où Adobe Campaign ne fournit pas d’outils de « correspondance approximative », leur suppression sera très difficile.
* Les données transactionnelles doivent être dotées d&#39;une clé de réconciliation et être réconciliées avec les données existantes afin d&#39;éviter la création de doublons.
* **Les fichiers liés doivent être importés dans l&#39;ordre**. Si l&#39;import est composé de fichiers multiples et interdépendants, le workflow doit vérifier que les fichiers sont importés dans l&#39;ordre. Si un fichier échoue, les autres fichiers ne sont pas importés.
* **Dédupliquez**, réconciliez et maintenez la cohérence lorsque vous importez des données.

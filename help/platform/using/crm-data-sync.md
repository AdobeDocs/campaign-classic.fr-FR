---
product: campaign
title: Synchronisation des données des connecteurs CRM
description: Gérer les données entre Campaign et votre gestion de la relation client (CRM)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Salesforce Integration, Microsoft CRM Integration
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '1627'
ht-degree: 100%

---

# Synchroniser les données entre Campaign et le CRM {#data-synchronization}



La synchronisation des données entre Adobe Campaign et la gestion de la relation client (CRM) est réalisée à travers une activité de workflow dédiée : [connecteur CRM](../../workflow/using/crm-connector.md).

Par exemple, pour importer les données Microsoft Dynamics dans Adobe Campaign, créez un workflow du type suivant :

![](assets/crm_connectors_msdynamics_07.png)

Ce workflow importe les contacts depuis Microsoft Dynamics, les synchronise avec les données Adobe Campaign existantes, déduplique les contacts et met à jour la base de données Adobe Campaign.

L&#39;activité **[!UICONTROL Connecteur CRM]** doit être paramétrée pour synchroniser les données.

![](assets/crm_connectors_msdynamics_08.png)

Avec cette activité, vous pouvez effectuer les actions suivantes :

* Import depuis le CRM - [En savoir plus](#importing-from-the-crm)
* Export vers le CRM - [En savoir plus](#exporting-to-the-crm)
* Import des objets supprimés dans le CRM - [En savoir plus](#importing-objects-deleted-in-the-crm)
* Suppression d&#39;objets dans le CRM - [En savoir plus](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Sélectionnez le compte externe correspondant au CRM avec lequel vous souhaitez paramétrer une synchronisation puis choisissez l&#39;objet à synchroniser : comptes, opportunités, leads, contacts, etc.

![](assets/crm_task_select_obj.png)

La configuration de cette activité dépend ensuite du traitement à réaliser. Les différents types de paramétrages sont présentés ci-après.

## Import depuis le CRM {#importing-from-the-crm}

Pour importer des données depuis le CRM dans Adobe Campaign, vous devez réaliser un workflow du type :

![](assets/crm_wf_import.png)

Pour un import, les étapes de paramétrage de l&#39;activité **[!UICONTROL Connecteur CRM]** sont les suivantes :

1. Sélectionnez une opération de type **[!UICONTROL Import depuis le CRM]**.
1. Dans la liste déroulante **[!UICONTROL Objet distant]**, sélectionnez l&#39;objet concerné par le traitement. Cet objet correspond à l&#39;une des tables créées dans Adobe Campaign lors de la configuration du connecteur.
1. Dans la section **[!UICONTROL Champs distants]**, indiquez les champs à importer.

   Pour ajouter un champ, cliquez sur le bouton **[!UICONTROL Ajouter]** de la barre d&#39;outils puis sur l&#39;icône **[!UICONTROL Editer l&#39;expression]**.

   ![](assets/crm_task_import_add_field.png)

   Si nécessaire, modifiez le format des données dans la liste déroulante des colonnes **[!UICONTROL Conversion]**. Les types de conversion possibles sont détaillés dans la section [Format des données](#data-format).

   >[!IMPORTANT]
   >
   >L&#39;identifiant de l&#39;enregistrement dans le CRM est obligatoire pour relier les objets côté CRM et côté Adobe Campaign. Il est automatiquement ajouté lors de la validation de la boîte.
   >
   >La date de la dernière modification côté CRM est également requise pour permettre l&#39;import incrémental des données.

1. Vous pouvez également filtrer les données à importer selon vos besoins. Pour cela, cliquez sur le lien **[!UICONTROL Editer le filtre...]**.

   Dans l&#39;exemple suivant, Adobe Campaign n&#39;importera que les contact ayant eu une activité après le 1er novembre 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >Les limitations relatives au mode de filtrage des données sont décrites dans la section [Filtrer les données](#filtering-data).

1. L&#39;option **[!UICONTROL Utiliser l&#39;index automatique...]** permet de gérer automatiquement la synchronisation incrémentale des objets entre le CRM et Adobe Campaign, selon la date de leur dernière modification.

   Voir à ce sujet la section [Gestion des variables](#variable-management).

### Gérer les variables {#variable-management}

Activez l’option **[!UICONTROL Index automatique]** pour ne collecter que les objets modifiés depuis la dernière exécution de l’import.

![](assets/crm_task_import_option.png)

La date de la dernière synchronisation est stockée dans l&#39;option indiquée dans la fenêtre de paramétrage, par défaut : **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Cette note s&#39;applique uniquement à l&#39;activité **[!UICONTROL Connecteur CRM]** générique. Pour les autres activités CRM, le processus est automatique.
>
>Cette option doit être créée et renseignée manuellement sous **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]**. Il doit s’agir d’une option de texte et sa valeur doit correspondre au format suivant : **aaaa/MM/jj hh:mm:ss**.
> 
>Pour tout autre import, vous devez mettre à jour manuellement cette option.

Vous pouvez indiquer le champ CRM distant à prendre en compte pour identifier les modifications les plus récentes.

Par défaut, les champs suivants sont utilisés (dans l&#39;ordre indiqué) :

* Pour Microsoft Dynamics : **modifiedon**,
* Pour Salesforce.com : **LastModifiedDate**, **SystemModstamp**.

L&#39;activation de l&#39;option **[!UICONTROL Index automatique]** génère trois variables, qui pourront être exploitées dans le workflow de synchronisation, via une activité de type **[!UICONTROL Code JavaScript]**. Ces variables sont les suivantes :

* **vars.crmOptionName** : représente le nom de l&#39;option contenant la date du dernier import.
* **vars.crmStartImport** : représente la date de début (incluse) de la dernière récupération des données.
* **vars.crmEndDate** : représente la date de fin (exclue) de la dernière récupération des données.

   >[!NOTE]
   >
   >Ces dates sont exprimées au format **aaaa/MM/jj hh:mm:ss**.

### Filtrage des données {#filtering-data}

Afin d&#39;assurer un bon fonctionnement avec les différents CRM, les filtres doivent être créés selon les règles suivantes :

* Chaque niveau de filtrage ne peut utiliser qu&#39;un seul type d&#39;opérateur.
* L&#39;opérateur AND NOT n&#39;est pas supporté.
* Les comparaisons ne peuvent porter que sur des valeurs nulles (de type &#39;est vide&#39;/&#39;n&#39;est pas vide&#39;) ou des nombres. Lorsque la colonne Valeur (colonne de droite) est évaluée, le résultat de cette évaluation doit être une valeur numérique.
* Les données de la colonne Valeur sont évaluées en JavaScript.
* Les comparaisons de type JOIN ne sont pas supportées.
* L&#39;expression indiquée dans la colonne de gauche doit nécessairement être un champ. Elle ne peut pas être une combinaison de plusieurs expressions, un nombre, etc.

Par exemple, les critères de filtrage suivants ne seront PAS valides dans le cadre d&#39;un import CRM, car l&#39;opérateur OU est placé au même niveau que les opérateurs ET :

* l&#39;opérateur OU est placé au même niveau que les opérateurs ET
* des comparaisons portent sur des chaînes de texte

![](assets/crm_import_wrong_filter.png)

### Ordre de tri {#order-by}

Sous Microsoft Dynamics et Salesforce.com, vous pouvez trier les champs distants à importer, par ordre descendant ou ascendant.

Pour cela, cliquez sur le lien **[!UICONTROL Ordre de tri]** et ajoutez les colonnes dans la liste.

L&#39;ordre des colonnes dans la liste indique l&#39;ordre de tri :

![](assets/crm_import_order.png)

### Identification des enregistrements {#record-identification}

Plutôt que d&#39;importer directement des éléments contenus (et éventuellement filtrés) dans le CRM, vous pouvez utiliser une population calculée en amont dans le workflow.

Pour cela, sélectionnez l&#39;option **[!UICONTROL Utiliser la population calculée en amont]** et indiquez le champ contenant l&#39;identifiant distant.

Sélectionnez ensuite les champs à importer depuis la population entrante, comme dans l&#39;exemple ci-dessous :

![](assets/crm_wf_import_calculated_population.png)

## Export vers le CRM {#exporting-to-the-crm}

L&#39;export de données Adobe Campaign dans le CRM permet de copier l&#39;intégralité d&#39;un contenu vers une base CRM.

Pour exporter des données vers le CRM, vous devez réaliser un workflow du type :

![](assets/crm_export_diagram.png)

Pour un export, les étapes de paramétrage de l&#39;activité **[!UICONTROL Connecteur CRM]** sont les suivantes :

1. Sélectionnez une opération de type **[!UICONTROL Exporter vers le CRM]**.
1. Dans la liste déroulante **[!UICONTROL Objet distant]**, sélectionnez l&#39;objet concerné par le traitement. Cet objet correspond à l&#39;une des tables créées dans Adobe Campaign lors de la configuration du connecteur.

   >[!IMPORTANT]
   >
   >La fonction d&#39;export de l&#39;activité **[!UICONTROL Connecteur CRM]** peut insérer ou mettre à jour des champs côté CRM. Pour activer les mises à jour des champs dans le CRM, vous devez spécifier la clé primaire de la table distante. Si la clé est manquante, les données sont insérées (au lieu d&#39;être mises à jour).

1. Consultez **[!UICONTROL Exportation par lots]** si vous avez besoin d’exportations plus rapides.

   ![](assets/crm_export_config_2.png)

1. Dans la section **[!UICONTROL Mapping]**, cliquez sur **[!UICONTROL Nouveau]** pour indiquer les champs à exporter et leur mapping dans le CRM.

   ![](assets/crm_export_config.png)

   Pour ajouter un champ, cliquez sur le bouton **[!UICONTROL Ajouter]** de la barre d&#39;outils puis sur l&#39;icône **[!UICONTROL Editer l&#39;expression]**.

   >[!NOTE]
   >
   >Pour un champ, si aucune correspondance n&#39;est définie côté CRM, alors les valeurs ne peuvent pas être mises à jour : elle seront directement insérées dans le CRM.

   Si nécessaire, modifiez le format des données dans la liste déroulante des colonnes **[!UICONTROL Conversion]** . Les types de conversion possibles sont détaillés dans la section [Format des données](#data-format).

   >[!NOTE]
   >
   >La liste des enregistrements à exporter et le résultat de l&#39;export sont conservés dans un fichier temporaire qui reste accessible tant que le workflow n&#39;est pas terminé ou redémarré, ce qui permet de reprendre le traitement en cas d&#39;erreur, sans risquer d&#39;exporter plusieurs fois le même enregistrement et sans perte de données.

## Paramétrages additionnels {#additional-configurations}

### Sur le format des données saisies {#data-format}

Vous pouvez convertir à la volée le format des données lors de leur import depuis le CRM ou lors de leur export vers le CRM.

Pour cela, sélectionnez la conversion à appliquer dans la colonne correspondante.

![](assets/crm_task_import.png)

Le mode **[!UICONTROL par défaut]** applique une conversion automatique des données, qui correspond dans la plupart des cas, à un copier/coller des données. Toutefois, la gestion des fuseaux horaires est appliquée.

Les autres conversions possibles sont les suivantes :

* **[!UICONTROL Date seulement]** : ce mode supprime les heures des champs de type Date + Heure.
* **[!UICONTROL Sans décalage]** : ce mode annule la gestion des fuseaux horaires appliquée dans le mode par défaut.
* **[!UICONTROL Copié/collé]** : ce mode utilise les données brutes comme des chaînes (pas de conversion).

### Traitement des erreurs {#error-processing}

Dans le cadre d&#39;un import ou d&#39;un export de données, il est possible d&#39;appliquer un traitement spécifique aux erreurs et rejets. Pour cela, sélectionnez les options **[!UICONTROL Traiter les rejets]** et **[!UICONTROL Traiter les erreurs]**, dans l&#39;onglet **[!UICONTROL Comportement]**.

![](assets/crm_export_options.png)

Ces options positionnent les transitions sortantes correspondantes.

![](assets/crm_export_transitions.png)

Positionnez ensuite les activités relatives aux traitements à appliquer.

Pour traiter les erreurs, vous pouvez par exemple positionner une boîte d&#39;attente puis planifier des reprises.

Les rejets sont collectés avec leur code d&#39;erreur et le message correspondant, vous pouvez donc mettre en place un tracking des rejets afin d&#39;optimiser vos processus de synchronisation.

>[!NOTE]
>
>Même lorsque l&#39;option **[!UICONTROL Traiter les rejets]** n&#39;est pas activée, un avertissement est généré pour chaque colonne rejetée, avec le code erreur et le message correspondant.

La transition sortante **[!UICONTROL Rejet]** permet d&#39;accéder au schéma de sortie qui contient les colonnes spécifiques relatives aux codes et messages d&#39;erreur. Pour Salesforce.com, cette colonne est **errorSymbol** (symbole de l&#39;erreur, différent du code de l&#39;erreur), **errorMessage** (description du contexte de l&#39;erreur).

## Import d&#39;objets supprimés dans le CRM {#importing-objects-deleted-in-the-crm}

Afin de permettre la mise en place d&#39;un processus exhaustif de synchronisation des données, vous pouvez importer dans Adobe Campaign les objets supprimés côté CRM.

Pour cela, les étapes sont les suivantes :

1. Sélectionnez une opération de type **[!UICONTROL Import des objets supprimés dans le CRM]**.
1. Dans la liste déroulante **[!UICONTROL Objet distant]**, sélectionnez l&#39;objet concerné par le traitement. Cet objet correspond à l&#39;une des tables créées dans Adobe Campaign lors de la configuration du connecteur.
1. Indiquez la période de suppression à prendre en compte dans les champs **[!UICONTROL Date de début]** et **[!UICONTROL Date de fin]**. Ces dates seront incluses dans la période.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >La période de suppression des éléments à récupérer doit correspondre aux limitations propres au CRM. Ainsi, par exemple, pour Salesforce.com, les éléments dont la suppression remonte à plus de 30 jours ne peuvent pas être récupérés.

## Suppression d&#39;objets dans le CRM {#deleting-objects-in-the-crm}

Pour supprimer des objets côté CRM, vous devez indiquer la clé primaire des éléments distants à effacer.

![](assets/crm_delete_in_crm.png)

L&#39;onglet **[!UICONTROL Comportement]** vous permet d&#39;activer le traitement des rejets. Cette option génère une seconde transition en sortie de l&#39;activité **[!UICONTROL Connecteur CRM]**. Voir à ce sujet la section [Traitement des erreurs](#error-processing).

>[!NOTE]
>
>Même lorsque l&#39;option **[!UICONTROL Traiter les rejets]** n&#39;est pas activée, un avertissement est généré pour chaque colonne rejetée.

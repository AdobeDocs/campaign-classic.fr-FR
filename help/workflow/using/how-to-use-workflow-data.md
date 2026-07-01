---
product: campaign
title: Utiliser les données d'un workflow
description: Découvrez comment utiliser les données d'un workflow
feature: Workflows, Data Management
hide: true
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
TQID: https://experienceleague.adobe.com/xasYSu6WyHC0T6CpKn51bZ5K7WlspJAbB0R45AeXb8M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 417
ht-degree: 100%

---

# Utiliser les données d&#39;un workflow{#how-to-use-workflow-data}



## Mettre à jour la base de données {#updating-the-database}

Toutes les données collectées peuvent être utilisées pour mettre à jour la base de données ou dans des diffusions.Vous pouvez, par exemple, enrichir les possibilités de personnalisation du contenu des messages (inclure le nombre de contrats dans le message, indiquer le panier moyen pour l’année écoulée, etc.)ou cibler précisément une population (envoyer un message aux personnes co-titulaires d’un contrat, cibler les 1 000 meilleures personnes abonnées aux services en ligne, etc.).Ces données peuvent également être exportées ou archivées sous forme de liste.

### Listes et mises à jour directes {#lists-and-direct-updates}

Les données de la base Adobe Campaign et les listes existantes peuvent être mises à jour via deux activités dédiées :

* L&#39;activité **[!UICONTROL Mise à jour de liste]** permet de stocker les tables de travail dans une liste de données.

  Vous pouvez sélectionner une liste existante ou en créer-une.Dans ce cas, le nom et éventuellement le dossier d’enregistrement sont calculés.

  ![](assets/s_user_create_list.png)

  Pour plus d&#39;informations, consultez la section [Mise à jour de liste](list-update.md).

* L&#39;activité **[!UICONTROL Mise à jour de données]** permet de mettre à jour en masse les champs de la base de données.

  Pour plus d’informations, consultez la section [Mise à jour de données](update-data.md).

### Gérer les abonnements/désabonnements {#subscription-unsubscription-management}

Pour comprendre comment abonner et désabonner des destinataires à un service d&#39;information via un workflow, consultez la section [Services d’abonnement](subscription-services.md).

## Envoyer via un workflow {#sending-via-a-workflow}

### Activité Diffusion {#delivery-activity}

L’activité de diffusion est présentée dans la section [Diffusion](delivery.md).

### Enrichir et cibler les diffusions {#enriching-and-targeting-deliveries}

Les diffusions peuvent exploiter les données issues des workflows pour personnaliser le contenu ou dans le cadre de la sélection de la population cible.

Par exemple, dans le cadre d&#39;une diffusion courrier, vous pouvez inclure dans le fichier d&#39;extraction les données additionnelles issues des manipulations de données réalisées dans le workflow :

![](assets/s_advuser_add_data_postal_mail.png)

Outre les champs de personnalisation habituels, vous pouvez ajouter des champs de personnalisation des étapes de workflow au contenu de la diffusion. Les données supplémentaires définies dans les activités du workflow peuvent être conservées et rendues accessibles dans l’assistant de diffusion, comme dans l’exemple ci-dessous, afin de définir le nom du fichier de sortie dans le cadre de la diffusion courrier :

![](assets/s_advuser_using_additional_data.png)

Les données contenues dans la table du workflow sont identifiables par leur nom : il est toujours composé du lien **targetData**. Pour plus d’informations, consultez la section [Données de la cible](data-life-cycle.md#target-data).

Dans le cadre d&#39;une diffusion par email, les champs de personnalisation peuvent également utiliser les données issues de l&#39;extension de la cible réalisée dans les étapes du workflow de ciblage, comme dans l&#39;exemple ci-dessous :

![](assets/s_advuser_add_data_email.png)

Si un code segment est spécifié dans une activité de ciblage, il est ajouté dans une colonne spécifique de la table du workflow et il sera proposé avec les champs de personnalisation. Pour afficher tous les champs de personnalisation, cliquez sur le lien **[!UICONTROL Extension de la cible > Autre]** accessible au moyen du bouton de personnalisation.

![](assets/s_advuser_segment_code_select.png)

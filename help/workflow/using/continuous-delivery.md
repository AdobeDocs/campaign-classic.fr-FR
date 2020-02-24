---
title: Diffusion (au fil de l'eau)
seo-title: Diffusion (au fil de l'eau)
description: Diffusion (au fil de l'eau)
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Diffusion (au fil de l&#39;eau){#continuous-delivery}

Une activité de type **Diffusion au fil de l&#39;eau** permet d&#39;ajouter de nouveaux destinataires à une action de diffusion existante. Ce type de diffusion évite de créer une diffusion complète à chaque fois : ce mode de fonctionnement est souvent plus efficace, notamment pour les notifications ou alertes de faible volume effectuées au fil de l&#39;eau. Au niveau du modèle de diffusion, vous pouvez indiquer un script de calcul du libellé (et du dossier de campagne) de la diffusion associée. Si le script calcule une diffusion qui n&#39;existe pas encore, elle est alors créée à la volée.

![](assets/edit_diffusion_fil.png)

L&#39;option **[!UICONTROL Traiter les erreurs]** fait apparaître une transition particulière qui sera activée si une erreur est générée. Dans ce cas, le workflow ne passe pas en état d&#39;erreur et continue son exécution.

Les erreurs prises en compte sont les erreurs du système de fichiers (impossible de déplacer un fichier, impossible d&#39;accéder au répertoire, etc.).

Cette option ne traite pas les erreurs liées au paramétrage de l&#39;activité, c&#39;est-à-dire des valeurs invalides.

## Paramètres d&#39;entrée {#input-parameters}

* tableName
* schema

Chacun des événements entrants doit spécifier une cible définie par ces paramètres.

Uniquement lorsque l&#39;action **[!UICONTROL Spécifiés par l&#39;événement entrant]** est sélectionnée.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Ce triplet de valeurs identifie la cible résultant de la diffusion à la volée. **[!UICONTROL tableName]** est le nom de la table qui mémorise les identifiants de la cible, **[!UICONTROL schema]** est le schéma de la population (habituellement nms:recipient) et **[!UICONTROL recCount]** est le nombre d&#39;éléments dans la table.

La transition associée au complémentaire possède les mêmes paramètres.

---
product: campaign
title: Diffusion au fil de l'eau
description: Diffusion au fil de l'eau
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '369'
ht-degree: 100%

---

# Diffusion au fil de l&#39;eau{#continuous-delivery}



Une action de type **diffusion au fil de l’eau** permet d‘ajouter de nouveaux destinataires à une diffusion existante. Ce type de diffusion évite d’avoir à créer une diffusion à chaque fois. Ce mode est souvent plus efficace, en particulier pour les alertes de faible volume ou les notifications envoyées selon les besoins.

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](#continuous-delivery-video)

Au niveau du modèle de diffusion, vous pouvez spécifier un script pour calculer le libellé (et le dossier de campagne) de la diffusion associée. Si le script calcule une diffusion qui n’existe pas encore, elle est créée à la volée.

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

## Comment configurer une diffusion au fil de l’eau

Cette section explique comment configurer une diffusion au fil de l’eau.

Une **diffusion au fil de l’eau** permet d&#39;ajouter de nouveaux destinataires à une diffusion existante, ce qui évite d&#39;avoir à créer une diffusion chaque fois qu’un nouveau destinataire est ajouté. Vous pouvez mettre à jour le contenu créatif directement dans le workflow de campagne et le modèle sera mis à jour dans le dossier Ressource du modèle de diffusion.

Une diffusion au fil de l’eau crée une diffusion et des logs de diffusion UNIQUES (broadLog) et des logs de tracking qui font référence à l&#39;ajout d&#39;une diffusion chaque fois qu&#39;elle s&#39;exécute.

![Diffusion au fil de l’eau](assets/delivery_continuous.jpg)

## Tutoriel vidéo {#continuous-delivery-video}

Cette vidéo montre comment configurer une diffusion en continu avec une requête incrémentale.

>[!VIDEO](https://video.tv.adobe.com/v/30233?quality=12&captions=fre_fr)

D’autres vidéos pratiques sur Campaign Classic sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).

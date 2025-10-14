---
product: campaign
title: FAQ sur les workflows
description: FAQ Campaign Classic
feature: Troubleshooting, Workflows
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7d1bb3c6-d056-4212-9500-75459a0046fa
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 65%

---

# FAQ sur les workflows {#workflows-faq}



Apprenez à orchestrer les processus et les tâches à l&#39;aide des workflows Adobe Campaign.

## Quelles sont les principales étapes pour créer un workflow ? {#what-are-the-key-steps-to-create-a-workflow-}

Découvrez comment créer votre premier workflow dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=fr){target="_blank"} : découvrez les concepts et les bonnes pratiques pour créer des workflows dans Campaign.

## Comment importer des données dans Campaign ? {#how-can-i-import-data-in-campaign-}

Découvrez les bonnes pratiques pour importer des données dans [cette section](../../platform/using/import-export-best-practices.md).

## Est-il possible de surveiller l’exécution des workflows ? {#can-i-monitor-workflow-execution-}

Découvrez comment surveiller l&#39;exécution des workflows Campaign dans la documentation de [Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution)
.html){target="_blank"}.

## Comment mettre à jour les données de Campaign avec un workflow ? {#how-can-i-update-campaign-data-with-a-workflow-}

Vous pouvez effectuer une mise à jour, une fusion et une insertion massives sur la base de données.

Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html?lang=fr){target="_blank"}.

## Comment utiliser les fonctionnalités de Data Management ? {#how-can-i-leverage-data-management-capabilities-}

Dans Adobe Campaign, vous pouvez utiliser un ensemble d&#39;activités permettant de répondre à des problématiques complexes de ciblage en proposant des outils plus efficaces et plus souples. Les activités de Data Management permettent de mettre en place une gestion cohérente de toutes les communications vers un contact, en utilisant les informations liées à ses contrats, ses abonnements, sa réactivité aux diffusions, etc. Le Data Management permet de suivre le cycle de vie des données lors des opérations de segmentation, notamment :

* simplifier et optimiser les processus de ciblage, y compris en incluant des données qui n&#39;ont pas été modélisées dans le datamart (création de nouvelles tables : extension locale à chaque workflow de ciblage, en fonction de son paramétrage).
* conserver et véhiculer des calculs intermédiaires, notamment dans les phases de construction des cibles ou pour l&#39;administration des bases de données.
* accéder aux bases externes (optionnel) : prise en compte de bases de données hétérogènes dans le processus de ciblage.

Découvrez comment concevoir une cible complexe et travailler sur vos données en combinant les activités de workflow de gestion des données dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html?lang=fr){target="_blank"}.

## Est-il possible d&#39;automatiser l&#39;envoi de messages personnalisés ? {#can-i-automate-personalized-messages-sending-}

Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/enrich-data.html?lang=fr){target="_blank"} pour savoir comment envoyer des messages personnalisés à des personnes en fonction de leurs scores les plus élevés dans un jeu-concours.

## Comment partager une audience en sous-ensembles avec un workflow ? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

Découvrez comment diviser une cible en plusieurs sous-ensembles dans la documentation de [Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=fr){target="_blank"}.

## Comment mettre à jour les données des destinataires à partir d&#39;un fichier externe ? {#how-can-i-update-recipient-data-from-an-external-file-}

Vous pouvez modifier certains champs dans une table Campaign avec les valeurs d&#39;un fichier texte externe.

[Cliquez ici pour découvrir comment](../../platform/using/import-operations-samples.md#example--enrich-the-values-with-those-of-an-external-file).

## Comment identifier et cibler de nouveaux destinataires ? {#how-can-i-identify-and-target-new-recipients-}

Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html?lang=fr){target="_blank"} pour découvrir comment utiliser des agrégats afin d’identifier automatiquement les derniers destinataires ajoutés à la base de données et leur envoyer un message de bienvenue.

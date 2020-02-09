---
title: Utilisation du tableau Destinataire d’Adobe Campaign Classic
description: Découvrez comment utiliser le tableau de destinataires prêt à l’emploi dans Adobe Campaign Classic lors de la conception de votre modèle de données.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# Meilleures pratiques du modèle de données{#data-model-best-practices}

Vous trouverez ci-dessous quelques bonnes pratiques à suivre lors de la conception de votre modèle de données à l’aide de tableaux volumineux et de jointures complexes.

* Lors de l’utilisation de tables de destinataires personnalisées supplémentaires, veillez à disposer d’une table de journaux dédiée pour chaque mappage de remise.
* Réduisez le nombre de colonnes, notamment en identifiant celles qui ne sont pas utilisées.
* Optimisez les relations du modèle de données en évitant les jointures complexes, telles que les jointures sur plusieurs conditions et/ou plusieurs colonnes.
* Pour les clés de jointure, utilisez toujours des données numériques plutôt que des chaînes de caractères.
* Réduisez autant que possible la profondeur de rétention du journal. Si vous avez besoin d’un historique plus détaillé, vous pouvez agréger le calcul et/ou gérer des tables de journaux personnalisées pour stocker un historique plus volumineux.

Pour plus d’informations sur les meilleures pratiques relatives à l’optimisation de la conception de base de données pour des volumes plus importants, voir [Campagne Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).

---
title: À propos du modèle de données Adobe Campaign Classic
description: Ce document décrit les bases du modèle de données Adobe Campaign Classic.
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
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Using a custom recipient table{#custom-recipient-table}

Lors de la conception de votre modèle de données Adobe Campaign, vous pouvez utiliser le tableau [](../../configuration/using/default-recipient-table.md)Destinataire prêt à l’emploi ou décider de créer un tableau de destinataires non standard pour stocker vos profils marketing.

En effet, si votre modèle de données ne correspond pas à la structure axée sur les destinataires, vous pouvez configurer d’autres tableaux comme dimension de ciblage dans Adobe Campaign. Par exemple, cela peut être pertinent lorsque vous devez cibler les ménages, les comptes (comme les téléphones portables) et les entreprises/sites plutôt que simplement les destinataires.

>[!NOTE]
>
>Dans ce cas, vous devrez créer un nouveau mappage [de](../../configuration/using/target-mapping.md)cible.

Tous les principes et étapes nécessaires lors de l’utilisation d’un tableau de destinataires personnalisé sont détaillés dans cette [section](../../configuration/using/about-custom-recipient-table.md).

Les avantages de l’utilisation d’un tableau Destinataire personnalisé sont les suivants :

## Modèle de données flexible {#flexible-data-model}

Le tableau Destinataire prêt à l’emploi est inutile si vous n’avez pas besoin de la plupart des champs de la table Destinataire ou si le modèle de données n’est pas centré sur le destinataire.

## Évolutivité {#scalability}

Les gros volumes nécessitent un tableau rationalisé avec peu de champs pour une conception efficace. Le tableau des destinataires prêts à l’emploi comporterait trop de champs inutiles, ce qui pourrait avoir un impact sur les performances et un manque d’efficacité.

## Emplacement des données {#data-location}

Si les données résident dans une base de données marketing externe existante, il peut s’avérer nécessaire de faire trop d’efforts pour utiliser la table Destinataire prête à l’emploi. Il est plus simple de créer une structure basée sur une structure existante.

## Migration aisée {#easy-migration}

Aucune maintenance n’est nécessaire pour vérifier que toutes les extensions sont toujours valides lors de la mise à niveau.

>[!IMPORTANT]
>
>L’utilisation d’une table de destinataires personnalisée est réservée aux utilisateurs avancés et est soumise à certaines restrictions. Voir à ce propos cette section.

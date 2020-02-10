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
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Extension du modèle de données{#extending-data-model}

Lorsque vous commencez par Adobe Campaign, vous devez évaluer le modèle de données par défaut pour vérifier quel tableau est le mieux adapté au stockage de vos données marketing.

Le cas échéant, vous pouvez utiliser le tableau Destinataire par défaut avec les champs prêts à l’emploi, comme décrit dans cette [section](../../configuration/using/default-recipient-table.md).

Si nécessaire, vous pouvez l’étendre avec deux mécanismes :

* Etendez un tableau existant avec de nouveaux champs. Par exemple, vous pouvez ajouter un nouveau champ &quot;Fidélité&quot; à la table Destinataire.
* Créez une table, par exemple une table &quot;Achat&quot; répertoriant tous les achats effectués par chaque profil de la base de données et liez-la à la table Destinataire.

Pour plus d’informations sur la configuration des schémas d’extension pour étendre le modèle de données conceptuelles, voir [A propos de l’édition](../../configuration/using/about-schema-edition.md)de schémas.

>[!IMPORTANT]
>
>L’extension du modèle de données est réservée aux utilisateurs avancés.

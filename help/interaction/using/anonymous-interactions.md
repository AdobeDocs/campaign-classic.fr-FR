---
title: Interactions anonymes
seo-title: Interactions anonymes
description: Interactions anonymes
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8e37be4f764feadb49c70a9d598f8f3b8f864380

---


# Interactions anonymes{#anonymous-interactions}

Regardez cette [vidéo](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) pour obtenir un aperçu de la manière dont les offres sont diffusées sur des cibles identifiées et anonymes.

## Ciblage et stockage d&#39;un environnement pour interactions anonymes {#targeting-and-storing-an-environment-for-anonymous-interactions}

Par défaut, l’interaction est fournie avec un environnement préconfiguré pour cibler la table des destinataires (offres identifiées). Si vous souhaitez cibler une autre table (table des visiteurs pour les offres anonymes ou table des destinataires spécifique), vous devez utiliser l’assistant de mappage de cible pour créer l’environnement. For more on this, see [Creating an offer environment](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Lorsque vous créez un environnement anonyme via l’assistant de création de mappage, la **[!UICONTROL Environment dedicated to incoming anonymous interactions]** zone est automatiquement cochée dans l’onglet **[!UICONTROL General]** de l’environnement.

La **[!UICONTROL Targeting dimension]** procédure est automatiquement terminée. Par défaut, il est lié au tableau des visiteurs.

Le **[!UICONTROL Visitor folder]** champ apparaît. Le lien vers le **[!UICONTROL Visitors]** dossier est automatiquement terminé. Ce champ vous permet de choisir l’emplacement de stockage des profils des visiteurs.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>If you want to filter several types of visitors, for instance in the case of anonymous offers presented for one or more brands, you need to create an environment for each brand, and a **[!UICONTROL Visitors]** type folder for each environment.

## Catalogue d&#39;offres pour interactions anonymes {#offer-catalog-for-anonymous-interactions}

Comme les interactions sortantes, les interactions entrantes sont organisées au sein d&#39;un catalogue d&#39;offres composé de catégories et d&#39;offres.

Pour créer des catégories et des espaces, appliquez le même processus que pour les visiteurs identifiés (voir [Création de catégories](../../interaction/using/creating-offer-categories.md) d’offres et [Création d’un environnement](../../interaction/using/live-design-environments.md#creating-an-offer-environment)d’offres).

## Les visiteurs anonymes {#anonymous-visitors}

Les visiteurs anonymes peuvent être soumis à un processus d&#39;identification par cookies intervenant au moment de la connexion. Cette reconnaissance implicite s&#39;effectue à partir de l&#39;historique de navigation du visiteur.

Durant cette étape, un rapprochement est effectué entre les données récupérées par les cookies et celles contenues dans votre base de données. Dans certains cas, le visiteur est reconnu (il est alors identifié implicitement), dans d&#39;autres, il ne l&#39;est pas (et reste donc anonyme).

Pour exécuter cette analyse, cochez l’ **[!UICONTROL Implicitly identify the individual based on their browser history]** option correspondant à l’espace d’offre.

![](assets/identification_anonymous_visitors.png)

## Traitement des visiteurs anonymes non identifiés {#processing-unidentified-anonymous-visitors}

Après analyse, si un visiteur anonyme n&#39;est pas identifié, il vous est possible de stocker ses données dans un emplacement donné, ce qui vous permettra de proposer des offres spécifiquement destinées à ce type de visiteurs, répondant à des règles de typologie précises.

En cas d&#39;absence d&#39;élément permettant d&#39;identifier un contact ou si vous ne souhaitez pas proposer d&#39;offre identifiée à un contact pouvant être identifié implicitement, vous pouvez choisir d&#39;effectuer un basculement vers un environnement anonyme.

Pour ce faire, vérifiez le **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**, puis spécifiez l’environnement dédié à ces visiteurs non identifiés dans le **[!UICONTROL Linked anonymous space]** lorsque vous spécifiez un espace d’offre.

![](assets/anonymous_to_anonymous_environment.png)


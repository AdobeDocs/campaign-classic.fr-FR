---
title: Définir un contenu conditionnel
seo-title: Définir un contenu conditionnel
description: Définir un contenu conditionnel
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Définir un contenu conditionnel{#defining-a-conditional-content}

Vous pouvez conditionner l&#39;affichage de certains éléments d&#39;un rapport ou d&#39;une ou plusieurs pages du rapport.

Pour rendre des éléments spécifiques conditionnels, adaptez leurs paramètres de visibilité. For more on this, refer to [Conditioning item display](#conditioning-item-display).

Pour rendre l’affichage d’une ou de plusieurs pages conditionnel, utilisez une activité de **[!UICONTROL Test]** type. Voir à ce sujet la section [Conditionner l&#39;affichage d&#39;une page](#conditioning-page-display).

## Conditionner l&#39;affichage d&#39;un élément {#conditioning-item-display}

Pour rendre l&#39;affichage d&#39;une partie d&#39;un rapport conditionnel, vous devez définir ses conditions de visibilité : si ces conditions ne sont pas remplies, alors le ou les éléments ne seront pas affichés.

Les conditions de visibilité peuvent dépendre par exemple du statut de l&#39;opérateur ou des éléments qu&#39;il a sélectionnés ou renseignés dans la page du rapport.

Des exemples d&#39;affichages conditionnels des éléments d&#39;une page sont proposés dans [cette section](../../web/using/form-rendering.md#defining-fields-conditional-display).

Dans l&#39;exemple suivant, la condition d&#39;affichage dépend de la langue :

![](assets/reporting_display_condition.png)

## Conditionner l&#39;affichage d&#39;une page {#conditioning-page-display}

Dans le diagramme d&#39;un rapport, l&#39;activité **[!UICONTROL Test]** vous permet de modifier l&#39;enchaînement des pages du rapport en fonction d&#39;une ou plusieurs conditions.

Le principe de fonctionnement de cette activité est le suivant :

1. Positionnez un **[!UICONTROL Test]** dans le diagramme puis éditez-le.
1. Click the **[!UICONTROL Add]** button to create the various possible cases.

   ![](assets/reporting_test_sample.png)

   Chaque cas ajoute une transition de sortie supplémentaires à l&#39;activité **[!UICONTROL Test]**.

   ![](assets/reporting_test_transitions.png)

1. Select the **[!UICONTROL Enable default transition]** to add a transition, in case one of the configured conditions isn&#39;t met.

   Voir à ce propos [cette section](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

Une activité **[!UICONTROL Test]** peut être positionnée en début de diagramme afin de conditionner l&#39;affichage selon le contexte par exemple, ou le profil de l&#39;opérateur.

---
title: A propos de l'éditeur HTML de Campaign
seo-title: A propos de l'éditeur HTML de Campaign
description: A propos de l'éditeur HTML de Campaign
seo-description: null
page-status-flag: never-activated
uuid: 1b1d392d-4f19-4092-b57d-02051a242675
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 1ffe9f58-7258-4794-a314-524065f8a33b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# A propos de l&#39;éditeur HTML de Campaign{#about-campaign-html-editor}

Le **Digital Content Editor (DCE)** est un éditeur de contenus HTML qui permet de créer ou modifier facilement des modèles ou du contenu au format HTML dans Adobe Campaign.

Le Digital Content Editor permet de faciliter l&#39;insertion et la mise en forme d&#39;éléments de la page ainsi que l&#39;association des champs de la base avec les éléments d&#39;une page HTML. Il est proposé par défaut lors de la création d&#39;une page d&#39;une application Web, ou disponible lors de la création de diffusions basées sur un modèle dans lequel il est actif.

>[!NOTE]
>
>Le DCE permet uniquement d&#39;effectuer les opérations décrites dans cette section.
>
>Si vous souhaitez ajouter du code JavaScript côté serveur, il convient de le faire dans des blocs de personnalisation. Pour plus d’informations sur la création et la modification des blocs de personnalisation, consultez [cette page](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

## Fonctionnement général de l&#39;éditeur de contenus {#content-editor-general-operation}

Cette section présente les grandes étapes d&#39;édition et de mise en ligne d&#39;un contenu édité avec le DCE dans le cadre d&#39;une application web et dans le contexte d&#39;une diffusion.

Le fonctionnement général est le suivant :

![](assets/dce_schema.png)

Pour créer une application Web simple, procédez comme suit :

* Pour plus d&#39;informations, reportez-vous à la section [Création d&#39;une page](../../web/using/creating-a-landing-page.md)d&#39;entrée,
* Select existing content or creating content from a standard template, for more on this, refer to [Template management](../../web/using/template-management.md),
* Pour plus d’informations sur ce sujet, reportez-vous à la section [Modification du contenu](../../web/using/editing-content.md),
* Publish the Web application, for more on this, refer to [Publishing content](../../web/using/creating-a-landing-page.md#step-3---publishing-content) and [this page](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of a Web application, refer to [Creating a landing page](../../web/using/creating-a-landing-page.md).

Dans le contexte d&#39;une diffusion par email, les étapes de création sont les suivantes :

* Créez une diffusion à partir d’un modèle de type de courrier électronique dans lequel le DCE est actif,
* Sélectionnez un contenu existant ou créez du contenu à partir d’un modèle standard,
* Modifier et configurer le contenu en ligne,
* Envoyez la livraison, pour plus d&#39;informations, reportez-vous à [cette section](../../delivery/using/communication-channels.md).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of an email delivery, refer to [this use case](../../web/using/use-case--creating-an-email-delivery.md).


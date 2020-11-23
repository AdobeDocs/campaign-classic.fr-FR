---
solution: Campaign Classic
product: campaign
title: A propos de l'éditeur HTML de Campaign
description: A propos de l'éditeur HTML de Campaign
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 100%

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

Dans le contexte d&#39;une application Web simple, les étapes de création sont les suivantes :

* Création d’une application web, lire à ce sujet la section [Créer une landing page](../../web/using/creating-a-landing-page.md),
* Sélection d&#39;un contenu existant ou création d&#39;un contenu à partir d&#39;un modèle standard, lire à ce sujet la section [Gestion des modèles](../../web/using/template-management.md),
* Édition et configuration du contenu, lire à ce sujet la section [Editer le contenu](../../web/using/editing-content.md),
* Publication de l’application web, lire à ce sujet la section [Publier le contenu](../../web/using/creating-a-landing-page.md#step-3---publishing-content) et [cette page](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>Pour un exemple complet de mise en œuvre du DCE dans le cadre d&#39;une application Web, consultez la section [Créer une landing page](../../web/using/creating-a-landing-page.md).

Dans le contexte d&#39;une diffusion par email, les étapes de création sont les suivantes :

* Création d&#39;une diffusion à partir d&#39;un modèle de type email dans lequel le DCE est activé,
* Sélection d&#39;un contenu existant ou création d&#39;un contenu à partir d&#39;un modèle standard,
* Modification et configuration du contenu en ligne,
* Envoi de la diffusion, lire à ce sujet [cette section](../../delivery/using/steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Pour un exemple complet de mise en œuvre du DCE dans le cadre d&#39;une diffusion par emai, consultez [ce cas d’utilisation](../../web/using/use-case--creating-an-email-delivery.md).


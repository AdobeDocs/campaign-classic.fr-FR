---
product: campaign
title: Prise en main des applications web
description: Créer et partager des applications web, des landing pages et des questionnaires
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
TQID: https://experienceleague.adobe.com/GP-1vCAYzcgjaOyUs-Zkx6rXOLSNbpF7962OEMsw5YM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a7760dfc-5c44-4d77-bb68-c50b1e265c93id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 730
ht-degree: 73%

---

# Prise en main des applications web{#about-web-applications}



Adobe Campaign permet la création d’applications web dynamiques et interactives, composées de données issues de la base et dont le contenu est adapté en fonction des droits de l’utilisateur connecté.

Vous pouvez créer des pages, telles qu&#39;un formulaire d&#39;édition sur un extranet, ou des formulaires de notification incluant des données de la base de données avec des tableaux, graphiques, formulaires de saisie, etc. Cette fonctionnalité vous permet de concevoir et de publier des pages web dans lesquelles les utilisateurs peuvent rechercher ou saisir des informations.

Il peut par exemple s’agir d’un formulaire d’inscription dont les données ont été pré-remplies avec les informations contenues dans la base Adobe Campaign, comme dans l’exemple ci-dessous :

![](assets/webapp_form_sample.png)

Ce chapitre présente la gestion des applications web.

>[!NOTE]
>
>Consultez la [Liste de contrôle relative à la sécurité et à la confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html) pour savoir comment optimiser la sécurité pour les applications web.

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d’utiliser HTTPS pour toutes les ressources externes.

## Portée des applications web {#web-application-scope}

Sous Adobe Campaign, les applications web permettent d’accéder aux fonctionnalités suivantes :

* Création de formulaires multi-pages. Voir à ce propos [cette page](about-web-forms.md).
* Gestion de formulaires multilingues, avec un outil de traduction intégré. Voir à ce propos [cette page](translating-a-web-application.md).
* Interface graphique de gestion des pages, mise en page en multi-colonnes. Voir à ce propos [cette page](designing-a-web-application.md).
* Personnalisation du rendu et du positionnement des champs. Voir à ce propos [cette page](editing-content.md#adding-personalization-content).
* Affichage conditionnel des champs du formulaire en fonction des réponses. Voir à ce propos [cette page](form-rendering.md#defining-fields-conditional-display).
* Affichage aléatoire de questions. Voir à ce propos [cette page](../../surveys/using/building-a-survey.md#adding-questions).
* Affichage conditionnel des pages. Voir à ce propos [cette page](defining-web-forms-page-sequencing.md#conditional-page-display).
* Vérification des informations avant validation en fonction du type de données attendu (numéro, adresse e-mail, date, etc.) et les champs obligatoires. Pour en savoir plus à ce sujet, consultez cette [page](form-rendering.md#defining-control-settings).
* Invitations ou notifications par e-mail. Voir à ce propos [cette page](publishing-a-web-form.md#delivering-a-form-via-email).
* Personnalisation des messages d’erreur et de fin. Voir à ce propos [cette page](defining-web-forms-properties.md#setting-up-an-error-page).
* Utilisation d&#39;images, vidéos, liens hypertextes, captcha, etc. Voir à ce propos cette [page](editing-content.md).
* Suivi des réponses en temps réel. Voir à ce propos [cette page](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).

Le module de création **Questionnaire** optionnel offre les fonctionnalités additionnelles suivantes :

* Extension dynamique de la base de données : création de réponses ne faisant pas partie du modèle de données initial. Voir à ce propos [cette page](../../surveys/using/managing-answers.md#storing-collected-answers).
* Génération de rapports dédiés. Voir à ce propos [cette page](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).

Par rapport aux applications Web, les questionnaires proposent une interface graphique allégée : le nombre de contrôles d’édition est réduit.

>[!NOTE]
>
>Les enquêtes sont présentées dans [cette section](../../surveys/using/about-surveys.md).
>
>Les fonctionnalités générales des formulaires web sous Adobe Campaign sont présentées dans [cette section](about-web-forms.md).

## Implémentation d’applications web {#web-application-implementation}

Pour créer et rendre disponible une application web, vous devez :

1. Créer le contenu (champs, listes, tableaux, graphiques, etc.)

   Vous pouvez également consulter la section qui présente les champs disponibles pour les formulaires : tous ces champs sont aussi disponibles pour les applications web. Ces informations sont disponibles dans [cette page](adding-fields-to-a-web-form.md).

1. Ajouter, au besoin, des étapes de préchargement, de test, d’enregistrement et paramétrer le contrôle d’accès (principalement dans le cadre d’une publication sur un extranet).
1. Publier l’application web pour la rendre disponible sur un extranet ou dans Adobe Campaign.

## Configuration initiale des applications web {#web-application-initial-configuration}

Les application web sont créées à partir du lien **[!UICONTROL Applications web]** dans les onglets **[!UICONTROL Campagne]** et **[!UICONTROL Profils et cibles]**.

Les applications web sont stockées dans le nœud **[!UICONTROL Ressources > En ligne > Applications Web]** de l&#39;arborescence Adobe Campaign. Les configurations sont réparties dans les dossiers suivants :

* **[!UICONTROL Administration > Paramétrage > Rendus des formulaires]** : contient les modèles de rendu pour la présentation des formulaires Web (applications et questionnaires). Le modèle permet de générer le formulaire. Il utilise également une feuille de style CSS. Cette feuille de style peut être surchargée au niveau du modèle. Pour plus d’informations, consultez [cette page](form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Ressources > Modèles > Modèles d’application web]** : contient des modèles de formulaire. Pour créer un formulaire ou une application Web, vous devez partir d&#39;un modèle.

## Modèles d’applications web {#web-application-templates}

Par défaut, Adobe Campaign fournit un modèle par type d’application web disponible sur votre instance.

>[!NOTE]
>
>Vous pouvez convertir une application web existante en modèle. Pour ce faire, sélectionnez le formulaire et cliquez avec le bouton droit de la souris. Choisissez **[!UICONTROL Actions > Sauver comme modèle]**.

Vous pouvez créer des modèles à partir du nœud **[!UICONTROL Ressources > Modèles > Modèles d’applications web]** de l’arborescence Adobe Campaign.

L’assistant de création vous permet de sélectionner les options à activer, comme dans l’exemple ci-dessous.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Les applications disponibles dépendent de vos options et modules. Veuillez vérifier votre accord de licence.

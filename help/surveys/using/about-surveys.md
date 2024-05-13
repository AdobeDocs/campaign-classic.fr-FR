---
product: campaign
title: Prise en main des questionnaires
description: Prise en main des questionnaires Campaign
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '544'
ht-degree: 100%

---

# Prise en main des questionnaires{#about-surveys}



Adobe Campaign comprend un module graphique pour définir et publier des applications Web. Il est utilisé pour créer des pages, telles qu&#39;un formulaire d&#39;édition sur un réseau extranet, ou des formulaires de notification comprenant des données de la base de données avec des tableaux, graphiques, formulaires de saisie, etc. Utilisez cette fonctionnalité pour concevoir et publier des pages web dans lesquelles les utilisateurs peuvent rechercher ou saisir des informations.

Le module complémentaire **Questionnaire** facultatif permet de créer un nouveau type d&#39;application web pour créer et gérer des questionnaires en ligne, tels que des formulaires permettant d&#39;ajouter ou de modifier des informations de profil, de vous abonner ou de vous désabonner d&#39;une publication, ou un formulaire de participation à un concours. Une fois les réponses collectées, elles sont stockées dans la base de données ou dans des variables locales. Le modèle de données peut être étendu dynamiquement à l&#39;aide des réponses données aux questionnaires. Vous pouvez visualiser les résultats en temps réel, filtrer les réponses et les analyser à l&#39;aide de graphiques dédiés.

Ce chapitre présente la création et la gestion des **formulaires**, la gestion des champs et des pages, les modes de stockage et les enregistrements.

Découvrez comment créer votre premier questionnaire dans [cette page](getting-started-with-surveys.md).

>[!NOTE]
>
>* Les étapes détaillées de création d&#39;un formulaire web standard sont présentées dans [ce document](../../web/using/about-web-forms.md).
>
>* La gestion des applications web est présentée dans [ce document](../../web/using/about-web-applications.md). Pour plus d&#39;informations, reportez-vous à ce chapitre.

## Périmètre de la fonctionnalité {#campaign-surveys-scope}

Dans Adobe Campaign, utilisez [Applications Web](../../web/using/about-web-forms.md) pour :

* créer des formulaires multi-pages ;
* gérer des formulaires multilingues avec un outil de traduction intégré ;
* gérer l&#39;interface graphique, la mise en page en multi-colonnes ;
* ajouter une personnalisation et définir la position du champ ;
* conditionner l&#39;affichage des champs du formulaire en fonction des réponses ;
* conditionner l&#39;affichage de la page ;
* vérifier les informations avant validation, en fonction du type de données attendu (nombre, adresse e-mail, date, etc.) et les champs obligatoires ;
* envoyer des invitations/notifications par e-mail ;
* personnaliser les pages d&#39;erreur et de fin ;
* ajouter des images, vidéos, liens hypertexte, Captcha, etc., dans les formulaires.

Le module facultatif de création de questionnaires propose une interface utilisateur conviviale et les fonctionnalités supplémentaires suivantes :

* Extension dynamique de la base de données : création de réponses qui ne font pas partie du modèle de données initial. [En savoir plus](../../surveys/using/managing-answers.md#storing-collected-answers).
* Gestion des scores. [En savoir plus](../../surveys/using/managing-answers.md#score-management).
* Affichage aléatoire des questions. [En savoir plus](../../surveys/using/building-a-survey.md#adding-questions).
* Tracking en temps réel des réponses. [En savoir plus](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).
* Génération de rapports dédiés. [En savoir plus](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).


## Étapes dʼimplémentation {#surveys-implementation-steps}

Pour créer, diffuser et exploiter les résultats d&#39;un questionnaire, les étapes sont les suivantes :

1. Créer la ou les pages et leur contenu (champs de saisie, listes déroulantes, questions, etc.).
1. Définir le mode d&#39;enregistrement des réponses. Il est possible d&#39;insérer une étape de préchargement des données afin de préremplir le formulaire avec les données déjà en base. Vous pouvez également ajouter une boîte de test.
1. Publiez puis diffusez le questionnaire aux destinataires (par exemple, incluez un lien dans une diffusion ou dans un site Web).
1. Suivre les réponses et consulter les rapports.

Pour plus d&#39;informations sur la configuration et le séquencement de ces étapes, voir [ce document ](../../web/using/about-web-forms.md). Seules les configurations spécifiques aux questionnaires sont détaillées dans ce chapitre.

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

## Paramètres       {#settings}

Par défaut, les questionnaires sont disponibles dans le nœud **[!UICONTROL Ressources > En ligne > Applications Web]** de l&#39;arborescence Adobe Campaign.

Les paramètres sont stockés dans les dossiers suivants :

* **[!UICONTROL Administration > Paramétrage > Rendus des formulaires]** : contient les modèles de rendu pour la présentation des formulaires Web (applications et questionnaires).
* **[!UICONTROL Ressources > Modèles > Modèles d&#39;application Web]** : contient des modèles de formulaires. Pour créer un formulaire, vous devez partir d&#39;un modèle.

>[!NOTE]
>
>Les détails des paramètres sont disponibles dans [ce document](../../web/using/about-web-forms.md).

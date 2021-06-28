---
product: campaign
title: Prise en main des questionnaires
description: Prise en main des questionnaires Campaign
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 37%

---

# Prise en main des questionnaires{#about-surveys}

Adobe Campaign comprend un module graphique pour définir et publier des applications Web. Il est utilisé pour créer des pages, telles qu’un formulaire d’édition sur un extranet, ou des formulaires de notification comprenant des données de la base avec des tableaux, graphiques, formulaires de saisie, etc. Utilisez cette fonctionnalité pour concevoir et publier des pages web dans lesquelles les utilisateurs peuvent rechercher ou saisir des informations.

Le module complémentaire optionnel **Survey** permet de créer un nouveau type d&#39;application Web pour créer et gérer des questionnaires en ligne, tels que des formulaires pour ajouter ou modifier des informations de profil, pour vous abonner ou vous désabonner à un service d&#39;information ou un formulaire de participation à un concours. Une fois les réponses collectées, elles sont stockées dans la base de données ou dans des variables locales. Le modèle de données peut être étendu dynamiquement au travers des réponses fournies aux questionnaires. Vous pouvez visualiser les résultats en temps réel, filtrer les réponses et les analyser à l&#39;aide de graphiques dédiés.

Ce chapitre présente la création et la gestion des **enquêtes**, la gestion des champs et des pages, les modes de stockage et les enregistrements.

[!DNL :bulb:] Découvrez comment créer votre première enquête dans  [cette page](getting-started-with-surveys.md).

>[!NOTE]
>
>* Les étapes détaillées pour créer un formulaire web standard sont présentées dans [ce document](../../web/using/about-web-forms.md).
   >
   >
* La gestion des applications web est présentée dans [ce document](../../web/using/about-web-applications.md). Reportez-vous à ce chapitre pour plus d’informations.


## Portée de la fonctionnalité {#campaign-surveys-scope}

Dans Adobe Campaign, utilisez [Applications Web](../../web/using/about-web-forms.md) pour :

* Créer des formulaires multi-pages,
* gérer des formulaires multilingues avec un outil de traduction intégré,
* gérer l&#39;interface graphique, la mise en page à plusieurs colonnes,
* Ajouter une personnalisation et définir la position du champ,
* Affichage de la condition des champs du questionnaire en fonction des réponses,
* Affichage de la page de condition,
* Vérifiez les informations avant validation, en fonction du type de données attendu (nombre, adresse email, dates, etc.) et les champs obligatoires,
* Envoyer des invitations/notifications par email,
* Personnaliser les pages d&#39;erreur et de fin,
* Ajouter des images, vidéos, liens hypertexte, captcha, etc., dans les formulaires

Le module optionnel de création de questionnaires propose une interface utilisateur conviviale et les fonctionnalités supplémentaires suivantes :

* Extension dynamique de la base de données : création de réponses qui ne font pas partie du modèle de données initial. [En savoir plus](../../surveys/using/managing-answers.md#storing-collected-answers).
* Gestion des scores. [En savoir plus](../../surveys/using/managing-answers.md#score-management).
* Affichage aléatoire des questions. [En savoir plus](../../surveys/using/building-a-survey.md#adding-questions).
* Tracking en temps réel des réponses. [En savoir plus](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Génération de rapports dédiés. [En savoir plus](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Étapes d&#39;implémentation {#surveys-implementation-steps}

Pour créer, diffuser et exploiter les résultats d&#39;un questionnaire, les étapes sont les suivantes :

1. Créer la ou les pages et leur contenu (champs de saisie, listes déroulantes, questions, etc.).
1. Définir le mode d&#39;enregistrement des réponses. Il est possible d&#39;insérer une étape de préchargement des données afin de préremplir le formulaire avec les données déjà en base. Vous pouvez également ajouter une boîte de test.
1. Publiez puis diffusez le questionnaire aux destinataires (par exemple, incluez un lien dans une diffusion ou dans un site Web).
1. Suivre les réponses et consulter les rapports.

Pour plus d&#39;informations sur la configuration et le séquencement de ces étapes, consultez [ce document](../../web/using/about-web-forms.md). Seules les configurations spécifiques aux questionnaires sont détaillées dans ce chapitre.

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

## Paramètres       {#settings}

Par défaut, les questionnaires sont disponibles dans le noeud **[!UICONTROL Ressources > On-line > Applications Web]** de l&#39;arborescence Adobe Campaign.

Les paramètres sont stockés dans les dossiers suivants :

* **[!UICONTROL Administration > Paramétrage > Rendus des formulaires]** : contient les modèles de rendu pour la présentation des formulaires Web (applications et questionnaires).
* **[!UICONTROL Ressources > Modèles > Modèles d&#39;application Web]** : contient des modèles de formulaires. Pour créer un formulaire, vous devez partir d&#39;un modèle.

>[!NOTE]
>
>Les détails des paramètres sont disponibles dans [ce document](../../web/using/about-web-forms.md).

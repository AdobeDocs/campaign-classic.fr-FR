---
title: A propos des questionnaires
seo-title: A propos des questionnaires
description: A propos des questionnaires
seo-description: null
page-status-flag: never-activated
uuid: 31a07a48-2ebb-4b51-ae24-382f3ce3f04a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: ef7d9b16-506a-409c-a578-000b88cd17a2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# A propos des questionnaires{#about-surveys}

Adobe Campaign intègre un module graphique de définition et de publication d&#39;applications Web afin de créer des pages, par exemple pour formulaire d&#39;édition sur un extranet ou des formulaires de notification, incluant des données de la base avec des tableaux, graphiques, champs de saisie, etc. Cette fonctionnalité vous permet de concevoir et mettre en ligne des pages web auxquelles les utilisateurs pourront accéder pour consulter ou renseigner des informations.

Le module optionnel **Questionnaires (Survey)** permet de créer un nouveau type d&#39;applications Web afin de créer et gérer des questionnaires en ligne, par exemple des formulaires d&#39;ajout ou de modification de données d&#39;un profil, d&#39;inscription et de désinscription à un service d&#39;information ou un jeu-concours. Lorsque des réponses sont collectées, elles sont stockées dans la base de données ou dans des variables locales. Le modèle de données peut être étendu dynamiquement par les différentes réponses aux questionnaires. Vous pouvez visualiser les résultats en temps réel, filtrer les réponses et les analyser au travers de graphiques dédiés.

Ce chapitre présente le mode de création et de gestion des questionnaires (**Survey**), la gestion des champs et des pages, les modes de stockage et d&#39;enregistrement.

Les étapes de création d&#39;un formulaire web standard sont présentées dans [cette section](../../web/using/about-web-forms.md).

La gestion des applications web est présentée dans [cette section](../../web/using/about-web-applications.md). Veuillez vous y référer.

>[!CAUTION]
>
>Pour des raisons de confidentialité, nous vous recommandons d&#39;utiliser HTTPS pour toutes les ressources externes.

## Étendue des enquêtes de campagne {#campaign-surveys-scope}

Sous Adobe Campaign, les applications Web en général permettent d&#39;accéder aux fonctionnalités suivantes :

* Création de formulaires multi-pages,
* Gestion de formulaires multilingues, avec un outil de traduction intégré,
* Interface graphique de gestion des pages, mise en page en multi-colonnes,
* Personnalisation du rendu et du positionnement des champs,
* Affichage conditionnel des champs du formulaire en fonction des réponses,
* Conditionnement de l&#39;affichage des pages,
* Vérification des informations avant validation, en fonction du type de données attendu (nombre, adresse e-mail, date, etc.) et des champs obligatoires,
* Invitations/Notification par e-mail,
* Personnalisation des messages d&#39;erreur et de fin,
* Ajout d&#39;images, vidéos, liens hypertextes, captcha, etc.

>[!NOTE]
>
>Tous les paramétrages communs avec les formulaires web sont présentés dans [cette section](../../web/using/about-web-forms.md). Reportez-vous à ce document pour maîtriser tous les concepts et connaître des fonctionnalités relatives aux formulaires web sous Adobe Campaign.

Le module optionnel de création de questionnaires (**Survey**) propose les fonctionnalités supplémentaires suivantes :

* Extension dynamique de la base de données : création de réponses qui ne font pas partie du modèle de données initial. Pour plus d’informations, reportez-vous à la section [Stockage des réponses](../../web/using/managing-answers.md#storing-collected-answers)collectées.
* Gestion des scores. For more on this, refer to [Score management](../../web/using/managing-answers.md#score-management).
* Affichage aléatoire des questions. For more on this, refer to [Adding questions](../../web/using/building-a-survey.md#adding-questions).
* Suivi en temps réel des réponses. For more on this, refer to [Response tracking](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Génération de rapports dédiés. Pour en savoir plus, consultez [Rapports sur les enquêtes](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Par rapport aux applications Web, les questionnaires proposent une interface graphique allégée : le nombre de contrôles d&#39;édition est réduit.

## Etapes de mise en œuvre des enquêtes {#surveys-implementation-steps}

Pour créer, diffuser et exploiter les résultats d&#39;un questionnaire, les étapes sont les suivantes :

1. Créer la ou les pages et leur contenu (champs de saisie, listes déroulantes, questions, etc.).
1. Définir le mode d&#39;enregistrement des réponses.

   Il est possible d&#39;insérer une étape de préchargement des données afin de préremplir le formulaire avec les données déjà en base. Vous pouvez également ajouter une boîte de test.

1. Publiez, puis diffusez l&#39;enquête aux destinataires (par exemple, incluez un lien dans une diffusion ou dans un site Web).
1. Suivre les réponses et consulter les rapports.

Pour plus d’informations sur la configuration et le séquencement de ces étapes, voir [cette section](../../web/using/about-web-forms.md). Seules les configurations spécifiques aux enquêtes sont détaillées dans ce chapitre.

## Paramétrage des enquêtes {#surveys-configuration}

Les questionnaires sont stockés dans le noeud **[!UICONTROL Ressources > On-line > Applications Web]** de l&#39;arborescence Adobe Campaign. Les paramétrages sont répartis dans les dossiers suivants :

* **[!UICONTROL Administration > Paramétrage > Rendus des formulaires]** : contient les modèles de rendu pour la présentation des formulaires Web (applications et questionnaires).
* **[!UICONTROL Ressources > Modèles > Modèles d&#39;application Web]** : contient des modèles de formulaires. Pour créer un formulaire, vous devez partir d&#39;un modèle.

>[!NOTE]
>
>Les informations sur le paramétrage sont présentées dans [cette section](../../web/using/about-web-forms.md).


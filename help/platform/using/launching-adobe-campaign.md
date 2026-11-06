---
product: campaign
title: Lancement d’Adobe Campaign
description: Lancement d’Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
TQID: 'https://experienceleague.adobe.com/qpZM0jaN1ht6QfReQBy1c7jONGdc2PQ0ORepDaVficQ'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
    internal-label: Permissions
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 96%
---
# Lancement d’Adobe Campaign {#launching-adobe-campaign}

La console cliente Campaign est un client riche qui vous permet de vous connecter à votre ou vos serveur(s) applicatif(s) Campaign. Découvrez comment télécharger et configurer la console cliente en consultant [cette page](../../installation/using/installing-the-client-console.md).

Dans le cadre de la transition de Campaign v7 vers v8, la documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour en savoir plus sur la connexion à Campaign, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/connect){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/connect){target=_blank}

>[!CAUTION]
>
>Vérifiez la compatibilité de votre système et de vos outils avec la console cliente Adobe Campaign dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems).

## Lancement d’Adobe Campaign {#starting-adobe-campaign}

Vous pouvez démarrer Adobe Campaign à partir du menu **[!UICONTROL Démarrer/Tous les programmes/Adobe Campaign v.X/Console cliente Adobe Campaign]**.

La page de connexion de la console cliente permet de configurer ou de sélectionner une base de données existante, et de s’y connecter en utilisant un identifiant et un mot de passe :

![](assets/acc-logon.png)

## Connexion à Adobe Campaign {#connecting-to-adobe-campaign}

### Vous connecter avec votre Adobe ID

Pour configurer la connexion de Campaign Classic v7 avec le système de gestion des identités Adobe (IMS), consultez [cette page](../../integrations/using/about-adobe-id.md).

### Vous connecter avec un identifiant et un mot de passe

Vous pouvez aussi vous connecter à l’aide d’un identifiant et d’un mot de passe dédiés. Cette connexion est appelée « Authentification native » dans Campaign :

1. Saisissez l’identifiant du compte opérateur dans le champ **[!UICONTROL Login]**.

   L’identifiant vous est fourni par l’administrateur de la plateforme Adobe Campaign.

1. Saisissez votre mot de passe dans le champ **[!UICONTROL Mot de passe]**.

   La première fois que vous accédez à la base de données, votre mot de passe est celui qui vous a été attribué par l’équipe d’administration. Une fois connecté, vous pouvez modifier votre mot de passe via le menu **[!UICONTROL Outils > Changer le mot de passe…]** Des détails sur les opérateurs et les connexions sont disponibles dans [Gestion des accès](../../platform/using/access-management.md).

1. Cliquez sur **[!UICONTROL SE CONNECTER]** pour valider.

Vous pouvez maintenant accéder à l’[espace de travail d’Adobe Campaign](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} (documentation de Campaign v8).

## Opérateurs et autorisations {#operators-and-permissions}

Les identifiants et mots de passe des opérateurs ayant accès au logiciel, ainsi que leurs autorisations respectives, sont définis par l’administrateur du système Adobe Campaign dans le nœud **[!UICONTROL Administration > Gestion des accès > Opérateurs]** de l’arborescence d’Adobe Campaign.

Cette fonctionnalité est décrite dans la section [Gestion des accès](../../platform/using/access-management.md).

## Obtention de la version d’Adobe Campaign {#getting-your-campaign-version}

Le menu **[!UICONTROL Aide > À propos...]** vous permet d’accéder aux informations suivantes :

* numéro de **version** de la console cliente Campaign et du serveur applicatif
* numéro de **build** de la console cliente Campaign et du serveur applicatif
* lien pour contacter l&#39;Assistance clientèle d&#39;Adobe
* liens vers la Politique de confidentialité, les Conditions d&#39;utilisation et la Politique relative aux cookies d&#39;Adobe

![](assets/about-acc.png)

Lorsque vous contactez l&#39;équipe d&#39;Assistance clientèle d&#39;Adobe, vous devez indiquer les numéros de version et de build du serveur applicatif et de la console cliente Campaign.


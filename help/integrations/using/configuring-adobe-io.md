---
product: campaign
title: Configuration de Developer Console pour Adobe Experience Cloud Triggers
description: Découvrez comment configurer Developer Console pour Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: true
internal: 'n'
snippet: 'y'
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
    internal-label: Triggers
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 92%
---
# Configuration de Developer Console pour Adobe Experience Cloud Triggers {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Conditions préalables {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Avant de commencer cette implémentation, vérifiez que vous disposez des éléments suivants :

* un **identifiant d’organisation** valide : l’identifiant de l’organisation est l’identifiant unique dans Adobe Experience Cloud. Il est utilisé, entre autres, pour le service VisitorID et l’authentification unique (SSO) de l’IMS. [En savoir plus](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr)
* Un **accès développeur** à votre organisation. La personne en charge de l’administration système de l’organisation doit suivre la procédure **Ajouter des développeurs à un profil de produit unique** présentée [dans cette page](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html) pour fournir aux développeurs l’accès au profil du produit `Analytics - {tenantID}` Adobe Analytics associé à Triggers.

## Étape 1 : créer/mettre à jour un projet OAuth {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> Les informations d’identification du compte de service (JWT) sont en train d’être abandonnées par Adobe. Les intégrations de Campaign aux solutions et applications Adobe doivent désormais s’appuyer sur les informations d’identification de serveur à serveur OAuth. </br>
>
> * Si vous avez implémenté des intégrations entrantes pour Campaign, vous devez migrer votre compte technique comme décrit dans [cette documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Les [informations d’identification de compte de service (JWT)](oauth-technical-account.md) existantes continueront de fonctionner jusqu’au 27 janvier 2025.</br>
>
> * Si vous avez implémenté des intégrations sortantes, telles qu’une intégration Campaign-Analytics ou une intégration Experience Cloud Triggers, celles-ci continueront de fonctionner jusqu’au 27 janvier 2025. Toutefois, avant cette date, vous devez mettre à niveau votre environnement Campaign vers la version 7.4.1 et migrer votre compte technique vers OAuth.

Pour poursuivre la configuration de votre connecteur Adobe Analytics, accédez à Adobe Developer Console et créez votre projet OAuth serveur à serveur.

Consultez [cette page](oauth-technical-account.md#oauth-service) pour accéder à la documentation détaillée.

## Étape 2 : ajouter les informations d’identification du projet dans Adobe Campaign {#add-credentials-campaign}

Suivez les étapes détaillées sur [cette page](oauth-technical-account.md#add-credentials) pour ajouter vos informations d’identification de projet OAuth dans Adobe Campaign.

## Étape 3 : mettre à jour la balise en pipeline {#update-pipelined-tag}

Pour mettre à jour la balise [!DNL pipelined], vous devez mettre à jour le type d’authentification au projet Developer Console dans le fichier de configuration **config-&lt; nom-instance >.xml** comme suit :

```
<pipelined ... authType="imsJwtToken"  ... />
```

Ensuite, exécutez `config -reload` et redémarrez [!DNL pipelined] pour que les modifications soient prises en compte.

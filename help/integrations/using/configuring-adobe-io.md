---
product: campaign
title: Configuration de Developer Console pour Adobe Experience Cloud Triggers
description: Découvrez comment configurer Developer Console pour Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: ht
source-wordcount: '312'
ht-degree: 100%

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
> Les informations d’identification de compte de service (JWT) étant abandonnées par Adobe, les intégrations de Campaign aux solutions et aux applications Adobe doivent désormais utiliser des informations d’identification OAuth serveur à serveur.</br>
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

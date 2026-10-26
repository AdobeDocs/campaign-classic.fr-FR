---
product: campaign
title: Paramétrer IMS
description: Découvrez comment vous connecter via un Adobe ID
feature: Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/fr/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models" tooltip="Applies to on-premise and hybrid deployments only"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Target integration
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%
---
# Paramétrer IMS{#configuring-ims}

>[!IMPORTANT]
>
>En tant qu’utilisateur ou utilisatrice de services hébergés ou gérés par Campaign, votre implémentation d’Adobe IMS appartient à Adobe. Les étapes décrites ci-dessous s’appliquent uniquement aux clientes et clients On-Premise et hybrides.
> L’implémentation d’Adobe IMS ne doit être effectuée que par des administrateurs et administratrices techniques d’Adobe. Contactez votre représentant ou représentante Adobe pour démarrer le processus d’implémentation.

## Conditions préalables {#prerequisites}

* Vous devez disposer d’un nom et d’un identifiant de l’organisation Adobe Experience Cloud. Pour trouver l’identifiant de votre organisation, reportez-vous à [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr){_blank}.
* Vous devez ajouter des utilisateurs dans Experience Cloud. Voir à ce propos [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=fr){_blank}.

>[!NOTE]
>
>Veuillez vous assurer que vos utilisateurs sont associés à des groupes Adobe Experience Cloud qui seront synchronisés avec Adobe Campaign. [En savoir plus](#configuring-the-external-account).

## Mettre à jour la console {#updating-the-console}

Pour utiliser cette fonctionnalité, vous devez impérativement installer la version la plus récente de la console cliente.

## Installer le package {#installing-the-package}

Vous devez installer le pack intégré **[!UICONTROL Intégration à Adobe Experience Cloud]**. L’installation d’un pack d’intégration est identique à l’installation d’un pack standard, qui est détaillée dans [cette page](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurer le compte externe {#configuring-the-external-account}

Configurez le compte externe **Adobe Experience Cloud** dans **[!UICONTROL Administration > Plateforme > Comptes externes]**.

![](assets/ims_5.png)

Renseignez les informations suivantes :

* Informations de connexion au serveur IMS utilisé (ID et secret). Ces informations sont fournies par l’équipe Assistance clientèle d’Adobe. Pour plus d’informations, voir les [Questions fréquentes à l’intention des administrateurs et administratrices Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=fr).

  L’adresse du **[!UICONTROL serveur de rappel]** doit être indiquée en **https**. Ce champ correspond à l’URL d’accès à votre instance Adobe Campaign.

* ID d’organisation : pour trouver l’identifiant de votre organisation, reportez-vous à [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr){_blank}.

* Masque de correspondance : ce champ vous permet de définir la syntaxe qui permettra de synchroniser les noms de configuration dans le tableau de bord Enterprise avec les groupes dans Adobe Campaign. Si vous utilisez la syntaxe « Campaign - tenant_id - (.&#42;) », le groupe de sécurité créé dans Adobe Campaign sera associé au nom de configuration « Campaign - tenant_id - internal_name » dans le tableau de bord Enterprise.

* Informations de connexion à Adobe Experience Cloud, c’est-à-dire le nom du client Adobe Experience Cloud.

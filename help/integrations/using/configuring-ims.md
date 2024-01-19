---
product: campaign
title: Paramétrer IMS
description: Découvrez comment vous connecter via un Adobe ID
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: ht
source-wordcount: '346'
ht-degree: 100%

---

# Paramétrer IMS{#configuring-ims}

>[!IMPORTANT]
>
>En tant qu’utilisateur ou utilisatrice de services hébergés ou gérés par Campaign, votre implémentation d’Adobe IMS appartient à Adobe. Les étapes décrites ci-dessous s’appliquent uniquement aux clientes et clients On-Premise et hybrides.
> L’implémentation d’Adobe IMS ne doit être effectuée que par des administrateurs et administratrices techniques d’Adobe. Contactez votre représentant ou représentante Adobe pour démarrer le processus d’implémentation.

## Conditions préalables {#prerequisites}

* Vous devez disposer d’un nom et d’un identifiant de l’organisation Adobe Experience Cloud. Pour trouver l’identifiant de votre organisation, reportez-vous à [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr){_blank}.
* Vous devez ajouter des utilisateurs dans Experience Cloud. Pour en savoir plus, reportez-vous à [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=fr){_blank}.

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

  L&#39;adresse du **[!UICONTROL Serveur de rappel]** (callback server) doit être indiquée en **https**. Ce champ correspond à l&#39;URL d&#39;accès à votre instance Adobe Campaign.

* Identifiant de l’organisation : pour trouver l’identifiant de votre organisation, reportez-vous à [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr){_blank}.

* Masque de correspondance : ce champ permet de définir la syntaxe qui permettra de synchroniser les noms de configuration dans Enterprise Dashboard avec les groupes dans Adobe Campaign. Si vous utilisez la syntaxe &quot;Campaign - tenant_id - (.&#42;)&quot;, le groupe de sécurité créé dans Adobe Campaign sera associé au nom de configuration &quot;Campaign - tenant_id - internal_name&quot; dans Enterprise Dashboard.

* Informations de connexion à Adobe Experience Cloud, c’est-à-dire le nom du client Adobe Experience Cloud.

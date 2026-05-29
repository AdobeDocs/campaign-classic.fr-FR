---
product: campaign
title: Paramétrer IMS
description: Découvrez comment vous connecter via un Adobe ID
feature: Configuration
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
feature_v2: []
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 361
ht-degree: 69%

---

# Paramétrer IMS{#configuring-ims}

>[!IMPORTANT]
>
>En tant qu&#39;utilisateur de Campaign hébergé ou Managed Services, votre implémentation d&#39;Adobe IMS appartient à Adobe. Les étapes décrites ci-dessous s’appliquent uniquement aux clients On-Premise et hybrides.
> L’implémentation d’Adobe IMS ne doit être effectuée que par les administrateurs techniques d’Adobe. Contactez votre représentant Adobe pour démarrer le processus de mise en œuvre.

## Conditions préalables {#prerequisites}

* Vous devez disposer d’un nom et d’un identifiant de l’organisation Adobe Experience Cloud. Pour trouver votre identifiant d’organisation, reportez-vous à [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr){_blank}.
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

  L’adresse **[!UICONTROL Serveur de rappel]** doit être spécifiée en **https**. Ce champ correspond à l’URL d’accès à votre instance Adobe Campaign.

* Identifiant de l’organisation : pour trouver l’identifiant de votre organisation, reportez-vous à [cette page](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr){_blank}.

* Masque de correspondance : ce champ permet de définir la syntaxe qui permettra la synchronisation des noms de configuration dans Enterprise Dashboard avec les groupes d’Adobe Campaign. Si vous utilisez la syntaxe « Campaign - tenant_id - (.&#42;) », le groupe de sécurité créé dans Adobe Campaign est lié au nom de configuration « Campaign - tenant_id - internal_name » dans Enterprise Dashboard.

* Informations de connexion à Adobe Experience Cloud, c’est-à-dire le nom du client Adobe Experience Cloud.

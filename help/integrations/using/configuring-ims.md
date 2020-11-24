---
solution: Campaign Classic
product: campaign
title: Paramétrer IMS
description: Découvrez comment vous connecter via un Adobe ID
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 100%

---


# Paramétrer IMS{#configuring-ims}

## Prérequis {#prerequisites}

Pour utiliser l&#39;intégration avec l&#39;IMS, les éléments suivants sont requis :

* Vous devez disposer d’une organisation Adobe Experience Cloud et d’identifiants IMS (fournis lors de la première connexion à Adobe Experience Cloud).
* Vous devez ajouter des utilisateurs dans Experience Cloud. Voir à ce propos [cette page](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Veuillez vous assurer que vos utilisateurs sont associés à des groupes Adobe Experience Cloud qui seront synchronisés avec Adobe Campaign. Voir la section [Configuration du compte externe](#configuring-the-external-account).

## Mettre à jour la console {#updating-the-console}

Pour utiliser cette fonctionnalité, vous devez impérativement installer la version la plus récente de la console.

## Installer le package {#installing-the-package}

Vous devez installer le package **[!UICONTROL Intégration avec Adobe Experience Cloud]**. L’installation d’un package d’intégration est identique à l’installation d’un package standard, détaillée sur [cette page](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurer le compte externe {#configuring-the-external-account}

Configurez le compte externe **Adobe Experience Cloud** dans **[!UICONTROL Administration > Plateforme > Comptes externes]**.

>[!CAUTION]
>
>Ce paramétrage est réservé à l&#39;administrateur technique.

![](assets/ims_5.png)

Renseignez les informations suivantes :

* les informations de connexion au serveur IMS utilisé (identifiant et secret). Ces informations sont fournies par le support Adobe. Pour plus d&#39;informations, consultez la [FAQ Adobe Experience Cloud](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/faq.html).

   L&#39;adresse du **[!UICONTROL Serveur de rappel]** (callback server) doit être indiquée en **https**. Ce champ correspond à l&#39;URL d&#39;accès à votre instance Adobe Campaign.

* l’identifiant de l’organisation IMS : cette information est disponible dans Experience Cloud (dans **[!UICONTROL Administration > Détails Experience Cloud]**). Elle est fournie lors de votre première connexion à Adobe Experience Cloud.
* le masque de correspondance : ce champ permet de définir la syntaxe qui permettra la synchronisation des noms de configuration dans Enterprise Dashboard avec les groupes d&#39;Adobe Campaign. Si vous utilisez la syntaxe &quot;Campaign - tenant_id - (.*)&quot;, le groupe de sécurité créé dans Adobe Campaign sera associé au nom de configuration &quot;Campaign - tenant_id - internal_name&quot; dans Enterprise Dashboard.

   >[!CAUTION]
   >
   >Le masque de correspondance est indispensable au bon fonctionnement de la connexion via l&#39;Adobe ID.

* les informations de connexion à Adobe Experience Cloud, notamment le nom du tenant Adobe Experience Cloud.


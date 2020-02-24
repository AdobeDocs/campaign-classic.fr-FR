---
title: Paramétrer IMS
seo-title: Paramétrer IMS
description: Paramétrer IMS
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Paramétrer IMS{#configuring-ims}

## Prérequis {#prerequisites}

Pour utiliser l&#39;intégration avec l&#39;IMS, les éléments suivants sont requis :

* Vous devez disposer d&#39;une organisation Adobe Marketing Cloud et d&#39;identifiants IMS (fournis lors de la première connexion à Adobe Marketing Cloud).
* Vous devez ajouter les utilisateurs dans Marketing Cloud. Voir à ce propos la page suivante : [https://marketing.adobe.com/resources/help/fr_FR/mcloud/admin_getting_started.html](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html).

>[!NOTE]
>
>Assurez-vous que vos utilisateurs sont liés aux groupes Adobe Marketing Cloud qui seront synchronisés avec Adobe Campaign. Reportez-vous à [Configuration du compte](#configuring-the-external-account)externe.

## Mettre à jour la console {#updating-the-console}

Pour utiliser cette fonctionnalité, vous devez impérativement installer la version la plus récente de la console.

## Installer le package {#installing-the-package}

Vous devez installer le package **[!UICONTROL Intégration avec Adobe Experience Cloud]**. L’installation d’un package d’intégration est identique à l’installation d’un package standard, détaillée sur [cette page](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurer le compte externe {#configuring-the-external-account}

Configurez le compte externe **Adobe Experience Cloud** dans **[!UICONTROL Administration > Plate-forme > Comptes externes]**.

>[!CAUTION]
>
>Ce paramétrage est réservé à l&#39;administrateur technique.

![](assets/ims_5.png)

Renseignez les informations suivantes :

* les informations de connexion au serveur IMS utilisé (identifiant et secret). Ces informations sont fournies par le support Adobe. Pour plus d&#39;informations, consultez la [FAQ Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/faq.html).

   L&#39;adresse du **[!UICONTROL Serveur de rappel]** (callback server) doit être indiquée en **https**. Ce champ correspond à l&#39;URL d&#39;accès à votre instance Adobe Campaign.

* l’identifiant de l’organisation IMS : cette information est disponible dans Experience Cloud (dans **[!UICONTROL Administration > Détails Experience Cloud]**). Elle est fournie lors de votre première connexion à Adobe Experience Cloud.
* le masque de correspondance : ce champ permet de définir la syntaxe qui permettra la synchronisation des noms de configuration dans Enterprise Dashboard avec les groupes d&#39;Adobe Campaign. Si vous utilisez la syntaxe &quot;Campaign - tenant_id - (.*)&quot;, le groupe de sécurité créé dans Adobe Campaign sera associé au nom de configuration &quot;Campaign - tenant_id - internal_name&quot; dans Enterprise Dashboard.

   >[!CAUTION]
   >
   >Le masque de correspondance est indispensable au bon fonctionnement de la connexion via l&#39;Adobe ID.

* les informations de connexion à Adobe Experience Cloud, notamment le nom du tenant Adobe Experience Cloud.


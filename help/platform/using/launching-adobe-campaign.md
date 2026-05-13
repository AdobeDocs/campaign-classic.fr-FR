---
product: campaign
title: Lancement d’Adobe Campaign
description: Lancement d’Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
TQID: https://experienceleague.adobe.com/qpZM0jaN1ht6QfReQBy1c7jONGdc2PQ0ORepDaVficQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: e3988c18-3cfa-4f16-b812-ac2d2b1056faid: efa38731-2723-4334-8d8b-a778af834835
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 474
ht-degree: 100%

---

# Lancement d’Adobe Campaign {#launching-adobe-campaign}

La console cliente Campaign est un client riche qui vous permet de vous connecter à votre ou vos serveur(s) applicatif(s) Campaign. Découvrez comment télécharger et configurer la console cliente en consultant [cette page](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Vérifiez la compatibilité de votre système et de vos outils avec la console cliente Adobe Campaign dans la [matrice de compatibilité](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems).

## Lancement d’Adobe Campaign {#starting-adobe-campaign}

Vous pouvez démarrer Adobe Campaign à partir du menu **[!UICONTROL Démarrer/Tous les programmes/Adobe Campaign v.X/Console cliente Adobe Campaign]**.

La page de connexion de la console cliente permet de configurer ou de sélectionner une base de données existante, et de s’y connecter en utilisant un identifiant et un mot de passe :

![](assets/acc-logon.png)

## Connexion à Adobe Campaign {#connecting-to-adobe-campaign}

### Vous connecter avec votre Adobe ID

Les utilisateurs de Campaign se connectent à la console Adobe Campaign à l&#39;aide de leur Adobe ID, via le système IMS (Adobe Identity Management System). Ils peuvent utiliser le même identifiant pour toutes les solutions d&#39;Adobe. La connexion est enregistrée lors de l&#39;utilisation d&#39;Adobe Campaign avec d&#39;autres solutions. Pour en savoir plus sur Adobe IMS, consultez [cette page](https://helpx.adobe.com/fr/enterprise/using/identity.html).

Pour configurer la connexion de Campaign Classic v7 avec le système de gestion des identités Adobe (IMS), consultez [cette page](../../integrations/using/about-adobe-id.md).

Une fois la configuration terminée, découvrez comment vous connecter à Campaign avec votre Adobe ID dans la [documentation de Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/connect){target=_blank}.


### Vous connecter avec un identifiant et un mot de passe

Vous pouvez aussi vous connecter à l’aide d’un identifiant et d’un mot de passe dédiés. Cette connexion est appelée « Authentification native » dans Campaign :

1. Saisissez l’identifiant du compte opérateur dans le champ **[!UICONTROL Login]**.

   L’identifiant vous est fourni par l’administrateur de la plateforme Adobe Campaign.

1. Saisissez votre mot de passe dans le champ **[!UICONTROL Mot de passe]**.

   La première fois que vous accédez à la base de données, votre mot de passe est celui qui vous a été attribué par l’équipe d’administration. Une fois connecté, vous pouvez modifier votre mot de passe via le menu **[!UICONTROL Outils > Changer le mot de passe…]** Des détails sur les opérateurs et les connexions sont disponibles dans [Gestion des accès](../../platform/using/access-management.md).

1. Cliquez sur **[!UICONTROL SE CONNECTER]** pour valider.

Vous pouvez maintenant accéder à l’[espace de travail Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configurer des connexions {#setting-up-connections}

Vous pouvez accéder aux paramètres de connexion au serveur via le lien situé au-dessus de la zone de saisie.

![](assets/s_ncs_user_connections_management.png)

Découvrez comment configurer des connexions dans la [documentation de Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/connect#create-your-connection){target=_blank}.

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


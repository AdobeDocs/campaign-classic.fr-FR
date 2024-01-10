---
product: campaign
title: Utilisez votre Adobe ID pour vous connecter à Adobe Campaign
description: En savoir plus sur l’implémentation d’Adobe IMS dans Adobe Campaign
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 60%

---

# À propos des Adobe ID {#about-adobe-id}

Le système Adobe IDentity Management System (IMS) permet aux administrateurs de créer et de gérer l&#39;accès des utilisateurs aux applications et services. Pour plus d’informations sur les différents types d’Adobe ID, consultez [cette page](https://helpx.adobe.com/fr/enterprise/using/identity.html).

Les utilisateurs de Campaign peuvent se connecter à la console Adobe Campaign à l’aide de leur Adobe ID, au lieu de la fonction [authentification par utilisateur/mot de passe natif](../../platform/using/access-management-operators.md). Cette implémentation présente les avantages suivants :

* utilisation d&#39;un même identifiant pour toutes les solutions Experience Cloud
* La connexion est conservée lors de l’utilisation d’Adobe Campaign avec différentes intégrations.
* Stratégie de gestion des mots de passe plus sécurisée que le login/mot de passe natif.
* utilisation de comptes de type Federated ID (fournisseur d&#39;identité externe)

<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## Plus de ressources

| Pages utiles | Autres ressources |
|---|---|
| [Paramétrer IMS](../../integrations/using/configuring-ims.md) | [FAQ sur Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=fr) |
| [Implémenter IMS](../../integrations/using/implementing-ims.md) | [Gestion des accès](../../platform/using/access-management.md) |
| [Dépanner IMS](../../integrations/using/ims-troubleshooting.md) | [Installation des packages Campaign](../../installation/using/installing-campaign-standard-packages.md) |

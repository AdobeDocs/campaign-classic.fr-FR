---
product: campaign
title: Utiliser votre Adobe ID pour vous connecter à Adobe Campaign
description: En savoir plus sur l’implémentation d’Adobe IMS dans Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 84%

---

# À propos des Adobe ID {#about-adobe-id}

Le système Adobe IDentity Management System (IMS) permet aux administrateurs de créer et de gérer l&#39;accès des utilisateurs aux applications et services. Pour plus d’informations sur les différents types d’Adobe ID, consultez [cette page](https://helpx.adobe.com/fr/enterprise/using/identity.html).

Les utilisateurs et utilisatrices de Campaign peuvent se connecter à la console Adobe Campaign à l’aide de leur Adobe ID, plutôt que via l’[authentification native utilisateur/mot de passe](../../platform/using/access-management-operators.md). Cette implémentation présente les avantages suivants :

* utilisation d&#39;un même identifiant pour toutes les solutions Experience Cloud
* mémorisation de la connexion lors de l&#39;utilisation d&#39;Adobe Campaign avec les différentes intégrations
* politique de gestion des mots de passe plus sécurisée qu’avec le nom d’utilisateur/mot de passe natif.
* utilisation de comptes de type Federated ID (fournisseur d&#39;identité externe)

>[!IMPORTANT]
>
> Notez que dans Campaign v8, la connexion par nom d’utilisateur ou d’utilisatrice et mot de passe (ou authentification native) n’est plus autorisée. **Adobe recommande d&#39;effectuer cette migration à partir de Campaign v7.3.5 afin de pouvoir migrer en douceur vers Campaign v8.**
>
>Découvrez comment migrer vers Adobe IMS dans [cette section](../../technotes/using/ac-ims.md).
>


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

---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 4be5bf54362240aac1b77298b08b14d3e5542f52
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 93%

---

# Dernière version {#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## Version 7.4.1 - Build 9383 {#release-7-4-1}

[!BADGE Disponibilité générale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité générale"}

_18 juin 2024_

### Modifications et améliorations {#release-7-4-1-changes}

* Les informations d’identification de compte de service (JWT) étant considérées obsolètes par Adobe, les intégrations sortantes de Campaign aux solutions et aux applications Adobe utilisent désormais des informations d’identification OAuth serveur à serveur. Si vous avez implémenté des intégrations sortantes, telles qu’une intégration Campaign-Analytics ou une intégration Experience Cloud Triggers, vous devez mettre à niveau votre environnement Campaign vers la version 7.4.1 et migrer votre compte technique vers OAuth avant le 27 janvier 2025. [En savoir plus](../../integrations/using/oauth-technical-account.md)

* Une fois que vous avez [migré vos opérateurs et opératrices techniques Campaign vers Developer Console](../../technotes/using/ims-migration.md) et [migré vers IMS pour l’authentification des utilisateurs et des utilisatrices finaux](../../technotes/using/migrate-users-to-ims.md), vous pouvez désormais activer les restrictions de l’interface d’utilisation et de l’API pour supprimer les options et les fonctionnalités spécifiques à l’authentification native. [En savoir plus](../../technotes/using/impact-ims-migration.md)


### Mises à jour de compatibilité {#release-7-4-1-compat}

La [matrice de compatibilité pour Adobe Campaign](compatibility-matrix.md) a été mise à jour avec les modifications qui accompagnent cette nouvelle version. Celles-ci sont répertoriées ci-dessous.

* Adobe Campaign est désormais compatible avec **Microsoft Server 2022** et **RHEL 9** comme systèmes d’exploitation.

* Adobe Campaign est désormais compatible avec **Microsoft SQL Server 2022** et **Oracle 23c** comme base de données relationnelle, et dans Federated Data Access (FDA).

* Adobe Campaign requiert désormais au moins un kit de développement Java (JDK) 11. Sous Windows, le JRE doit être disponible, comme décrit dans [cette section](../../installation/using/application-server.md#jdk).

* Le SDK Campaign (Neolane) pour les applications mobiles est désormais obsolète. Vous devez maintenant migrer vers le SDK Adobe Experience Platform. [En savoir plus](deprecated-features.md).

  En attendant, pour assurer la continuité du service, Campaign v7.4 propose :

   * un nouveau SDK Campaign 1.0.27 pour iOS, compatible avec iOS 16 et 17, et avec les dernières [Exigences d’Apple iOS en matière de demandes d’accès aux informations personnelles](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * un nouveau SDK Campaign pour Android 14.

### Autres changements {#release-7-4-1-other}

À compter de la version 7.4.1, les bibliothèques XML pour les packages RPM Linux ne sont plus incluses dans Campaign. En tant que client on-premise ou hybride, votre administrateur doit installer ces bibliothèques.

### Correctifs {#release-7-4-1-patches}

Cette version comprend les correctifs suivants :

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


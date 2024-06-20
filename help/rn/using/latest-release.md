---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: d31aa28da06e65664da655b6b082563767b35f7a
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 19%

---

# Dernière version {#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## Version 7.4.1 - Build 9383 {#release-7-4-1}

[!BADGE Disponibilité générale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité générale"}

_mercredi 18 juin 2024_

### Modifications et améliorations {#release-7-4-1-changes}

* Les informations d’identification du compte de service (JWT) étant abandonnées par Adobe, les intégrations sortantes de Campaign avec les solutions et applications d’Adobe dépendent désormais des informations d’identification OAuth serveur à serveur. Si vous avez implémenté des intégrations sortantes, telles que l’intégration Campaign-Analytics ou l’intégration des Triggers Experience Cloud, vous devez mettre à niveau votre environnement Campaign vers la version 7.4.1 et migrer votre compte technique vers oAuth avant le 27 janvier 2025. [En savoir plus](../../integrations/using/oauth-technical-account.md)

* Une fois que vous avez [migration des opérateurs techniques Campaign vers Developer Console](../../technotes/using/ims-migration.md) et [transition vers IMS pour l’authentification des utilisateurs finaux](../../technotes/using/migrate-users-to-ims.md), vous pouvez désormais activer les restrictions de l’interface utilisateur et de l’API pour supprimer les options et fonctionnalités spécifiques à l’authentification native. [En savoir plus](../../technotes/using/impact-ims-migration.md)



### Mises à jour de compatibilité {#release-7-4-1-compat}

La variable [matrice de compatibilité pour Adobe Campaign](compatibility-matrix.md) a été mis à jour avec les modifications accompagnant cette nouvelle version. Elles sont répertoriées ci-dessous.

* Adobe Campaign est désormais compatible avec **Microsoft Server 2022** et **RHEL 9** en tant que systèmes d’exploitation.

* Adobe Campaign est désormais compatible avec **Microsoft SQL Server 2022** et **Oracle 23c** en tant que systèmes de gestion des bases de données des relations et dans Federated Data Access (FDA).

* Adobe Campaign requiert désormais au moins un Java Development Kit (JDK) 11. Sous Windows, JRE doit être disponible comme décrit dans la section [cette section](../../installation/using/application-server.md#jdk).

* Le SDK Campaign (Neolane) pour les applications mobiles est désormais obsolète. Vous devez maintenant passer au SDK Adobe Experience Platform. [En savoir plus](deprecated-features.md).

  En attendant, pour assurer la continuité de service, Campaign v7.4 est livré avec :

   * un nouveau SDK Campaign 1.0.27 pour iOS, compatible avec iOS 16 et 17, et la dernière version [Conditions requises pour une demande d’accès à des informations personnelles dans Apple iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * un nouveau SDK Campaign pour Android 14.


### Correctifs {#release-7-4-1-patches}

Cette version est fournie avec les correctifs suivants :

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-696 51, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-66 2575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


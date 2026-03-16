---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 66387e2e008051901fe3385f571d7fe798829100
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 28%

---

# Dernière version {#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## Version 7.4.3 - Build 9392 {#release-7-4-3}

[!BADGE Disponibilité générale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité générale"}

_mardi 16 mars 2026_

>[!CAUTION]
>
> La mise à niveau de la console cliente est obligatoire.

### Améliorations de la sécurité {#security-7-4-3}

* Pour maintenir une sécurité, une stabilité et une conformité optimales, Debian a été mis à niveau vers la version 13 et PostgreSQL vers la version 17. Reportez-vous à la [ matrice de compatibilité ](compatibility-matrix.md).

### Correctifs {#fixes-7-4-3}

* Correction d’un problème en raison duquel le composant de code à barres autorisait un paramètre de hauteur illimité, ce qui pouvait entraîner une vulnérabilité de sécurité. (NEO-89984)
* Correction d’un problème où les champs d’énumération dans les listes créées via les workflows ne comportaient pas d’attributs de nom temporaires, ce qui entraînait l’affichage de libellés d’énumération incorrects ou vides dans l’interface. (NEO-91158)
* Correction d’un problème en raison duquel les statistiques de diffusion n’étaient pas entièrement recalculées pour certaines diffusions, ce qui affectait particulièrement les indicateurs de succès. (NEO-88106)
* Correction d’un problème en raison duquel la préparation de la diffusion échouait avec des erreurs de personnalisation lors de l’utilisation des champs targetData dans les workflows avec des activités de déduplication. (NEO-87693)
* Correction d’un problème en raison duquel la concaténation de champs de chaîne à un seul caractère avec d’autres chaînes échouait dans PostgreSQL 15 en raison d’exigences de conversion de type. (NEO-88028)
* Correction d’un problème où les logs de tracking des campagnes collaboratives dans le marketing distribué n’étaient pas écrits dans la base de données en raison d’une incohérence entre les identifiants de diffusion parents et enfants. (NEO-86836)
* Correction d’un problème en raison duquel les logs de diffusion affichaient les messages comme annulés même s’ils étaient correctement envoyés, ce qui affectait particulièrement les diffusions avec planification des vagues. (NEO-78933)
* Correction d’un problème en raison duquel le workflow de nettoyage de la base ne purgeait pas efficacement les données, ce qui pouvait avoir un impact sur les performances. (NEO-76439)


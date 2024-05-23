---
product: campaign
title: Dernière version
description: Notes de mise à jour de la dernière version de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# Dernière version{#latest-release}

Cette page répertorie les nouvelles fonctionnalités, les améliorations et les correctifs apportés à la **dernière version de Campaign Classic v7**. Chaque nouvelle build est fournie avec un statut matérialisé par une couleur. En savoir plus sur les statuts de build de Campaign Classic v7 dans [cette page](rn-overview.md).

## Version 7.3.5 - Build 9368 {#release-7-3-5}

[!BADGE Disponibilité générale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=fr#rn-statuses" tooltip="Disponibilité générale"}


_5 décembre 2023_


### Améliorations de la sécurité {#release-7-3-5-security}


* Avec Campaign Classic v7.3.5, le processus d’authentification a été amélioré et sécurisé. Les opérateurs ou opératrices techniques doivent à présent utiliser Adobe Identity Management System (IMS) pour se connecter à Campaign. Découvrez comment migrer votre ou vos comptes techniques existants dans [cette note technique](../../technotes/using/ims-migration.md).

* En outre, dans le cadre des efforts visant à renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de migrer le mode d’authentification de l’utilisateur final et de l’utilisatrice finale et de passer de l’authentification native par nom d’utilisateur ou d’utilisatrice/mot de passe à Adobe Identity Management System (IMS). Découvrez comment effectuer la migration de vos opérateurs et opératrices dans [cette note technique](../../technotes/using/migrate-users-to-ims.md).

* Désormais, lorsqu’un formulaire web a le statut **En attente de publication**, il n’est plus automatiquement mis en ligne. Pour éviter tout problème de sécurité, il doit être publié avant qu’il ne passe **En ligne** et devienne accessible via l’URL du formulaire web dans un navigateur web. [En savoir plus](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Correctifs {#release-7-3-5-patches}

* Correction d’un problème lors de l’utilisation de données d’une base de données Google Big Query et de la mise à jour de données dans une base de données Oracle : toutes les clés étaient définies sur `0` dans la table temporaire du workflow. (NEO-65091)
* Correction d’un problème qui entraînait l’échec de l’exécution d’un workflow lorsque deux requêtes sur une base de données Google Big Query étaient combinées dans une activité de workflow d’**Union**. (NEO-63705)
* Correction d’un problème en raison duquel la personne était invitée à se réauthentifier lors du clic sur le bouton `Back` d’un rapport Campaign. (NEO-65087)
* Correction d’une erreur dans le workflow Nettoyage de la base qui se produisait lorsqu’une diffusion était supprimée avant ses BAT. (NEO-48114)
* Correction d’un problème lors de la connexion à la console cliente : les mises à jour récentes de la vérification TLS entraînaient une erreur de connexion. (NEO-50488)
* Correction d’un problème lié à l’authentification du proxy HTTP après le mise à jour vers Campaign 7.3.1. Les requêtes HTTP dans les workflows de campagne échouaient avec l’erreur suivante : `error 407 – proxy auth required is returned`. (NEO-49624)
* Correction d’un échec intermittent avec le déchiffrement GPG dans les activités de workflow **Script**. Le message d’erreur associé était : `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->


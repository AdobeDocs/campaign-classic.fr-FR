---
title: Accès à une base de données externe
seo-title: Accès à une base de données externe
description: Accès à une base de données externe
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Droits d&#39;accès à la base externe {#remote-database-access-rights}

Tout d&#39;abord, afin qu&#39;un utilisateur puisse effectuer des opérations sur une base externe via FDA, ce dernier doit disposer d&#39;un droit nommé spécifique dans Adobe Campaign.

1. Sélectionnez le noeud **[!UICONTROL Administration > Gestion des accès > Droits nommés]** de l&#39;explorateur Adobe Campaign.
1. Créez un nouveau droit en indiquant le libellé de votre choix.
1. Le champ **[!UICONTROL Nom]** doit être de la forme suivante : **user:base@server**, où :

   * **user** correspond au nom de l&#39;utilisateur sur la base de données externe.
   * **base** correspond au nom de la base de données externe.
   * **server** correspond au nom du serveur de la base de données externe.

      >[!NOTE]
      >
      >La partie **:base** est optionnelle sur Oracle.

1. Enregistrez le droit nommé puis associez-le à l&#39;utilisateur de votre choix à partir du noeud **[!UICONTROL Administration > Gestion des accès > Opérateurs]** de l&#39;explorateur Adobe Campaign.

Ensuite, pour exploiter les données contenues dans une base externe, l&#39;utilisateur Adobe Campaign doit au minimum avoir les droits en &#39;Ecriture&#39; sur cette base, afin de permettre la création des tables de travail. Ces tables sont automatiquement supprimées par Adobe Campaign.

En règle générale, les droits d&#39;accès suivants sont nécessaires :

* **CONNECT** : connexion à la base distante,
* **READ Data** : accès en lecture aux tables contenant les données du client,
* **READ &#39;MetaData&#39;** : accès aux catalogues de données du serveur afin d&#39;obtenir la structure des tables,
* **LOAD** : chargement en masse dans des tables de travail (opération nécessaire lorsque l&#39;on travaille sur des collections et des jointures),
* **CREATE/DROP** pour **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** (recommandé) : pour le suivi des performances en cas de problème,
* **WRITE Data** (selon le scénario d&#39;intégration).

>[!NOTE]
>
>L&#39;administrateur de la base de données doit faire correspondre ces droits avec les droits spécifiques à chaque moteur de base de données. Pour plus d&#39;informations, consultez les [Droits spécifiques par SGBDR](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html) (document en anglais).
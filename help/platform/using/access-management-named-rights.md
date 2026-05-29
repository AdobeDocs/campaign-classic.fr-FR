---
product: campaign
title: Utiliser des droits nommés pour configurer des autorisations
description: Découvrez comment utiliser des droits nommés pour configurer des autorisations
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
TQID: https://experienceleague.adobe.com/GApH-ZtovMX--PzISD-Pvafo3pfcbG-OqHzp5kCvcNQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 711
ht-degree: 76%

---

# Utilisation des droits nommés pour la configuration des autorisations{#named-rights}

Par défaut, Adobe Campaign propose un ensemble de droits nommés qui permettent de définir les autorisations attribuées aux opérateurs et groupes d&#39;opérateurs. Ces droits peuvent être modifiés à partir du nœud **[!UICONTROL Administration > Gestion des accès > Droits nommés]** de l&#39;arborescence.

![](assets/s_ncs_admin_named_rights.png)

Ces droits sont les suivants :

* **[!UICONTROL ADMINISTRATION]** : les opérateurs disposant du droit **[!UICONTROL ADMINISTRATION]** ont un accès total à l’instance. Les administrateurs peuvent exécuter/créer/éditer/supprimer tout objet tel que workflow, diffusion, script, etc.

  >[!IMPORTANT]
  >
  >**Après la migration vers IMS :** une fois la migration vers Adobe Identity Management System (IMS) terminée, tout profil de produit ou droit nommé contenant le mot « admin » dans son nom (par exemple, « Administrateurs », « admin », « admins », etc.) accordera automatiquement l&#39;accès au Panneau de Contrôle Campaign. Nous vous recommandons d’éviter l’utilisation de « admin » dans les noms de droits ou de rôles nommés, sauf si vous avez l’intention d’accorder un accès par Panneau de Contrôle à ces utilisateurs. En savoir plus sur la [migration IMS](../../technotes/using/migrate-users-to-ims.md) et la [gestion de l’accès aux Panneaux de Contrôle &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.

* **[!UICONTROL ADMINISTRATION DES VALIDATIONS]** : vous pouvez définir plusieurs étapes de validation dans les workflows et les diffusions pour vous assurer que l’état actuel a été validé par un opérateur ou un groupe affecté. Les utilisateurs disposant du droit **[!UICONTROL ADMINISTRATION DES VALIDATIONS]** peuvent définir les étapes de validation et affecter un opérateur ou un groupe d’opérateurs chargé de valider ces étapes.

  >[!IMPORTANT]
  >
  >**Après la migration vers IMS :** les profils de produit ou les droits nommés contenant le mot « admin » (par exemple, « Administrateur d’approbation ») accordent l’accès au Panneau de Contrôle Campaign. En savoir plus sur la [migration IMS](../../technotes/using/migrate-users-to-ims.md) et la [gestion de l’accès aux Panneaux de Contrôle &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.

* **[!UICONTROL CENTRAL]** : droit de gestion en central (Marketing distribué).

* **[!UICONTROL SUPPRESSION DES DOSSIERS]** : droit de supprimer des dossiers. Avec ce droit, les utilisateurs sont autorisés à supprimer des dossiers dans la vue de l’explorateur.

* **[!UICONTROL ÉDITION DES DOSSIERS]** : droit de modifier les propriétés du dossier telles que le nom interne, le libellé, l’image associée, l’ordre des sous-dossiers, etc.

* **[!UICONTROL EXPORT]** : les utilisateurs peuvent exporter des données depuis leurs instances Adobe Campaign vers un fichier du serveur ou de l’ordinateur local à l’aide de l’activité de workflow **[!UICONTROL EXPORT]**.

* **[!UICONTROL ACCÈS AUX FICHIERS]** : droit d’accès aux fichiers en lecture et écriture via un script pouvant être écrit dans l’activité de workflow **[!UICONTROL JavaScript]** pour lire/écrire des fichiers sur un serveur.

* **[!UICONTROL IMPORT GÉNÉRIQUE]** : droit d’import générique de données. **[!UICONTROL IMPORT]** permet d’importer des données dans n’importe quelle autre table, tandis que le droit **[!UICONTROL IMPORT DE DESTINATAIRES]** ne permet d’effectuer un import que dans la table des destinataires.

* **[!UICONTROL INSERTION DES DOSSIERS]** : droit d’insérer des dossiers. Les utilisateurs disposant du droit **[!UICONTROL INSERTION DES DOSSIERS]** peuvent créer des dossiers dans l’arborescence de dossiers à l’aide de la vue de l’explorateur.

* **[!UICONTROL LOCAL]** : droit de gestion en local (Marketing distribué).

* **[!UICONTROL FUSION]** : droit de fusionner les enregistrements sélectionnés en un seul. S’il existe des doublons de destinataires, le droit **[!UICONTROL FUSION]** permet de les sélectionner et de les fusionner dans un destinataire principal.

* **[!UICONTROL PRÉPARER DES DIFFUSIONS]** : droit de créer, éditer et enregistrer une diffusion. Les utilisateurs disposant du droit **[!UICONTROL PRÉPARER DES DIFFUSIONS]** peuvent également lancer le processus d’analyse de diffusion.

* **[!UICONTROL DROIT RELATIF AUX DONNÉES PERSONNELLES]** : droit de collecter et de supprimer des informations personnelles. Voir à ce propos [cette page](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html).

* **[!UICONTROL EXÉCUTION DE PROGRAMMES]** : droit d’exécuter des commandes dans divers langages de programmation.

* **[!UICONTROL IMPORT DE DESTINATAIRES]** : droit d’importer des destinataires. Les utilisateurs disposant du droit **[!UICONTROL IMPORT DE DESTINATAIRES]** peuvent importer un fichier local dans la table des destinataires.

* **[!UICONTROL EXÉCUTION DE SCRIPTS SQL]** : droit d’exécuter des commandes SQL sur la base de données.

* **[!UICONTROL DÉMARRER DES DIFFUSIONS]** : droit de valider les diffusions préalablement analysées. Une fois l’analyse de diffusion terminée, la diffusion s’interrompt pour différentes étapes de validation et doit être approuvée pour reprendre. Les utilisateurs disposant du droit **[!UICONTROL DÉMARRER DES DIFFUSIONS]** sont autorisés à valider des diffusions.

* **[!UICONTROL UTILISER L’ACTIVITÉ DE GESTION DES DONNÉES SQL]** : droit d’écriture de vos propres scripts SQL, à l’aide de l’activité Gestion des données SQL, dans le but de créer et de remplir des tables de travail. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-data-management.html?lang=fr){target="_blank"}.

* **[!UICONTROL WORKFLOW]** : droit d’exécuter des workflows. Sans ce droit, les utilisateurs ne peuvent pas démarrer, arrêter ou redémarrer des workflows.

* **[!UICONTROL WEBAPP]** : droit d’utilisation des applications web.

>[!NOTE]
>
>Cette liste peut varier en fonction des composants additionnels installés sur la plateforme.

## Matrice des droits d’accès {#access-rights-matrix}

Les groupes par défaut et les droits nommés permettent aux opérateurs d&#39;accéder à certains dossiers de l&#39;arborescence, et accordent des autorisations en lecture, écriture et suppression.

La matrice des droits d&#39;accès Adobe Campaign est disponible [ici](/help/platform/using/assets/access-rights-matrix.pdf).

[![image](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf)

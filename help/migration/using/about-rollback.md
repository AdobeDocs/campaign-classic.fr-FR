---
product: campaign
title: Restauration de la version précédente
description: Découvrez comment restaurer la version précédente
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 100%

---

# Restauration de la version précédente{#about-rollback}



Après une migration, en cas de problème, vous devrez peut-être revenir à la version précédente de Campaign.

La procédure de restauration dépend de votre version initiale de Campaign.

Voici la procédure pour restaurer la version v6.1 à partir de la version v7.

1. Récupérez la sauvegarde de la base de données et restaurez-la.
1. Récupérez le dossier Adobe Campaign **v6.back** (**nl6.back** sous Linux), renommez-le **Neolane v6** (**nl6** sous Linux) et restaurez-le à son emplacement d&#39;origine.
1. Reparamétrez IIS en réaffectant les ports d&#39;écoute afin de rétablir l&#39;intégration d&#39;Adobe Campaign v6.1 au niveau du site Web IIS.
1. Arrêtez le service Adobe Campaign v7.
1. Redémarrez IIS.
1. Redémarrez le service Adobe Campaign v6.1.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->
---
product: campaign
title: Restauration
description: Restauration
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: ba4db1af-778c-4c34-9a3c-49f41faa49b5
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 100%

---

# Restauration{#restoration}



La procédure de restauration sur un serveur vierge est la suivante :

* sur un système d&#39;exploitation installé et paramétré (Réseaux),
* installation des applications tierces : serveur WEB, JDK (si nécessaire),
* installation des binaires Adobe Campaign du même build que le système source,
* copie des fichiers de configuration, des logs de tracking ainsi que des fichiers de redirection,
* création et remontage de la base de données,
* lancement d&#39;Adobe Campaign.

Pour plus d&#39;informations, reportez-vous au **Guide d&#39;Installation**.

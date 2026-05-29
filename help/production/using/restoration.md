---
product: campaign
title: Restauration
description: Restauration
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: ba4db1af-778c-4c34-9a3c-49f41faa49b5
TQID: https://experienceleague.adobe.com/ZXUhBpNXWOjaLlJ0U1ToxAi9HlC0AKenRKIIu0z-63c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 96
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

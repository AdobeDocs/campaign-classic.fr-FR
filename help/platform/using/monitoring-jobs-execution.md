---
product: campaign
title: Surveillance de l'exécution des traitements
description: Découvrez comment surveiller l'exécution des traitements d'import et d'export.
feature: Monitoring
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
TQID: 'https://experienceleague.adobe.com/g25R2WVJ2ULkITvhyNbvq87lxMdUNaHDJdm9rZNg-PA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 59d78c785d8984861fd537c2f64f82a7d2d77fbf
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 89%
---
# Surveillance de l’exécution des traitements {#monitoring-job-execution}



Vous pouvez suivre l&#39;exécution de vos traitements d&#39;import et d&#39;export directement depuis la liste des traitements d&#39;import/export.

![](assets/s_ncs_user_export_list_and_details.png)

* L&#39;onglet **[!UICONTROL Journal]** permet de consulter les messages de logs relatifs à l&#39;exécution.
* L’onglet **[!UICONTROL Rejets]** contient les enregistrements rejetés. Voir [cette section](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/data/import#behavior-in-the-event-of-an-error){target="_blank"} (documentation de Campaign v8).

Dans l&#39;onglet **[!UICONTROL Général]**, le champ **[!UICONTROL Statut]** indique le statut actuel d&#39;un traitement.

Chaque statut est représenté par une icône et un libellé spéciaux. Les statuts et leurs icônes sont répertoriés ci-dessous :

![](assets/s_ncs_user_export_status.png)

* **Edition en cours**

  Traitement en cours de création.

* **En cours d&#39;exécution**

  Traitement en cours d&#39;exécution.

* **Annuler**

  Clic sur le bouton **[!UICONTROL Annuler]** : l&#39;annulation du traitement en cours.

* **Annulation en cours**

  La commande d&#39;annulation a été prise en compte et le traitement est en cours d&#39;annulation.

* **Pause en cours**

  Clic sur le bouton **[!UICONTROL Pause]** : la suspension du traitement est en cours.

* **En pause**

  Clic sur le bouton **[!UICONTROL Pause]** : le traitement est suspendu. Il peut être redémarré en cliquant sur **[!UICONTROL Démarrer]**.

* **Terminé**

  Exécution du traitement terminée.

* **Terminé en erreur**

  Le traitement n&#39;a pas été exécuté à cause d&#39;une erreur technique.

* **Arrêt du serveur en cours**

  Le traitement en cours est interrompu à cause d&#39;un arrêt du serveur Adobe Campaign.

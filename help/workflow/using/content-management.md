---
product: campaign
title: Gestion de contenu
description: Gestion de contenu
feature: Workflows, Data Management
hide: true
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
TQID: https://experienceleague.adobe.com/L48BSqjuFHlOqQXephJbhjEzEvDkBooRCQpdd4WtbSs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 463
ht-degree: 100%

---

# Gestion de contenu{#content-management}



Une activité **Gestion de contenu** vous permet de créer et de manipuler un contenu ainsi que de générer les fichiers à partir de ce contenu.Ce contenu peut ensuite être diffusé à l’aide d’une activité « Diffusion ».

>[!CAUTION]
>
>La gestion de contenu est un module optionnel d’Adobe Campaign.Veuillez vérifier votre contrat de licence.

Les propriétés de l&#39;activité se divisent en trois étapes :

* **Sélection du contenu**: le contenu peut avoir été créé précédemment ou peut être créé depuis l&#39;activité.
* **Mise à jour du contenu**: la tâche peut modifier l&#39;objet du contenu ou importer tout le contenu XML.
* **Action**: le contenu résultant peut être enregistré ou généré.

  ![](assets/content_mgmt_edit.png)

  Le paramétrage et l&#39;utilisation de la gestion de contenu dans Adobe Campaign sont présentés dans cette [section](../../delivery/using/about-content-management.md).

1. **Content**

   * **[!UICONTROL Spécifié par la transition]**

     Cette option vous permet d’utiliser le contenu spécifié dans la transition, c’est-à-dire que l’événement qui active la gestion de contenu doit contenir une variable **[!UICONTROL contentId]**.Cette variable peut avoir été définie par une gestion de contenu précédente ou par un quelconque script.

   * **[!UICONTROL Explicite]**

     Cette option permet de sélectionner un contenu déjà créé, à partir du champ **[!UICONTROL Contenu]**. Ce champ n&#39;est visible que lorsque l&#39;option **[!UICONTROL Explicite]** est sélectionnée.

     ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculé par un script]**

     L&#39;identifiant du contenu est calculé par un script. Le champ **[!UICONTROL Script]** permet de définir un template JavaScript évaluant l&#39;identifiant (la clé primaire) du contenu. Ce champ n&#39;est visible que lorsque l&#39;option **[!UICONTROL Calculé par un script]** est sélectionnée.

     ![](assets/content_mgmt_script.png)

   * **[!UICONTROL Nouveau, créé depuis un modèle de publication]**

     Créer un nouveau contenu depuis un modèle de publication. Ce nouveau contenu sera enregistré dans le dossier indiqué dans le champ **[!UICONTROL Chaîne]**. Le champ **[!UICONTROL Modèle]** indique le modèle de publication à utiliser pour créer le contenu.

     ![](assets/content_mgmt_new.png)

1. **Mettre à jour le contenu**

   * **[!UICONTROL Objet]**

     Ce champ permet de modifier l&#39;objet du contenu.

   * **[!UICONTROL Accès aux données provenant d&#39;un flux XML]**

     Cette option permet de construire le contenu à partir d&#39;un document XML téléchargé depuis un serveur Web et éventuellement de le transformer via une feuille de style XSL. Lorsque cette option est cochée, le champ **[!UICONTROL URL]** indique l&#39;URL de téléchargement du contenu XML. Le champ **[!UICONTROL Feuille de style XSL]** permet d&#39;indiquer la feuille de style à utiliser pour transformer le document XML téléchargé. Cette propriété est optionnelle.

     ![](assets/content_mgmt_xmlcontent.png)

1. **Action à effectuer**

   * **[!UICONTROL Enregistrer]**

     Cette option enregistre le contenu créé ou modifié.

     La transition sortante est activée une seule fois avec pour paramètre l&#39;identifiant du contenu enregistré dans la variable **[!UICONTROL contentId]**.

   * **[!UICONTROL Générer]**

     Cette option enregistre le contenu puis génère les fichiers de sortie pour chacun des modèles de transformation dont le type de publication est &#39;Fichier&#39;.

     ![](assets/content_mgmt_generate.png)

     La transition sortante est activée pour chacun des fichiers générés avec pour paramètre l&#39;identifiant du contenu enregistré dans la variable **[!UICONTROL contentId]** et le nom du fichier dans la variable **[!UICONTROL filename]**.

## Paramètres d&#39;entrée {#input-parameters}

* contentId

Identifiant du contenu à utiliser, si l&#39;option **[!UICONTROL Spécifié par la transition]** est activée.

## Paramètres de sortie {#output-parameters}

* contentId

  Identifiant du contenu.

* filename

  Nom complet du fichier généré, si l&#39;action sélectionnée est **[!UICONTROL Générer]**.

## Exemples {#examples}

Des exemples sont proposés dans cette [section](../../delivery/using/automating-via-workflows.md#examples).

---
solution: Campaign Classic
product: campaign
title: Documents et compositions de diffusion des campagnes marketing
description: En savoir plus sur les documents et compositions de diffusion des campagnes marketing
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 65%

---


# Gérer les documents associés {#managing-associated-documents}

Vous pouvez associer divers documents à une campagne : rapports, photos, pages Web, diagrammes, etc. Ces documents peuvent être dans n’importe quel format (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, etc.).

>[!IMPORTANT]
>
>Cette fonctionnalité est réservée aux petits actifs et documents.

Dans une campagne, vous pouvez également faire référence à d’autres éléments, tels que des bons promotionnels, des offres spéciales relatives à une marque ou à un magasin spécifique, etc. Lorsque ces éléments sont inclus dans un plan, ils peuvent être associés à une diffusion de messagerie directe. Voir [Associer et structurer des ressources liées par une composition de diffusion](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Si vous utilisez le module de gestion des Ressources marketing Campaign, vous pouvez également gérer une bibliothèque de ressources marketing disponible pour plusieurs utilisateurs pour le travail collaboratif. [En savoir plus](../../campaign/using/managing-marketing-resources.md).

## Documents d&#39;Ajoute {#adding-documents}

Des documents peuvent être associés au niveau de l&#39;opération (documents contextuels) ou au niveau du programme (documents généraux).

L&#39;onglet **[!UICONTROL Documents]** contient :

* la liste de tous les documents nécessaires au contenu (maquette, images, etc.) qui pourront être téléchargés en local par les opérateurs Adobe Campaign possédant les droits adéquats,
* les documents contenant des informations destinées au routeur, s&#39;ils existent.

Les documents sont rattachés au programme ou à l&#39;opération via leur onglet **[!UICONTROL Edition > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

Vous pouvez également ajouter un document dans une opération via le lien proposé dans son tableau de bord.

![](assets/add_a_document_in_op.png)

Cliquez sur l&#39;icône **[!UICONTROL Détails]** pour visualiser le contenu d&#39;un fichier et ajouter des informations complémentaires :

![](assets/s_ncs_user_op_add_document_details.png)

Au niveau du tableau de bord, les documents associés à l&#39;opération sont regroupés dans la section **[!UICONTROL Document(s)]**, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_op_edit_document.png)

Ils peuvent également être édités et modifiés depuis cette vue.

## Associer et structurer des ressources liées par une composition de diffusion {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Les compositions sont exclusivement utilisées dans le cadre d&#39;opérations courrier.

Une composition de diffusion désigne un ensemble structuré d’éléments (documents, magasins, bons promotionnels, etc.) créée par la société et pour une campagne particulière.

Ces éléments sont regroupés en compositions de diffusion et chaque composition de diffusion sera associée à une diffusion ; il sera référencé dans le fichier d&#39;extraction envoyé au **prestataire** afin d&#39;être joint à la diffusion. Par exemple, vous pouvez créer une composition de diffusion qui fait référence à une branche et aux brochures marketing qu’elle utilise.

Les compositions permettent, au niveau de l&#39;opération, de structurer des éléments externes qui seront associés à la diffusion en fonction de certains critères : agence de rattachement, offre promotionnelle accordée, invitation à un événement local, etc.

### Créer un plan {#creating-an-outline}

Pour créer une composition, cliquez sur le sous-onglet **[!UICONTROL Compositions de diffusions]** proposé dans l&#39;onglet **[!UICONTROL Edition > Documents]** de l&#39;opération concernée.

>[!NOTE]
>
>Si cet onglet n&#39;est pas présent, alors cette fonctionnalité n&#39;est pas prise en compte pour cette opération. Reportez-vous à la configuration du modèle d&#39;opération.
>   
>Pour plus d’informations sur les modèles de , reportez-vous à [cette section](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Cliquez ensuite sur **[!UICONTROL Ajouter une composition de diffusion]** et créez l&#39;arborescence des compositions pour l&#39;opération :

1. Cliquez avec le bouton droit sur la racine de l&#39;arborescence et choisissez **[!UICONTROL Nouveau > Compositions de diffusion]**.
1. Cliquez avec le bouton droit de la souris sur la composition que vous venez de créer et choisissez **[!UICONTROL Nouveau > Article]** ou **[!UICONTROL Nouveau > Champs de personnalisation]**.

![](assets/s_ncs_user_op_add_composition.png)

Une composition peut contenir des articles, des champs de personnalisation, des ressources et des offres :

* Les articles sont par exemple des documents physiques qui sont ici référencés et décrits, et seront joints à la diffusion.
* Les champs de personnalisation permettent de créer des éléments de personnalisation relatifs aux diffusions et non aux destinataires. Ainsi, il est possible de créer des valeurs qui seront utilisées dans les diffusions pour une cible spécifique (offre de bienvenue, pourcentage de réduction, etc.) Ils sont créés dans Adobe Campaign et importés dans la composition, via le lien **[!UICONTROL Importer des champs de personnalisation...]**.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   Ils peuvent également être créés directement dans la composition, en cliquant sur l&#39;icône **[!UICONTROL Ajouter]** située à droite de la zone de liste.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Les ressources sont des ressources marketing générées dans le tableau de bord de ressource marketing accessibles via le lien **[!UICONTROL Ressources]** de l&#39;onglet **[!UICONTROL Campagnes]**.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Pour plus d&#39;informations sur les ressources marketing, consultez [cette section](../../campaign/using/managing-marketing-resources.md).

### Sélectionner un contour {#selecting-an-outline}

Pour chaque diffusion, vous pouvez sélectionner la composition à associer à partir de la section réservée à la configuration de l&#39;extraction, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_op_select_composition.png)

La composition sélectionnée est alors affichée dans la section inférieure de la fenêtre. Elle peut être éditée à partir de l&#39;icône située à droite du champ ou modifiée en utilisant la liste déroulante :

![](assets/s_ncs_user_op_select_composition_b.png)

L&#39;onglet **[!UICONTROL Résumé]** de la diffusion affiche également cette information :

![](assets/s_ncs_user_op_select_composition_c.png)

### Résultat de l&#39;extraction {#extraction-result}

Dans le fichier extrait et transmis au prestataire, le nom de la composition et éventuellement ses caractéristiques (coût, description, etc.) sont ajoutés au contenu, selon les informations présentes dans le modèle d&#39;export associé au prestataire.

Dans l&#39;exemple suivant, le libellé, le coût prévisionnel estimé et la description de la composition associée à la diffusion seront ajoutés dans le fichier d&#39;extraction.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Le modèle d&#39;export doit être associé au prestataire sélectionné pour la diffusion concernée. Reportez-vous à [cette section](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Pour plus d&#39;informations sur les exportations, consultez la section [cette section](../../platform/using/get-started-data-import-export.md).

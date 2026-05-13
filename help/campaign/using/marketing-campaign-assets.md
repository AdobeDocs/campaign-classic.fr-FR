---
product: campaign
title: Compositions de diffusions et documents des campagnes marketing
description: En savoir plus sur les compositions de diffusions et sur les documents des campagnes marketing
role: User
feature: Campaigns
hide: true
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
TQID: https://experienceleague.adobe.com/ZHqo0izYPVfaxPIShcjgPpg-5SIGkdQAwbD6dV1r6bE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 788
ht-degree: 68%

---

# Gestion des documents associés {#managing-associated-documents}

Vous pouvez associer différents documents à une opération : rapports, photos, pages web, diagrammes, etc. Ces documents peuvent avoir n’importe quel format (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, etc.).

>[!IMPORTANT]
>
>Cette fonctionnalité est réservée aux petites ressources et documents.

Dans une campagne, vous pouvez également faire référence à d’autres articles, tels que des coupons promotionnels, des offres spéciales liées à une marque ou à un magasin spécifique, etc. Lorsque ces éléments sont inclus dans une composition, ils peuvent être associés à une diffusion courrier. Voir à ce sujet la section [Association et structure des ressources liées via une composition de diffusion](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Si vous utilisez le module de gestion de ressources marketing de Campaign, vous pouvez également gérer une bibliothèque de ressources marketing sur lesquelles plusieurs intervenants peuvent agir dans un mode collaboratif. [En savoir plus](../../mrm/using/managing-marketing-resources.md).

## Ajout de documents {#adding-documents}

Des documents peuvent être associés au niveau de l&#39;opération (documents contextuels) ou au niveau du programme (documents généraux).

L&#39;onglet **[!UICONTROL Documents]** contient :

* La liste de tous les documents requis pour le contenu (modèle, images, etc.) qui peuvent être téléchargés localement par les opérateurs Adobe Campaign disposant des droits adéquats,
* les documents contenant des informations destinées au routeur, s&#39;ils existent.

Les documents sont rattachés au programme ou à l&#39;opération via leur onglet **[!UICONTROL Edition > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

Vous pouvez également ajouter un document dans une opération via le lien proposé dans son tableau de bord.

![](assets/add_a_document_in_op.png)

Cliquez sur l&#39;icône **[!UICONTROL Détails]** pour visualiser le contenu d&#39;un fichier et ajouter des informations complémentaires :

![](assets/s_ncs_user_op_add_document_details.png)

Au niveau du tableau de bord, les documents associés à l&#39;opération sont regroupés dans la section **[!UICONTROL Document(s)]**, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_op_edit_document.png)

Ils peuvent également être édités et modifiés depuis cette vue.

## Association et structure des ressources liées via une composition de diffusion {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Les compositions de diffusion sont exclusivement utilisées dans le cadre de campagnes courrier.

Une composition de diffusion désigne un ensemble structuré d’éléments (documents, magasins, coupons promotionnels, etc.) créé par la société et pour une opération particulière.

Ces éléments sont regroupés au sein de compositions de diffusions, chacune associée à une diffusion. La composition de diffusion sera référencée dans le fichier d’extraction envoyé au **fournisseur** afin d’être jointe à la diffusion. Par exemple, vous pouvez créer une composition de diffusion qui fait référence à une branche et aux brochures marketing qu’elle utilise.

Les compositions de diffusions permettent, au niveau de la campagne, de structurer des éléments externes qui seront associés à la diffusion en fonction de certains critères : branche de rattachement, offre promotionnelle accordée, invitation à un événement local, etc.

### Création d’une composition {#creating-an-outline}

Pour créer une composition, cliquez sur le sous-onglet **[!UICONTROL Compositions de diffusions]** proposé dans l&#39;onglet **[!UICONTROL Edition > Documents]** de l&#39;opération concernée.

>[!NOTE]
>
>Si cet onglet n’est pas présent, cette fonctionnalité n’est pas disponible pour cette campagne. Pour plus d&#39;informations, consultez la section configuration du modèle de campagne .
>   
>Pour plus d’informations sur les modèles, reportez-vous à [cette section](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Cliquez ensuite sur **[!UICONTROL Ajouter une composition de diffusion]** et créez l&#39;arborescence des compositions pour l&#39;opération :

1. Cliquez avec le bouton droit sur la racine de l&#39;arborescence et choisissez **[!UICONTROL Nouveau > Compositions de diffusion]**.
1. Cliquez avec le bouton droit de la souris sur la composition que vous venez de créer et choisissez **[!UICONTROL Nouveau > Article]** ou **[!UICONTROL Nouveau > Champs de personnalisation]**.

![](assets/s_ncs_user_op_add_composition.png)

Une composition peut contenir des articles, des champs de personnalisation, des ressources et des offres :

* Les articles sont par exemple des documents physiques qui sont ici référencés et décrits, et seront joints à la diffusion.
* Les champs de personnalisation permettent de créer des éléments de personnalisation relatifs aux diffusions et non aux destinataires. Il est ainsi possible de créer des valeurs qui seront utilisées dans les diffusions pour une cible spécifique (offre de bienvenue, remise, etc.) Ils sont créés dans Adobe Campaign et importés dans la composition via le lien **[!UICONTROL Importer des champs de personnalisation...]** .

  ![](assets/s_ncs_user_op_add_composition_field.png)

  Ils peuvent également être créés directement dans la composition, en cliquant sur l&#39;icône **[!UICONTROL Ajouter]** située à droite de la zone de liste.

  ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Les ressources sont des ressources marketing générées dans le tableau de bord des ressources marketing, lequel est accessible à partir du lien **[!UICONTROL Ressources]** de l’onglet **[!UICONTROL Campagnes]**.

  ![](assets/s_ncs_user_mkg_resource_ovv.png)

  >[!NOTE]
  >
  >Pour plus d’informations sur les ressources marketing, reportez-vous à [cette section](../../mrm/using/managing-marketing-resources.md).

### Sélection d’une composition {#selecting-an-outline}

Pour chaque diffusion, vous pouvez sélectionner la composition à associer à partir de la section réservée à la configuration de l&#39;extraction, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_op_select_composition.png)

La composition sélectionnée est alors affichée dans la section inférieure de la fenêtre. Elle peut être modifiée à l’aide de l’icône située à droite du champ ou dans la liste déroulante :

![](assets/s_ncs_user_op_select_composition_b.png)

L&#39;onglet **[!UICONTROL Résumé]** de la diffusion affiche également cette information :

![](assets/s_ncs_user_op_select_composition_c.png)

### Résultat de l&#39;extraction {#extraction-result}

Dans le fichier extrait et transmis au prestataire, le nom de la composition et le cas échéant ses caractéristiques (coût, description, etc.) sont ajoutées au contenu en fonction des informations du modèle d’exportation associé au fournisseur de services.

Dans l&#39;exemple suivant, le libellé, le coût prévisionnel estimé et la description de la composition associée à la diffusion seront ajoutés dans le fichier d&#39;extraction.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Le modèle d&#39;export doit être associé au prestataire sélectionné pour la diffusion concernée. Consultez [cette section](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Pour plus d’informations sur les exports, reportez-vous à [cette section](../../platform/using/get-started-data-import-export.md).

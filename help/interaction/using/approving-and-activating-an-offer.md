---
product: campaign
title: Valider et activer une offre
description: Valider et activer une offre
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 98%

---

# Valider et activer une offre{#approving-and-activating-an-offer}



Une fois le contenu de l&#39;offre terminé, vous devez procéder à sa validation afin qu&#39;elle soit dupliquée dans l&#39;environnement en ligne pour être diffusée par la suite. La validation porte sur le contenu de l&#39;offre et sur son éligibilité.

Un bandeau dans le tableau de bord de l&#39;offre vous permet de voir si l&#39;offre doit passer par le cycle de validation ou non.

![](assets/offer_validate_001.png)

## Valider le contenu d&#39;une offre {#approving-offer-content}

Valider le contenu d&#39;une offre consiste à choisir la ou les représentations que vous souhaitez rendre disponibles dans l&#39;environnement en ligne.

Le contenu d&#39;une offre a une représentation par emplacement. Chaque emplacement disposant de sa propre structure et ses propres fonctions de rendu, la représentation des offres peut varier.

Vous pouvez ainsi choisir de valider le contenu d&#39;une offre sur certains emplacements disponibles et ne pas le valider sur d&#39;autres.

>[!IMPORTANT]
>
>Lorsque le contenu et l&#39;éligibilité d&#39;une offre sont validés, le workflow de publication (Notification des offres) se lance automatiquement et l&#39;offre est ainsi mise en ligne et rendue disponible sur les emplacements activés.

Pour valider le contenu d&#39;une offre, procédez comme suit :

1. Cliquez sur le bouton **[!UICONTROL Validation]** et sélectionnez **[!UICONTROL Valider le contenu]** dans le menu contextuel.

   ![](assets/offer_validate_002.png)

1. A l&#39;aide de la liste déroulante, sélectionnez les représentations que vous souhaitez laisser en édition ou activer dans l&#39;environnement en ligne, puis cliquez sur **[!UICONTROL Validation du contenu]**.

   ![](assets/offer_validate_003.png)

   Lorsque le contenu de l&#39;offre est validé, les informations sont mises à jour dans le tableau de bord de l&#39;offre.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >La mention **[!UICONTROL Contenu validé]** ne signifie pas que toutes les représentations de l&#39;offre ont été activées et approuvées. Elle indique que le processus d&#39;approbation de contenu a été réalisé, que toutes les offres aient été activées/approuvées ou non.

## Valider l&#39;éligibilité d&#39;une offre {#approving-offer-eligibility}

Une tâche parent planifiée pour finir le mardi 9 octobre à 17h a 2 tâches enfants, la tâche A et la tâche B. La tâche A est planifiée pour commencer le 10 octobre à 14h et la tâche B, planifiée pour commencer le 12 octobre à 8h.

>[!IMPORTANT]
>
>Lorsque le contenu et l&#39;éligibilité d&#39;une offre sont validés, le workflow de publication (Notification des offres) se lance automatiquement et l&#39;offre est ainsi mise en ligne et rendue disponible sur les emplacements activés.

* La liste complète des règles peut être consultée lorsque vous cliquez sur **[!UICONTROL Planning et règle d&#39;éligibilité de l&#39;offre]**.

  ![](assets/offer_validate_005.png)

* Si vous souhaitez modifier les règles d&#39;éligibilité, cliquez sur **[!UICONTROL Rejeter]**, puis sur **[!UICONTROL Validation de l&#39;éligibilité]**.

  ![](assets/offer_validate_007.png)

  Les différents statuts sont mis à jour dans le tableau de bord de l&#39;offre.

  ![](assets/offer_validate_006.png)

* Pour accepter l&#39;éligibilité de l&#39;offre, cliquez sur **[!UICONTROL Valider l&#39;éligibilité]**.

  ![](assets/offer_validate_008.png)

  Approuvez l&#39;éligibilité, ajoutez un commentaire le cas échéant, puis cliquez sur **[!UICONTROL Validation de l&#39;éligibilité]**.

  ![](assets/offer_validate_009.png)

  Les différents statuts sont mis à jour dans le tableau de bord de l&#39;offre.

  ![](assets/offer_validate_010.png)

## Suivi des validations {#approval-tracking}

Le suivi des validations est disponible dans le tableau de bord de l&#39;offre. Cliquez sur **[!UICONTROL Afficher/cacher le journal]** pour y accéder.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>Le suivi est également disponible dans l&#39;onglet **[!UICONTROL Suivi]** de l&#39;offre, avec le détail des commentaires des validants.

## Réinitialiser la validation {#restart-the-approval}

Une fois la validation lancée, il est possible de la réinitialiser. Pour ce faire, suivez les instructions suivantes :

1. Sur le tableau de bord de l&#39;offre, cliquez sur **[!UICONTROL Contenu validé]**.
1. Dans la fenêtre **[!UICONTROL Edition]** qui apparait, sélectionnez la validation à réinitialiser, puis cliquez sur **[!UICONTROL Réinitialiser la validation pour la soumettre à nouveau]**.
1. Confirmez en cliquant sur **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## Publication de l&#39;offre {#publishing-the-offer}

Lorsque le contenu et l&#39;éligibilité de l&#39;offre ont tous deux été validés, l&#39;offre est mise en ligne. La mise en ligne est effectuée par un workflow technique qui se lance automatiquement pour chaque offre dont le cycle de validation est terminé. Le workflow **[!UICONTROL Notification des offres]** se lance également toutes les heures afin de synchroniser (si besoin) les emplacements et les catégories contenues dans le catalogue d&#39;offres depuis l&#39;environnement en édition vers l&#39;environnement en ligne.

Le tableau de bord de l&#39;offre disponible dans l&#39;environnement en édition contient les informations relatives à la mise en ligne, notamment le nom de l&#39;offre correspondante dans l&#39;environnement en ligne.

![](assets/offer_golive_001.png)

Pour afficher l&#39;offre disponible dans l&#39;environnement en ligne, cliquez sur le libellé de l&#39;offre : l&#39;offre en ligne dispose d&#39;un tableau de bord dans lequel se trouvent toutes les informations qui lui sont relatives.

![](assets/offer_golive_002.png)

## Désactiver une offre {#disabling-an-offer}

Une fois une offre validée, il est possible de la désactiver.

Pour ce faire, rendez-vous sur le tableau de bord d&#39;une offre en ligne ou en attente de mise en ligne, puis cliquez sur **[!UICONTROL Désactiver l&#39;offre]**.

Vous pouvez également désactiver directement une catégorie en vous rendant dans l&#39;onglet **[!UICONTROL Eligibilité]** d&#39;une catégorie puis en décochant la case **[!UICONTROL Activée]**.

>[!NOTE]
>
>Lorsqu&#39;une offre est supprimée dans un environnement en édition, elle est automatiquement désactivée dans l&#39;environnement en ligne associé. Après un délai de rétention des propositions, les offres désactivées sont supprimées de l&#39;environnement en ligne.

![](assets/offer_preview_deactivate.png)

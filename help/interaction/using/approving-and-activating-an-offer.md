---
title: Valider et activer une offre
seo-title: Valider et activer une offre
description: Valider et activer une offre
seo-description: null
page-status-flag: never-activated
uuid: 1be96bb4-ef17-4b4d-b872-05e1c6b1412d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 7b1c58a0-6fd6-4c9d-b1c4-f3dffda42523
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Valider et activer une offre{#approving-and-activating-an-offer}

Une fois le contenu de l&#39;offre terminé, vous devez procéder à sa validation afin qu&#39;elle soit dupliquée dans l&#39;environnement en ligne pour être diffusée par la suite. La validation porte sur le contenu de l&#39;offre et sur son éligibilité.

Un bandeau dans le tableau de bord de l&#39;offre vous permet de voir si l&#39;offre doit passer par le cycle de validation ou non.

![](assets/offer_validate_001.png)

## Valider le contenu d&#39;une offre {#approving-offer-content}

Valider le contenu d&#39;une offre consiste à choisir la ou les représentations que vous souhaitez rendre disponibles dans l&#39;environnement en ligne.

Le contenu d&#39;une offre a une représentation par emplacement. Chaque emplacement disposant de sa propre structure et ses propres fonctions de rendu, la représentation des offres peut varier.

Vous pouvez ainsi choisir de valider le contenu d&#39;une offre sur certains emplacements disponibles et ne pas le valider sur d&#39;autres.

>[!CAUTION]
>
>Lorsque le contenu et l&#39;éligibilité d&#39;une offre sont validés, le workflow de publication (Notification des offres) se lance automatiquement et l&#39;offre est ainsi mise en ligne et rendue disponible sur les emplacements activés.

Pour valider le contenu d&#39;une offre, procédez comme suit :

1. Cliquez sur le **[!UICONTROL Approval]** bouton et sélectionnez **[!UICONTROL Approve content]** dans la fenêtre contextuelle.

   ![](assets/offer_validate_002.png)

1. Using the drop-down list, select the representations you want to keep editing or those you want to publish to the live environment, then click **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   Lorsque le contenu de l&#39;offre est validé, les informations sont mises à jour dans le tableau de bord de l&#39;offre.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >La **[!UICONTROL Content approved]** mention ne signifie pas que toutes les représentations de l’offre ont été activées et approuvées. Il indique que le processus d’approbation du contenu a été effectué, que toutes les offres aient été activées/approuvées ou non.

## Valider l&#39;éligibilité d&#39;une offre {#approving-offer-eligibility}

Valider l&#39;éligibilité d&#39;une offre consiste à accepter ou non les poids de l&#39;offre et les règles d&#39;éligibilité également paramétrés dans l&#39;offre ou hérités des règles créées au niveau de sa catégorie mère.

>[!CAUTION]
>
>Lorsque le contenu et l&#39;éligibilité d&#39;une offre sont validés, le workflow de publication (Notification des offres) se lance automatiquement et l&#39;offre est ainsi mise en ligne et rendue disponible sur les emplacements activés.

* Vous pouvez afficher la liste complète des règles en cliquant sur **[!UICONTROL Schedule and eligibility rules]**.

   ![](assets/offer_validate_005.png)

* Pour modifier les règles d’éligibilité, cliquez sur **[!UICONTROL Reject]**, puis sur **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_007.png)

   Les différents statuts sont mis à jour dans le tableau de bord de l&#39;offre.

   ![](assets/offer_validate_006.png)

* To accept the offer eligibility, click **[!UICONTROL Approve eligibility]**.

   ![](assets/offer_validate_008.png)

   Approve eligibility, add a comment if necessary, then click **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_009.png)

   Les différents statuts sont mis à jour dans le tableau de bord de l&#39;offre.

   ![](assets/offer_validate_010.png)

## Suivi des validations {#approval-tracking}

Le suivi des approbations est disponible dans le tableau de bord des offres. Cliquez **[!UICONTROL Hide/display logs]** pour y accéder.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>Tracking is also available in the **[!UICONTROL Audit]** tab of the offer, with details of reviewers&#39; comments.

## Réinitialiser la validation {#restart-the-approval}

Une fois la validation lancée, il est possible de la réinitialiser. Pour ce faire, suivez les instructions suivantes :

1. Cliquez sur **[!UICONTROL Content approved]** dans le tableau de bord de l’offre.
1. Dans la **[!UICONTROL Edit]** fenêtre qui s’affiche, sélectionnez l’approbation à redémarrer, puis cliquez sur **[!UICONTROL Re-initialize approval to submit it again]**.
1. Confirm by clicking **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## Mise en ligne de l&#39;offre {#publishing-the-offer}

Une fois que le contenu et l’éligibilité d’une offre ont été approuvés, l’offre est publiée par un processus qui s’exécute automatiquement pour chaque offre dont le cycle d’approbation est terminé. Le **[!UICONTROL Offer notification]** processus s’exécute également toutes les heures afin de synchroniser (si nécessaire) les espaces et catégories contenus dans le catalogue d’offres, de l’environnement de conception à l’environnement de production.

Le tableau de bord de l&#39;offre disponible dans l&#39;environnement en édition contient les informations relatives à la mise en ligne, notamment le nom de l&#39;offre correspondante dans l&#39;environnement en ligne.

![](assets/offer_golive_001.png)

Pour afficher l&#39;offre disponible dans l&#39;environnement en ligne, cliquez sur le libellé de l&#39;offre : l&#39;offre en ligne dispose d&#39;un tableau de bord dans lequel se trouvent toutes les informations qui lui sont relatives.

![](assets/offer_golive_002.png)

## Désactiver une offre {#disabling-an-offer}

Une fois une offre validée, il est possible de la désactiver.

To do this, go to the dashboard for an online offer or an offer waiting to go online, then click **[!UICONTROL Disable offer]**.

You can also directly disable a category by going to the **[!UICONTROL Eligibility]** tab and checking the **[!UICONTROL Enabled]** box.

>[!NOTE]
>
>Lorsqu&#39;une offre est supprimée dans un environnement en édition, elle est automatiquement désactivée dans l&#39;environnement en ligne associé. Après un délai de rétention des propositions, les offres désactivées sont supprimées de l&#39;environnement en ligne.

![](assets/offer_preview_deactivate.png)


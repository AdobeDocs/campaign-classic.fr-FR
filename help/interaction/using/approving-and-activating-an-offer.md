---
product: campaign
title: Valider et activer une offre
description: Valider et activer une offre
feature: Interaction, Offers
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
TQID: https://experienceleague.adobe.com/f0zYxpc5-71Ci-4Q485v4rRdD1xHs6tKLkl7vrITMP0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 672
ht-degree: 100%

---

# Validation et activation d&#39;une offre{#approving-and-activating-an-offer}



Une fois le contenu de l’offre terminé, vous devez procéder à son approbation afin qu’elle soit dupliquée dans l’environnement en ligne pour être diffusée par la suite.La validation porte sur le contenu de l’offre et sur son éligibilité.

Un bandeau dans le tableau de bord de l&#39;offre vous permet de voir si l&#39;offre doit passer par le cycle de validation ou non.

![](assets/offer_validate_001.png)

## Valider le contenu d&#39;une offre {#approving-offer-content}

Valider le contenu d&#39;une offre consiste à choisir la ou les représentations que vous souhaitez rendre disponibles dans l&#39;environnement en ligne.

Le contenu d’une offre a une représentation par emplacement.Chaque emplacement disposant de sa propre structure et ses propres fonctions de rendu, la représentation des offres peut varier.

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
   >La mention **[!UICONTROL Contenu approuvé]** ne signifie pas que toutes les représentations de l’offre ont été activées et validées.Elle indique que le processus d’approbation du contenu a été réalisé, que toutes les offres aient été activées/approuvées ou non.

## Valider l&#39;éligibilité d&#39;une offre {#approving-offer-eligibility}

Approuver l’éligibilité d’une offre signifie accepter ou rejeter les pondérations de l’offre et les règles d’éligibilité également configurées dans l’offre ou héritées des règles créées dans la catégorie parente.

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

## Redémarrer la validation {#restart-the-approval}

Une fois la validation lancée, il est possible de la relancer.Pour ce faire, suivez les instructions suivantes :

1. Sur le tableau de bord de l&#39;offre, cliquez sur **[!UICONTROL Contenu approuvé]**.
1. Dans la fenêtre **[!UICONTROL Édition]** qui apparait, sélectionnez la validation à redémarrer, puis cliquez sur **[!UICONTROL Réinitialiser la validation pour la soumettre à nouveau]**.
1. Confirmez en cliquant sur **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## Publication de l&#39;offre {#publishing-the-offer}

Une fois le contenu et l&#39;éligibilité d&#39;une offre approuvés, l&#39;offre est publiée par un workflow qui s&#39;exécute automatiquement pour chaque offre dont le cycle d’approbation est terminé. Le workflow **[!UICONTROL Notification d’offre]** s’exécute également toutes les heures afin de synchroniser (si nécessaire) les emplacements et catégories contenus dans le catalogue d’offres de l’environnement en édition avec l’environnement en ligne.

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
>Lorsqu’une offre est supprimée dans un environnement de conception, elle est automatiquement désactivée dans l’environnement en ligne associé.Après une période de rétention des propositions, les offres désactivées sont supprimées de l’environnement en ligne.

![](assets/offer_preview_deactivate.png)

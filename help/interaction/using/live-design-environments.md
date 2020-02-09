---
title: Environnements en ligne/édition
seo-title: Environnements en ligne/édition
description: Environnements en ligne/édition
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Environnements en ligne/édition{#live-design-environments}

## Principe de fonctionnement {#operating-principle}

Interaction fonctionne avec deux types d&#39;environnements d&#39;offres :

* **[!UICONTROL Design]** environnements d’offres qui incluent des offres en cours de modification et qui peuvent être modifiées. Ces offres ne sont pas passées par le cycle d’approbation et ne sont pas diffusées aux contacts.
* **[!UICONTROL Live]** environnements d’offres qui incluent des offres approuvées lorsqu’elles sont présentées à des contacts. Les offres de cet environnement sont en lecture seule.

![](assets/offer_environments_overview_001.png)

Chaque **[!UICONTROL Design]** environnement est lié à un **[!UICONTROL Live]** environnement. Lorsqu’une offre est terminée, son contenu et ses règles d’éligibilité sont soumis à un cycle d’approbation. Une fois ce cycle terminé, l’offre concernée est automatiquement déployée dans l’ **[!UICONTROL Live]** environnement. À partir de ce moment, il sera disponible pour livraison.

Par défaut, l’interaction s’accompagne d’un **[!UICONTROL Design]** environnement et d’un **[!UICONTROL Live]** environnement qui lui sont associés. Les deux environnements sont préconfigurés pour cibler le tableau des destinataires prêts à l’emploi.

>[!NOTE]
>
>Pour cibler une autre table (table des visiteurs pour les offres anonymes ou table des destinataires spécifique), vous devez utiliser l’assistant de mappage de cible pour créer les environnements. Pour plus d’informations, reportez-vous à la section [Création d’un environnement](#creating-an-offer-environment)d’offre.

![](assets/offer_environments_overview_002.png)

Les gestionnaires des offres et les responsables de la prestation ont accès à différentes vues de l’environnement. Les responsables de prestation peuvent uniquement afficher l’environnement des **[!UICONTROL Live]** offres et utiliser les offres pour les diffuser. Les gestionnaires d’offres peuvent afficher et modifier l’ **[!UICONTROL Design]** environnement et afficher l’ **[!UICONTROL Live]** environnement. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## Créer un environnement d&#39;offres {#creating-an-offer-environment}

Par défaut, Interaction est livré avec un environnement pré-paramétré pour cibler la table des destinataires (offres identifiées). Si vous souhaitez cibler une autre table (table des visiteurs pour les offres anonymes ou table de destinataires spécifique), vous devez effectuer le paramétrage suivant :

1. Placez votre curseur sur le noeud **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** . Cliquez avec le bouton droit sur le mappage de remise à utiliser (**[!UICONTROL Visitors]** si vous souhaitez utiliser des offres anonymes) et sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Cliquez **[!UICONTROL Next]** pour passer à l’écran suivant de l’assistant, cochez la **[!UICONTROL Generate a storage schema for propositions]** case et cliquez sur **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Si la case était déjà cochée, décochez-la puis recochez-la.

1. Adobe Campaign crée deux environnements (**[!UICONTROL Design]** et **[!UICONTROL Live]** ) avec des informations de ciblage issues du mappage de cible précédemment activé. L’environnement est préconfiguré avec les informations de ciblage.

   Si vous avez activé **[!UICONTROL Visitor]** le mappage, la **[!UICONTROL Environment dedicated to incoming anonymous interactions]** case est automatiquement cochée dans l’ **[!UICONTROL General]** onglet de l’environnement.

   Cette option permet d&#39;activer les fonctions spécifiques aux interactions anonymes, notamment dans le paramétrage des emplacements de l&#39;environnement. Vous pourrez ainsi paramétrer des options permettant de basculer d&#39;un environnement &quot;identifié&quot; à un environnement &quot;anonyme&quot;.

   Par exemple, vous pouvez lier un espace d’offre d’environnement de destinataire (contact identifié) à un espace d’offre qui correspond à un environnement de visiteur (contact non identifié). De cette façon, différentes offres seront mises à la disposition du contact selon qu’il est identifié ou non. For more on this, refer to [Creating offer spaces](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>For more information on anonymous interactions on an inbound channel, refer to [Anonymous interactions](../../interaction/using/anonymous-interactions.md).


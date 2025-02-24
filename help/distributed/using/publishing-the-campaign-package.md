---
product: campaign
title: Publier le pack de campagnes
description: Publier le pack de campagnes
feature: Distributed Marketing
hide: true
hidefromtoc: true
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: 36fe54cf6d4d762d96205bd637311a426c741427
workflow-type: ht
source-wordcount: '482'
ht-degree: 100%

---

# Publier le pack de campagnes{#publishing-the-campaign-package}



Les opérateurs et opératrices de l’entité centrale publient dans la **[!UICONTROL liste des kits de campagne]**, les kits qu’ils souhaitent proposer aux entités locales.

Avant de pouvoir être publiés dans la liste des kits de campagne, les kits de campagnes doivent être validés par l’entité centrale. Pour cela, vous pouvez définir un réviseur ou une réviseuse, ou un groupe de réviseurs ou de réviseuses, au moyen de l’option **[!UICONTROL Paramètres de validation]** dans le kit de campagne.

## Définir un opérateur validant {#assigning-a-reviewer}

Pour indiquer le validant, cliquez sur le lien **[!UICONTROL Paramètres de validation...]** du kit d&#39;opération et choisissez l&#39;opérateur concerné dans la liste déroulante.

![](assets/s_advuser_mkg_dist_define_valid.png)

Vous pouvez alors lancer le processus de validation en cliquant sur le bouton **[!UICONTROL Soumettre à validation]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Un message de notification est alors envoyé au validant afin de confirmer la mise à disposition de ce kit d&#39;opération. Ce message propose un lien pour accepter ou refuser la validation via un accès web.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>Au niveau de l&#39;entité organisationnelle, vous pouvez également spécifier des opérateurs validants pour approuver les commandes. Pour plus d&#39;informations, consultez la section [Entités organisationnelles](about-distributed-marketing.md#organizational-entities).

## Ajouter d&#39;autres opérateurs validants {#adding-other-reviewers}

Depuis le lien **[!UICONTROL Paramètres de validation...]** du kit d&#39;opération, le lien **[!UICONTROL Editer...]** permet d&#39;ajouter d&#39;autres opérateurs validants.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Délais de validation {#approval-periods}

Par défaut, les opérateurs et opératrices validants disposent de trois jours pour procéder à la validation, à partir de la date de soumission.

Dans la fenêtre d’édition des réviseurs et des réviseuses, vous pouvez également paramétrer des rappels afin d’envoyer un ou plusieurs messages en cas de non validation d’un kit de campagne. Pour ce faire, cliquez sur le lien **[!UICONTROL Ajouter un rappel]**, puis sur le bouton **[!UICONTROL Ajouter]**.

Les rappels peuvent être envoyés à une date donnée et/ou **x** jours après la date d’envoi. Le type de rappel peut être paramétré dans la première colonne du tableau des rappels. Dans l&#39;exemple ci-dessous, les validants recevront un premier message de rappel le 29/01/2014, soit deux jours avant la date sélectionnée dans la colonne **[!UICONTROL Date]**, et un second message de rappel un jour avant la fin de la période de validation, c’est-à-dire deux jours après la date de soumission pour validation.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Une fois défini et une fois que le package a été soumis à validation, le planning des traitements est affiché directement dans l&#39;onglet **[!UICONTROL Suivi]**. Il indique la date limite de traitement calculée à partir de la configuration spécifiée ci-avant, et la date du ou des rappels paramétrés.

## Validation via la console Adobe Campaign {#approving-via-the-adobe-campaign-console}

Si aucun validant n&#39;a été défini ou si aucun des opérateurs notifiés n&#39;a validé le kit, le bouton **[!UICONTROL Valider le kit]** permet de procéder directement à la validation depuis l&#39;onglet **[!UICONTROL Tableau de bord]** du kit d&#39;opération ou depuis la vue d&#39;ensemble des kits.

![](assets/s_advuser_mkg_dist_valid_button.png)

Une fois validée, l&#39;opération est alors publiée, ajoutée à la liste et les entités locales pourront l&#39;utiliser dès que sa date de disponibilité sera atteinte. Si des entités locales ont été définies lors de la création de l&#39;opération, un message est envoyé aux opérateurs appartenant au groupe de notification des kits d&#39;opération pour les informer de la disponibilité de l&#39;opération. Si aucune entité n&#39;a été définie en amont, l&#39;opération est accessible par défaut pour toutes les entités locales. Pour plus d&#39;informations, consultez la section [Entités organisationnelles](about-distributed-marketing.md#organizational-entities).

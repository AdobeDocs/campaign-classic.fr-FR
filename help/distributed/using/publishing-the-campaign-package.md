---
product: campaign
title: Publier le pack de campagnes
description: Publier le pack de campagnes
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '479'
ht-degree: 100%

---

# Publier le pack de campagnes{#publishing-the-campaign-package}



Les opérateurs de l&#39;entité centrale publient dans la **[!UICONTROL liste des kits d&#39;opérations]**, les kits qu&#39;ils souhaitent proposer aux entités locales.

Avant d&#39;être publiés dans la liste des kits d&#39;opération, les kits d&#39;opération doivent être validés par l&#39;entité centrale. Pour cela, vous pouvez définir un validant ou groupe de validants à partir du lien **[!UICONTROL Paramètres de validation...]** du kit d&#39;opération.

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

Par défaut, les opérateurs validants disposent de trois jours pour procéder à la validation, à partir de la date de soumission.

Vous pouvez aussi, dans la section inférieure de la fenêtre d&#39;édition des validants, paramétrer des rappels afin d&#39;envoyer un ou plusieurs messages d&#39;alerte en cas de non validation du kit d&#39;opération. Pour cela, cliquez sur le lien **[!UICONTROL Ajouter un rappel]** puis sur le bouton **[!UICONTROL Ajouter]**.

Les rappels peuvent être envoyés à une date donnée et/ou **x** jours à partir de la date de soumission. Le type de rappel est sélectionné dans la première colonne du tableau des rappels. Dans l&#39;exemple ci-dessous, les opérateurs validants recevront un message de rappel un jour avant la fin de la période de validation, soit deux jours après la date de soumission à validation, puis un second rappel le 29/01/2014, soit deux jours avant la date sélectionnée dans la colonne **[!UICONTROL Date]**.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Une fois défini et une fois que le kit a été soumis à validation, le planning des traitements est affiché directement dans l&#39;onglet **[!UICONTROL Suivi]**. Il indique la date limite de traitement calculée à partir du paramétrage spécifié ci-avant, et la date du ou des rappels paramétrés.

## Validation via la console Adobe Campaign {#approving-via-the-adobe-campaign-console}

Si aucun validant n&#39;a été défini ou si aucun des opérateurs notifiés n&#39;a validé le kit, le bouton **[!UICONTROL Valider le kit]** permet de procéder directement à la validation depuis l&#39;onglet **[!UICONTROL Tableau de bord]** du kit d&#39;opération ou depuis la vue d&#39;ensemble des kits.

![](assets/s_advuser_mkg_dist_valid_button.png)

Une fois validée, l&#39;opération est alors publiée, ajoutée à la liste et les entités locales pourront l&#39;utiliser dès que sa date de disponibilité sera atteinte. Si des entités locales ont été définies lors de la création de l&#39;opération, un message est envoyé aux opérateurs appartenant au groupe de notification des kits d&#39;opération pour les informer de la disponibilité de l&#39;opération. Si aucune entité n&#39;a été définie en amont, l&#39;opération est accessible par défaut pour toutes les entités locales. Pour plus d&#39;informations, consultez la section [Entités organisationnelles](about-distributed-marketing.md#organizational-entities).

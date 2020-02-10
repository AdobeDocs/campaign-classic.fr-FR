---
title: Approbation des campagnes marketing
seo-title: Approbation des campagnes marketing
description: Approbation des campagnes marketing
seo-description: null
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---

# Approbation des campagnes marketing {#approving-marketing-campaigns}

## Processus de validation {#approval-process}

Chaque étape d&#39;une diffusion peut faire l&#39;objet d&#39;une validation afin d&#39;assurer un suivi et un contrôle complet des différents traitements de l&#39;opération : ciblage, contenu, budget, extraction ou envoi d&#39;un BAT.

>[!NOTE]
>
>Vous devez vérifier que les réviseurs disposent des droits appropriés pour l’approbation. Vérifiez également que leur zone de sécurité est correctement définie.

Des emails de notification sont envoyés aux opérateurs Adobe Campaign désignés comme validants afin de les avertir d&#39;une demande de validation.

La procédure d&#39;approbation est présentée dans [Vérification et approbation des livraisons](#checking-and-approving-deliveries).

>[!NOTE]
>
>Seul le propriétaire de la remise peut lancer une livraison. Pour qu’un autre opérateur (ou groupe d’opérateurs) puisse démarrer une diffusion, vous devez les ajouter en tant que réviseurs dans le **[!UICONTROL Delivery start:]** champ.\
>Voir aussi [Sélection de réviseurs](#selecting-reviewers).

### Principe de fonctionnement {#operating-principle-}

Par exemple, pour la validation du budget, le mail standard sera le suivant :

![](assets/s_user_validation_link_in_mail.png)

Les opérateurs validants peuvent alors choisir de valider ou non l&#39;étape concernée.

![](assets/s_user_validation_page_confirm.png)

Après confirmation du choix de l&#39;opérateur, la validation ou le refus du traitement est remontée au niveau du tableau de bord de la diffusion.

![](assets/s_user_validation_link_in_op_board.png)

The information is also available in the approval logs of the campaign (Accessed via the **[!UICONTROL Edit > Tracking > Approvals]** tab):

![](assets/s_user_validation_log_in_op_edit_tab.png)

Ces messages de notification sont envoyés aux opérateurs spécifiés pour chaque traitement pour lequel la validation a été activée.

Les validations peuvent être activées au niveau du modèle de l&#39;opération, au niveau de chaque opération ou au niveau de la diffusion.

Toutes les tâches nécessitant une approbation sont sélectionnées dans le modèle de campagne ( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** onglet), tout comme les opérateurs chargés de l’approbation (ils recevront des notifications, sauf si cette option n’est pas activée). For more on this, refer to [Approving processes](#approving-processes).

These settings can be overridden for each campaign created using this template, and individually for each campaign delivery: click the **[!UICONTROL Properties]** button, then the **[!UICONTROL Approvals]** tab.

Dans l&#39;exemple ci-dessous, le contenu de cette diffusion courrier ne fera l&#39;objet d&#39;aucune validation :

![](assets/s_user_validation_select_process_from_del.png)

### Sélection des opérateurs validants {#selecting-reviewers}

Pour chaque type d’approbation, les opérateurs ou groupes d’opérateurs chargés de l’approbation sont sélectionnés dans la liste déroulante de la remise. D’autres opérateurs peuvent être ajoutés à l’aide du **[!UICONTROL Edit...]** lien. Cette fenêtre vous permet également de modifier la date limite d’approbation.

![](assets/s_user_validation_add_operator.png)

Si aucun réviseur n’est spécifié, le gestionnaire de campagne est responsable de l’approbation et reçoit les notifications. Le gestionnaire de campagne est spécifié dans l’ **[!UICONTROL Edit > Properties]** onglet de la campagne :

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>All other Adobe Campaign operators with **[!UICONTROL Administrator]** rights can also approve jobs, but they will not receive notifications.\
>Par défaut, le responsable de la campagne ne peut pas effectuer de validation ou démarrer les diffusions si des opérateurs validants sont définis. Vous pouvez modifier ce comportement et autoriser le responsable de la campagne à valider/démarrer les diffusions en créant l&#39;option **NmsCampaign_Activate_OwnerConfirmation** avec pour valeur **1**.

### Modes de validation {#approval-modes}

#### Validation via le tableau de bord {#approval-via-the-dashboard}

Pour valider un traitement depuis la console ou l&#39;interface web, cliquez sur le lien correspondant dans le tableau de bord de l&#39;opération. Il est également possible de valider un traitement à partir du tracking des diffusions et du tableau de bord de la diffusion.

![](assets/s_user_validation_from_console.png)

Vérifiez les informations à approuver, choisissez d’accepter ou de rejeter l’approbation et, si nécessaire, saisissez un commentaire. Cliquez sur **[!UICONTROL Ok]** pour enregistrer.

>[!NOTE]
>
>Lorsqu&#39;un traitement a déjà été validé par un opérateur, le lien de validation n&#39;est pas proposé.

#### Validation via les messages de notification {#approval-via-notification-messages}

Cliquez sur le lien disponible dans le message de notification (voir [Notifications](#notifications)). Vous serez invité à vous identifier, comme illustré ci-dessous :

![](assets/s_user_validation__log_in.png)

Select **[!UICONTROL Accept]** or **[!UICONTROL Reject]** and enter a comment if necessary.

![](assets/s_user_validation_save_target_validation.png)

Clics **[!UICONTROL Validate]**.

>[!NOTE]
>
>Si des alertes ont été générées par le traitement, un message d&#39;avertissement est affiché dans la notification.

#### Suivi des validations {#approval-tracking}

Les informations sont remontées à différents niveaux :

* Dans le journal d’approbation de campagne, **[!UICONTROL Approvals]** sous-onglet de l’ **[!UICONTROL Edit > Tracking]** onglet :

   ![](assets/s_user_validation_log_from_op.png)

* Dans le journal de diffusion de la campagne, **[!UICONTROL Deliveries]** sous-onglet de l’ **[!UICONTROL Edit > Tracking]** onglet :

   ![](assets/s_user_validation_log_from_delivery_list.png)

* The approval status for each delivery can be viewed by clicking the **[!UICONTROL Hide/show log]** option of the **[!UICONTROL Summary]** tab.

   ![](assets/s_user_validation_log_delivery.png)

* This information can also be accessed via the **[!UICONTROL Tracking > Approvals]** tab of each delivery:

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>Lorsqu&#39;un opérateur a enregistré une réponse pour une validation, les autres opérateurs validants ne peuvent plus agir sur la validation.

#### Validation automatique et validation manuelle {#automatic-and-manual-approval}

Lors de la création d&#39;un workflow de ciblage, lorsque la validation est automatique (mode par défaut), Adobe Campaign propose le lien de validation ou envoie une notification dès qu&#39;un ciblage est à valider.

To choose the approval mode (manual or automatic), click the **[!UICONTROL Edit > Properties]** tab of the campaign or campaign template, then click **[!UICONTROL Advanced campaign settings...]** and finally the **[!UICONTROL Approvals]** tab.

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>Le mode de validation sélectionné sera appliqué à toutes les diffusions de l&#39;opération.

Lorsqu’un processus de ciblage est en cours de création, l’approbation manuelle vous permet d’éviter de créer des liens d’approbation ou d’envoyer automatiquement des notifications. Le tableau de bord de la campagne propose ensuite un **[!UICONTROL Submit targeting for approval]** lien permettant de lancer manuellement le processus d’approbation.

Un message de confirmation vous permet d’autoriser les approbations pour les tâches sélectionnées pour cette remise.

Les boutons de validation sont alors affichés dans le tableau de bord de l&#39;opération (au niveau de cette diffusion), dans le tableau de bord de la diffusion et dans le tracking des diffusions. Si les notifications sont activées, elles seront parallèlement envoyées.

Ce mode d&#39;activation des validations permet de travailler sur des recherches de ciblage sans notifier les opérateurs validants de façon intempestive.

### Notifications {#notifications}

Les notifications sont des emails spécifiques envoyés aux opérateurs validants afin de les avertir qu&#39;un traitement est en attente de validation. Lorsque l&#39;opérateur clique sur le lien contenu dans le message, il accède à une page d&#39;authentification. Après connexion, il peut consulter les éléments concernés puis valider ou non le traitement. Il peut également saisir un commentaire dans la fenêtre de validation.

Le contenu des courriers électroniques de notification peut être personnalisé. Voir Contenu [des](#notification-content)notifications.

#### Activation/Désactivation de la notification {#enabling-disabling-notification}

Par défaut, les messages de notification sont envoyés si la validation du traitement correspondant est activée au niveau du modèle de l&#39;opération, au niveau de l&#39;opération ou au niveau de la diffusion concernée. Toutefois, il est possible de désactiver les notifications afin de n&#39;autoriser les validations que depuis la console.

Pour ce faire, modifiez la fenêtre d’approbation de la campagne ou du modèle de campagne ( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** onglet) et sélectionnez **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

#### Contenu des messages de notification {#notification-content}

Le contenu de la notification est défini dans un modèle spécifique : **[!UICONTROL Notification of validations for the marketing campaign]**. Ce modèle est enregistré dans le **[!UICONTROL Administration > Campaign management > Technical delivery templates]** dossier de l’arborescence Adobe Campaign.

## Contrôler et valider les diffusions {#checking-and-approving-deliveries}

Adobe Campaign vous permet de configurer des processus d’approbation pour les principales étapes de la campagne marketing en mode collaboratif.

Pour les livraisons par courrier direct, les opérateurs Adobe Campaign peuvent afficher le fichier d&#39;extraction avant qu&#39;il ne soit envoyé au routeur et, si nécessaire, modifier le format et relancer l&#39;extraction. See [Approving an extraction file](#approving-an-extraction-file).

Pour chaque campagne, vous pouvez approuver la cible de diffusion, le contenu (voir [Approbation de contenu](#approving-content)) et les coûts. Les opérateurs Adobe Campaign en charge de l’approbation peuvent être avertis par courrier électronique et peuvent accepter ou refuser l’approbation de la console ou par une connexion Web. Voir [Approbation de processus](#approving-processes).

Une fois ces phases de validation terminées, la remise peut être lancée. Voir [Démarrage d’une remise](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery).

>[!NOTE]
>
>For further information about approval modes and tracking, see [Approval process](#approval-process).

### Valider les traitements {#approving-processes}

Les étapes qui doivent être approuvées apparaissent dans le tableau de bord de la campagne (via la console de l’interface Web). Elles apparaissent également dans le tableau de suivi des remises et dans le tableau de bord des remises.

At this point, the status of the campaign is **[!UICONTROL To validate]**.

>[!NOTE]
>
>* Pour sélectionner les processus qui seront soumis à approbation, modifiez le modèle de campagne. For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).
   >
   >
* Also refer to the section on the [Approval process](#approval-process).



![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>Dans un processus de ciblage, si une erreur liée à un problème de configuration se produit pendant la préparation du message, le lien s’affiche sur le tableau de bord. **[!UICONTROL Restart message preparation]** Corrigez l’erreur et cliquez sur ce lien pour redémarrer la préparation des messages tout en contournant l’étape de ciblage.

![](assets/s_user_validation_relaunch_message_preparation.png)

Pour chaque diffusion de l&#39;opération, il est possible de valider les traitements suivants :

* **Valider le ciblage, le contenu, le budget**

   Lorsque les options **[!UICONTROL Enable target approval]**, **[!UICONTROL Enable content approval]** ou **[!UICONTROL Enable budget approval]** sont sélectionnées dans la fenêtre des paramètres d’approbation des tâches, les liens pertinents s’affichent dans le tableau de bord de campagne pour les livraisons concernées.

   >[!NOTE]
   >
   >La validation du budget n&#39;est disponible que si vous avez activé la validation du ciblage, dans la fenêtre de paramétrage de la validation des traitements. Le lien proposant la validation du budget ne s&#39;affiche qu&#39;une fois que la cible a été analysée. De plus, ce lien s&#39;affiche en même temps que le lien proposant la validation du ciblage.

   Si les options **[!UICONTROL Assign content editing]** ou **[!UICONTROL External content approval]** sont sélectionnées dans la fenêtre des paramètres d’approbation, le tableau de bord affiche les **[!UICONTROL Available content]** liens et **[!UICONTROL External content approval]** les liens.

   La validation du contenu permet d&#39;accéder aux BAT envoyés.

* **Valider l&#39;extraction (diffusion courrier)**

   When **[!UICONTROL Enable extraction approval]** is selected in the approval settings window, the extracted file must be approved before the router can be notified.

   An **[!UICONTROL Approve content]** link is available on the campaign dashboard as shown below:

   ![](assets/s_ncs_user_edit_file_valid.png)

   Vous pouvez visualiser un aperçu du fichier d&#39;extraction à partir de la boîte de validation puis accepter ou non la validation.

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >La prévisualisation du fichier d&#39;extraction porte sur un échantillon de données. Elle ne charge pas l&#39;intégralité du fichier de sortie.

* **Valider les diffusions associées**

   L’ **[!UICONTROL Enable individual approval of each associated delivery]** option est utilisée pour une remise principale associée aux livraisons secondaires. Par défaut, cette option n’est pas sélectionnée afin qu’une approbation globale de la remise principale puisse être effectuée. Si cette option est sélectionnée, chaque remise doit être approuvée individuellement.

   ![](assets/s_ncs_user_task_valid_associate.png)

#### Sélection des processus à approuver {#choosing-the-processes-to-be-approved}

Les phases d’approbation sont définies avec le modèle associé à la campagne. Vous devez sélectionner les éléments à approuver à partir du modèle et spécifier les opérateurs Adobe Campaign qui seront responsables de ces approbations. For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>Le paramétrage des validations effectué au niveau de l&#39;opération ou du modèle d&#39;opération sera appliqué à toutes les futures diffusions liées à cette opération. Toute modification de paramétrage ne sera pas appliquée aux diffusions antérieures.

Ces informations peuvent cependant être surchargées au niveau de chaque opération et de chacune des diffusions.

For a campaign, click the **[!UICONTROL Edit > Properties]** tab, then the **[!UICONTROL Advanced campaign settings...]** link, and finally the **[!UICONTROL Approvals]** sub-tab to access the approvals configuration page.

Vous pouvez sélectionner et désélectionner les traitements à valider et désigner les opérateurs Adobe Campaign chargés de la validation. Il peut s&#39;agir d&#39;un opérateur individuel, d&#39;un groupe d&#39;opérateurs ou d&#39;une liste d&#39;opérateurs.

To select a list of operators, click the **[!UICONTROL Edit...]** link to the right of the field designating the first reviewer and add as many operators as necessary, as shown below:

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Lorsqu&#39;une liste de validants est définie, le traitement est validé dès que l&#39;un des opérateurs de la liste a donné son accord. Le lien de validation correspondant n&#39;est alors plus proposé dans le tableau de bord. Lorsque l&#39;envoi de notifications est activé et qu&#39;un autre validant clique sur le lien de validation du mail de notification, il est alors averti qu&#39;un autre opérateur a déjà validé le traitement.
>* Vous pouvez définir un planning de validation pour l&#39;opération, dans la section inférieure de la fenêtre d&#39;édition des validants. Par défaut, les validants ont trois jours à partir de la date de soumission pour valider les traitements. Il est possible de définir un rappel qui sera automatiquement envoyé aux opérateurs concernés avant l&#39;expiration du délai de validation.
>* Vous pouvez ajouter des rappels depuis cette section.
>



![](assets/s_ncs_user_edit_op_valid_calendar.png)

For each delivery, click the **[!UICONTROL Audit]** button and the **[!UICONTROL Approvals]** tab to view and edit approval dates and automatic reminders.

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Cet onglet est disponible lorsque la validation du contenu est démarrée.

### Valider le contenu {#approving-content}

>[!CAUTION]
>
>Pour valider un contenu, vous devez toujours passer par un cycle de Bon A Tirer (BAT). En effet, les BAT permettent de valider l&#39;affichage des informations, les données de personnalisation, ainsi que le bon fonctionnement des liens. Le mode de création d&#39;un BAT et son cycle de vie sont présentés dans la section [Envoyer les messages](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>Les fonctionnalités de validation du contenu présentées ci-après doivent venir en complément de l&#39;envoi des BAT.

Il est possible de configurer un cycle d’approbation du contenu. Pour ce faire, sélectionnez l’ **[!UICONTROL Enable content approval]** option dans la fenêtre des paramètres d’approbation. Les étapes principales du cycle d’approbation du contenu sont les suivantes :

1. After creating a new delivery, the campaign manager clicks the **[!UICONTROL Submit content]** link on the campaign dashboard to start the content approval cycle.

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Si l’ **[!UICONTROL Enable the sending of proofs]** option (pour les livraisons par courrier électronique) ou **[!UICONTROL Enable the sending and approval of proofs]** (pour les livraisons par courrier électronique direct) a été sélectionnée dans la fenêtre des paramètres d’approbation, les épreuves sont envoyées automatiquement.

1. Un email de notification est envoyé au responsable du contenu. Celui-ci choisi alors de valider ou non le contenu :

   * à partir de l&#39;email de notification :

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >L&#39;email de notification propose un lien vers les BAT envoyés, et éventuellement vers le rendu du message dans les différents webmails, sous réserve que l&#39;option **Deliverability** soit active pour cette instance.

   * à partir de la console ou de l&#39;interface web, au niveau du tracking des diffusions, du tableau de bord de la diffusion ou du tableau de bord de l&#39;opération :

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >Ce tableau de bord de campagne vous permet d’afficher la liste des épreuves qui ont été envoyées en cliquant sur le **[!UICONTROL Inbox rendering...]** lien. Pour afficher leur contenu, cliquez sur l’ **[!UICONTROL Detail]** icône à droite de la liste.

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. Un courrier électronique de notification est envoyé à la personne responsable de la campagne pour l’informer de l’approbation ou non du contenu.

   >[!NOTE]
   >
   >La personne responsable de la campagne peut relancer le cycle d’approbation du contenu à tout moment. Pour ce faire, cliquez sur le lien sur la **[!UICONTROL Content status]** ligne du tableau de bord de la campagne (au niveau de la diffusion), puis cliquez sur **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### Assigner l&#39;édition du contenu {#assign-content-editing}

Cette option vous permet de définir une personne responsable de la modification du contenu, par exemple un webmestre. Si l’ **[!UICONTROL Assign content editing]** option est sélectionnée dans la fenêtre des paramètres d’approbation, plusieurs étapes d’approbation sont ajoutées entre la création et la remise du courrier électronique de notification à la personne responsable du contenu :

1. After creating a new delivery, the person responsible for the campaign clicks the **[!UICONTROL Submit content editing]** link in the campaign dashboard to start the content editing cycle.

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. Le responsable de l&#39;édition du contenu reçoit un email l&#39;informant de la mise à disposition du contenu.

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. Il se connecte à la console, ouvre la diffusion et l&#39;édite via un assistant d&#39;édition simplifié lui permettant de modifier l&#39;objet, le contenu HTML et texte, et d&#39;envoyer des BAT.

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Si l’ **[!UICONTROL Enable the sending of proofs]** option (pour les livraisons par courrier électronique) ou **[!UICONTROL Enable the sending and approval of proofs]** (pour les livraisons par courrier électronique direct) a été sélectionnée dans la fenêtre des paramètres d’approbation, les épreuves sont envoyées automatiquement.

1. Lorsqu&#39;il a terminé l&#39;édition du contenu de la diffusion, le responsable de l&#39;édition du contenu peut mettre le contenu à disposition.

   Pour cela, il peut :

   * click the **[!UICONTROL Available content]** link via the Adobe Campaign console.

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * cliquer sur le lien proposé dans le message de notification puis valider la mise à disposition du contenu.

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      L&#39;opérateur peut ajouter un commentaire avant de soumettre le contenu au responsable de l&#39;opération.

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      Le message de notification permet au responsable de valider ou refuser le contenu qui lui a été soumis.

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### Validation externe du contenu {#external-content-approval}

Cette option vous permet de définir un opérateur externe chargé d’approuver le rendu de remise, tel que la cohérence de la communication avec la marque, les tarifs, etc. Lorsque l’ **[!UICONTROL External content approval]** option est sélectionnée dans la fenêtre des paramètres d’approbation, plusieurs étapes d’approbation sont ajoutées entre l’approbation du contenu et la remise de la notification à la personne responsable de la campagne :

1. Le responsable externe du contenu reçoit un email de notification l&#39;informant que le contenu a été validé et que la validation externe doit être effectuée.
1. L&#39;email de notification propose des liens vers les BAT envoyés, lui permettant de visualiser le rendu de la diffusion, et un bouton pour valider ou refuser le contenu de la diffusion.

   >[!NOTE]
   >
   >Ces liens ne sont disponibles que si un ou plusieurs BAT ont été envoyés. Si ce n&#39;est pas le cas, vous devez accéder à la console ou l&#39;interface web pour visualiser le rendu de la diffusion.

   ![](assets/s_user_validation_external_content.png)

### Valider un fichier d&#39;extraction {#approving-an-extraction-file}

Pour les diffusions offline, Adobe Campaign génère un fichier d&#39;extraction qui, selon le paramétrage, est transmis au routeur. Le contenu du fichier dépend du modèle d&#39;export utilisé.

When the content, targeting and budget have been approved, the delivery changes to **[!UICONTROL Extraction pending]** until the extraction workflow for the campaigns is launched.

![](assets/s_ncs_user_waiting_file_extraction.png)

On the extraction request date, the extraction file is created and the delivery status changes to **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

Vous pouvez visualiser le contenu du fichier extrait (en cliquant sur son nom), le valider, ou, au besoin, modifier le format et relancer l&#39;extraction, via les liens proposés dans le tableau de bord.

Une fois le fichier approuvé, vous pouvez envoyer l&#39;e-mail de notification au routeur. Pour plus d’informations, reportez-vous à [Démarrage d’une diffusion](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery)hors ligne.

---
product: campaign
title: Configuration et gestion du processus de validation
description: Découvrez comment gérer les validations des campagnes marketing
language: en
role: User
feature: Approvals, Campaigns
hide: true
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
TQID: https://experienceleague.adobe.com/xRSXwdwAWrtY5l-khF8ewhOZR9IUvTl3aWLO3eb-6cw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
  - id: f863efa9-030c-4466-a2b8-a52aea6b722c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: c35995a47788db080636c66827a4bd6dc98806cf
workflow-type: tm+mt
source-wordcount: 2841
ht-degree: 100%

---

# Configuration et gestion du processus de validation {#approving-marketing-campaigns}

Chaque étape d’une diffusion peut faire l’objet d’une validation pour assurer une surveillance et un contrôle complets des processus de campagne. Il s’agit notamment du ciblage, du contenu, du budget, de l’extraction et de l’envoi d’un BAT.

Des messages de notification sont envoyés aux opérateurs et opératrices [!DNL Adobe Campaign] désignés comme réviseurs et réviseuses afin de les avertir d’une demande de validation. Vérifiez que les validants disposent des **autorisations appropriées** pour la validation et que leur zone de sécurité est correctement définie. [En savoir plus sur la sélection des réviseurs et réviseuses](#selecting-reviewers).

La procédure de validation est présentée dans la [vue d’ensemble de la procédure de validation](#checking-and-approving-deliveries).

>[!NOTE]
>
>Seule la personne propriétaire de la diffusion peut démarrer une diffusion. Pour qu’un autre opérateur (ou un groupe d’opérateurs) puisse démarrer une diffusion, vous devez l’ajouter comme validant au niveau du champ **[!UICONTROL Démarrage de la diffusion :]**.\
>[En savoir plus sur la sélection des réviseurs et réviseuses](#selecting-reviewers).

## Principe de fonctionnement {#operating-principle-}

Par exemple, pour la validation du budget, le message standard est le suivant :

![E-mail de notification de validation avec lien de validation](assets/s_user_validation_link_in_mail.png)

Les opérateurs validants peuvent alors choisir de valider ou non le budget.

![Page de confirmation de validation avec options d’acceptation ou de rejet](assets/s_user_validation_page_confirm.png)

Après validation de l’opérateur, la validation ou le refus du traitement est remontée au niveau du tableau de bord de la diffusion.

![Tableau de bord de la campagne présentant le lien de validation d’un traitement](assets/s_user_validation_link_in_op_board.png)

Les informations sont également disponibles dans les logs de validation de la campagne. Ces logs sont accessibles à partir de l’onglet **[!UICONTROL Modifier > Tracking > Validations]**.

![Onglet Modifier de la campagne affichant le log de validation](assets/s_user_validation_log_in_op_edit_tab.png)

Ces messages de notification sont envoyés aux opérateurs spécifiés pour chaque traitement pour lequel la validation a été activée.

Les validations peuvent être activées au niveau du modèle de l&#39;opération, au niveau de chaque opération ou au niveau de la diffusion.

Tous les traitements qui doivent faire l’objet d’une validation sont sélectionnés dans le modèle de campagne (onglet **[!UICONTROL Propriétés]** > **[!UICONTROL Paramètres avancés de l’opération…]** > **[!UICONTROL Validations]**). Les opérateurs et opératrices en charge de la validation y sont également sélectionnés et reçoivent des notifications, sauf si cette option est désactivée. Pour en savoir plus à ce sujet, consultez les [étapes d’approbation d’une diffusion](#approving-processes).

Ce paramétrage peut être surchargé au niveau de chaque opération créée depuis ce modèle et également unitairement au niveau de chacune des diffusions de l&#39;opération, en cliquant sur le bouton **[!UICONTROL Propriétés]** puis sur l&#39;onglet **[!UICONTROL Validations]**.

Dans l&#39;exemple ci-dessous, le contenu de cette diffusion courrier ne fera l&#39;objet d&#39;aucune validation :

![Paramètres de validation de la diffusion avec sélection du processus](assets/s_user_validation_select_process_from_del.png)

## Sélection des validants {#selecting-reviewers}

Pour chaque type de validation, les opérateurs ou groupes d’opérateurs chargés de la validation sont sélectionnés dans la liste déroulante de la diffusion. Vous pouvez ajouter d’autres opérateurs à l’aide du lien **[!UICONTROL Modifier...]**. Cette fenêtre vous permet également de modifier la date limite de validation.

![Boîte de dialogue d’ajout de réviseur ou réviseuse pour les opérateurs et opératrices de validation](assets/s_user_validation_add_operator.png)

Si aucun réviseur n&#39;est spécifié, la personne responsable de la campagne est en charge de l’approbation et reçoit les notifications. La personne responsable de la campagne est indiquée dans l&#39;onglet **[!UICONTROL Edition > Propriétés]** de la campagne :

![Propriétés de la campagne affichant le champ de la personne responsable](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>Tous les autres opérateurs et opératrices [!DNL Adobe Campaign] disposant de droits **[!UICONTROL Administrateur ou administratrice]** sont également habilités à approuver les traitements. En revanche, ils ne reçoivent pas de notifications.\
>Par défaut, le responsable de la campagne ne peut pas effectuer de validation ou démarrer les diffusions si des opérateurs validants sont définis. Vous pouvez modifier ce comportement et autoriser le responsable de la campagne à valider/démarrer les diffusions en créant l&#39;option **NmsCampaign_Activate_OwnerConfirmation** avec pour valeur **1**.

## Modes de validation {#approval-modes}

### Validation via le tableau de bord {#approval-via-the-dashboard}

Pour approuver un traitement à partir de la console ou de l’interface web, cliquez sur le lien adéquat dans le tableau de bord de la campagne. Les traitements peuvent également être approuvés via le tracking des diffusions ou depuis le tableau de bord des diffusions.

![Actions de validation du tableau de bord de la campagne dans la console](assets/s_user_validation_from_console.png)

Vérifiez les informations, puis acceptez ou refusez la validation. Saisissez éventuellement un commentaire et cliquez sur **[!UICONTROL Ok]** pour enregistrer.

>[!NOTE]
>
>Lorsqu&#39;un traitement a déjà été validé par un opérateur, le lien de validation n&#39;est pas proposé.

### Validation via les messages de notification {#approval-via-notification-messages}

Cliquez sur le lien disponible dans le message de notification (voir [Notifications](#notifications)). Vous devez vous connecter, comme illustré ci-dessous :

![Page de connexion de validation pour le lien de notification](assets/s_user_validation__log_in.png)

Sélectionnez **[!UICONTROL Accepter]** ou **[!UICONTROL Refuser]** et saisissez éventuellement un commentaire.

![Page de validation avec options d’acceptation ou de rejet et de commentaire](assets/s_user_validation_save_target_validation.png)

Cliquez sur **[!UICONTROL Approuver]**.

>[!NOTE]
>
>Si des alertes ont été générées par le traitement, un message d&#39;avertissement est affiché dans la notification.

### Suivi des validations {#approval-tracking}

Les informations sont remontées à différents niveaux :

* Au niveau du log des validations de l&#39;opération, sous-onglet **[!UICONTROL Validations]** de l&#39;onglet **[!UICONTROL Edition > Tracking]** :

  ![Liste des logs de validation de la campagne](assets/s_user_validation_log_from_op.png)

* Dans le log des diffusions de l&#39;opération, sous-onglet **[!UICONTROL Diffusions]** de l&#39;onglet **[!UICONTROL Edition > Tracking]** :

  ![Liste des logs de diffusion avec statut de validation](assets/s_user_validation_log_from_delivery_list.png)

* Au niveau de chaque diffusion, l&#39;état des validations peut être consulté en cliquant sur l&#39;option **[!UICONTROL Afficher/cacher le log]**, dans l&#39;onglet **[!UICONTROL Résumé]** :

  ![Résumé de la diffusion affichant le log de validation](assets/s_user_validation_log_delivery.png)

* Ces informations sont également accessibles depuis l&#39;onglet **[!UICONTROL Tracking > Validations]** de chaque diffusion :

  ![Onglet de validations du tracking des diffusions](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>Une fous qu’un traitement a été approuvé ou rejeté, les autres opérateurs validants ne peuvent plus agir sur l’approbation.

### Validation automatique et validation manuelle {#automatic-and-manual-approval}

Lors de la création d’un workflow de ciblage, lorsque la validation est automatique (mode par défaut), [!DNL Adobe Campaign] affiche le lien de validation ou envoie une notification dès qu’une validation est requise.

Pour sélectionner le mode de validation (manuelle ou automatique), cliquez sur l&#39;onglet **[!UICONTROL Edition > Propriétés]** de l&#39;opération ou du modèle d&#39;opération, puis sur l&#39;option **[!UICONTROL Paramètres avancés de l&#39;opération...]**, et enfin sur l&#39;onglet **[!UICONTROL Validations]**.

![Paramètres de validation en mode manuel et automatique](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>Le mode de validation sélectionné sera appliqué à toutes les diffusions de l&#39;opération.

Lorsqu’un workflow de ciblage est en cours de construction, la validation manuelle permet d’éviter de créer des liens de validation ou d’envoyer automatiquement des notifications. Le tableau de bord de la campagne propose alors un lien **[!UICONTROL Soumettre le ciblage pour validation]** afin de lancer manuellement le processus de validation.

Un message de confirmation permet d&#39;autoriser les validations sur les traitements sélectionnés pour cette diffusion.

Les boutons de validation sont alors affichés dans le tableau de bord de la campagne (au niveau de cette diffusion), dans le tableau de bord de la diffusion et dans le tracking des diffusions. Si les notifications sont activées, elles seront parallèlement envoyées.

Ce mode d&#39;activation des validations permet de travailler sur des recherches de ciblage sans notifier les opérateurs validants de façon intempestive.

## Notifications {#notifications}

Les notifications sont des e-mails spécifiques envoyés aux réviseurs et réviseuses pour les informer qu’un processus est en attente de validation. Lorsque l’opérateur ou l’opératrice clique sur le lien contenu dans le message, une page d’authentification s’affiche. Après connexion, l’opérateur ou l’opératrice peut consulter les informations et approuver ou rejeter le traitement. Un commentaire peut également être saisi dans la fenêtre de validation.

Le contenu des emails de notification peut être personnalisé. Voir [Contenu des notifications](#notification-content).

### Activation/désactivation de la notification {#enabling-disabling-notification}

Par défaut, les messages de notification sont envoyés si l’approbation du traitement correspondant est activée dans le modèle de campagne, la campagne ou la diffusion. Toutefois, les notifications peuvent être désactivées afin d’autoriser les validations à partir de la console uniquement.

Pour cela, éditez la fenêtre de validation de l&#39;opération ou du modèle d&#39;opération concerné (onglet **[!UICONTROL Edition > Propriétés]** > **[!UICONTROL Paramètres avancés de l&#39;opération...]** > **[!UICONTROL Validations]**) et cochez l&#39;option **[!UICONTROL Ne pas activer l&#39;envoi de notifications]**.

![Paramètres de validation avec notifications désactivées](assets/s_user_validation_notif_desactivate.png)

### Contenu des messages de notification {#notification-content}

Le contenu des notifications est défini dans un modèle spécifique : **[!UICONTROL Notification des validations pour la campagne marketing]**. Ce modèle est enregistré dans le dossier **[!UICONTROL Administration > Gestion des campagnes > Modèles des diffusions techniques]** de l’arborescence [!DNL Adobe Campaign].

## Révision et validation des diffusions {#checking-and-approving-deliveries}

Grâce à [!DNL Adobe Campaign], vous pouvez mettre en place des processus de validation des principales étapes d’une campagne marketing, dans un mode collaboratif.

Pour les diffusions par publipostage direct, les opérateurs et opératrices [!DNL Adobe Campaign] peuvent visualiser le fichier d’extraction avant l’envoi au routeur et, si nécessaire, modifier le format et relancer l’extraction. Voir [Validation d’un fichier d’extraction](#approving-an-extraction-file).

Pour chaque campagne, vous pouvez approuver la cible de diffusion, le contenu (consultez [Approuvez le contenu](#approving-content)) et les coûts. Les opérateurs et opératrices [!DNL Adobe Campaign] en charge de la validation peuvent être informés par e-mail et peuvent accepter ou rejeter la validation depuis la console ou via une connexion web. Voir les [Étapes de validation d’une diffusion](#approving-processes).

Une fois ces phases de validation achevées, la diffusion peut être lancée. [En savoir plus sur le démarrage d’une diffusion](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery).

### Étapes de validation d’une diffusion {#approving-processes}

Les étapes qui doivent être validées apparaissent dans le tableau de bord de la campagne (via la console de l’interface web). Elles apparaissent également dans la table de tracking des diffusions et dans le tableau de bord des diffusions.

Le statut de l&#39;opération est alors **[!UICONTROL A valider]**.

>[!NOTE]
>
>Pour sélectionner les processus nécessitant une validation, modifiez le modèle de la campagne. Pour plus d’informations à ce sujet, consultez la section [Modèles de campagnes](../../campaign/using/marketing-campaign-templates.md#campaign-templates).
>

![Tableau de bord de la campagne présentant le statut de la diffusion À valider](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>Dans un workflow de ciblage, si une erreur liée à un problème de configuration se produit lors de la préparation du message, le lien **[!UICONTROL Redémarrer la préparation des messages]** s&#39;affiche sur le tableau de bord. Corrigez l&#39;erreur, puis cliquez sur ce lien afin de relancer la préparation des messages sans repasser par la phase de ciblage.

![Lien du tableau de bord pour redémarrer la préparation des messages](assets/s_user_validation_relaunch_message_preparation.png)

Pour chaque diffusion de l&#39;opération, il est possible de valider les traitements suivants :

* **Valider le ciblage, le contenu, le budget**

  Lorsque les options **[!UICONTROL Activer la validation de la cible]**, **[!UICONTROL Activer la validation du contenu]** ou **[!UICONTROL Activer la validation du budget]** sont sélectionnées dans la fenêtre de paramétrage de la validation des traitements, alors les liens correspondants sont proposés dans le tableau de bord de l&#39;opération pour les diffusions concernées.

  >[!NOTE]
  >
  >La validation du budget n’est disponible que si celle du ciblage est activée dans la fenêtre des paramètres de la validation. Le lien de la validation du budget ne s&#39;affiche qu&#39;une fois la cible analysée. En outre, ce lien s’affiche avec le lien pour la validation de la cible.

  Lorsque les options **[!UICONTROL Assigner l&#39;édition du contenu]** ou **[!UICONTROL Validation externe du contenu]** sont sélectionnées dans la fenêtre de paramétrage de la validation des traitements, le tableau de bord propose respectivement les liens **[!UICONTROL Contenu disponible]** et **[!UICONTROL Validation externe du contenu]**.

  La validation du contenu permet d&#39;accéder aux BAT envoyés.

* **Valider l&#39;extraction (diffusion courrier)**

  Lorsque l&#39;option **[!UICONTROL Activer la validation de l&#39;extraction]** est sélectionnée dans la fenêtre de paramétrage de la validation des traitements, le fichier extrait doit être validé avant que le routeur puisse être notifié.

  Un lien **[!UICONTROL Valider le contenu]** est proposé dans le tableau de bord de l&#39;opération, comme dans l&#39;exemple ci-dessous :

  ![Tableau de bord de validation présentant le lien d’approbation du contenu](assets/s_ncs_user_edit_file_valid.png)

  Vous pouvez visualiser un aperçu du fichier d&#39;extraction à partir de la boîte de validation puis accepter ou non la validation.

  ![Prévisualisation du fichier d’extraction dans la boîte de dialogue de validation](assets/s_ncs_user_edit_file_valid_preview_file.png)

  >[!NOTE]
  >
  >La prévisualisation du fichier d’extraction correspond à un exemple de données uniquement. Le fichier de sortie entier n’est pas chargé.

* **Valider les diffusions associées**

  L’option **[!UICONTROL Activer la validation individuelle de chaque diffusion associée]** est utilisée pour une diffusion principale associée à des diffusions secondaires. Par défaut, cette option n&#39;est pas sélectionnée afin d&#39;effectuer une validation globale de la diffusion principale. Si cette option est sélectionnée, chaque diffusion doit être validée individuellement.

  ![Option permettant d’activer la validation individuelle des diffusions associées](assets/s_ncs_user_task_valid_associate.png)

### Sélection des processus à valider {#choosing-the-processes-to-be-approved}

Les phases de validation sont définies avec le modèle associé à la campagne. Vous devez sélectionner les éléments à approuver à partir du modèle et spécifier les opérateurs et opératrices [!DNL Adobe Campaign] qui seront responsables de ces approbations. Pour en savoir plus sur les modèles de campagne, consultez les [modèles de campagne](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>La configuration de la validation pour la campagne (ou le modèle de campagne) s’applique à toutes les futures diffusions liées à cette campagne. Aucune modification de configuration ne sera appliquée aux diffusions précédentes.

Ces informations peuvent cependant être surchargées au niveau de chaque opération et de chacune des diffusions.

Au niveau de l&#39;opération, cliquez sur l&#39;onglet **[!UICONTROL Edition > Propriétés]**, puis sur le lien **[!UICONTROL Paramètres avancés de l&#39;opération...]** et enfin sur le sous-onglet **[!UICONTROL Validations]** pour accéder à la page de paramétrage du mode de validation des traitements.

Vous pouvez sélectionner et désélectionner les processus à approuver et désigner les opérateurs et opératrices [!DNL Adobe Campaign] chargés de la validation. Il peut s’agir d’opérateurs et d’opératrices individuels, d’un groupe d’opérateurs et d’opératrices ou d’une liste d’opérateurs et d’opératrices.

Pour désigner une liste d&#39;opérateurs, cliquez sur le lien **[!UICONTROL Editer...]** situé à droite du champ désignant le premier validant et ajoutez autant d&#39;opérateurs additionnels que nécessaire, comme dans l&#39;exemple ci-dessous :

![Boîte de dialogue d’ajout de réviseur ou réviseuse pour les opérateurs et opératrices de validation](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Si une liste de validants est définie, un traitement est validé lorsqu’un validant l’accepte. Le lien de validation concerné n’est alors plus proposé dans le tableau de bord. Lorsque l’envoi de notifications est activé et qu’un autre validant clique sur le lien de validation du message de notification, il est alors averti qu’un autre opérateur a déjà validé le traitement.
>* Vous pouvez définir un planning de validation pour la campagne dans la section inférieure de la fenêtre de modification des réviseurs et réviseuses. Par défaut, les réviseurs disposent de trois jours à partir de la date de soumission pour valider un processus. Il est possible de configurer un rappel qui sera envoyé automatiquement aux opérateurs et opératrices concernés avant la date limite de validation.
>* Vous pouvez ajouter des rappels depuis cette section.
>

![Calendrier d’approbation et paramètres de rappel](assets/s_ncs_user_edit_op_valid_calendar.png)

Au niveau de chaque diffusion, cliquez sur le bouton **[!UICONTROL Suivi]** puis sur l&#39;onglet **[!UICONTROL Validations]** pour visualiser et modifier les dates de validation et de rappel calculées automatiquement.

![Onglet Validation de la diffusion avec des dates et des rappels](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Cet onglet est disponible lorsque la validation du contenu est démarrée.

### Validation d’un contenu {#approving-content}

>[!CAUTION]
>
>Pour approuver un contenu, un cycle de BAT est obligatoire. Les BAT vous permettent d’approuver l’affichage des informations, les données de personnalisation et de vérifier que les liens fonctionnent. Découvrez comment créer un BAT dans [créer un BAT](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>Les fonctionnalités de validation du contenu décrites ci-dessous se rapportent à la diffusion du BAT.

Il est possible de configurer un cycle de validation du contenu. Pour ce faire, sélectionnez l’option **[!UICONTROL Activer la validation du contenu]** dans la fenêtre des paramètres de validation. Les étapes principales du processus de validation de contenu sont les suivantes :

1. Après la création d&#39;une nouvelle diffusion, le responsable de l&#39;opération clique sur le lien **[!UICONTROL Soumettre le contenu]**, dans le tableau de bord de l&#39;opération, pour lancer le cycle de validation du contenu.

   ![Lien du tableau de bord de la campagne pour soumettre du contenu pour validation](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Si vous avez sélectionné, dans la fenêtre de paramétrage de la validation des traitements, l&#39;option **[!UICONTROL Activer l&#39;envoi des BAT]** (pour une diffusion email) ou **[!UICONTROL Activer l&#39;envoi et la validation des BAT]** (pour une diffusion courrier), l&#39;envoi des BAT se fait automatiquement.

1. Un email de notification est envoyé au responsable du contenu. Celui-ci choisit alors de valider ou non le contenu :

   * à partir de l&#39;email de notification :

     ![E-mail de notification de validation du contenu pour les BAT](assets/s_ncs_user_del_content_valid_bat_notif.png)

     >[!NOTE]
     >
     >L&#39;email de notification propose un lien vers les BAT envoyés, et éventuellement vers le rendu du message dans les différents webmails, sous réserve que l&#39;option **Deliverability** soit active pour cette instance.

   * à partir de la console ou de l&#39;interface web, au niveau du tracking des diffusions, du tableau de bord de la diffusion ou du tableau de bord de l&#39;opération :

     ![Tracking des diffusions affichant la liste des BAT de contenu](assets/s_ncs_user_validation_content_bat_op.png)

     >[!NOTE]
     >
     >Ce tableau de bord de la campagne permet de visualiser la liste des BAT envoyés, en cliquant sur le lien **[!UICONTROL Inbox rendering…]**. Pour afficher leur contenu, cliquez sur l’icône **[!UICONTROL Détail]** situé à droite de la liste.

     ![Vue des détails du BAT pour la validation du contenu](assets/s_ncs_user_validation_content_BAT_details.png)

1. Un email de notification est envoyé au responsable de la campagne pour l’informer de la validation ou de la non-validation du contenu.

   >[!NOTE]
   >
   >La personne responsable de la campagne peut à tout moment relancer le cycle de validation du contenu. Pour ce faire, cliquez sur le lien de la ligne **[!UICONTROL Statut du contenu]** du tableau de bord de la campagne (au niveau de la diffusion), puis cliquez sur **[!UICONTROL Réinitialiser la validation du contenu pour la soumettre à nouveau]**.

   ![Lien du tableau de bord de la campagne pour redémarrer la validation du contenu](assets/s_user_validation_relaunch_content_validation.png)

#### Assigner l’édition du contenu {#assign-content-editing}

Cette option vous permet de définir une personne responsable de l’édition du contenu, par exemple un ou une webmaster. Si l’option **[!UICONTROL Assigner l’édition du contenu]** est sélectionnée dans la fenêtre de paramétrage de la validation, plusieurs étapes de validation sont ajoutées entre la création de la diffusion et la diffusion de l’e-mail de notification à la personne responsable du contenu :

1. Après la création d&#39;une nouvelle diffusion, le responsable de l&#39;opération clique sur le lien **[!UICONTROL Soumettre l&#39;édition du contenu]**, dans le tableau de bord de l&#39;opération, pour lancer le cycle d&#39;édition du contenu.

   ![Lien du tableau de bord de la campagne pour envoyer la modification du contenu](assets/s_ncs_user_validation_submit_content_edition.png)

1. Le responsable de l&#39;édition du contenu reçoit un email l&#39;informant de la mise à disposition du contenu.

   ![E-mail de notification de modification du contenu](assets/s_ncs_user_validation_submit_content_notif.png)

1. Cette personne se connecte à la console, ouvre la diffusion et la modifie via un assistant de modification simplifié lui permettant de modifier l’objet, le contenu HTML et texte, et d’envoyer des BAT.

   ![Assistant simplifié de modification du contenu de la diffusion](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Si vous avez sélectionné, dans la fenêtre de paramétrage de la validation des traitements, l&#39;option **[!UICONTROL Activer l&#39;envoi des BAT]** (pour une diffusion email) ou **[!UICONTROL Activer l&#39;envoi et la validation des BAT]** (pour une diffusion courrier), l&#39;envoi des BAT se fait automatiquement.

1. Lorsqu&#39;il a terminé l&#39;édition du contenu de la diffusion, le responsable de l&#39;édition du contenu peut mettre le contenu à disposition.

   Pour cela, il peut :

   * cliquer sur le lien **[!UICONTROL Contenu disponible]** à partir de la console [!DNL Adobe Campaign].

     ![Lien de la console pour rendre le contenu disponible](assets/s_ncs_user_validation_submit_content_available.png)

   * cliquer sur le lien proposé dans le message de notification puis valider la mise à disposition du contenu.

     ![Lien de notification pour approuver la disponibilité du contenu](assets/s_ncs_user_validation_submit_content_available2.png)

     L&#39;opérateur peut ajouter un commentaire avant de soumettre le contenu au responsable de l&#39;opération.

     ![Champ de commentaire avant d’envoyer la disponibilité du contenu](assets/s_ncs_user_validation_submit_content_available3.png)

     Le message de notification permet au réviseur de valider ou refuser le contenu qui lui a été soumis.

     ![Réponse d’approbation pour la disponibilité du contenu](assets/s_ncs_user_validation_submit_content_available4.png)

#### Validation externe du contenu {#external-content-approval}

Cette option vous permet de définir un opérateur ou une opératrice externe en charge de la validation du rendu de la diffusion, par exemple la cohérence de la communication de la marque, les taux, etc. Lorsque l’option **[!UICONTROL Validation externe du contenu]** est sélectionnée dans la fenêtre des paramètres de validation, plusieurs étapes de validation sont ajoutées entre la validation du contenu et la diffusion de la notification à la personne en charge de la campagne :

1. Le responsable externe du contenu reçoit un email de notification l&#39;informant que le contenu a été validé et que la validation externe doit être effectuée.
1. L&#39;email de notification propose des liens vers les BAT envoyés, lui permettant de visualiser le rendu de la diffusion, et un bouton pour valider ou refuser le contenu de la diffusion.

   >[!NOTE]
   >
   >Ces liens ne sont disponibles que si un ou plusieurs BAT ont été envoyés. Dans le cas contraire, le rendu de la diffusion n’est disponible que via la console ou l’interface web.

   ![E-mail de validation de contenu externe avec liens des BAT](assets/s_user_validation_external_content.png)

### Validation d’un fichier d’extraction {#approving-an-extraction-file}

Pour les diffusions hors ligne, [!DNL Adobe Campaign] génère un fichier d’extraction qui, selon la configuration, est transmis au routeur. Son contenu dépend du modèle d’export utilisé.

Une fois le contenu, le ciblage et le budget validés, la diffusion passe à l&#39;état **[!UICONTROL Extraction en attente]**, en attendant le lancement du workflow d&#39;extraction pour les opérations.

![Statut de la diffusion indiquant que l’extraction est en attente](assets/s_ncs_user_waiting_file_extraction.png)

A la date de la demande d&#39;extraction, le fichier d&#39;extraction est créé et la diffusion passe à l&#39;état **[!UICONTROL Fichier à valider]**.

![Statut de la diffusion indiquant le fichier à approuver](assets/s_ncs_user_file_extract_to_valid.png)

Vous pouvez visualiser le contenu du fichier extrait (en cliquant sur son nom), le valider, ou, au besoin, modifier le format et relancer l&#39;extraction, via les liens proposés dans le tableau de bord.

Une fois le fichier validé, vous pouvez envoyer l’e-mail de notification au routeur. Pour plus d’informations à ce sujet, consultez la section [Démarrage d’une diffusion hors ligne](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).


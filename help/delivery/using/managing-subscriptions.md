---
title: Gestion des inscriptions
seo-title: Gestion des inscriptions
description: Gestion des inscriptions
seo-description: null
page-status-flag: never-activated
uuid: a2c526fa-3080-4dd5-9628-f0e7040f93cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 9a61fe74-f779-4f23-be25-3d9a8e95704a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Gestion des inscriptions{#managing-subscriptions}

## A propos des services d&#39;informations {#about-information-services}

Un service d&#39;information est caractérisé par :

* une inscription, un abonnement (opt-in),
* une désinscription, un désabonnement volontaire (opt-out) ou automatique (service à durée limitée : par exemple pour une offre d&#39;essai),
* des mécanismes de confirmation d&#39;inscription et/ou de désinscription (mécanismes simples avec confirmation, double opt-in, etc.),
* un tracking de l&#39;historique des inscrits.

Ces services sont accompagnés, en standard, des rapports et de statistiques spécifiques : tracking des inscrits, niveaux de fidélité, courbes de désinscription, etc.

Pour les emails, les liens de désinscription obligatoires sont automatiquement générés et l&#39;ensemble du processus opt-in/opt-out est alors totalement automatisé avec un tracking des historiques garantissant une totale conformité avec les règlementations en vigueur.

Les opérations d&#39;abonnement/désabonnement aux services peuvent être réalisées selon trois modes différents :

1. manuellement,
1. par un import (abonnement seulement),
1. via un formulaire web,

>[!NOTE]
>
>Un exemple de création d&#39;un formulaire d&#39;abonnement avec double opt-in est présenté dans [cette section](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## Créer un service d&#39;information {#creating-an-information-service}

Vous pouvez créer et gérer des abonnements à des services d&#39;information auxquels seront associés des messages de confirmation ou des diffusions automatiques vers les abonnés.

Pour accéder à la vue d&#39;ensemble des services d&#39;information, positionnez-vous sur l&#39;univers **[!UICONTROL Profils et cibles]**, et cliquez sur le lien **[!UICONTROL Services et abonnements]**.

![](assets/s_ncs_user_services_new.png)

Pour éditer un service existant, cliquez sur son nom. Pour créer un service, cliquez sur le bouton **[!UICONTROL Créer]** situé au-dessus de la liste.

![](assets/s_ncs_user_services_add.png)

* Saisissez le nom du service dans le champ **[!UICONTROL Libellé]** et sélectionnez le canal de diffusion : Email, Mobile, Facebook, Twitter, Application mobile.

   >[!NOTE]
   >
   >Les abonnements Facebook et Twitter sont détaillés dans [cette section](../../social/using/about-social-marketing.md). Les abonnements aux applications mobiles sont détaillés dans [A propos du canal](../../delivery/using/about-mobile-app-channel.md)des applications mobiles.

* Pour un service de type Email, choisissez le **mode de diffusion**. Les modes possibles sont : **[!UICONTROL Newsletter]** ou **[!UICONTROL Viral]**.
* You can send **confirmation messages** for a subscription or unsubscription. To do this, select the delivery templates to be used to create the corresponding deliveries from the **[!UICONTROL Subscription]** and **[!UICONTROL Unsubscription]** fields. These templates must be configured with a **[!UICONTROL Subscription]** type target mapping, without a defined target. Voir la section [A propos du canal](../../delivery/using/about-email-channel.md)de messagerie.
* Par défaut, les abonnements sont illimités. Vous pouvez décocher l&#39;option **[!UICONTROL Illimité]** pour définir la durée de validité du service. La durée peut alors être spécifiée en jours (**[!UICONTROL j]**) ou en mois (**[!UICONTROL m]** ).

Once the service has been saved, it is added to the Services and Subscriptions list: Click its name to edit it. Several tabs are available. The **[!UICONTROL Subscriptions]** tab lets you look at the list of subscribers to the information service (**[!UICONTROL Active subscriptions]** tab) or the subscription/unsubscription history (**[!UICONTROL History]** tab). You can also add and delete subscribers from this tab. See [Adding and deleting subscribers](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Le bouton **[!UICONTROL Détail...]** permet de consulter les propriétés de l&#39;abonnement pour le destinataire sélectionné.

Vous pouvez modifier les propriétés de l&#39;abonnement pour un destinataire.

![](assets/s_ncs_user_services_modify.png)

Depuis le tableau de bord, cliquez sur **[!UICONTROL Rapports]** pour suivre les abonnements : évolution des inscriptions, nombre total d&#39;inscrits, etc. Vous pouvez archiver les rapports et consulter les historiques depuis cet onglet.

## Ajouter et supprimer des abonnés {#adding-and-deleting-subscribers}

Depuis l&#39;onglet **[!UICONTROL Abonnements]** d&#39;un service d&#39;information, cliquez sur le bouton **[!UICONTROL Ajouter]** pour abonner des destinataires. Vous pouvez également cliquer avec le bouton droit de la souris dans la liste des abonnés et choisir **[!UICONTROL Ajouter]**. Sélectionnez ensuite le dossier où sont stockés les profils à abonner puis sélectionnez les profils à inscrire et cliquez sur **[!UICONTROL OK]** pour valider.

Pour supprimer des abonnés, sélectionnez-les puis cliquez sur le bouton **[!UICONTROL Supprimer]**. Vous pouvez également cliquer avec le bouton droit de la souris dans la liste des abonnés et choisir **[!UICONTROL Supprimer]**.

Dans les deux cas, vous pouvez envoyer un message de confirmation aux utilisateurs concernés si un modèle de remise de désabonnement a été joint au service (voir [Création d’un service](#creating-an-information-service)d’informations). Un avertissement vous permet de valider ou non cette remise :

![](assets/s_ncs_user_services_update.png)

See [Subscription and unsubscription mechanisms](#subscription-and-unsubscription-mechanisms).

## Diffuser aux abonnés d&#39;un service {#delivering-to-the-subscribers-of-a-service}

Pour diffuser aux abonnés d&#39;un service d&#39;information, vous devez cibler sur les abonnés au service d&#39;information visé, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>Le mapping de ciblage doit être **[!UICONTROL Abonnements]**.

Sélectionnez **[!UICONTROL Abonnés d&#39;un service d&#39;information]** et cliquez sur **[!UICONTROL Suivant]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Choisissez le service d&#39;information ciblé et cliquez sur **[!UICONTROL Terminer]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

L&#39;onglet **[!UICONTROL Aperçu]** permet de visualiser la liste des abonnés au service d&#39;informations sélectionné.

## Inscription et désinscription {#subscription-and-unsubscription-mechanisms}

Vous pouvez mettre en place des mécanismes d&#39;inscription et de désinscription afin d&#39;automatiser les processus et la gestion des abonnés.

>[!NOTE]
>
>Vous pouvez envoyer un message de confirmation aux nouveaux inscrits/désinscrits.\
>Le contenu de ce message est défini dans le paramétrage du service d&#39;information, depuis le champ **[!UICONTROL Inscription]** ou **[!UICONTROL Désinscription]**.
>
>Les messages de confirmation sont créés à partir des modèles de diffusion indiqués dans ces champs. Ces modèles doivent utiliser le mapping de ciblage des **[!UICONTROL Abonnements]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Inscrire un destinataire à un service {#subscribing-a-recipient-to-a-service}

Pour inscrire des destinataires à un service d&#39;information, vous pouvez :

* Ajouter manuellement ce service : pour cela, depuis l&#39;onglet **[!UICONTROL Abonnements]** de leur profil, cliquez sur le bouton **[!UICONTROL Ajouter]** et sélectionnez le service d&#39;information visé.

   Voir à ce sujet la section sur l&#39;édition de profils dans [cette section](../../platform/using/editing-a-profile.md).

* Abonner automatiquement à ce service un ensemble de destinataires. La liste de ces destinataires peut être issue d&#39;une opération de filtrages, d&#39;un groupe, d&#39;un dossier, d&#39;un import ou d&#39;une sélection directe par la souris. Pour abonner ces destinataires, sélectionnez les profils et cliquez sur le bouton droit de la souris. Choisissez **[!UICONTROL Actions > Abonner la sélection à un service...]** puis sélectionnez le service visé et lancez l&#39;opération.
* Importer des destinataires et les abonner automatiquement à un service d&#39;information : pour cela, sélectionnez le service visé dans la dernière étape de l&#39;assistant d&#39;import.

   Voir à ce propos [cette section](../../platform/using/importing-data.md#import-wizard).

* Utiliser un formulaire web pour que les destinataires puissent s&#39;abonner à un service.

   Voir à ce propos [cette section](../../web/using/about-web-applications.md).

* Créer un workflow de ciblage et utiliser une boîte de type **[!UICONTROL Service d&#39;inscriptions]**.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   Les workflows et leur utilisation sont présentés dans [cette section](../../workflow/using/about-workflows.md).

### Désinscrire un destinataire d&#39;un service {#unsubscribing-a-recipient-from-a-service}

#### Désinscription manuelle {#manual-unsubscribing}

Les diffusions par email doivent légalement contenir un lien de désinscription. Les destinataires peuvent cliquer sur ce lien pour mettre à jour leur profil et ainsi être exclu des cibles des prochaines diffusions.

Le lien de désabonnement par défaut est inséré via le dernier bouton de la barre d’outils de l’éditeur de contenu fourni dans l’assistant de distribution (voir [A propos de la personnalisation](../../delivery/using/about-personalization.md)). Lorsque le destinataire clique sur ce lien, le profil est mis sur liste noire (exclusion), ce qui signifie que ce destinataire ne sera plus ciblé par une action de remise.

Les destinataires peuvent toutefois choisir de se désabonner d’un service sans s’abonner à tous les services. Pour ce faire, vous pouvez utiliser un formulaire Web (reportez-vous à [cette section](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) ou insérer un lien personnalisé de désabonnement (voir les blocs [de](../../delivery/using/personalization-blocks.md)personnalisation).

Vous pouvez également désinscrire manuellement un destinataire à partir de son profil. Pour cela, cliquez sur l&#39;onglet **[!UICONTROL Abonnements]** du destinataire visé, sélectionnez le ou les services d&#39;information concernés et cliquez sur **[!UICONTROL Supprimer]**.

Vous pouvez enfin désinscrire un ou plusieurs destinataires depuis le service d&#39;information concerné. Pour cela, cliquez sur l&#39;onglet **[!UICONTROL Abonnements]** du service, sélectionnez le ou les destinataires concernés et cliquez sur **[!UICONTROL Supprimer]**.

#### Désinscription automatique {#automatic-unsubscription}

Un service d&#39;information peut avoir une durée limitée : les destinataires seront automatiquement désabonnés une fois le délai de validité expiré. Ce délai est spécifié dans l&#39;onglet **[!UICONTROL Edition]** des propriétés du service. Il est exprimé en jours.

![](assets/s_ncs_user_services_delay.png)

You can also set up an unsubscription workflow for a population. To do this, follow the same procedure as for a subscription workflow, but select the **[!UICONTROL Unsubscription]** option. See [Subscribing a recipient to a service](#subscribing-a-recipient-to-a-service).

### Tracking des inscrits {#subscriber-tracking}

Le lien **[!UICONTROL Rapport]** du tableau de bord permet de suivre les variations d&#39;inscription aux services d&#39;information.

![](assets/s_ncs_user_services_report.png)

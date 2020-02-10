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

Pour accéder à la carte des services d&#39;information, allez dans l&#39; **[!UICONTROL Profiles and Targets]** univers et cliquez sur le **[!UICONTROL Services and Subscriptions]** lien.

![](assets/s_ncs_user_services_new.png)

Pour modifier un service existant, cliquez sur son nom. Pour créer un service, cliquez sur le **[!UICONTROL Create]** bouton situé au-dessus de la liste.

![](assets/s_ncs_user_services_add.png)

* Enter the name of the service in the **[!UICONTROL Label]** field and select the delivery channel: email, mobile, Facebook, Twitter, or mobile applications.

   >[!NOTE]
   >
   >Les abonnements Facebook et Twitter sont détaillés dans [cette section](../../social/using/about-social-marketing.md). Les abonnements aux applications mobiles sont détaillés dans [A propos du canal](../../delivery/using/about-mobile-app-channel.md)des applications mobiles.

* Pour un service de type Courrier électronique, sélectionnez le mode **de** livraison. Les modes possibles sont les suivants : **[!UICONTROL Newsletter]** ou **[!UICONTROL Viral]**.
* Vous pouvez envoyer des messages **de** confirmation pour un abonnement ou un désabonnement. Pour ce faire, sélectionnez les modèles de remise à utiliser pour créer les livraisons correspondantes à partir des **[!UICONTROL Subscription]** champs et **[!UICONTROL Unsubscription]** . Ces modèles doivent être configurés avec un mappage de cible de **[!UICONTROL Subscription]** type, sans cible définie. Voir la section [A propos du canal](../../delivery/using/about-email-channel.md)de messagerie.
* Par défaut, les abonnements sont illimités. Vous pouvez désélectionner l’ **[!UICONTROL Unlimited]** option pour définir la durée de validité du service. La durée peut être spécifiée en jours (**[!UICONTROL d]** ) ou en mois (**[!UICONTROL m]** ).

Une fois le service enregistré, il est ajouté à la liste Services et abonnements : Cliquez sur son nom pour le modifier. Plusieurs onglets sont disponibles. L’ **[!UICONTROL Subscriptions]** onglet permet de consulter la liste des abonnés au service d’informations (**[!UICONTROL Active subscriptions]** onglet) ou l’historique d’abonnement/désabonnement (**[!UICONTROL History]** onglet). Vous pouvez également ajouter et supprimer des abonnés de cet onglet. See [Adding and deleting subscribers](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

The **[!UICONTROL Detail...]** button lets you look at the subscription properties for the selected recipient.

Vous pouvez modifier les propriétés de l&#39;abonnement pour un destinataire.

![](assets/s_ncs_user_services_modify.png)

Sur le tableau de bord, cliquez sur l’ **[!UICONTROL Reports]** onglet pour effectuer le suivi des abonnements : modifications des niveaux d’abonnement, du nombre total d’abonnés, etc. Vous pouvez archiver des rapports et consulter l’historique à partir de cet onglet.

## Ajouter et supprimer des abonnés {#adding-and-deleting-subscribers}

Dans l’ **[!UICONTROL Subscriptions]** onglet d’un service d’informations, cliquez **[!UICONTROL Add]** pour ajouter des abonnés. Vous pouvez également cliquer avec le bouton droit sur la liste des abonnés et sélectionner **[!UICONTROL Add]**. Sélectionnez le dossier dans lequel les profils à abonner sont stockés, puis sélectionnez les profils à abonner et cliquez sur **[!UICONTROL OK]** pour valider.

To delete subscribers, select them and click **[!UICONTROL Delete]**. You can also right-click the subscriber list and select **[!UICONTROL Delete]**.

Dans les deux cas, vous pouvez envoyer un message de confirmation aux utilisateurs concernés si un modèle de remise de désabonnement a été joint au service (voir [Création d’un service](#creating-an-information-service)d’informations). Un avertissement vous permet de valider ou non cette remise :

![](assets/s_ncs_user_services_update.png)

See [Subscription and unsubscription mechanisms](#subscription-and-unsubscription-mechanisms).

## Diffuser aux abonnés d&#39;un service {#delivering-to-the-subscribers-of-a-service}

Pour diffuser aux abonnés d&#39;un service d&#39;information, vous devez cibler sur les abonnés au service d&#39;information visé, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>The target mapping must be **[!UICONTROL Subscriptions]**.

Sélectionnez **[!UICONTROL Subscribers of an information service]** puis cliquez sur **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Select the targeted information service and click **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

The **[!UICONTROL Preview]** tab lets you view the list of subscribers to the selected information service.

## Inscription et désinscription {#subscription-and-unsubscription-mechanisms}

Vous pouvez mettre en place des mécanismes d&#39;inscription et de désinscription afin d&#39;automatiser les processus et la gestion des abonnés.

>[!NOTE]
>
>Vous pouvez envoyer un message de confirmation aux nouveaux inscrits/désinscrits.\
>The content of this message is defined in the information service configuration via the **[!UICONTROL Subscription]** or **[!UICONTROL Unsubscription]** fields.
>
>The confirmation messages are created via the delivery templates specified in these fields. These target mappings must be **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Inscrire un destinataire à un service {#subscribing-a-recipient-to-a-service}

Pour inscrire des destinataires à un service d&#39;information, vous pouvez :

* Manually add the service: to do this, from the **[!UICONTROL Subscriptions]** tab of their profile, click **[!UICONTROL Add]** and select the information service concerned.

   Voir à ce sujet la section sur l&#39;édition de profils dans [cette section](../../platform/using/editing-a-profile.md).

* Abonnez automatiquement un ensemble de destinataires à ce service. La liste des destinataires peut provenir d’une opération de filtrage, d’un groupe, d’un dossier, d’une importation ou d’une sélection directe effectuée à l’aide de la souris. Pour abonner ces destinataires, sélectionnez les profils et cliquez avec le bouton droit de la souris. Sélectionnez **[!UICONTROL Actions > Subscribe selection to a service...]**, sélectionnez le service concerné et lancez l’opération.
* Importer des destinataires et les abonner automatiquement à un service d&#39;information : pour cela, sélectionnez le service visé dans la dernière étape de l&#39;assistant d&#39;import.

   Voir à ce propos [cette section](../../platform/using/importing-data.md#import-wizard).

* Utiliser un formulaire web pour que les destinataires puissent s&#39;abonner à un service.

   Voir à ce propos [cette section](../../web/using/about-web-applications.md).

* Creating a targeting workflow and using a **[!UICONTROL Subscription service]** box.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   Les workflows et leur utilisation sont présentés dans [cette section](../../workflow/using/about-workflows.md).

### Désinscrire un destinataire d&#39;un service {#unsubscribing-a-recipient-from-a-service}

#### Désinscription manuelle {#manual-unsubscribing}

Les diffusions par email doivent légalement contenir un lien de désinscription. Les destinataires peuvent cliquer sur ce lien pour mettre à jour leur profil et ainsi être exclu des cibles des prochaines diffusions.

Le lien de désabonnement par défaut est inséré via le dernier bouton de la barre d’outils de l’éditeur de contenu fourni dans l’assistant de distribution (voir [A propos de la personnalisation](../../delivery/using/about-personalization.md)). Lorsque le destinataire clique sur ce lien, le profil est mis sur liste noire (exclusion), ce qui signifie que ce destinataire ne sera plus ciblé par une action de remise.

Les destinataires peuvent toutefois choisir de se désabonner d’un service sans s’abonner à tous les services. Pour ce faire, vous pouvez utiliser un formulaire Web (reportez-vous à [cette section](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) ou insérer un lien personnalisé de désabonnement (voir les blocs [de](../../delivery/using/personalization-blocks.md)personnalisation).

Vous pouvez également désabonner manuellement un destinataire du profil du destinataire. Pour ce faire, cliquez sur l’ **[!UICONTROL Subscriptions]** onglet du destinataire concerné, sélectionnez le ou les services d’information concernés, puis cliquez sur **[!UICONTROL Delete]**.

Vous pouvez enfin vous désabonner d&#39;un ou de plusieurs destinataires par l&#39;intermédiaire du service d&#39;information concerné. Pour ce faire, cliquez sur l’ **[!UICONTROL Subscriptions]** onglet du service, sélectionnez les destinataires concernés et cliquez sur **[!UICONTROL Delete]**.

#### Désinscription automatique {#automatic-unsubscription}

Un service d’information peut avoir une durée limitée. Les destinataires seront désabonnés automatiquement à l’expiration de la période de validité. Cette période est spécifiée dans l’ **[!UICONTROL Edit]** onglet des propriétés du service. Elle est exprimée en jours.

![](assets/s_ncs_user_services_delay.png)

Vous pouvez également configurer un processus de désabonnement pour une population. Pour ce faire, suivez la même procédure que pour un processus d’abonnement, mais sélectionnez l’ **[!UICONTROL Unsubscription]** option. See [Subscribing a recipient to a service](#subscribing-a-recipient-to-a-service).

### Tracking des inscrits {#subscriber-tracking}

You can track the changes in subscriptions to the information services using the **[!UICONTROL Reports]** link on the dashboard.

![](assets/s_ncs_user_services_report.png)

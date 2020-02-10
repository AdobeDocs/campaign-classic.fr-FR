---
title: Accès aux informations sur les diffusions
seo-title: Accès aux informations sur les diffusions
description: Accès aux informations sur les diffusions
seo-description: null
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Accès aux informations sur les diffusions{#accessing-deliveries-information}

## Accès à la liste des diffusions {#accessing-the-list-of-deliveries}

To access the list of deliveries, go to the **[!UICONTROL Campaigns]** universe and click the **[!UICONTROL Deliveries]** link.

If you use [the Explorer view](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer), you can access all deliveries via the **[!UICONTROL Campaign management > Deliveries]** node in the tree.

>[!NOTE]
>
>L&#39;espace de travail d&#39;Adobe Campaign est présenté dans [cette section](../../platform/using/adobe-campaign-workspace.md).

Cette page vous donne accès à une vue d&#39;ensemble de vos diffusions : elle affiche toutes les diffusions de votre base. Vous pouvez y consulter leur état, taux de succès et date de modification.

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>Le filtrage des informations est présenté dans [cette section](../../platform/using/filtering-options.md).

L&#39;assistant de diffusion vous permet de paramétrer vos diffusions, d&#39;en lancer la validation puis de les envoyer. Le contenu de l&#39;assistant dépend du canal de communication (email, mobile, push, courrier) et des droits dont dispose l&#39;opérateur.

Pour agir sur les diffusions de la liste, cliquez sur la diffusion de votre choix. Celle-ci s&#39;ouvre dans une nouvelle fenêtre. Vous pouvez alors confirmer son envoi, ou l&#39;arrêter par exemple.

![](assets/s_ncs_user_interface_delivery02.png)

En fonction de l&#39;avancement dans le cycle de diffusion, les principaux états possibles sont :

* Annulée
* En échec
* En attente
* Terminé
* En pause
* En reprise
* En cours
* Prête à être diffusée
* En préparation
* Calcul de la cible
* En édition

A chaque état correspond une couleur et un libellé spécifique.

![](assets/s_ncs_user_status_campaigns_120.png)

The drop-down list next to the **[!UICONTROL Create]** button enables you to filter deliveries based on their status.

![](assets/delivery_filter_status.png)

## Accès au calendrier des diffusions {#accessing-the-delivery-calendar}

Pour accéder au calendrier de livraison, accédez à l’ **[!UICONTROL Campaign]** univers et cliquez sur le **[!UICONTROL Campaign calendar]** lien. Ce calendrier affiche la ventilation des campagnes au fil du temps. Vous pouvez personnaliser l’affichage par mois, semaine ou jour.

![](assets/s_ncs_user_interface_delivery04.png)

Click the name of a delivery to display the main information about it. You can also open the campaign if necessary by clicking **[!UICONTROL Open]**.

![](assets/s_ncs_user_interface_delivery05.png)

## Accès aux informations sur le débit des diffusions {#accessing-deliveries-throughput-information}

Les informations de la **[!UICONTROL Delivery throughput]** page concernent toutes les livraisons de la plateforme. Pour mesurer la vitesse à laquelle les messages sont diffusés, les critères sont le nombre de messages envoyés par heure et la taille des messages (en bits par seconde). Dans l’exemple ci-dessous, le premier graphique montre les livraisons réussies en bleu et le nombre de livraisons erronées en orange.

You can choose the time slot for which the throughput is calculated. To do this, select the value from the drop-down list, and then click **[!UICONTROL Refresh]**.

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers la MTA améliorée, la **[!UICONTROL Delivery throughput]** page n’affichera plus le débit vers vos destinataires de courrier électronique. Il indiquera la vitesse de débit du relais de vos messages de Campaign vers la MTA améliorée.
>
>Pour plus d’informations sur la MTA améliorée d’Adobe Campaign, reportez-vous à ce [document](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).
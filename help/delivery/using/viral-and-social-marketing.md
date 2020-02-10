---
title: Marketing viral et réseaux sociaux
seo-title: Marketing viral et réseaux sociaux
description: Marketing viral et réseaux sociaux
seo-description: null
page-status-flag: never-activated
uuid: dca3db7e-cc8d-42ca-b1b8-45e9fb739c97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 66f2b229-92d9-4db1-97a4-2d9eb2270446
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Marketing viral et réseaux sociaux{#viral-and-social-marketing}

## A propos du marketing viral {#about-viral-marketing}

Adobe Campaign permet de mettre en place les outils favorisant le marketing viral.

Vous pouvez ainsi permettre aux destinataires de vos diffusions, ou aux visiteurs de votre site Web, de partager l&#39;information avec leur réseau : ajouter le lien à leur profil Facebook, Twitter, etc., ou envoyer un message à un ami.

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>Pour que les liens ajoutés fonctionnent correctement, la page miroir du message correspondant doit obligatoirement être disponible. Pour cela, vous devez inclure dans la diffusion le lien vers la page miroir.

## Réseaux sociaux : partager un lien {#social-networks--sharing-a-link}

Pour permettre aux destinataires de vos diffusions de partager le contenu des messages avec les membres de leur réseau, vous devez inclure le bloc de personnalisation correspondant.

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>Par défaut, ce lien n’est pas proposé dans la liste des blocs. Vous pouvez y accéder en cliquant sur **[!UICONTROL Other...]**, puis en sélectionnant le **[!UICONTROL Social network sharing links]** bloc.

![](assets/s_ncs_user_viral_add_link_via_others.png)

Le rendu sera le suivant :

![](assets/s_ncs_user_viral_add_link_rendering.png)

Lorsque le destinataire clique sur l&#39;icône d&#39;un des réseaux sociaux proposés, il est automatiquement redirigé vers son compte afin de partager le lien vers le contenu de ce message. Les membres de son réseau pourront ainsi accéder à cette communication.

>[!NOTE]
>
>Ce bloc de personnalisation contient tous les liens (pour l’envoi et le partage de messages avec tous les réseaux sociaux). Il peut être modifié pour répondre à vos besoins. Toutefois, la configuration est réservée aux utilisateurs avancés. Pour modifier le bloc de personnalisation correspondante, accédez au **[!UICONTROL Resources > Campaign management > Personalization blocks]** noeud de l’arborescence Adobe Campaign.

## Marketing viral : transférer à un ami {#viral-marketing--forward-to-a-friend}

Un service viral permet de mettre en place des actions de type parrainage : ces actions permettent de transférer un message à un ami. Le profil du ou des filleuls est alors stocké provisoirement dans la base de données (dans une table dédiée). Le message transféré propose un lien afin de permettre au filleul de s&#39;abonner : il sera alors ajouté dans la base de données Adobe Campaign.

Pour permettre le transfert d&#39;un message, le principe est le même que pour le lien vers les réseaux sociaux.

Les étapes sont les suivantes :

1. Ajoutez le bloc **[!UICONTROL Social network sharing links]** de personnalisation dans le corps du message d’origine.
1. Le destinataire du message peut cliquer sur l&#39;icône **[!UICONTROL Email]** afin d&#39;envoyer ce message à un ou plusieurs amis.

   ![](assets/s_ncs_user_viral_email_link.png)

   Un formulaire de parrainage permet de renseigner les adresses email des filleuls.

   ![](assets/s_ncs_user_viral_email_msg.png)

   The message is sent to them when the main recipient clicks the **[!UICONTROL Next]** button.

   >[!NOTE]
   >
   >Le contenu de ce message peut être personnalisé pour répondre à vos besoins. Il est créé à partir du **[!UICONTROL Transfer of original message]** modèle, qui est stocké dans le **[!UICONTROL Administration > Campaign management > Technical delivery templates]** noeud.
   >
   >It is also possible to change the message forward form made available to the referrer To do this, you need to change the **Viral form** Web application stored in the **[!UICONTROL Resources > Online > Web applications]** node.

1. Dans le message transféré, un lien permet au filleul d&#39;enregistrer son profil dans la base de données. Pour cela, il dispose d&#39;un formulaire de saisie.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >Cette configuration peut être adaptée. Pour ce faire, vous devez modifier l’application Web d’abonnement **du** destinataire stockée dans le **[!UICONTROL Resources > Online > Web applications]** noeud.
   >
   >Pour plus d&#39;informations sur les applications Web, consultez [cette section](../../web/using/about-web-applications.md).

   Une fois la validation effectuée, un message de confirmation leur est envoyé : ils ne seront enregistrés pour de bon qu&#39;une fois qu&#39;ils auront activé le lien dans le message de confirmation. Ce message est créé en fonction du **[!UICONTROL Registration confirmation]** modèle, qui est stocké dans le **[!UICONTROL Administration > Campaign management > Technical delivery templates]** noeud.

   Le filleul est alors ajouté dans le dossier **Destinataires** de la base de données, et il est abonné (par défaut) au service d&#39;information **Newsletter**.

## Tracking du partage vers les réseaux sociaux {#tracking-social-network-sharing}

Chaque partage et chaque accès à l&#39;information partagée fait l&#39;objet d&#39;un tracking au niveau de la diffusion. Les informations de tracking collectées par Adobe Campaign sont accessibles à deux niveaux :

* Dans l&#39;onglet **[!UICONTROL Tracking]** de la diffusion (ou unitairement au niveau d&#39;un destinataire):

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* dans un **[!UICONTROL Sharing to social networks]** rapport dédié :

   ![](assets/s_ncs_user_viral_report.png)


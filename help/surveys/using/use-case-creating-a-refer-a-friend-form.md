---
product: campaign
title: Créer un questionnaire de parrainage d'un ami
description: Découvrez les étapes de création d'un formulaire de parrainage d'un ami
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
TQID: https://experienceleague.adobe.com/n0qp8Q0p18fMbRYxAOu5Qj-0TCf8YgL5vF71F-ZGjbM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 644
ht-degree: 66%

---

# Cas d’utilisation : création d’un formulaire de référence{#use-case-creating-a-refer-a-friend-form}



Dans cet exemple, nous allons proposer un jeu-concours aux destinataires en base. Le formulaire Web contiendra une section pour saisir les réponses et une autre pour recommander un ami en saisissant son adresse électronique.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

Les blocs d&#39;identification et de jeu sont construits selon les procédures décrites ci-avant, dans ce document.

Les étapes de paramétrage et de réalisation du bloc de parrainage sont les suivantes :

1. Créez un formulaire Web de jeu-concours, avec des questions et une zone de saisie des coordonnées d&#39;un ami, comme dans l&#39;exemple ci-dessous :

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   Le champ **Votre message** permet de saisir un message pour le filleul. Le référent doit également saisir ses **Nom**, **Prénom** et **E-mail**.

   Les informations saisies dans les champs sont stockées dans une table spécifique : la table des visiteurs.

   >[!NOTE]
   >
   >Tant que le destinataire n&#39;a pas exprimé son consentement, vous ne pouvez pas le stocker parmi les destinataires la base de données. Il sera donc provisoirement stocké dans la table des **visiteurs et visiteuses** (**nms:visitor**) conçue pour les campagnes de marketing viral. Cette table est régulièrement purgée de son contenu par les opérations de **cleansing**.
   >
   >Dans cet exemple, nous allons cibler des destinataires pour leur proposer de participer au jeu-concours proposé par leur parrain. Cependant, dans ce message, nous souhaitons également leur proposer un abonnement à l&#39;un de nos services d&#39;information. S’ils s’abonnent, ils peuvent être stockés dans la base de données.

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   Le contenu des champs relatifs au filleul sera utilisé dans le script de création de son profil ainsi que dans le message qui lui sera adressé.

1. Créez un premier script afin d&#39;associer le parrain à son filleul.

   Il contient les instructions suivantes :

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   Le nom, le prénom et l’adresse e-mail saisis dans le bloc d’identification de la page sont identifiés comme le nom, le prénom et l’adresse e-mail du référent. Ces champs seront réinjectés dans le corps du message envoyé au filleul.

   La valeur APP5 correspond au nom interne du formulaire Web : cette information permet de connaître l&#39;origine du filleul, c&#39;est-à-dire d&#39;associer le visiteur au formulaire Web à partir duquel il a été créé.

1. La boîte d&#39;enregistrement permet de collecter les informations et les stocker dans la base de données.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. Créez ensuite le modèle de diffusion associé au service d&#39;information créé lors de l&#39;étape 1. Il sera sélectionné dans le champ **[!UICONTROL Choix du scénario]** du service d&#39;information.

   Le modèle de diffusion utilisé pour créer le message de proposition de parrainage contient les informations suivantes :

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   Les caractéristiques de ce modèle sont les suivantes :

   * Vous devez sélectionner la table des visiteurs comme mapping de ciblage.

     ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * Les coordonnées du filleul ainsi que les informations sur le filleul sont extraites du tableau des visiteurs. Il est inséré à l’aide du bouton de personnalisation.

     ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * Ce modèle contient un lien vers le formulaire du jeu-concours et le lien d&#39;inscription pour que le filleul puisse s&#39;abonner à la newsletter.

     Le lien d&#39;inscription est inséré au travers d&#39;un bloc de personnalisation. Par défaut, il permet d&#39;abonner les profils au service **newsletter**. Ce bloc de personnalisation peut être modifié selon vos besoins, par exemple pour inscrire à un autre service.

   * Le nom interne (ici, « referrer ») sera utilisé dans le script de diffusion du message, à l’étape suivante.

   >[!NOTE]
   >
   >Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/create-templates.html?lang=fr){target="_blank"} pour plus d’informations sur les modèles de diffusion.

1. Créez le second script qui permet de procéder à l’envoi des messages d’abonnement.

   ![](assets/s_ncs_admin_survey_viral_sample_7c.png)

   ```
   // Updtate visitor to have a link to the referrer recipient
   ctx.recipient.visitor.@referrerId = ctx.recipient.@id
   ctx.recipient.visitor.@xtkschema = "nms:visitor"
   ctx.recipient.visitor.@_operation = "update" 
   ctx.recipient.visitor.@_key = "@id" 
   xtk.session.Write(ctx.recipient.visitor)
   
   // Send email to friend
   nms.delivery.QueueNotification("referrer",
   <delivery>
   <targets>
     <deliveryTarget>
       <targetPart type='query' exclusion='false' ignoreDeleteStatus='false'>
         <where>
           <condition expr={'@id IN ('+ ctx.recipient.visitor.@id +')' }/>
         </where>
       </targetPart>
      </deliveryTarget>
     </targets>
    </delivery>)
   ```

1. Publiez le formulaire du jeu-concours et envoyez une proposition de participation aux destinataires de la cible initiale. Lorsque l&#39;un d&#39;entre eux souhaite inviter un ami à participer, une diffusion basée sur le modèle **Offre de parrainage** est créée.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   Le filleul est ajouté dans le dossier des visiteurs, sous le noeud **[!UICONTROL Administration > Visiteurs]** :

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   Leur profil contient les informations saisies par leur référent. Il est stocké en fonction des paramétrages renseignés dans le script du formulaire. S’ils décident de s’abonner à la newsletter, ils seront enregistrés dans le tableau des destinataires.

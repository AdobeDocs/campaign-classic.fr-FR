---
product: campaign
title: Synchronisation des profils
description: Découvrez comment synchroniser les profils à lʼaide du connecteur ACS
feature: ACS Connector
hide: true
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
TQID: https://experienceleague.adobe.com/AmLdA4Rvz3MNJ1U5aqC4ITjfa66N86htyRMJWJKkMb8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1255
ht-degree: 66%

---

# Synchronisation des profils{#synchronizing-profiles}



ACS Connector réplique les données de Campaign v7 vers Campaign Standard. Les données reçues de Campaign v7 peuvent être utilisées dans Campaign Standard pour créer des diffusions. Vous pouvez voir comment les profils sont synchronisés en effectuant les opérations répertoriées ci-dessous.

* **Ajouter de nouveaux destinataires** : créez un nouveau destinataire dans Campaign v7 et vérifiez qu&#39;un profil correspondant a été répliqué vers Campaign Standard. Consultez la section [Création d’un nouveau destinataire](#creating-a-new-recipient).
* **Mise à jour des destinataires** : modifiez un nouveau destinataire dans Campaign v7 et visualisez le profil correspondant dans Campaign Standard pour vérifier que la mise à jour a été répliquée. Consultez la section [Modification d’un destinataire](#editing-a-recipient).
* **Création dʼun workflow dans Campaign Standard** : créez un workflow dans Campaign Standard qui comprend une requête avec une audience ou des profils répliqués depuis Campaign v7. Consultez la section [Création dʼun workflow](#creating-a-workflow).
* **Création dʼune diffusion dans Campaign Standard** : exécutez le workflow jusquʼà la fin pour envoyer une diffusion. Consultez la section [Création d’une diffusion](#creating-a-delivery).
* **Vérifier le lien de désinscription** : utilisez une application web de Campaign v7 pour vous assurer que le choix du destinataire de se désinscrire d’un service est envoyé à la base de données de Campaign v7. L’option permettant d’arrêter de recevoir le service est répliquée vers Campaign Standard. Consultez la section [Modification du lien de désinscription](#changing-the-unsubscription-link).

## Conditions préalables requises {#prerequisites}

Les sections suivantes décrivent comment ACS Connector vous permet d&#39;ajouter et de modifier des destinataires dans Campaign v7 et de les utiliser ensuite dans une diffusion Campaign Standard. ACS Connector requiert les éléments suivants :

* des destinataires dans Campaign v7 répliqués vers Campaign Standard,
* les droits utilisateurs pour exécuter des workflows dans Campaign v7 et Campaign Standard,
* les droits utilisateurs pour créer et exécuter une diffusion dans Campaign Standard.

## Modification du lien de désinscription {#changing-the-unsubscription-link}

Lorsqu’un destinataire clique sur le lien de désinscription dans un e-mail envoyé par Campaign Standard, le profil correspondant dans Campaign Standard est mis à jour. Pour vous assurer qu&#39;un profil répliqué comprend le choix d&#39;un utilisateur de se désabonner d&#39;un service, les informations doivent être envoyées à Campaign v7 plutôt qu&#39;à Campaign Standard. Pour effectuer la modification, le service de désabonnement est lié à une application web de Campaign v7 plutôt qu’à Campaign Standard.

>[!NOTE]
>
>Avant de suivre la procédure ci-dessous, demandez à votre consultant de configurer l&#39;application web pour le service de désinscription.

## Création dʼun destinataire {#creating-a-new-recipient}

1. Créez un nouveau destinataire dans Campaign v7 pour la réplication vers Campaign Standard. Saisissez autant d’informations que possible, y compris le nom de famille, le prénom, l’adresse e-mail et l’adresse postale du destinataire. Toutefois, ne choisissez pas de **[!UICONTROL Civilité]**, car elle sera ajoutée dans la section suivante, [Modifier une personne destinataire](#editing-a-recipient).

   ![](assets/acs_connect_profile_sync_01.png)

1. Vérifiez que le nouveau destinataire a été ajouté à Campaign Standard. Lors de la vérification du profil, assurez-vous que les données saisies dans Campaign v7 sont également disponibles dans Campaign Standard. Pour savoir où trouver les profils dans Campaign Standard, reportez-vous à la section [Principes de navigation](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=fr).

   ![](assets/acs_connect_profile_sync_02.png)

   Par défaut, la réplication périodique du connecteur ACS a lieu toutes les 15 minutes. Pour plus d’informations, voir [Réplication des données](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Modification dʼun destinataire {#editing-a-recipient}

Les étapes ci-dessous qui permettent de modifier un point unique de données constituent un exemple simple de la façon dont Campaign v7 devient la base de données principale de Campaign Standard lors de l’utilisation de la réplication de données. La modification ou la suppression de données répliquées dans Campaign v7 a le même effet sur les données correspondantes dans Campaign Standard.

1. Sélectionnez la personne destinataire créée lors de l’étape [Créer une personne destinataire](#creating-a-new-recipient) et modifiez son nom. Par exemple, choisissez une **[!UICONTROL Civilité]** pour la personne destinataire (par exemple, M. ou Mme).

   ![](assets/acs_connect_profile_sync_03.png)

1. Vérifiez que le nom de la personne destinataire a été mis à jour dans Campaign Standard. Pour savoir où trouver les profils dans Campaign Standard, reportez-vous à la section [Principes de base de navigation](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=fr).

   ![](assets/acs_connect_profile_sync_04.png)

   Par défaut, la réplication périodique du connecteur ACS a lieu toutes les 15 minutes. Pour plus d’informations, voir [Réplication des données](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Création dʼun workflow {#creating-a-workflow}

Les profils et services répliqués depuis Campaign v7 sont disponibles pour les spécialistes du marketing digital afin d&#39;exploiter les données complètes dans Campaign Standard. Les instructions ci-dessous montrent comment ajouter une requête à un workflow Campaign Standard, puis l’utiliser avec la base de données répliquée.

Pour plus d&#39;informations et des instructions complètes relatives aux workflows Campaign Standard, reportez-vous à la section [Workflows](../../workflow/using/about-workflows.md).

1. Allez dans Campaign Standard et cliquez sur **[!UICONTROL Activités marketing]**.
1. Cliquez sur **[!UICONTROL Créer]** en haut à droite.
1. Cliquez sur **[!UICONTROL Workflow]**.
1. Cliquez sur **[!UICONTROL Nouveau workflow]**, puis sur **[!UICONTROL Suivant]**.
1. Saisissez un nom pour le workflow dans le champ **[!UICONTROL Libellé]** et d&#39;autres informations si nécessaire. Cliquez sur **[!UICONTROL Suivant]**.
1. Depuis **[!UICONTROL Ciblage]** à gauche, déplacez une activité **[!UICONTROL Requête]** vers l&#39;espace de travail.

   ![](assets/acs_connect_profile_sync_05.png)

1. Double-cliquez sur l&#39;activité **[!UICONTROL Requête]** et choisissez un paramètre utilisable avec la base de données répliquée. Par exemple, vous pouvez :

   * Faites glisser **[!UICONTROL Profils]** dans l’espace de travail. Utilisez le menu déroulant du champ pour sélectionner **[!UICONTROL Est une ressource externe]** afin de trouver les profils qui ont été répliqués depuis Campaign v7.
   * Placer d&#39;autres paramètres de requête pour cibler davantage les profils répliqués.

## Création dʼune diffusion {#creating-a-delivery}

>[!NOTE]
>
>Les instructions pour créer la diffusion sʼappliquent au workflow commencé à la section [Création dʼun workflow](#creating-a-workflow).

Les spécialistes du marketing digital peuvent utiliser une application web de Campaign v7 pour s&#39;assurer que le choix d&#39;un destinataire de se désabonner d&#39;un service est envoyé à la base de données de Campaign v7. Une fois que le destinataire a cliqué sur le lien de désinscription, l&#39;option permettant d&#39;arrêter la réception du service est répliquée de Campaign v7 vers Campaign Standard. Pour plus dʼinformations, consultez la section [Modification du lien de désinscription](#changing-the-unsubscription-link).

Suivez la procédure ci-dessous pour ajouter une diffusion email à un workflow existant avec le service de désinscription créé dans Campaign v7. Pour obtenir des informations supplémentaires et des instructions complètes en ce qui concerne les workflows de Campaign Standard, consultez ce [document](../../workflow/using/about-workflows.md).

>[!NOTE]
>
>Avant de suivre la procédure ci-dessous, demandez à votre consultant de configurer l&#39;application web pour le service de désinscription.

1. Cliquez sur **[!UICONTROL Canaux]** à gauche.
1. Positionnez **[!UICONTROL Diffusion Email]** dans le workflow existant de l&#39;espace de travail.

   ![](assets/acs_connect_profile_sync_07.png)

1. Double-cliquez sur l&#39;activité **[!UICONTROL Diffusion Email]** et sélectionnez **[!UICONTROL Email unique]** ou **[!UICONTROL Email récurrent]**. Sélectionnez vos options, puis cliquez sur **[!UICONTROL Suivant]**.
1. Cliquez sur **[!UICONTROL Diffuser par email]**, puis sur **[!UICONTROL Suivant]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. Saisissez un nom pour la diffusion dans le champ **[!UICONTROL Libellé]** et d&#39;autres informations si nécessaire. Cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. Dans le champ **[!UICONTROL Objet]**, saisissez l&#39;objet qui apparaîtra dans la boîte email du destinataire.
1. Cliquez sur **[!UICONTROL Changer de contenu]** pour ajouter un modèle HTML.

   ![](assets/acs_connect_profile_sync_10.png)

1. Sélectionnez un contenu qui comprend le lien de désinscription au service. Cliquez sur **[!UICONTROL Confirmer]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. Le lien de désinscription actuel doit être remplacé par un nouveau lien utilisant l&#39;application web créée par votre consultant. Recherchez le lien de désinscription au bas du contenu de l’e-mail et cliquez dessus une fois. Cliquez sur l’icône de corbeille pour supprimer le lien.

   ![](assets/acs_connect_profile_sync_12.png)

1. Cliquez dans la même zone de contenu, puis saisissez **Lien de désinscription**.

   ![](assets/acs_connect_profile_sync_13.png)

1. Sélectionnez le texte avec votre curseur et cliquez sur l&#39;icône représentant une chaîne.
1. Cliquez sur **[!UICONTROL Lien vers une landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. Cliquez sur l&#39;icône représentant un dossier pour sélectionner la landing page.

   ![](assets/acs_connect_profile_sync_15.png)

1. Sélectionnez l&#39;application web créée par le consultant, puis cliquez sur **[!UICONTROL Confirmer]**.

   ![](assets/acs_connect_profile_sync_16.png)

1. Cliquez sur **[!UICONTROL Créer]**.
1. Revenez au workflow en cliquant sur le nom de la diffusion.

   ![](assets/acs_connect_profile_sync_17.png)

1. Cliquez sur **[!UICONTROL Démarrer]** pour envoyer la diffusion. L’icône de diffusion par e-mail clignote pour indiquer qu’elle est en cours de préparation pour la diffusion.

   ![](assets/acs_connect_profile_sync_18.png)

1. Double-cliquez sur le canal **[!UICONTROL Diffusion Email]** et sélectionnez **[!UICONTROL Confirmer]** pour envoyer l&#39;email. Cliquez sur **[!UICONTROL OK]** pour envoyer les messages.

   ![](assets/acs_connect_profile_sync_19.png)

## Vérification du service de désinscription {#verifying-the-unsubscription-service}

Suivez les instructions détaillées dans les sections [Création dʼun workflow](#creating-a-workflow) et [Création dʼune diffusion](#creating-a-delivery) avant de passer aux étapes ci-dessous.

1. Le destinataire clique sur le lien de désinscription dans la diffusion email.

   ![](assets/acs_connect_profile_sync_20.png)

1. Il confirme la désinscription.

   ![](assets/acs_connect_profile_sync_21.png)

1. Les données du destinataire dans Campaign v7 sont mises à jour pour prendre en compte la désinscription de l&#39;utilisateur. Vérifiez que la case **[!UICONTROL Ne plus contacter (tous canaux)]** est cochée pour la personne destinataire.

   ![](assets/acs_connect_profile_sync_22.png)

1. Allez dans Campaign Standard et affichez le détail du profil du destinataire. Vérifiez qu&#39;une case à cocher apparaît en regard de l&#39;option **[!UICONTROL Ne plus contacter (tous canaux)]**. Pour savoir où trouver les profils dans Campaign Standard, reportez-vous à la section [Principes de navigation](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=fr).

   ![](assets/acs_connect_profile_sync_23.png)

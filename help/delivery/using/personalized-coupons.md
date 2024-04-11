---
product: campaign
title: Coupons personnalisés
description: Découvrez comment créer et insérer des coupons personnalisés
badge-v8: label="S’applique également à la version 8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: Personalization
role: User
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 72%

---

# Coupons personnalisés{#personalized-coupons}

Le fait d&#39;ajouter des coupons à vos diffusions peut donner une valeur ajoutée à vos destinataires en termes de produits et services. Le module coupon de Campaign permet de créer un jeu de coupons à ajouter à des offres marketing à venir. Lorsque vous êtes prêt à créer une diffusion, assignez les coupons applicables. Dans la mesure où les coupons sont valables pendant une période définie, un coupon assigné est lié de façon unique à son message de diffusion. De plus, Campaign confirme qu&#39;il y a suffisamment de coupons par rapport au nombre de messages avant l&#39;envoi de la diffusion.

>[!NOTE]
>
>La Gestion des coupons est un package qui doit être installé. Pour confirmer que vous disposez de la Gestion des coupons, allez dans **[!UICONTROL Administration > Configuration > Gestion des packages > Packages installés.]**
>
>Les données de coupon peuvent être importées et exportées au format CSV et XML. Pour plus d&#39;informations sur l&#39;import et l&#39;export, voir [cette section](../../platform/using/get-started-data-import-export.md).

## Création dʼun coupon {#creating-a-coupon}

Le module coupon offre le choix entre deux options lors de la création de coupons :

* **Anonyme** : un coupon générique pour des destinataires précis ou une liste de destinataires.
* **Individuel** : un coupon personnalisé pour des destinataires précis.

Avant d&#39;appliquer les étapes ci-dessous, vérifiez que vous savez quel type de coupon vous souhaitez créer.

1. Dans l&#39;arborescence Campaign, allez dans **[!UICONTROL Ressources > Gestion de campagne > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. Cliquez sur le bouton **[!UICONTROL Nouveau]**.
1. Saisissez le nom du coupon dans la **[!UICONTROL Libellé]** champ . Un code unique a été automatiquement saisi dans **[!UICONTROL Code coupon]**. Vous pouvez conserver le code ou en saisir un nouveau.

   ![](assets/deliv_coup_02.png)

1. Sélectionnez **[!UICONTROL Date de début]** et **[!UICONTROL Date de fin]** pour configurer la période de validité du coupon.
1. Dans **[!UICONTROL Type de coupon]**, sélectionnez Anonyme ou Individuel.

   **[!UICONTROL Coupons anonymes]** : un coupon anonyme est identique pour tous les destinataires. Confirmez que l’option Anonyme est sélectionnée dans la variable **Type de coupon** et cliquez sur **Enregistrer** pour générer le coupon.

   **[!UICONTROL Coupons individuels]** : un coupon individuel peut être personnalisé davantage à l&#39;aide de codes coupon supplémentaires. Par exemple, un coupon individuel est créé pour une promotion dans un magasin d&#39;équipement sportif. Or, la liste des destinataires est longue et ceux-ci s&#39;intéressent à des sports différents. Vous pouvez ajouter des noms de code pour le coupon individuel en fonction d&#39;un sport précis (p.ex. le foot, le football américain, le baseball, etc.) et envoyer chaque code aux destinataires concernés.

   1. Lorsque vous sélectionnez Individuel, un nouvel onglet, Coupons, s’affiche en bas à gauche. Accédez au **[!UICONTROL Coupons]** et cliquez sur **[!UICONTROL Ajouter]**.
   1. Lorsque la fenêtre pop-up vous y invite, saisissez un code unique pour le coupon individuel.
   1. Cliquez sur **[!UICONTROL Enregistrer]** pour générer le coupon.

   Pour plus dʼinformations sur lʼonglet Coupons, consultez la section [Configuration de coupons individuels](#configuring-individual-coupons).

   >[!NOTE]
   >
   >Les coupons individuels peuvent être importés en bloc. Pour plus d&#39;informations sur l&#39;import et l&#39;export, voir [cette section](../../platform/using/get-started-data-import-export.md).

### Configuration de coupons individuels {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

L&#39;onglet Coupons n&#39;est disponible qu&#39;avec les Coupons Individuels. Une fois qu&#39;un coupon est associé à une diffusion, l&#39;onglet Coupon fournit les détails suivants :

* **[!UICONTROL Etat]** : Disponibilité du coupon.
* **[!UICONTROL Consommé le]** : Date à laquelle le coupon est consommé.
* **[!UICONTROL Canal]** : Canal utilisé pour envoyer le coupon.
* **[!UICONTROL Adresse]** : Adresses email des destinataires.

Valeurs de **[!UICONTROL status]**, **[!UICONTROL channel]**, et **[!UICONTROL address]** sont automatiquement terminées. Toutefois, les valeurs de **[!UICONTROL consommé le]** ne sont pas récupérés par Campaign. Vous pouvez les compléter en important un fichier contenant les détails du remboursement des coupons.

## Insertion dʼun coupon dans une diffusion e-mail {#inserting-a-coupon-into-an-email-delivery}

Dans l&#39;exemple ci-dessous, la diffusion est créée à partir de la page d&#39;accueil. Pour obtenir des instructions détaillées sur la création d&#39;une diffusion, reportez-vous à la section [cette section](about-email-channel.md). Vous pouvez également ajouter un coupon à une diffusion dans un workflow.

1. Allez sur **[!UICONTROL Campagnes]** et sélectionnez **[!UICONTROL Diffusions]**.
1. Cliquez sur **[!UICONTROL Créer]**.

   ![](assets/deliv_coup_04.png)

1. Saisissez un nom dans le champ **[!UICONTROL Libellé]** et cliquez sur **[!UICONTROL Continuer]**.
1. Cliquez sur **[!UICONTROL Pour]** pour ajouter des destinataires.
1. Cliquez sur **[!UICONTROL Ajouter]** pour sélectionner les destinataires de la diffusion. Une fois les destinataires sélectionnés, cliquez sur **[!UICONTROL Ok]** pour revenir à la diffusion.

   ![](assets/deliv_coup_05.png)

1. Saisissez un objet et ajoutez du contenu au message.

   ![](assets/deliv_coup_06.png)

1. Dans la barre d&#39;outils, cliquez sur **[!UICONTROL Propriétés]** et sélectionnez l&#39;onglet **[!UICONTROL Avancé]**.
1. Cliquez sur l&#39;icône dossier pour la **[!UICONTROL Gestion des coupons]**.

   ![](assets/deliv_coup_07.png)

1. Sélectionnez le coupon et cliquez sur **[!UICONTROL Ok]**. Cliquez sur **[!UICONTROL Ok]** encore une fois.

   ![](assets/deliv_coup_08.png)

1. Cliquez sur le message pour choisir l&#39;emplacement du coupon.

   ![](assets/deliv_coup_09.png)

1. Cliquez sur l&#39;icône de personnalisation pour choisir l&#39;une des options suivantes en fonction du type de coupon :

   * Coupon anonyme : **[!UICONTROL Coupon > Code coupon]**

     ![](assets/deliv_coup_10.png)

   * Coupon individuel : **[!UICONTROL Valeur de coupon > Code coupon]**

     ![](assets/deliv_coup_11.png)

     Le bon est inséré dans le message sous forme de code plutôt que sous le nom que vous avez attribué. Le code est utilisé dans le modèle de données de l’ootb Campaign.

   ![](assets/deliv_coup_12.png)

1. Exécutez un test pour confirmer le nom attribué au coupon. Accédez au **[!UICONTROL Aperçu]** et cliquez sur **[!UICONTROL Test de la personnalisation]**. Sélectionnez un destinataire pour le test.

   ![](assets/deliv_coup_13.png)

   A la suite du test, le coupon devrait apparaître sous forme du nom assigné et non du code.

   ![](assets/deliv_coup_14.png)

1. Dans la barre d&#39;outils, cliquez sur **[!UICONTROL Envoyer]** (en haut à gauche) et sélectionnez le mode d&#39;envoi de la diffusion.

   ![](assets/deliv_coup_15.png)

1. Cliquez sur **[!UICONTROL Analyser]**. Si le log d&#39;analyse confirme qu&#39;il y a suffisamment de coupons pour tous les destinataires, cliquez sur **[!UICONTROL Confirmer l&#39;envoi]** pour l’envoyer.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>Pour obtenir des instructions sur la gestion du manque de coupons pour une diffusion, consultez la section [Gestion des coupons insuffisants](#managing-insufficient-coupons).

Pour confirmer que la diffusion a abouti :

1. Allez sur **[!UICONTROL Explorateur > Ressources > Gestion de campagne > Coupons]**.
1. Cliquez sur l&#39;onglet **[!UICONTROL Diffusions]**.

   ![](assets/deliv_coup_17.png)

   En cas de diffusion réussie, l&#39;état est **[!UICONTROL Terminé]**.

>[!NOTE]
>
>Par défaut, le module de gestion des coupons utilise une table **nms:recipient**. [En savoir plus](../../configuration/using/about-data-model.md#default-recipient-table).
>
>Découvrez comment utiliser une table des destinataires personnalisée [sur cette page](../../configuration/using/about-custom-recipient-table.md).

## Gestion des coupons insuffisants {#managing-insufficient-coupons}

L&#39;analyse de la diffusion s&#39;arrête s&#39;il y a moins de coupons que de messages. Dans ce cas, vous pouvez importer plus de coupons ou restreindre le nombre de messages. Pour limiter le nombre de messages, suivez les consignes ci-dessous.

1. Allez dans la fenêtre de diffusion email.
1. Cliquez sur **[!UICONTROL Pour]**.
1. Dans **[!UICONTROL Choix de la cible]**, allez dans l&#39;onglet **[!UICONTROL Exclusions]**.

   ![](assets/deliv_coup_18.png)

1. Dans la section paramètres d&#39;exclusion, cliquez sur **[!UICONTROL Editer]**.
1. Saisissez le nombre de messages à envoyer dans **[!UICONTROL Limiter la diffusion à...messages]** et cliquez sur **[!UICONTROL Ok]**. Vous pouvez envoyer la diffusion.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>En cas de gestion d&#39;un nombre limité de coupons, un workflow de diffusion vous permet de diviser la diffusion en fonction de vos critères. Cette option est adaptée pour l&#39;envoi de coupons à une population précise sans limiter la cible.

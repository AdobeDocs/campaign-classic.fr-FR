---
product: campaign
title: Synchronisation des applications web
description: Découvrez comment synchroniser des applications web à lʼaide du connecteur ACS
feature: ACS Connector
hide: true
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
TQID: https://experienceleague.adobe.com/bPSfdUln5NEqvtnJxYQVbbUd6uOCdjDSDGRceee8i6o
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 870
ht-degree: 100%

---

# Synchronisation des applications web{#synchronizing-web-applications}



Dans ce cas d’utilisation, nous allons envoyer une communication, à l’aide de Campaign Standard, contenant un lien vers une application web de Campaign v7.Lorsque la personne destinataire clique sur le lien dans l’e-mail, l’application web affiche un formulaire contenant plusieurs champs préchargés avec les données de la personne destinataire, ainsi qu’un lien d’abonnement à une newsletter.La personne destinataire peut mettre à jour ses informations et s’abonner au service.Son profil sera mis à jour dans Campaign v7 et les informations seront répliquées dans Campaign Standard.

Si vous disposez d’un grand nombre de services et d’applications web dans Campaign v7, vous pouvez décider de ne pas tous les recréer dans Campaign Standard.Le connecteur ACS vous permet d’utiliser l’ensemble des services et des applications web de Campaign v7 et de les lier à une diffusion envoyée par Campaign Standard.

## Conditions préalables requises {#prerequisites}

Pour ce faire, les éléments suivants sont nécessaires :

* Des destinataires stockés dans la base de données de Campaign v7 et synchronisés avec Campaign Standard. Consultez la section [Synchronisation des profils](../../integrations/using/synchronizing-profiles.md).
* Un service et une application web créés et publiés dans Campaign v7.
* L&#39;application web doit contenir une activité **[!UICONTROL Pré-chargement]** utilisant la méthode d&#39;identification **[!UICONTROL Chiffrement Adobe Campaign]**.

## Création de lʼapplication web et du service {#creating-the-web-application-and-service}

Dans Campaign v7, vous pouvez créer des applications web qui permettent aux personnes destinataires de s’abonner à un service.L’application web et le service sont conçus et stockés dans Campaign v7. Ce service peut être mis à jour par le biais d’une communication de Campaign Standard.Pour en savoir plus sur les applications web dans Campaign v7, voir [cette section](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

Dans Campaign v7, les objets suivants ont été créés :

* un service de newsletter,
* une application web contenant des activités **[!UICONTROL Pré-chargement]**, **[!UICONTROL Page]** et **[!UICONTROL Enregistrement]**.

1. Accédez à **[!UICONTROL Ressources > On-line > Applications Web]** et sélectionnez une application web existante.

   ![](assets/acs_connect_lp_2.png)

1. Modifiez l&#39;activité **[!UICONTROL Pré-chargement]**. La case **[!UICONTROL Chargement automatique des données référencées dans le formulaire]** est cochée et la méthode d&#39;identification **[!UICONTROL Chiffrement Adobe Campaign]** est sélectionnée. L&#39;application web peut ainsi précharger les champs du formulaire avec les données stockées dans la base de données d&#39;Adobe Campaign. Pour plus d&#39;informations, consultez [ce document](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Modifiez la **[!UICONTROL Page]**. Trois champs (Nom, Email et Téléphone) ont été ajoutés, ainsi qu&#39;une case à cocher invitant le destinataire à s&#39;inscrire à une newsletter (service **[!UICONTROL Newsletter]**).

   ![](assets/acs_connect_lp_3.png)

1. Accédez à **[!UICONTROL Profils et cibles > Services et abonnements]** et ouvrez le service **[!UICONTROL Newsletter]**.Il s’agit du service qui sera mis à jour à partir de la communication de Campaign Standard.Vous pouvez constater qu’aucune personne destinataire ne s’est encore abonnée à ce service.

   ![](assets/acs_connect_lp_5.png)

1. Accédez à **[!UICONTROL Profils et cibles > Destinataire]** et sélectionnez un destinataire. Vous pouvez constater que ce profil ne s’est pas encore inscrit au service.

   ![](assets/acs_connect_lp_6.png)

## Réplication des données {#replicating-the-data}

Afin de répliquer les données nécessaires entre Campaign v7 et Campaign Standard, plusieurs modèles de workflows de réplication sont disponibles. Le workflow de **[!UICONTROL Réplication des profils]** reproduit automatiquement tous les destinataires de Campaign v7 vers Campaign Standard. Voir [Workflows techniques et de réplication](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). Le workflow de **[!UICONTROL Réplication des landing pages]** permet la réplication des applications Web que nous voulons utiliser dans Campaign Standard.

![](assets/acs_connect_lp_1.png)

Pour vérifier que les données ont été correctement répliquées, suivez la procédure suivante dans Campaign Standard :

1. Depuis l&#39;écran d&#39;accueil, cliquez sur **[!UICONTROL Profils clients]**.

   ![](assets/acs_connect_lp_7.png)

1. Recherchez votre destinataire Campaign v7 et vérifiez qu’il apparaît dans Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. Dans la barre supérieure, cliquez sur **[!UICONTROL Activités marketing]** et cherchez l’application web de Campaign v7.Elle apparaît sous forme de page de destination dans Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Cliquez sur le logo **[!UICONTROL Adobe Campaign]**, en haut à gauche, sélectionnez **Profils &amp; audiences > Services**, puis vérifiez que le service de newsletter apparaît également.

   ![](assets/acs_connect_lp_10.png)

## Conception et envoi de lʼe-mail {#designing-and-sending-the-email}

Dans cette partie, nous allons voir comment inclure un lien vers la landing page répliquée depuis une application web de Campaign v7 dans un email Campaign Standard.

Les étapes de création, de conception et d&#39;envoi de l&#39;email sont les mêmes que pour un email classique. Pour plus d&#39;informations, consultez la document [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/campaign-standard-home.html?lang=fr).

1. Créez un nouvel email et sélectionnez un ou plusieurs profils répliqués en tant qu&#39;audience.
1. Editez le contenu et insérez un **[!UICONTROL Lien vers une landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Sélectionnez la landing page qui a été répliquée depuis l&#39;application web de Campaign v7.

   ![](assets/acs_connect_lp_13.png)

1. Préparez votre email, envoyez les BAT, puis l&#39;email final.
1. Un des destinataires ouvre l&#39;email et clique sur le lien d&#39;inscription à la newsletter.

   ![](assets/acs_connect_lp_14.png)

1. Ce destinataire ajoute un numéro de téléphone et coche la case d’inscription à la newsletter.

   ![](assets/acs_connect_lp_15.png)

## Récupération des informations mises à jour {#retrieving-the-updated-information}

Lorsque la personne destinataire met ses données à jour via l’application web, Adobe Campaign v7 récupère de manière synchrone les informations mises à jour.Celles-ci sont ensuite répliquées depuis Campaign v7 vers Campaign Standard.

1. Dans Campaign v7, accédez à **[!UICONTROL Profils et cibles > Services et abonnements]** et ouvrez le service **[!UICONTROL Newsletter]**.Vous pouvez constater que la personne destinataire apparaît désormais dans la liste des personnes abonnées.

   ![](assets/acs_connect_lp_16.png)

1. Accédez à **[!UICONTROL Profils et cibles > Destinataire]** et sélectionnez la personne destinataire.Vous pouvez constater que le numéro de téléphone est désormais enregistré.

   ![](assets/acs_connect_lp_17.png)

1. Dans l’onglet **[!UICONTROL Abonnements]**, vous pouvez également constater que le destinataire s’est inscrit au service de newsletter.

   ![](assets/acs_connect_lp_18.png)

1. Patientez quelques minutes pendant l&#39;exécution du workflow de réplication.
1. Dans Campaign Standard, accédez au profil de votre destinataire pour vérifier que les données mises à jour ont été correctement répliquées depuis Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Modifiez le profil.Vous pouvez constater que le numéro de téléphone a été mis à jour.

   ![](assets/acs_connect_lp_20.png)

1. Cliquez sur l’onglet **[!UICONTROL Abonnements]**.Le service de newsletter apparaît maintenant.

   ![](assets/acs_connect_lp_21.png)

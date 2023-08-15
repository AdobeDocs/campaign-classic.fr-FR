---
product: campaign
title: Enrichissement des emails avec des champs de date personnalisés
description: Découvrez comment enrichir les emails avec des champs de date personnalisés
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 100%

---

# Enrichissement des emails avec des champs de date personnalisés{#email-enrichment-with-custom-date-fields}



Dans cet exemple, nous souhaitons envoyer un email avec des champs de données personnalisés aux destinataires qui célèbrent leur anniversaire ce mois-ci. Cet email inclura un coupon valide une semaine avant et après leur anniversaire.

Nous devons cibler à partir d&#39;une liste les destinataires qui célébreront leur anniversaire ce mois-ci avec une activité **[!UICONTROL Partage]**. Ensuite, grâce à l&#39;activité **[!UICONTROL Enrichissement]**, le champ de données personnalisé présentera les dates de validité dans l&#39;email pour l&#39;offre spéciale du client.

![](assets/uc_enrichment.png)

Pour réaliser cet exemple, les étapes sont les suivantes :

1. Dans l&#39;onglet **[!UICONTROL Ciblages et workflows]** de votre campagne, faites glisser et déposez une activité **[!UICONTROL Lecture de liste]** pour cibler votre liste de destinataires.
1. La liste à traiter peut être spécifiée explicitement, calculée par un script ou localisée dynamiquement, selon les options sélectionnées et les paramètres définis ici.

   ![](assets/uc_enrichment_1.png)

1. Ajoutez une activité **[!UICONTROL Partage]** pour différencier les destinataires qui célébreront leur anniversaire ce mois-ci des autres destinataires.
1. Pour partager votre liste, dans la catégorie **[!UICONTROL Filtrage des enregistrements sélectionnés]**, sélectionnez **[!UICONTROL Ajouter une condition de filtrage sur la population entrante]**, puis cliquez sur **[!UICONTROL Editer]**.

   ![](assets/uc_enrichment_2.png)

1. Sélectionnez **[!UICONTROL Critères de filtrage]**, puis cliquez sur le bouton **[!UICONTROL Editer l&#39;expression]** pour filtrer le mois de l&#39;anniversaire du destinataire.

   ![](assets/uc_enrichment_3.png)

1. Cliquez sur **[!UICONTROL Sélection avancée]**, puis sur **[!UICONTROL Editer la formule à partir d&#39;une expression]** et ajoutez l&#39;expression suivante : Month(@birthDate).
1. Dans la colonne **[!UICONTROL Opérateur]**, sélectionnez **[!UICONTROL égal à]**.
1. Filtrez davantage votre condition en ajoutant la **[!UICONTROL Valeur]** de mois de la date actuelle : Month(GetDate()).

   Cela interrogera les destinataires dont le mois d&#39;anniversaire correspond au mois actuel.

   ![](assets/uc_enrichment_4.png)

1. Cliquez sur **[!UICONTROL Terminer]**. Puis, dans l&#39;onglet **[!UICONTROL Général]** de votre activité **[!UICONTROL Partage]**, cliquez sur **[!UICONTROL Générer le complémentaire]** dans la catégorie **[!UICONTROL Résultats]**.

   Avec le résultat **[!UICONTROL Complément]**, vous pouvez ajouter une activité de diffusion ou mettre à jour une liste. Ici, nous avons ajouté une activité **[!UICONTROL Fin]**.

   ![](assets/uc_enrichment_6.png)

Vous devez maintenant paramétrer votre activité **[!UICONTROL Enrichissement]** :

1. Ajoutez une activité **[!UICONTROL Enrichissement]** après votre sous-ensemble pour ajouter vos champs de date personnalisés.

   ![](assets/uc_enrichment_7.png)

1. Ouvrez votre activité **[!UICONTROL Enrichissement]**. Dans la catégorie **[!UICONTROL Complément d&#39;information]**, cliquez sur **[!UICONTROL Ajouter des données]**.

   ![](assets/uc_enrichment_8.png)

1. Sélectionnez **[!UICONTROL Données liées à la dimension de filtrage]**, puis **[!UICONTROL Données de la dimension de filtrage]**.
1. Cliquez sur le bouton **[!UICONTROL Ajouter]**.

   ![](assets/uc_enrichment_9.png)

1. Ajoutez un **[!UICONTROL Libellé]**. Puis, dans la colonne **[!UICONTROL Expression]**, cliquez sur **[!UICONTROL Editer l&#39;expression]**.

   ![](assets/uc_enrichment_10.png)

1. Tout d’abord, nous devons cibler la semaine précédant la date d’anniversaire comme **Date de début de validité** à l’aide de l’**[!UICONTROL Expression]** suivante : `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Ensuite, pour créer le champ de date personnalisé **Date de fin de validité** qui ciblera la semaine après la date de naissance, vous devez ajouter l’**[!UICONTROL Expression]** : `AddDays([target/@birthDate], 7)`.

   Vous pouvez ajouter un libellé à votre expression.

   ![](assets/uc_enrichment_12.png)

1. Cliquez sur **[!UICONTROL Ok]**. Votre enrichissement est maintenant prêt.

Après votre activité **[!UICONTROL Enrichissement]**, vous pouvez ajouter une diffusion. Dans ce cas, nous avons ajouté une diffusion par email pour envoyer une offre spéciale avec des dates de validité aux clients célébrant leur anniversaire ce mois-ci.

1. Faites glisser et déposez une activité **[!UICONTROL Diffusion par email]** après votre activité **[!UICONTROL Enrichissement]**.

   ![](assets/uc_enrichment_15.png)

1. Double cliquez sur votre activité **[!UICONTROL Diffusion par email]** pour commencer à personnaliser votre diffusion.
1. Ajoutez un **[!UICONTROL Libellé]** à votre diffusion, puis cliquez sur **[!UICONTROL Continuer]**.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour créer votre diffusion par email.
1. Vérifiez dans l&#39;onglet **[!UICONTROL Approbation]** des **[!UICONTROL Propriétés]** de la diffusion par email que l&#39;option **[!UICONTROL Confirmer la diffusion avant l&#39;envoi]** est cochée.

   Ensuite, démarrez votre workflow pour enrichir votre transition sortante avec les informations ciblées.

   ![](assets/uc_enrichment_18.png)

Vous pouvez maintenant commencer à concevoir votre diffusion par email avec les champs de date personnalisés créés dans l&#39;activité **[!UICONTROL Enrichissement]**.

1. Double cliquez sur votre activité **[!UICONTROL Diffusion par email]**.
1. Ajoutez vos extensions cibles à votre email. Il devrait se trouver à l&#39;intérieur de l&#39;expression suivante afin de paramétrer le format de vos dates de validité :

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Cliquez sur ![](assets/uc_enrichment_16.png). Sélectionnez **[!UICONTROL Extension de la cible]**, puis les dates de validité personnalisées créées précédemment avec l&#39;activité **[!UICONTROL Enrichissement]** pour ajouter votre extension à l&#39;expression FormatDate.

   ![](assets/uc_enrichment_19.png)

1. Paramétrez votre contenu d&#39;email selon vos besoins.

   ![](assets/uc_enrichment_17.png)

1. Prévisualisez votre email pour vérifier si vos champs de date personnalisés ont été correctement paramétrés.

   ![](assets/uc_enrichment_20.png)

Votre email est maintenant prêt. Vous pouvez commencer à envoyer vos BAT et confirmer la diffusion concernant vos emails d’anniversaire.

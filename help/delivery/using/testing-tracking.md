---
title: Tester le tracking
seo-title: Tester le tracking
description: Tester le tracking
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tester le tracking{#testing-tracking}

Vous pouvez tester le tracking sur les pages miroir, les logs d&#39;email et les liens. Pour ce faire :

1. Créez une diffusion email qui sera utilisée pour le test.
1. Spécifiez l&#39;utilisateur qui recevra l&#39;email. Comme celui-ci devra ouvrir l&#39;email et cliquer sur les liens qu&#39;il contient, veillez à sélectionner une adresse de destinataire test que vous contrôlez.
1. Ajoutez un bloc de personnalisation de page miroir (MirrorPage) au contenu de l&#39;email.
1. Envoyez l&#39;email contenant un lien vers la page miroir.
1. Une fois l&#39;email reçu, ouvrez-le et cliquez sur le lien de la page miroir.
1. After you are correctly redirected to the mirror page, access the **Administration > Technical workflows** folder and open the **Tracking** workflow.
1. Start the workflow, right click the **Scheduler** activity and select **Execute pending task now**.
1. Patientez environ 30 secondes. Sélectionnez ensuite l&#39;onglet **Audit**. Vérifiez que l&#39;onglet contient au moins un enregistrement de log de tracking.

   Cliquez sur **Rafraîchir** si vous ne voyez aucun nouveau log.

1. Accédez à la page du profil du destinataire que vous avez utilisé pour le test, puis sélectionnez l&#39;onglet **Tracking**. Certains enregistrements doivent s&#39;afficher avec la valeur **Page miroir** dans la colonne **Type**.

   >[!NOTE]
   >
   >The recipient&#39;s profile page is located in the **Profiles and Targets > Recipients** folder by default.

   Pour vérifier le tracking des logs d&#39;email, recherchez les valeurs **Ouverture** et **[!UICONTROL Clic email]** dans la colonne **Type**.

   Si les logs d&#39;ouverture n&#39;apparaissent pas, accédez à la diffusion. Vérifiez dans ses **propriétés** que les options **Activer le tracking** et **[!UICONTROL Tracking d&#39;ouverture]** sont cochées.


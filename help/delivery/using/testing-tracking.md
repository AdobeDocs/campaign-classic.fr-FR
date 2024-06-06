---
product: campaign
title: Test du tracking des messages
description: Découvrez comment tester le tracking des messages
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Monitoring
role: User
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---

# Test du tracking des messages{#testing-tracking}

Vous pouvez tester le tracking sur les pages miroir, les logs d&#39;email et les liens. Pour ce faire :

1. Créez une diffusion email qui sera utilisée pour le test.
1. Spécifiez l&#39;utilisateur qui recevra l&#39;email. Comme celui-ci devra ouvrir l&#39;email et cliquer sur les liens qu&#39;il contient, veillez à sélectionner une adresse de destinataire test que vous contrôlez.
1. Ajoutez un bloc de personnalisation de page miroir (MirrorPage) au contenu de l&#39;email.
1. Envoyez l&#39;email contenant un lien vers la page miroir.
1. Une fois l&#39;email reçu, ouvrez-le et cliquez sur le lien de la page miroir.
1. Après avoir été redirigé vers la page miroir, accédez au dossier **Administration > Workflows techniques** et ouvrez le workflow **Tracking**.
1. Démarrez le workflow, cliquez avec le bouton droit sur l’activité **Planificateur** et sélectionnez **Traitement anticipé des tâches en attente**.
1. Patientez environ 30 secondes. Sélectionnez ensuite l&#39;onglet **Audit**. Vérifiez que l&#39;onglet contient au moins un enregistrement de log de tracking.

   Cliquez sur **Rafraîchir** si vous ne voyez aucun nouveau log.

1. Accédez à la page du profil du destinataire que vous avez utilisé pour le test, puis sélectionnez l&#39;onglet **Tracking**. Certains enregistrements doivent s&#39;afficher avec la valeur **Page miroir** dans la colonne **Type**.

   >[!NOTE]
   >
   >La page du profil du destinataire figure par défaut dans le dossier **Profils et Cibles > Destinataires**.

   Pour vérifier le tracking des logs d&#39;email, recherchez les valeurs **Ouverture** et **[!UICONTROL Clic email]** dans la colonne **Type**.

   Si les logs d&#39;ouverture n&#39;apparaissent pas, accédez à la diffusion. Vérifiez dans ses **propriétés** que les options **Activer le tracking** et **[!UICONTROL Tracking d&#39;ouverture]** sont cochées.

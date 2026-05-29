---
product: campaign
title: Charger le contenu de la diffusion
description: Charger le contenu de la diffusion
feature: Workflows
hide: true
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
TQID: https://experienceleague.adobe.com/xRyiD1VNPPhdRtnyRn6JX76vao1-b348bZPoQ3eraLQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 345
ht-degree: 64%

---

# Charger le contenu de la diffusion{#loading-delivery-content}



Si le contenu de votre diffusion figure dans un fichier HTML qui se trouve sur un serveur Amazon S3, FTP ou SFTP, vous pouvez facilement charger ce contenu dans les diffusions Adobe Campaign.

Pour cela :

1. Si vous n’avez pas encore défini de connexion entre Adobe Campaign et le serveur FTP ou SFTP hébergeant les fichiers de contenu, créez un compte externe S3, FTP ou SFTP dans **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Comptes externes]**. Spécifiez dans ce compte externe l&#39;adresse et les informations d&#39;identification utilisées pour établir la connexion au serveur S3 ou (S)FTP.

   Voici un exemple d&#39;un compte externe S3 :

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Créez un workflow depuis par exemple **[!UICONTROL Profils et Cibles]** > **[!UICONTROL Traitements]** > **[!UICONTROL Workflows de ciblage]**.
1. Ajoutez une activité **[!UICONTROL Transfert de fichier]** à votre workflow, puis configurez-la en indiquant les informations suivantes :

   * le compte externe à utiliser pour la connexion au serveur S3, FTP ou SFTP ;
   * le chemin d&#39;accès au fichier sur le serveur S3, FTP ou SFTP.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Ajoutez une activité **[!UICONTROL Diffusion]** et connectez-la à la transition sortante de l&#39;activité **[!UICONTROL Transfert de fichier]**. Configurez-le comme suit :

   * Diffusion : selon vos besoins, il peut s&#39;agir d&#39;une diffusion spécifique qui a déjà été créée dans le système ou d&#39;une nouvelle diffusion reposant sur un modèle existant.
   * Destinataires : dans cet exemple, la cible est spécifiée dans la diffusion elle-même.
   * Contenu : Même si le contenu est importé dans l&#39;activité précédente, sélectionnez **[!UICONTROL Spécifié dans la diffusion]**. Comme le contenu est importé directement à partir d&#39;un fichier situé sur un serveur distant, il n&#39;a pas d&#39;identifiant lorsqu&#39;il est traité par le workflow et ne peut pas être identifié comme provenant de l&#39;événement entrant.
   * Action à effectuer : sélectionnez **[!UICONTROL Enregistrer]** pour enregistrer la diffusion et y accéder depuis **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Diffusions]** une fois le workflow exécuté.

   ![](assets/delivery_loadcontent_activityexample.png)

1. Dans l&#39;onglet **[!UICONTROL Script]** de l&#39;activité **[!UICONTROL Diffusion]**, ajoutez la commande suivante pour charger le contenu du fichier importé dans la diffusion :

   ```
   delivery.content.html.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Enregistrez et exécutez le workflow. Une diffusion avec le contenu chargé est créée dans **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Diffusions]**.

>[!NOTE]
>
>Les bonnes pratiques et la résolution des problèmes liées à l&#39;utilisation du serveur SFTP sont présentées [dans cette page](../../platform/using/sftp-server-usage.md).

---
title: Champs de personnalisation
seo-title: Champs de personnalisation
description: Champs de personnalisation
seo-description: null
page-status-flag: never-activated
uuid: 3a94a50e-259e-40c3-ae67-8a2c42e9fad7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 27c8e443-ee6b-4d58-bc2d-81cf8391c5de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# Champs de personnalisation{#personalization-fields}

Les champs de personnalisation sont utilisés pour un premier niveau de personnalisation du contenu des messages diffusés. Les champs que vous insérez dans un contenu principal matérialisent l&#39;emplacement où insérer les informations provenant de la source de données sélectionnée.

Par exemple, le champ de personnalisation de syntaxe **&lt;%= recipient.LastName %>** spécifie à Adobe Campaign d&#39;insérer le nom du destinataire se trouvant dans la base de données (table des destinataires).

>[!NOTE]
>
>Le contenu des champs de personnalisation ne peut pas dépasser 1 024 caractères.

## Sources de données {#data-sources}

Les champs de personnalisation peuvent provenir de deux types de sources de données selon le mode de diffusion sélectionné :

* La source de données est la base de données Adobe Campaign. C&#39;est le cas le plus fréquent. On parlera par exemple de champs de personnalisation du destinataire : il s&#39;agit de l&#39;ensemble des champs définis dans la table des destinataires qu&#39;il s&#39;agisse de champs standards (typiquement nom, prénom, adresse, ville, date de naissance, etc.) ou de champs libres.
* La source de données est un fichier externe. Il s&#39;agit de l&#39;ensemble des champs définis dans les colonnes du fichier présenté en entrée lors d&#39;une diffusion utilisant les informations présentes dans un fichier externe.

>[!NOTE]
>
>Une balise de personnalisation Adobe Campaign est toujours de la forme **&lt;%=table.champ%>**.

## Insertion d&#39;un champ de personnalisation {#inserting-a-personalization-field}

Pour insérer des champs de personnalisation, cliquez sur l&#39;icône déroulante accessible depuis toute zone d&#39;édition des en-têtes, du sujet ou du corps principal du message.

![](assets/s_ncs_user_add_custom_field.png)

Après la sélection d’une source de données (champs de destinataire ou champ de fichier), cette insertion prend la forme d’une commande qui sera interprétée par Adobe Campaign et remplacée par la valeur du champ pour un destinataire donné. Le remplacement physique peut alors être affiché dans l’ **[!UICONTROL Preview]** onglet.

## Exemple de champ de personnalisation {#personalization-fields-example}

Nous allons créer un email dans lequel nous allons tout d&#39;abord insérer le nom du destinataire et ensuite ajouter dans le corps du message la date de création de son profil. Pour cela :

1. Créez une nouvelle diffusion ou ouvrez une diffusion existante de type email.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Saisissez &quot; **[!UICONTROL Special offer for]** &quot; et utilisez le bouton de la barre d’outils pour insérer un champ de personnalisation. Sélectionner **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. Répétez l&#39;opération pour insérer le nom du destinataire. Insérez des espaces entre chacun de ces champs de personnalisation.
1. Click **[!UICONTROL OK]** to validate.
1. Insérez ensuite la personnalisation dans le corps du message. Pour cela, cliquez dans le contenu du message et cliquez sur le bouton d&#39;insertion de champs.
1. Sélectionner **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Sélectionnez le champ contenant l&#39;information à afficher et cliquez sur **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Cliquez sur l’ **[!UICONTROL Preview]** onglet pour afficher le résultat de la personnalisation. Vous devez sélectionner un destinataire pour afficher son message.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >Lorsqu’une diffusion fait partie d’un processus, vous pouvez utiliser les données du tableau de processus temporaire. Ces données sont regroupées dans le **[!UICONTROL Target extension]** menu. Voir à ce propos [cette section](../../workflow/using/executing-a-workflow.md#target-data).

## Optimiser la personnalisation {#optimizing-personalization}

Vous pouvez optimiser la personnalisation à l’aide d’une option dédiée : **[!UICONTROL Prepare the personalization data with a workflow]**, disponible dans l’ **[!UICONTROL Analysis]** onglet des propriétés de diffusion.

Cette option permet, lors de l&#39;analyse de la diffusion, de créer automatiquement et d&#39;exécuter un workflow qui stocke dans une table temporaire toutes les données liées à la cible, notamment les données issues des tables liées en FDA.

En cochant cette option, vous pouvez obtenir des performances nettement améliorées pour réaliser de la personnalisation.

Par exemple, si vous rencontrez des problèmes de performances lorsque vous diffusez des messages à un grand nombre de destinataires tout en utilisant un nombre important de champs de personnalisation et/ou de blocs de personnalisation dans le contenu de vos messages, cette option peut accélérer le traitement de la personnalisation et, par conséquent, la diffusion de vos messages.

Pour utiliser cette option, procédez comme suit :

1. Créez une campagne. Voir à ce propos [cette section](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. In the **[!UICONTROL Targeting and workflows]** tab of your campaign, add a **Query** activity to your workflow. For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. Ajoutez une **[!UICONTROL Email delivery]** activité au processus et ouvrez-la. For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. Accédez à l’ **[!UICONTROL Analysis]** onglet de la **[!UICONTROL Delivery properties]** et sélectionnez l’ **[!UICONTROL Prepare the personalization data with a workflow]** option.

   ![](assets/perso_optimization.png)

1. Configurez la diffusion et démarrez le workflow afin de lancer l&#39;analyse.

Une fois l&#39;analyse terminée, les données de personnalisation sont stockées dans une table temporaire via un workflow technique temporaire créé à la volée lors de l&#39;analyse.

Ce workflow n&#39;est pas visible dans l&#39;interface d&#39;Adobe Campaign. Il s&#39;agit uniquement d&#39;un moyen technique permettant de stocker et de traiter rapidement les données de personnalisation.

Une fois l’analyse terminée, accédez au processus **[!UICONTROL Properties]** et sélectionnez l’ **[!UICONTROL Variables]** onglet. Vous pouvez y voir le nom de la table temporaire que vous pouvez utiliser pour effectuer un appel SQL afin d&#39;afficher les ID qu&#39;elle contient.

![](assets/perso_optimization_temp_table.png)

## Délai d’expiration de la phase de personnalisation {#timing-out-personalization}

Pour améliorer la protection de la diffusion, vous pouvez définir un délai d’expiration pour la phase de personnalisation.

Dans l’ **[!UICONTROL Delivery]** onglet de la **[!UICONTROL Delivery properties]**, sélectionnez une valeur maximale en secondes pour l’ **[!UICONTROL Maximum personalization run time]** option.

Lors de l’aperçu ou de l’envoi, si la phase de personnalisation dépasse la durée maximale définie dans ce champ, le processus est abandonné avec un message d’erreur et la diffusion échoue.

![](assets/perso_time-out.png)

La valeur par défaut est de 5 secondes.

Si vous définissez cette option sur 0, il n’y aura aucune limite de temps pour la phase de personnalisation.
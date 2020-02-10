---
title: Import et export d'audiences
seo-title: Import et export d'audiences
description: Import et export d'audiences
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Import et export d&#39;audiences{#importing-and-exporting-audiences}

## Importer une audience {#importing-an-audience}

L&#39;import d&#39;audiences/de segments depuis Audience Manager ou People core service dans Adobe Campaign peut être réalisé via les listes de destinataires.

1. Accédez au noeud **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** dans l’explorateur Adobe Campaign.
1. Dans la barre d’actions, sélectionnez **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. In the window that opens, click **[!UICONTROL Select a shared audience]** to go to the list of shared audiences/segments available from the other Adobe Experience Cloud solutions.
1. Sélectionnez l&#39;audience de votre choix puis validez. Les informations de l&#39;audience sélectionnée sont automatiquement renseignées.

   Notez que pour pouvoir importer une audience partagée, vous devez vous voir attribuer le **[!UICONTROL Audience library]** produit dans la console d’administration et être administrateur dans Audience Manager. Pour plus d&#39;informations à ce sujet, consultez la documentation relative à la [console d&#39;administration](https://helpx.adobe.com/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Select the AMC Data source from the **[!UICONTROL AMC Data source]** field to define the type of data expected.

   ![](assets/aam_import_audience_2.png)

1. Enregistrez l&#39;audience.

L&#39;audience est importée par l&#39;intermédiaire d&#39;un workflow technique. La liste importée contient des éléments réconciliables au moyen d&#39;une AMC Data source. Les éléments non reconnus par Adobe Campaign ne sont pas importés.

Le processus d&#39;import prend entre 24 et 36 heures pour se synchroniser lorsque les segments sont importés directement à partir de People core service ou d&#39;Audience Manager. Au terme de cette période, vous pourrez trouver et utiliser votre nouvelle audience dans Adobe Campaign.

>[!NOTE]
>
>Si vous importez des audiences d&#39;Adobe Analytics vers Adobe Campaign, celles-ci doivent d&#39;abord être partagées dans People core service ou Audience Manager. Ce processus prend entre 12 et 24 heures (temps venant s&#39;ajouter aux 24 à 36 heures requises pour la synchronisation avec Campaign).
>
>Dans ce cas spécifique, l&#39;échéance de partage d&#39;audience peut aller jusqu&#39;à 60 heures. Pour plus d&#39;informations sur le partage d&#39;audience Adobe Analytics dans People Core service et Audience manager, consultez cette [documentation](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html).

Lors de chaque synchronisation, les données de l&#39;audience sont entièrement remplacées. Seuls les segments peuvent être importés. Les données granulaires, notamment les paires clé-valeur, les caractéristiques et les règles ne sont pas prises en charge.

## Exporter une audience {#exporting-an-audience}

L&#39;export d&#39;une audience depuis Adobe Campaign vers People core service ou Audience Manager peut être réalisé à l&#39;aide d&#39;un workflow. La création et l&#39;utilisation d&#39;un workflow sont détaillées dans [ce document](../../workflow/using/building-a-workflow.md). Les audiences exportées sont enregistrées sous forme de segments dans People core service :

1. Créez un nouveau workflow de ciblage.
1. En utilisant les différentes activités à votre disposition, ciblez un ensemble de destinataires.
1. After the targeting, drag and drop an **[!UICONTROL Update shared audience]** activity, then open it.

   ![](assets/aam_export_example.png)

1. Définissez l’audience que vous souhaitez exporter via l’ **[!UICONTROL Select a shared audience]** option. Dans la fenêtre qui s’ouvre, vous pouvez sélectionner une audience existante ou en créer une nouvelle.

   Si vous sélectionnez une audience existante, seuls les nouveaux enregistrements seront ajoutés à l&#39;audience.

   Pour exporter votre liste de destinataires dans une nouvelle audience, renseignez le champ **[!UICONTROL Segment name]** puis cliquez sur **[!UICONTROL Create]** avant de sélectionner l&#39;audience nouvellement créée.

   Terminez l&#39;opération en cliquant sur la coche de validation située en haut à droite de la fenêtre, puis sur le bouton **[!UICONTROL OK]**.

1. Sélectionnez le type **[!UICONTROL AMC Data source]** de données attendu. Le schéma est déterminé automatiquement.

   ![](assets/aam_export_audience_activity.png)

1. Enregistrez l&#39;audience.

L&#39;audience est alors exportée. L&#39;activité de sauvegarde d&#39;audience a deux transitions sortantes. La transition principale contient les destinataires ayant été exportés avec succès. La transition complémentaire contient les destinataires n&#39;ayant pas pu être mappés avec un identifiant visiteur ou un declared ID.

La synchronisation entre Adobe Campaign et People core service prend entre 24 et 36 heures. Au terme de cette période, vous pourrez trouver votre nouvelle audience dans People core service et la réutiliser dans d&#39;autres solutions Adobe Experience Cloud. Pour plus d&#39;informations sur l&#39;utilisation d&#39;une audience partagée Adobe Campaign dans Adobe People core service, consultez cette [documentation](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html).

>[!NOTE]
>
>Pour pouvoir être réconciliés, les enregistrements doivent posséder un identifiant Adobe Experience Cloud (&#39;Visitor ID&#39; ou &#39;Declared ID&#39;). Les enregistrements ne disposant pas d&#39;un identifiant Adobe Experience Cloud sont ignorés lors de l&#39;export et de l&#39;import des audiences.


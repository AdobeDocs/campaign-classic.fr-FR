---
title: Paramétrer l'accès au rapport
seo-title: Paramétrer l'accès au rapport
description: Paramétrer l'accès au rapport
seo-description: null
page-status-flag: never-activated
uuid: d32d9805-f84f-457f-b37b-a8278642336a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: dd50ca25-8fa2-48fa-84cc-a63e476701a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Paramétrer l&#39;accès au rapport{#configuring-access-to-the-report}

## Contexte d&#39;affichage des rapports {#report-display-context}

Définissez le contexte d’affichage du rapport dans la plateforme Adobe Campaign à l’aide de l’ **[!UICONTROL Display]** onglet. L’accès à un rapport dépend du type de sélection, des conditions d’affichage et des autorisations d’accès.

### Type de sélection {#selection-type}

L’accès au rapport peut être limité à un contexte spécifique ou à un espace d’offre, par exemple une remise, un destinataire, une sélection de destinataires, etc. Cet accès est configuré dans la **[!UICONTROL Selection type]** section de l’ **[!UICONTROL Display]** onglet.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : le rapport n&#39;est accessible que lorsqu&#39;une entité spécifique est sélectionnée.
* **[!UICONTROL Multiple selection]** : le rapport est accessible lorsque plusieurs entités sont sélectionnées.
* **[!UICONTROL Global]** : le rapport est accessible depuis la liste des rapports disponibles dans l&#39;univers Rapport.

### Ordre d&#39;affichage {#display-sequence}

The **[!UICONTROL Sequence]** field lets you enter a numeric value that specifies the display sequence of the report in the list.

Par défaut, les rapports sont affichés par pertinence : la valeur saisie dans ce champ permet de trier les rapports, du plus pertinent (valeur la plus grande), au moins pertinent (valeur la plus petite).

Vous pouvez choisir librement l&#39;échelle à utiliser, selon vos besoins. Par exemple de 1 à 10, de 0 à 100, de -10 à 10, etc.

### Conditions d&#39;affichage {#display-conditions}

Vous pouvez également conditionner l&#39;affichage du rapport à l&#39;aide d&#39;une requête.

![](assets/s_ncs_advuser_report_visibility_5.png)

Dans l&#39;exemple ci-dessous la condition d&#39;affichage est que le canal principal de l&#39;opération soit l&#39;email.

![](assets/s_ncs_advuser_report_visibility_6.png)

Donc si le canal principal de l&#39;opération est le canal courrier, le rapport ne sera pas proposé parmi les rapports de l&#39;opération.

### Autorisation d&#39;accès {#access-authorization}

Le rapport peut être partagé ou non avec d&#39;autres opérateurs.

Pour rendre le rapport accessible, sélectionnez l’ **[!UICONTROL Report shared with other operators]** option. Si cette option n’est pas sélectionnée, seul l’opérateur qui a créé le rapport peut accéder au rapport.

Le rapport peut également être partagé avec des opérateurs ou des groupes d&#39;opérateurs spécifiques qui sont ajoutés dans la fenêtre des autorisations.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Définir les options de filtrage {#defining-the-filtering-options}

The **[!UICONTROL Reports]** universe displays all available reports in the platform and for which the connected operator has an access right.

Par défaut, ils sont triés par pertinence mais vous pouvez appliquer d&#39;autres types de filtres : alphabétique, par ancienneté, etc.

Vous pouvez également filtrer l&#39;affichage selon la catégorie du rapport :

![](assets/report_ovv_select_type.png)

To define the category of a report, select it via the **[!UICONTROL Display]** tab, as shown below:

![](assets/report_select_category.png)

Vous pouvez y saisir une nouvelle catégorie pour l&#39;ajouter dans la liste des catégories disponibles. L&#39;énumération correspondante est alors automatiquement mise à jour.

## Création d&#39;un lien vers un rapport {#creating-a-link-to-a-report-}

Vous pouvez faire en sorte qu&#39;un rapport soit accessible depuis un noeud spécifique de l&#39;arborescence comme une liste, un destinataire, une diffusion etc. Pour cela, il suffit de créer un lien vers le rapport concerné et de spécifier l&#39;entité dans laquelle il doit être disponible.

A titre d&#39;exemple, nous allons créer un lien vers un rapport afin qu&#39;il soit accessible depuis une liste de destinataires.

1. Cliquez sur **[!UICONTROL New]** puis sélectionnez **[!UICONTROL Create a link to an existing report]** dans l’assistant de création de rapports.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Sélectionnez le rapport vers lequel vous souhaitez créer un lien à l&#39;aide de la liste déroulante. Dans notre exemple nous sélectionnons le rapport **Répartition par pays**.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Précisez un libellé et choisissez le schéma. Dans notre exemple nous choisissons la table des listes de destinataires.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Cela signifie que ce rapport sera accessible depuis n&#39;importe quelle liste de destinataires et que les statistiques seront effectuées sur les destinataires contenus dans la liste sélectionnée.

1. Enregistrez et affichez votre rapport.
1. Renseignez la clé de liaison. Dans notre exemple il s&#39;agit de la Clé étrangère du lien &#39;Dossier&#39;.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Publiez votre rapport.
1. Go to one of your recipient lists and click the **[!UICONTROL Reports]** link: the report you have just created is accessible.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Aperçu du rapport {#preview-of-the-report}

Before publishing your report, make sure it is displayed correctly in the **[!UICONTROL Preview]** tab.

![](assets/s_ncs_advuser_report_preview_01.png)

To display the preview of the report, select the **[!UICONTROL Global]** or the **[!UICONTROL Selection]** option.

Ces deux options sont sélectionnées en fonction des paramètres d’affichage du rapport. Si le paramètre d’affichage est défini **[!UICONTROL Global]**, vous devez sélectionner l’option **[!UICONTROL Global]** Aperçu. Si les paramètres d’affichage sont **[!UICONTROL Single selection]** ou **[!UICONTROL Multiple selection]**, l’option **[!UICONTROL Selection]** d’aperçu doit être sélectionnée.

Pour plus d&#39;informations sur ce sujet, reportez-vous au contexte [d&#39;affichage des](#report-display-context)rapports.

Vous disposez également de paramètres qui vous permettent de contrôler les erreurs. Le paramètre **_uuid** est présent dans l&#39;URL du rapport. Vous pouvez lui adjoindre les paramètres **&amp;_preview** ou **&amp;_debug**.

Pour plus d&#39;informations sur ces paramètres, consultez la section **Définir les propriétés d&#39;un formulaire web** du chapitre [Formulaires Web](../../web/using/about-web-forms.md).

## Publication du rapport {#publishing-the-report}

La publication du rapport est obligatoire pour le partager avec d’autres opérateurs et l’afficher dans la liste des rapports disponibles (reportez-vous également au contexte [d’affichage des](#report-display-context)rapports). Cette opération doit être exécutée à nouveau chaque fois que le rapport est modifié.

1. Open the publishing wizard by clicking **[!UICONTROL Publish]** in the toolbar.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Cliquez sur **[!UICONTROL Start]** pour publier.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Click the **[!UICONTROL Enlarge]** icon to open the report in a web browser.


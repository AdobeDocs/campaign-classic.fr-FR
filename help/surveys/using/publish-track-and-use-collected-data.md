---
product: campaign
title: Publier, suivre et utiliser les données collectées
description: Découvrez comment publier, suivre et utiliser les données collectées dans un questionnaire
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
TQID: https://experienceleague.adobe.com/5faTMQayKA-bxeGrKlNlk7fxZUV2-TO-eVCSe3iRrgA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 917
ht-degree: 67%

---

# Publier, suivre et utiliser les données collectées{#publish-track-and-use-collected-data}



Une fois que le formulaire a été créé, paramétré et publié, vous pouvez partager le lien avec votre audience et suivre les réponses.

>[!NOTE]
>
>Le cycle de vie d’un questionnaire sous Adobe Campaign ainsi que ses modes de publication et de diffusion sont similaires à ceux d’un formulaire web : ils sont présentés dans [cette section](../../web/using/about-web-forms.md).

## Tableau de bord du questionnaire {#survey-dashboard}

Chaque questionnaire possède son propre tableau de bord qui permet de visualiser son statut, sa description, son URL publique et son planning de disponibilité. Il permet également de visualiser les rapports disponibles. [En savoir plus](#reports-on-surveys).

L&#39;URL publique du questionnaire est affichée dans le tableau de bord :

![](assets/survey_public_url.png)

## Suivre les réponses {#response-tracking}

Vous pouvez suivre les réponses au questionnaire dans les logs et dans les rapports.

### Les logs de questionnaires {#survey-logs}

Pour chaque questionnaire diffusé, vous pouvez tracker les réponses dans l&#39;onglet **[!UICONTROL Logs]**. Cet onglet affiche la liste des utilisateurs ayant répondu au questionnaire et leur origine :

![](assets/s_ncs_admin_survey_logs.png)

Double-cliquez sur une ligne pour afficher le formulaire rempli par le participant. Vous pouvez parcourir le questionnaire dans son intégralité et accéder aux réponses dans leur intégralité. Ils peuvent être exportés dans un fichier externe. Voir à ce sujet la section [Exporter les réponses](#exporting-answers).

L&#39;origine est une information indiquée dans l&#39;URL du questionnaire en y ajoutant les caractères suivants :

```
?origin=xxx
```

pendant la modification du questionnaire, son URL contient le paramètre __uuid ]**, qui indique qu&#39;il est en phase de test et pas encore en ligne.**[!UICONTROL  Lorsque vous accédez au questionnaire via cette URL, les enregistrements créés ne sont pas pris en compte dans le suivi (rapports). L&#39;origine est alors forcée à la valeur **[!UICONTROL Adobe Campaign]**.

Pour plus d&#39;informations sur les paramètres d&#39;URL, consultez [cette page](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Les rapports sur les questionnaires {#reports-on-surveys}

L&#39;onglet Tableau de bord permet d&#39;accéder aux rapports du questionnaire. Cliquez sur le nom d’un rapport pour l’afficher.

![](assets/s_ncs_admin_survey_report_doc.png)

La structure du questionnaire est synthétisée dans le rapport **[!UICONTROL Documentation]**.

Deux autres rapports sur les questionnaires Web sont également disponibles par défaut dans l&#39;onglet **[!UICONTROL Rapports]** des questionnaires : **[!UICONTROL Général]** et **[!UICONTROL Répartition des réponses]**.

* Général

  Ce rapport regroupe des informations générales sur le questionnaire : l&#39;évolution du nombre de réponses dans le temps, la répartition par origines et par langues.

  Exemple de rapport général :

  ![](assets/s_ncs_admin_survey_report_0.png)

* Répartition des réponses

  Ce rapport permet de consulter la répartition des réponses pour chaque question. Cette répartition n&#39;est disponible que pour les réponses fournies à des champs stockés dans des conteneurs de type **[!UICONTROL Question]**. Elle n&#39;est valable que pour les contrôles de sélection (pas de répartition sur les champs de type texte, par exemple).

  ![](assets/s_ncs_admin_survey_report_2.png)

## Exporter les réponses {#exporting-answers}

Les réponses à un questionnaire peuvent être exportées dans un fichier externe afin d&#39;être réexploitées ultérieurement. Vous avez le choix entre les deux méthodes suivantes :

1. Exporter les données d&#39;un rapport

   Pour exporter les données d&#39;un rapport, cliquez sur le bouton **[!UICONTROL Exporter]** et sélectionnez le format d&#39;export.

   L&#39;export des données d&#39;un rapport est présenté dans [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

1. Exporter les réponses

   Pour exporter les réponses, cliquez sur l&#39;onglet **[!UICONTROL Réponses]** du questionnaire et cliquez avec le bouton droit de la souris. Choisissez **[!UICONTROL Exporter...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Indiquez ensuite les informations à exporter et le fichier d’enregistrement.

   Vous pouvez configurer le contenu et le format du fichier de sortie dans l’assistant d’export.

   Ainsi, vous pouvez :

   * ajouter des colonnes supplémentaires dans le fichier de sortie et ainsi récupérer les informations stockées en base relatives au destinataire,
   * appliquer un formatage sur les données exportées,
   * sélectionner le format d&#39;encodage des informations dans le fichier.

   Si le questionnaire que vous souhaitez exporter contient plusieurs champs **[!UICONTROL Texte multi-lignes]** ou **[!UICONTROL Texte HTML]**, il doit être exporté au format **[!UICONTROL XML]**. Pour ce faire, sélectionnez ce format dans la liste déroulante du champ **[!UICONTROL Format de sortie]**, comme illustré ci-dessous :

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Cliquez sur **[!UICONTROL Démarrer]** pour lancer l&#39;export.

   >[!NOTE]
   >
   >Le déroulement d&#39;un export de données et les étapes de son paramétrage sont détaillés dans [cette section](../../platform/using/about-generic-imports-exports.md).

## Utiliser les données collectées {#using-the-collected-data}

Les informations collectées au travers des questionnaires en ligne peuvent être récupérées dans le cadre d&#39;un workflow de ciblage. Pour cela, utilisez la boîte **[!UICONTROL Réponses à un questionnaire]**.

Dans l&#39;exemple suivant, nous allons proposer une offre web dédiée aux cinq destinataires ayant au moins deux enfants et ayant obtenu les scores les plus élevés dans le cadre d&#39;un questionnaire en ligne. Les réponses à cette enquête sont les suivantes :

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

Dans le workflow de ciblage, la boîte **[!UICONTROL Réponses à un questionnaire]** sera paramétrée comme suit :

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Sélectionnez d&#39;abord l&#39;enquête concernée puis les données à extraire dans la partie centrale de la fenêtre. Dans ce cas, nous devons extraire au moins la colonne de score, car elle sera utilisée dans la boîte de partage pour récupérer les cinq scores les plus élevés.

Indiquez les conditions de filtrage des réponses en cliquant sur le lien **[!UICONTROL Editer la requête...]**.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Démarrez le workflow de ciblage. La requête récupère 8 destinataires.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Cliquez avec le bouton droit de la souris sur la transition sortante de la boîte de collecte pour les visualiser.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Positionnez ensuite dans le workflow une boîte de partage afin de ne récupérer que les 5 destinataires ayant obtenu le meilleur score.

Editez la boîte de partage pour la paramétrer :

* Sélectionnez d&#39;abord le schéma adéquat dans l&#39;onglet **[!UICONTROL Général]** avant de paramétrer le sous-ensemble :

  ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Dans l&#39;onglet **[!UICONTROL Sous-ensembles]**, sélectionnez l&#39;option **[!UICONTROL Limiter les enregistrements sélectionnés]** puis cliquez sur le lien **[!UICONTROL Editer...]**.

  ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Sélectionnez l&#39;option **[!UICONTROL Conserver les premiers suite à un tri]** et indiquez la colonne de tri. Cochez l&#39;option **[!UICONTROL Tri descendant]**.

  ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Cliquez sur le bouton **[!UICONTROL Suivant]** et limitez le nombre d&#39;enregistrements à 5.

  ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Cliquez sur **[!UICONTROL Terminer]** puis redémarrez le workflow pour valider le ciblage.

## Normaliser les données {#standardizing-data}

Il est possible de configurer des processus de normalisation dans Adobe Campaign pour les données collectées à l’aide d’alias. Vous pouvez ainsi standardiser les données stockées dans la base : pour cela, définissez des alias dans les énumérations qui contiennent les informations nécessaires. Découvrez comment **utiliser les énumérations** dans la [documentation d’Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.
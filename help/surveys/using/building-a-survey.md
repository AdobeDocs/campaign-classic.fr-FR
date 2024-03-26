---
product: campaign
title: Conception d’un questionnaire
description: Découvrez les étapes clés de la conception d'un questionnaire
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: Surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 71%

---

# Conception d’un questionnaire{#building-a-survey}



## Créer un nouveau questionnaire {#creating-a-new-survey}

Le chapitre suivant présente les étapes de conception d&#39;un formulaire de type **Questionnaire** sous Adobe Campaign, ainsi que les options et paramétrages disponibles. Adobe Campaign permet de mettre ce questionnaire à disposition des utilisateurs, et de collecter et archiver les réponses dans la base de données.

Les formulaires web sont accessibles à partir de **[!UICONTROL Ressources > On > Applications Web]** du noeud de l’arborescence. Pour créer un questionnaire, cliquez sur le bouton **[!UICONTROL Nouveau]** au-dessus de la liste des applications, ou cliquez avec le bouton droit de la souris dans la liste et choisissez **[!UICONTROL Nouveau]**.

Choisissez le modèle de questionnaire (par défaut **[!UICONTROL newSurvey]**).

![](assets/s_ncs_admin_survey_select_template.png)

Les pages du formulaire sont créées au travers d&#39;un éditeur spécifique qui permet de définir et paramétrer des zones de saisie (textes), des champs de sélection (listes, cases à cocher, etc.) et des éléments statiques (images, contenus HTML, etc.). Ils peuvent être regroupés dans des conteneurs et mis en page selon vos besoins. [En savoir plus](#adding-questions)).

>[!NOTE]
>
>La définition du contenu et de la mise en page des écrans d&#39;un formulaire web sont présentés dans [ce document ](../../web/using/about-web-forms.md).

## Ajouter des champs {#adding-fields}

Les champs d’un formulaire permettent aux utilisateurs de saisir des informations et de sélectionner des options. Pour chaque page du formulaire, elles sont créées à partir du premier bouton de la barre d&#39;outils, à partir du **[!UICONTROL Ajouter à l’aide de l’assistant]** .

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>Vous pouvez également utiliser le bouton droit de la souris pour insérer une zone de saisie. Par défaut, la zone est toujours insérée à la fin de l&#39;arborescence courante. Elle peut être déplacée en utilisant les flèches de la barre d&#39;outils.

### Types de champs {#types-of-fields}

Lorsque vous ajouter un champ dans un questionnaire, vous devez sélectionner le type de champ à ajouter. Les options suivantes sont disponibles :

1. **[!UICONTROL Répondre à une question]**: cette option permet de déclarer un nouveau champ (appelé &quot;champ archivé&quot;) afin de stocker les réponses. Dans ce cas, toutes les valeurs collectées sont enregistrées, même lorsqu’un participant remplit le formulaire plusieurs fois. Ce mode de stockage n’est disponible que dans **Questionnaires**. [En savoir plus](../../surveys/using/managing-answers.md#storing-collected-answers).
1. **[!UICONTROL Éditer un destinataire]** : cette option permet de sélectionner un champ de la base de données. Dans ce cas, les réponses des utilisateurs seront stockées dans ce champ. Pour chaque participant, seule la dernière valeur saisie est conservée. Elle est ajoutée aux données de son profil.
1. **[!UICONTROL Ajouter une variable]** : cette option permet de ne pas conserver les informations dans la base de données. Les variables locales peuvent être déclarées en amont. Vous pouvez également en ajouter directement lors de la création du champ.
1. **[!UICONTROL Importer une question existante]** : cette option permet d’importer des questions existantes, créées dans d’autres questionnaires.

   >[!NOTE]
   >
   >Les modes de stockage ainsi que l&#39;import de champs sont présentés dans [cette section](../../surveys/using/managing-answers.md#storing-collected-answers).

La nature du champ à ajouter (liste déroulante, champ de texte, cases à cocher, etc.) s’adapte au mode de stockage sélectionné. Vous pouvez la modifier à l’aide de la fonction **[!UICONTROL Type]** du champ **[!UICONTROL Général]** , mais assurez-vous de rester cohérent avec le type de données.

![](assets/s_ncs_admin_survey_change_type.png)

Les différents types de champs disponibles sont présentés dans [cette section](../../web/using/about-web-forms.md).

## Éléments spécifiques aux questionnaires {#survey-specific-elements}

Les questionnaires en ligne reposent sur les fonctionnalités des applications web. Les fonctionnalités spécifiques à un questionnaire sont présentées ci-dessous.

### Choix multiples {#multiple-choice}

Pour **[!UICONTROL Choix multiples]** des contrôles de type , vous pouvez définir un nombre minimal et maximal de sélections. Par exemple, cette option vous permet de forcer la sélection au moins pour **2** et au plus **4** des options disponibles :

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Si le nombre de sélections n&#39;est pas atteint ou s&#39;il est dépassé, le message correspondant sera affiché.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>Dans ce cas, les options sont sélectionnées via des cases à cocher. Lorsqu&#39;un seul choix est possible, il s&#39;agit de boutons radio.

Le paramétrage correspondant sera le suivant :

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

De plus, l&#39;espace de stockage pour ce champ de saisie doit être un **champ archivé** de type **[!UICONTROL Valeurs Multiples]** :

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Cette fonctionnalité n&#39;est disponible que dans les formulaires de type **Questionnaires**.
>* Cette option n’est pas compatible avec l’affichage de questions aléatoires. [En savoir plus](#adding-questions).

### Ajouter des questions {#adding-questions}

Les conteneurs peuvent être de deux types : standard ou question. Les conteneurs standards sont utilisés à des fins de mise en page et pour paramétrer un affichage conditionnel dans une page. [En savoir plus](../../web/using/about-web-forms.md).

Utilisez un conteneur de type **Question** pour ajouter une question dans la page et insérer les réponses possibles en sous-arborescence. Les réponses des utilisateurs aux questions qui ont été positionnées dans ce type de conteneurs peuvent être analysées dans des rapports.

>[!CAUTION]
>
>Vous ne devez pas insérer un conteneur de type **Question** en sous arborescence d&#39;un autre conteneur de type **Question**.

![](assets/s_ncs_admin_question_label.png)

Le libellé de la question est saisi dans le champ libellé. Dans ce cas, le style de la feuille de style du formulaire est appliqué. Sélectionnez la variable **[!UICONTROL Saisissez le titre au format HTML]** pour la personnaliser. Vous aurez ainsi accès à l’éditeur de HTMLS.

>[!NOTE]
>
>L&#39;utilisation de l&#39;éditeur HTML est présentée dans [ce document ](../../web/using/about-web-forms.md).

Par exemple :

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

Dans l&#39;exemple ci-dessus, le rendu sera le suivant :

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Chaque question correspond à un conteneur de type **Question**.

Vous pouvez activer le tirage aléatoire des questions par Adobe Campaign. Il est ensuite possible d&#39;indiquer le nombre de questions à afficher dans la page, dans le champ situé en bas de la fenêtre de configuration.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

Le rendu sera par exemple :

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

Lorsque la page est actualisée, les questions affichées ne sont pas les mêmes.

>[!CAUTION]
>
>Lorsque vous affichez aléatoirement telle ou telle question (option **[!UICONTROL Tirage aléatoire des questions]** cochée au niveau de la page), vous devez veiller à ne pas utiliser dans ces questions des listes à choix multiples dans lesquelles une ou plusieurs sélections sont obligatoires.

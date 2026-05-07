---
product: campaign
title: Définir les propriétés des formulaires web
description: Définir les propriétés des formulaires web
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: 1d4990917fea54e67ed23cd0771295de03a4f01a
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 67%

---

# Définir les propriétés des formulaires web{#defining-web-forms-properties}



Vous pouvez configurer et personnaliser entièrement les formulaires web pour répondre à vos besoins. Les paramètres doivent être renseignés dans la fenêtre des propriétés.

La fenêtre des propriétés est accessible à partir du bouton **[!UICONTROL Propriétés]** situé dans la barre d&#39;outils du formulaire Web. Cette fenêtre permet d&#39;accéder à un ensemble de paramètres spécifiques au formulaire Web. Certains paramètres peuvent provenir de la configuration du modèle.

![](assets/s_ncs_admin_survey_properties_general.png)

## Propriétés générales du formulaire {#overall-form-properties}

Dans l&#39;onglet **[!UICONTROL Général]** de la fenêtre des propriétés, vous pouvez modifier le **Libellé** du formulaire. Il est fortement déconseillé de modifier le **Nom interne**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

Le modèle de formulaire est choisi lors de la création du formulaire. Elle ne peut pas être modifiée ultérieurement. Pour plus d’informations sur la création et la gestion des modèles de formulaire, voir [Utiliser un modèle de formulaire web](using-a-web-form-template.md).

## Stockage des données d&#39;un formulaire {#form-data-storage}

Par défaut, les champs des formulaires Web sont stockés dans la table des destinataires. Vous pouvez modifier la table utilisée en sélectionnant une nouvelle table dans le champ **[!UICONTROL Type de document]**. L&#39;icône **[!UICONTROL Loupe]** permet de visualiser le contenu du tableau sélectionné.

Les réponses fournies sont stockées par défaut dans la table **Réponse à un formulaire d&#39;un destinataire**.

## Paramétrer une page d&#39;erreur {#setting-up-an-error-page}

Vous pouvez paramétrer une page d&#39;erreur : cette page est affichée en cas d&#39;erreur lors de l&#39;exécution du formulaire.

La page d&#39;erreur est définie dans l&#39;onglet correspondant de la fenêtre des propriétés du formulaire.

Par défaut, elle affiche les informations suivantes :

![](assets/s_ncs_admin_survey_default_error_page.png)

Le contenu des chaînes affichées est défini dans l&#39;onglet **[!UICONTROL Page d’erreur]** de la fenêtre des propriétés. L’onglet **[!UICONTROL HTML]** affiche le rendu, tandis que l’onglet **[!UICONTROL Textes]** vous permet de modifier les chaînes de texte et d’ajouter du texte si nécessaire :

![](assets/s_ncs_admin_survey_error_page.png)

## Localisation d&#39;un formulaire {#form-localization}

L&#39;onglet **[!UICONTROL Localisation]** permet de sélectionner les langues de conception et d&#39;affichage du formulaire Web.

Voir [Traduire un formulaire web](translating-a-web-form.md).

## Navigation dans un formulaire et rendu {#form-browsing-and-rendering}

L&#39;onglet **[!UICONTROL Rendu]** permet de définir le type de navigation entre les pages du formulaire Web et le modèle de rendu utilisé.

Vous pouvez choisir de naviguer via des liens ou des boutons.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Par défaut, les boutons constituent les éléments de navigation. Elles permettent d’effectuer les actions suivantes :

* Valider la page courante et afficher la page suivante en cliquant sur **[!UICONTROL Suivant]**. Ce bouton s’affiche sur toutes les pages, à l’exception de la dernière.
* Affichez la page précédente en cliquant sur **[!UICONTROL Précédent]**. Ce bouton s’affiche sur toutes les pages, à l’exception de la première.
* Enregistrez les réponses du formulaire en cliquant sur le bouton **[!UICONTROL Approuver]**. Ce bouton ne s&#39;affiche que sur la dernière page.

Ces éléments sont affichés au bas de chaque page. Leurs positions peuvent être modifiées. Pour ce faire, vous devez modifier la feuille de style.

>[!NOTE]
>
>Le bouton **[!UICONTROL Précédent]** peut être masqué sur certaines pages. Pour cela, cochez l&#39;option **[!UICONTROL Ne pas autoriser le retour à la page précédente]** dans la page concernée. Cette option est accessible lorsque la racine de l&#39;arborescence de la page est sélectionnée.

Le champ **[!UICONTROL Modèle]** de l&#39;onglet **[!UICONTROL Rendu]** permet de sélectionner un thème parmi ceux disponibles.

Les thèmes sont enregistrés dans le nœud **[!UICONTROL Administration > Configuration > Rendus des formulaires]** de l’arborescence. Voir [Choisir le modèle de rendu du formulaire](form-rendering.md#selecting-the-form-rendering-template).

Un exemple de rendu est affiché dans la section inférieure de la fenêtre des propriétés. L&#39;icône **[!UICONTROL Editer le lien]** permet de visualiser le paramétrage correspondant au thème sélectionné.

![](assets/s_ncs_admin_survey_properties_render.png)

## Logo dans le formulaire {#logo-in-the-form}

Vous pouvez remplacer le logo utilisé dans le formulaire par votre propre logo.

Dans l’onglet **[!UICONTROL Rendu]** dans les **[!UICONTROL propriétés]** de votre application web, cliquez sur l’icône en forme de loupe de votre modèle :

![](assets/logo_glass.png)

Dans la nouvelle fenêtre, cliquez sur le lien **[!UICONTROL Mise en page]** :

![](assets/logo_pagelayout.png)

Vous aurez la possibilité de modifier le chemin de l’image du logo ici :

![](assets/logo_path.png)

Les images disponibles se trouvent sous **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]**. Vous pouvez ajouter votre logo ici.

Ces images sont placées dans le répertoire back-end de l’instance. *datakit\nms\fra\img\activities* ou *datakit\nms\eng\img\activities* (eng ou fra, selon la langue de l’instance).

Pour qu’une nouvelle image soit disponible dans ce répertoire (et dans Images), contactez le support Adobe pour apporter des modifications aux répertoires back-end.

Pour les instances sur site, vous pouvez ajouter vous-même des images au datakit.

Il n’est pas nécessaire que l’image chargée soit visible à partir du client Campaign. Le chemin correct est suffisant pour être utilisé comme nouveau logo.

## Textes du formulaire {#texts-in-the-form}

L&#39;onglet **[!UICONTROL Page]** permet de définir le contenu de l’en-tête et du pied de page du formulaire. Voir [Définir les en-têtes et pieds de page](form-rendering.md#defining-headers-and-footers).

Il permet aussi de gérer les traductions. Voir [Traduire un formulaire web](translating-a-web-form.md).

## Accessibilité du formulaire {#accessibility-of-the-form}

Un formulaire web est accessible aux utilisateurs s’il est **[!UICONTROL En ligne]** et si la date actuelle est comprise dans sa période de validité. Le statut du formulaire est modifié au cours de l’étape de publication (voir [Publier un formulaire](publishing-a-web-form.md#publishing-a-form)). Le statut s’affiche dans la section **Projet** de l’onglet **[!UICONTROL Général]** de la fenêtre des propriétés.

La période de validité s’étend de la date de **[!UICONTROL début]** à la date de **[!UICONTROL fin]**. Si aucune date n’est spécifiée dans ces champs, le formulaire a une validité permanente.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>Si le formulaire est fermé, donc si sa période de validité n&#39;est pas atteinte ou est dépassée, ou s&#39;il a été fermé par l&#39;opérateur Adobe Campaign, alors un message s&#39;affiche lorsque l&#39;utilisateur tente d&#39;y accéder. Vous pouvez personnaliser ce message en cliquant sur le lien **[!UICONTROL Personnaliser le message affiché si le formulaire est fermé...]**.

## Contrôle d&#39;accès au formulaire {#form-access-control}

Par défaut, l&#39;accès aux formulaires Web se fait en mode anonyme : tous les opérateurs qui accèdent au formulaire se voient attribuer les droits correspondant à l&#39;opérateur WebApp.

Vous pouvez activer le contrôle d’accès pour l’affichage du formulaire, par exemple lorsque vous diffusez un formulaire sur un site intranet, afin d’authentifier les utilisateurs et utilisatrices. Pour ce faire, affichez la variable **[!UICONTROL Propriétés]** du formulaire concerné et cliquez sur l’option **[!UICONTROL Activer le contrôle d’accès]**, comme illustré ci-dessous :

![](assets/s_ncs_admin_survey_access_ctrl.png)

Lors de l&#39;accès au formulaire, la page d&#39;authentification suivante sera affichée :

![](assets/s_ncs_admin_survey_access_login.png)

Les login et mot de passe sont ceux des opérateurs Adobe Campaign. Pour plus d’informations, consultez [cette section](../../platform/using/access-management.md).

L&#39;option **[!UICONTROL Utiliser un compte spécifique]** permet de limiter les droits en lecture ou écriture de l&#39;opérateur accédant au formulaire. Utilisez la liste déroulante pour sélectionner un opérateur ou un groupe d’opérateurs qui sera chargé d’accorder ces autorisations.

![](assets/s_ncs_admin_survey_access_op_select.png)

## Paramètres d&#39;URL de formulaire {#form-url-parameters}

Vous pouvez ajouter des paramètres supplémentaires dans l’URL d’un formulaire afin d’en personnaliser le contenu et d’initialiser un contexte (langue, identifiant de destinataire chiffré, société, formule calculée stockée dans une variable, etc.). Vous pouvez ainsi donner accès à un formulaire via plusieurs URL différentes et personnaliser le contenu des pages en fonction de la valeur du ou des paramètres indiqués dans l’URL.

Par défaut, Adobe Campaign propose des paramètres pour prévisualiser le formulaire et vérifier les erreurs. Vous pouvez créer de nouveaux paramètres liés au formulaire, qui pourront utiliser les valeurs d&#39;un champ de la base de données ou d&#39;une variable locale.

## Paramètres standards {#standard-parameters}

Par défaut, les paramètres suivants sont disponibles :

* **Id** pour indiquer l’identifiant chiffré.
* **lang** pour modifier la langue d&#39;affichage.
* **origin** pour indiquer l&#39;origine du répondant.
* **_uuid** permet l’affichage des formulaires avant publication et le suivi des erreurs. Ce paramètre est destiné à une utilisation interne (création et débogage) : lorsque vous accédez au formulaire Web via cette URL, les enregistrements créés ne sont pas pris en compte dans le suivi (rapports). L&#39;origine est alors forcée à la valeur **[!UICONTROL Adobe Campaign]**.

  S&#39;utilise avec les paramètres **_preview** et/ou **_debug** :

  **_preview** pour afficher la dernière version enregistrée. Ce paramètre ne doit être utilisé que lors de la phase de test.

  **_debug** pour afficher la trace de l&#39;entrée de données ou calculée dans les pages du formulaire. Cette fonctionnalité permet d’obtenir plus d’informations sur les erreurs, y compris une fois le formulaire publié.

  >[!CAUTION]
  >
  >Lorsque le formulaire est affiché via une URL avec le paramètre **_uuid**, la valeur du paramètre **[!UICONTROL origin]** est forcée à **Adobe Campaign**.

## Ajouter des paramètres {#adding-parameters}

Les paramètres peuvent être ajoutés à partir de l&#39;onglet **[!UICONTROL Paramètres...]** de la fenêtre des propriétés du formulaire. Elles peuvent être rendues obligatoires, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_admin_survey_properties_param.png)

Vous devez indiquer un espace de stockage d&#39;où sera récupérée la valeur du paramètre. Pour cela, sélectionnez une des options de stockage puis cliquez sur l&#39;onglet **[!UICONTROL Stockage]** pour sélectionner le champ ou la variable concernée. Les options de stockage sont détaillées dans les [Champs de stockage des réponses](web-forms-answers.md#response-storage-fields).

Le statut du répondant (0, 1 ou toute autre valeur) peut ensuite être ajouté à l’URL pour accéder au formulaire. Ces informations peuvent être réutilisées dans les pages du formulaire ou dans une boîte de test. Les pages affichées peuvent être conditionnées en fonction de la valeur du contexte, comme dans l&#39;exemple ci-dessous :

1. Page d&#39;accueil pour les clients (**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. Page d&#39;accueil pour les prospects (**status=0**) :

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. Page d&#39;accueil pour d&#39;autres profils (par exemple, **status =12**) :

   ![](assets/s_ncs_admin_survey_test_other.png)

Pour paramétrer ce formulaire, créez une boîte de test et positionnez-la au début du diagramme, comme suit :

![](assets/s_ncs_admin_survey_test.png)

La boîte de test permet de paramétrer les conditions d&#39;enchaînement des pages :

![](assets/s_ncs_admin_survey_test_box.png)

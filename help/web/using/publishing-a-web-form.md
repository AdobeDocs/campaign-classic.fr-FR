---
title: Publier un formulaire web
seo-title: Publier un formulaire web
description: Publier un formulaire web
seo-description: null
page-status-flag: never-activated
uuid: 37222829-1d56-438c-a4ca-878925debcb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: f4322902-c72d-4443-9c30-09add4c615a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Publier un formulaire web{#publishing-a-web-form}

## Précharger les données du formulaire {#pre-loading-the-form-data}

Si vous souhaitez mettre à jour les profils stockés en base via un formulaire web, vous pouvez utiliser une boîte de préchargement. La boîte de préchargement permet d&#39;indiquer comment retrouver l&#39;enregistrement à mettre à jour dans la base de données.

Les méthodes d&#39;identification possibles sont les suivantes :

* **[!UICONTROL Adobe Campaign Encryption]**

   Cette méthode de cryptage utilise l&#39;identifiant (ID) crypté par Adobe Campaign. Cette méthode n&#39;est applicable que sur un objet Adobe Campaign et l&#39;identifiant crypté ne peut être généré que par la plateforme Adobe Campaign.

   When using this method, you need to adapt the URL of the form to deliver to the email address by adding the **`<%=escapeUrl(recipient.cryptedId) %>`** parameter. Pour plus d’informations, reportez-vous à la section [Diffusion d’un formulaire par courrier électronique](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   Cette méthode de chiffrement utilise un identifiant (ID) fourni en externe, lié à une clé partagée par Adobe Campaign et le fournisseur externe. Le **[!UICONTROL Des key]** champ vous permet de saisir cette clé de chiffrement.

* **[!UICONTROL List of fields]**

   Cette option permet de sélectionner parmi les champs du contexte courant du formulaire, ceux qui seront utilisés pour retrouver le profil correspondant dans la base de données.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   Les champs peuvent être ajoutés aux propriétés du formulaire via l’ **[!UICONTROL Parameters]** onglet (voir [Ajout de paramètres](../../web/using/defining-web-forms-properties.md#adding-parameters)). Ils sont placés dans l’URL du formulaire ou dans les zones d’entrée.

   >[!CAUTION]
   >
   >Les données des champs sélectionnés ne sont pas chiffrées. Il ne doit pas être fourni sous forme chiffrée, car Adobe Campaign ne pourra pas le déchiffrer si l’ **[!UICONTROL Field list]** option est sélectionnée.

   Dans l&#39;exemple ci-dessous, le pré-chargement du profil est basé sur l&#39;adresse email.

   L&#39;URL peut contenir l&#39;adresse email en clair, auquel cas l&#39;utilisateur accède directement à la page qui le concerne.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   Dans le cas contraire, il devra fournir son mot de passe.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >Si plusieurs champs sont indiqués dans la liste, les données de **TOUS LES CHAMPS** doivent correspondre avec les informations stockées en base pour que le profil soit mis à jour. Dans le cas contraire, un nouveau profil est créé.
   > 
   >Cette fonctionnalité est particulièrement utile dans les applications Web mais n&#39;est pas recommandée dans les formulaires publics. L&#39;option de contrôle d&#39;accès sélectionnée doit être &quot;Activer le contrôle d&#39;accès&quot;.

Cette **[!UICONTROL Skip preloading if identification is empty]** option doit être sélectionnée si vous ne souhaitez pas mettre à jour les profils. Dans ce cas, chaque profil saisi sera ajouté à la base de données après approbation du formulaire. Cette option est utilisée, par exemple, lorsque le formulaire est publié sur un site Web.

Cette **[!UICONTROL Auto-load data referenced in the form]** option vous permet de précharger automatiquement les données qui correspondent aux champs d’entrée et de fusion dans le formulaire. Toutefois, les données référencées dans **[!UICONTROL Script]** et **[!UICONTROL Test]** les activités ne sont pas concernées. Si cette option n’est pas sélectionnée, vous devez définir les champs à l’aide de l’ **[!UICONTROL Load additional data]** option.

The **[!UICONTROL Load additional data]** option lets you add information which is not used in the pages of the form, but will nonetheless be preloaded.

Vous pouvez par exemple précharger le genre du destinataire et l&#39;orienter automatiquement vers la page correspondante via une boîte de test.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Gérer la diffusion et le tracking des formulaires web {#managing-web-forms-delivery-and-tracking}

Une fois le formulaire créé, configuré et publié, vous pouvez le diffuser et effectuer un tracking des réponses des utilisateurs.

### Cycle de vie d&#39;un formulaire {#life-cycle-of-a-form}

Le cycle de vie d&#39;un formulaire se décompose en trois étapes :

1. **Formulaire en édition**

   C&#39;est la phase de conception initiale. Lorsqu’un nouveau formulaire est créé, il est en phase de modification. L’accès au formulaire, à des fins de test uniquement, nécessite l’utilisation du paramètre **[!UICONTROL __uuid]** dans son URL. Cette URL est accessible dans le **[!UICONTROL Preview]** sous-onglet. Voir Paramètres [d’URL de](../../web/using/defining-web-forms-properties.md#form-url-parameters)formulaire.

   >[!CAUTION]
   >
   >Tant que le formulaire est en édition, son URL d&#39;accès est une URL spécifique.

1. **Formulaire en ligne**

   Une fois la phase de conception terminée, le formulaire peut être remis. Tout d&#39;abord, il doit être publié. Pour plus d’informations, reportez-vous à la section [Publication d’un formulaire](#publishing-a-form).

   The form will be **[!UICONTROL Live]** until it expires.

   >[!CAUTION]
   >
   >To be delivered, the URL of the survey must not contain the **[!UICONTROL __uuid]** parameter.

1. **Formulaire indisponible**

   Une fois la date de clôture du formulaire atteinte, la phase de diffusion est terminée et le formulaire est indisponible : il n&#39;est plus accessible aux utilisateurs.

   La date d’expiration peut être définie dans la fenêtre des propriétés du formulaire. Pour plus d’informations à ce sujet, voir [Mise à disposition d’un formulaire en ligne](#making-a-form-available-online)

L&#39;état de publication d&#39;un formulaire est affiché dans la liste des formulaires.

![](assets/s_ncs_admin_survey_status.png)

### Publier un formulaire {#publishing-a-form}

Pour modifier l’état d’un formulaire, vous devez le publier. Pour ce faire, cliquez sur le **[!UICONTROL Publication]** bouton au-dessus de la liste des formulaires Web et sélectionnez l’état dans la liste déroulante.

![](assets/webapp_publish_webform.png)

### Mettre un formulaire à disposition {#making-a-form-available-online}

Pour que les utilisateurs puissent y accéder, le formulaire doit être en production et démarré, c’est-à-dire pendant la période de validité. Les dates de validité sont saisies via le **[!UICONTROL Properties]** lien du formulaire.

* Use the fields in the **[!UICONTROL Project]** section to enter start and end dates for the form.

   ![](assets/webapp_availability_date.png)

* Cliquez sur le **[!UICONTROL Personalize the message displayed if the form is closed...]** lien pour définir le message d’erreur à afficher si l’utilisateur tente d’accéder au formulaire alors qu’il n’est pas valide.

   See [Accessibility of the form](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form).

### Diffuser un formulaire par email {#delivering-a-form-via-email}

Lorsque vous envoyez une invitation par courrier électronique, vous pouvez utiliser l’ **[!UICONTROL Adobe Campaign Encryption]** option de rapprochement des données. Pour ce faire, accédez à l’assistant de remise et adaptez le lien au formulaire en ajoutant le paramètre suivant :

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

Dans ce cas, la clé de rapprochement pour le stockage des données doit être l’identifiant chiffré du destinataire. Pour plus d’informations, reportez-vous à la section [Préchargement des données](#pre-loading-the-form-data)de formulaire.

Dans ce cas, vous devez cocher l’ **[!UICONTROL Update the preloaded record]** option dans la zone d’enregistrement. Pour plus d&#39;informations, reportez-vous à la section [Enregistrement des réponses](../../web/using/web-forms-answers.md#saving-web-forms-answers)aux formulaires Web.

![](assets/s_ncs_admin_survey_save_box_option.png)

### Log responses {#log-responses}

Le suivi des réponses peut être activé dans un onglet dédié pour surveiller l&#39;impact de votre formulaire Web. Pour ce faire, cliquez sur le **[!UICONTROL Advanced parameters...]** lien dans la fenêtre des propriétés du formulaire et sélectionnez l’ **[!UICONTROL Log responses]** option.

![](assets/s_ncs_admin_survey_trace.png)

The **[!UICONTROL Responses]** tab appears to let you view the identity of respondents.

![](assets/s_ncs_admin_survey_trace_tab.png)

Select a recipient and click the **[!UICONTROL Detail...]** button to view the responses provided.

![](assets/s_ncs_admin_survey_trace_edit.png)

Vous pouvez exploiter les traces des réponses fournies dans des requêtes, par exemple pour cibler uniquement les non-répondants dans le cadre d&#39;une relance ou proposer des communications spécifiques aux seuls répondants.

>[!NOTE]
>
>Pour réaliser un tracking complet des réponses fournies, exporter les réponses et consulter ou créer des rapports dédiés, vous devez utiliser le module optionnel **Questionnaire** (survey). Voir à ce sujet [cette section](../../web/using/about-surveys.md).


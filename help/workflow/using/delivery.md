---
title: Delivery
seo-title: Delivery
description: Delivery
seo-description: null
page-status-flag: never-activated
uuid: 3a74fd0b-8598-46a0-bf13-cf35db0987d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9fd7122e-22c7-4f9a-a2a4-5de3daaa3c2e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 366d2149933fa68dfec2a732d1014e1875709cff

---


# Diffusion{#delivery}

Une activité de type **Diffusion** permet de créer une action de diffusion. Elle peut être construite à partir des éléments entrants.

Pour la paramétrer, éditez l&#39;activité et renseignez les options de la diffusion.

![](assets/edit_diffusion.png)

1. **Diffusion**

   Vous pouvez ainsi :

   * Agissez sur le  spécifié dans le entrant . Pour ce faire, sélectionnez la première option de la **[!UICONTROL Delivery]** section de la fenêtre.

      Cette option peut être utilisée lorsqu&#39;une activité précédente du workflow a déjà créé ou spécifié la diffusion. Cela peut avoir été effectué, comme dans l&#39;exemple ci-dessous, par une activité du même type ayant généré une transition sortante.

      Dans l&#39;exemple suivant, la diffusion est créée dans un premier temps. La population et le contenu sont définis ensuite. Enfin, les informations de ces trois éléments sont reprises dans une nouvelle activité de diffusion via la transition entrante, afin que cette dernière puisse être envoyée.

      ![](assets/specified_transition_option_exemple.png)

   * Sélectionnez directement le  concerné. Pour ce faire, sélectionnez l’ **[!UICONTROL Explicit]** option et sélectionnez le  dans le déroulant du **[!UICONTROL Delivery]** champ.

      Le  affiche par défaut le inachevé  contenu dans le dossier **** . Pour accéder à d&#39;autres campagnes, cliquez sur l&#39; **[!UICONTROL Select link]** icône .

      ![](assets/diffusion_edit_1.png)

      Select the campaign from the drop-down list of the **[!UICONTROL Folder]** field, or click **[!UICONTROL Display sub-levels]** to display all of the deliveries contained in sub-folders:

      ![](assets/diffusion_edit_2.png)

      After selecting the delivery action, you can display the content by clicking the **[!UICONTROL Edit link]** icon.

   * Créez un script pour calculer le  du. Pour ce faire, sélectionnez l’ **[!UICONTROL Computed by a script]** option et saisissez le script. Vous pouvez ouvrir une fenêtre d’entrée en cliquant sur l’ **[!UICONTROL Edit...]** option. L’exemple suivant récupère l’identifiant de l’ :

      ![](assets/diffusion_edit_3.png)

   * Créez un nouveau  de. Pour ce faire, sélectionnez l’ **[!UICONTROL New, created from a template]** option et sélectionnez le  sur lequel le  sera basé.

      ![](assets/diffusion_edit_4.png)

      Click the **[!UICONTROL Select link]** icon to browse the folders, and click the **[!UICONTROL Edit link]** icon if you wish to view the content of the selected template.

1. **Destinataires**

   Les destinataires peuvent être spécifiés par les événements entrants, par exemple suite à un import de fichier, ou spécifiés dans l&#39;action de diffusion. Ils peuvent également être stockés dans un ou plusieurs fichiers.

   ![](assets/diffusion_edit_5.png)

1. **Content**

   Le contenu du message peut être défini dans la diffusion ou dans l&#39;événement entrant.

   ![](assets/diffusion_edit_6.png)

1. **Action à effectuer**

   Vous pouvez créer la diffusion, la préparer, la démarrer, estimer la cible ou envoyer un bon à tirer.

   ![](assets/diffusion_edit_7.png)

   Sélectionnez le type d&#39;action à effectuer parmi les options disponibles :

   * **[!UICONTROL Save]**: cette option vous permet de créer le  et de l’enregistrer. Il ne l&#39;analysera ni ne le livrera.
   * **[!UICONTROL Estimate the target]**: cette option vous permet de calculer le   afin d’évaluer son potentiel (première phase dela première phase de l’). Cette action équivaut à sélectionner l’ **[!UICONTROL Estimate the population to be targeted]** option et à cliquer **[!UICONTROL Analyze]** lors de l’envoi d’un au principal par l’intermédiaire de l’ **** du.
   * **[!UICONTROL Prepare]**: cette option vous permet d’exécuter le processus  de  complet (calcul de l’et préparation de contenu). Le  n&#39;est pas envoyé. Cette action équivaut à sélectionner l’ **[!UICONTROL Deliver as soon as possible]** option et à cliquer **[!UICONTROL Analyze]** lors de l’envoi d’un au principal avec des **** de.
   * **[!UICONTROL Send a proof]**: cette option vous permet d’envoyer un du  de. Cette action équivaut à cliquer sur le **[!UICONTROL Send a proof]** bouton dans la barre d’outils d’un avec un ****
   * **[!UICONTROL Prepare and start]**: cette option lance le processus de  de complet (calcul de l’et préparation du contenu) et envoie le. Cette action équivaut à cliquer sur **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** et **[!UICONTROL Confirm delivery]** sur l’option lors de l’envoi d’un au principal avec **des** de.
   Le  de  **[!UICONTROL Act on a delivery]** utilisé plus loin dans le flux de travail vous permet de lancer toutes les étapes restantes requises pour démarrer le (calcul du, préparation du contenu,). For more on this, refer to [Delivery control](../../workflow/using/delivery-control.md).

   Les options suivantes sont également disponibles :

   * **[!UICONTROL Generate an outbound transition]**

      Crée une transition sortante qui sera activée à la fin de l&#39;exécution. Vous pouvez choisir de récupérer la cible de l&#39;action de diffusion en sortie, ou non.

   * **[!UICONTROL Do not recover target]**

      Ne récupère pas la cible de l&#39;action de diffusion en sortie.

   * **[!UICONTROL Processing errors]**

      Reportez-vous au contrôle [](../../workflow/using/delivery-control.md).
   L&#39;onglet **Script** permet de modifier les paramètres de la diffusion.

   ![](assets/edit_diffusion_fil_script.png)

## Exemple : workflow de diffusion {#example--delivery-workflow}

Créez un nouveau workflow et ajoutez des activités comme dans l&#39;exemple ci-dessous :

![](assets/new-workflow-5.png)

Ouvrez l&#39;activité **Diffusion** et définissez ses propriétés comme suit :

* Dans la **[!UICONTROL Delivery]** section, sélectionnez **[!UICONTROL New, created from a template]** et sélectionnez un  de.
* Dans la **[!UICONTROL Recipients]** section, sélectionnez **[!UICONTROL Specified in the delivery]**.
* Dans la **[!UICONTROL Action to execute]** section, conservez l’ **[!UICONTROL Prepare]** option.

![](assets/new-workflow-param-delivery.png)

Cliquez sur **[!UICONTROL OK]** pour fermer la fenêtre de propriétés. Vous venez de configurer un   qui consiste à créer et à préparer un nouveau à partir d&#39;undont le sera spécifié.

Ouvrez l&#39;activité **Validation** et définissez ses propriétés comme suit :

1. Dans le **[!UICONTROL Assignment type]** champ, sélectionnez un groupe dans lequel vous êtes enregistré. Si vous êtes connecté à l’aide du compte &quot;admin&quot;, sélectionnez le groupe Administration.
1. Saisissez ensuite un titre et insérez le texte suivant dans le corps du message :

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Il s’agit d’un message qui comprend un   écrit en JavaScript : **[!UICONTROL vars.recCount]** représente le nombre de ciblés par le de la  précédente. Pour plus d’informations sur le  JavaScript, reportez-vous à la section Scripts [JavaScript et modèles](../../workflow/using/javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   The Approval task is detailed in [Approval](../../workflow/using/approval.md).

## Paramètres d&#39;entrée {#input-parameters}

Identifiant , si l’ **[!UICONTROL Specified in the transition]** option est sélectionnée dans la **[!UICONTROL Delivery]** section.

* deliveryId
* tableName
* schema

Chacun des événements entrants doit spécifier une cible définie par ces paramètres.

>[!NOTE]
>
>Ce paramètre s’affiche uniquement si l’ **[!UICONTROL Specified by inbound event(s)]** option est sélectionnée dans la **[!UICONTROL Recipients]** section.

* filename

   Nom complet du fichier généré si l’ **[!UICONTROL File(s) specified by inbound event(s)]** option est sélectionnée dans la **[!UICONTROL Recipients]** section.

* contentId

   Identifiant du contenu si l’ **[!UICONTROL Specified by inbound events]** option est sélectionnée dans la **[!UICONTROL Content]** section.

## Paramètres de sortie {#output-parameters}

* tableName
* schema
* recCount

Cet ensemble de trois valeurs identifie le  résultant de la  de. **[!UICONTROL tableName]** est le nom de la table qui mémorise les identifiants du , **[!UICONTROL schema]** est le de la population (généralement nms: **[!UICONTROL recCount]** ) etest le nombre d&#39;éléments dans le tableau.

La transition associée au complémentaire possède les mêmes paramètres.

>[!NOTE]
>
>Il n’existe aucun paramètre de sortie lorsque l’ **[!UICONTROL Do not recover target]** option est sélectionnée.


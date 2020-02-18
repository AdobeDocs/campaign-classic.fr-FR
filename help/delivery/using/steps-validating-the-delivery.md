---
title: Valider la diffusion
seo-title: Valider la diffusion
description: Valider la diffusion
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Valider la diffusion {#validating-the-delivery}

Une fois la diffusion créée et paramétrée, vous devez la valider avant de l&#39;envoyer à la cible principale.

Pour cela :

1. **Analyser la diffusion**: cette étape vous permet de préparer les messages à diffuser. Reportez-vous à [Analyse de la diffusion](#analyzing-the-delivery).

   Les modes de validation disponibles sont détaillés dans [Modification du mode](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)d’approbation.

1. **Envoyer des preuves**: cette étape vous permet d’approuver le contenu, les URL, les champs de personnalisation, etc. Reportez-vous aux sections [Envoi d’une preuve](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) et [Définition d’une cible](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)de preuve spécifique.

>[!CAUTION]
>
>Ces deux étapes sont nécessaires et doivent être reproduites après chaque modification du contenu des messages.

## Analyser la diffusion {#analyzing-the-delivery}

L’analyse est l’étape au cours de laquelle la population cible est calculée et le contenu de la diffusion préparé. Une fois la livraison terminée, elle est prête à être envoyée. Pour lancer l’analyse de diffusion, cliquez sur **[!UICONTROL Send]**, puis sélectionnez **[!UICONTROL Deliver as soon as possible]**.

![](assets/s_ncs_user_email_del_send.png)

Le **[!UICONTROL Analyze]** bouton permet de lancer l’analyse manuellement. La barre de progression indique la progression de l’analyse. La section inférieure de la fenêtre affiche le résultat de l’analyse. Les icônes spéciales affichent des avertissements.

![](assets/s_ncs_user_interface_delivery04b.png)

>[!NOTE]
>
>Les règles de validation sont décrites dans le processus de [validation avec des typologies](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

You can stop this job at any time by clicking **[!UICONTROL Stop]**.

![](assets/s_ncs_user_wizard_email01_16.png)

Pendant la phase d&#39;analyse, aucun message n&#39;est envoyé. Vous pouvez donc lancer ou annuler cette opération sans aucun risque.

>[!CAUTION]
>
>L&#39;analyse fige la diffusion (ou le BAT) à l&#39;instant de l&#39;analyse. Toute modification sur la diffusion (ou le BAT) doit être suivie d&#39;une nouvelle analyse pour être prise en compte.

Le dernier message de logs affiche les erreurs éventuelles et leur nombre. Une icône spécifique permet de visualiser le type d&#39;erreur rencontrée : l&#39;icône jaune indique une erreur de traitement non bloquante, l&#39;icône rouge indique une erreur qui empêche le lancement de la diffusion.

![](assets/s_ncs_user_email_del_analyze_error.png)

Cliquez sur **[!UICONTROL Close]** pour corriger les erreurs. Après avoir apporté les modifications, vous devez redémarrer l’analyse.

Vérifiez le résultat de l’analyse avant de cliquer **[!UICONTROL Confirm delivery]** pour envoyer le message à la cible spécifiée. Un message de confirmation vous permet de lancer la diffusion.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Cliquez sur le **[!UICONTROL Change the main delivery target]** lien si le nombre de messages à envoyer ne correspond pas à votre configuration. Vous pouvez ainsi modifier la définition de la population cible et relancer l’analyse.

The delivery parameters **[!UICONTROL Analysis]** tab lets you define a set of information concerning the preparation of messages during the analysis phase.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Cet onglet permet d&#39;accéder aux options suivantes :

* **[!UICONTROL Label and code of the delivery]** : les options concernant cette section de l’écran sont utilisées pour calculer les valeurs de ces champs pendant la phase d’analyse de la remise. Le **[!UICONTROL Calculate the execution folder during the delivery analysis]** champ calcule le nom du dossier qui contiendra cette action de remise pendant la phase d’analyse.
* **[!UICONTROL Approval mode]** : ce champ vous permet de sélectionner le type d’approbation de remise. Les modes d’approbation sont présentés dans le processus de [validation avec des typologies](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).
* **[!UICONTROL Prepare the personalization data with a workflow]** : cette option permet de préparer les données de personnalisation contenues dans votre diffusion dans un processus automatique. Il permet d&#39;améliorer grandement les performances de l&#39;analyse de la diffusion lorsque beaucoup de données sont en cours de traitement, surtout si les données de personnalisation proviennent d&#39;une table externe par l&#39;intermédiaire de la FDA. Consultez la section [Accès à une base de données externe (FDA)](../../platform/using/additional-options.md#optimizing-email-personalization-with-external-data) .
* **[!UICONTROL Start job in a detached process]** : Cette option vous permet de lancer l’analyse de remise dans un processus distinct. La fonction d’analyse utilise par défaut le processus du serveur d’applications Adobe Campaign (web nlserver). En sélectionnant cette option, vous vous assurez que l’analyse sera terminée, même en cas d’échec du serveur d’applications.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** : cette option ajoute les journaux de requête SQL au journal de remise pendant la phase d&#39;analyse.
* **[!UICONTROL Ignore personalization scripts during sending]** : cette option vous permet de contourner l’interprétation des directives JavaScript trouvées dans le contenu HTML. Ils s’afficheront comme dans le contenu livré. Ces directives sont introduites avec la balise **&lt;%=** ).

### Configuration de la priorité d’analyse {#analysis-priority-}

Lorsque la diffusion fait partie d’une campagne, l’ **[!UICONTROL Advanced]** onglet propose une option supplémentaire. Vous pouvez ainsi organiser l’ordre de traitement pour les livraisons de la même campagne.

Avant envoi, chaque diffusion est analysée. La durée d&#39;analyse dépend de la taille du fichier d&#39;extraction de la diffusion. Plus sa taille est importante, plus l&#39;analyse est longue, ce qui met en attente les diffusions suivantes.

Les options de la **[!UICONTROL Message preparation by the scheduler]** liste vous permettent de hiérarchiser l’analyse de diffusion dans un processus de campagne.

![](assets/delivery_analysis_priority.png)

Si une diffusion est trop volumineuse, il est préférable de lui administrer une priorité basse afin de ne pas ralentir l’analyse des autres diffusions du workflow.

>[!NOTE]
>
>To ensure that the larger delivery analyses do not slow down the progress of your workflows, you can schedule their executions by ticking the **[!UICONTROL Schedule execution for a time of low activity]**.

## Envoyer un bon à tirer {#sending-a-proof}

Afin de détecter les éventuelles erreurs de paramétrage de vos messages, Adobe recommande vivement de mettre en place un cycle de validation de vos diffusions. Pour cela, faites-en valider le contenu autant de fois que nécessaire en envoyant des bons à tirer auprès de destinataires test. Un BAT doit être envoyé afin de valider le contenu après chaque modification.

>[!NOTE]
>
>* Les modes de validation disponibles sont détaillés dans [Modification du mode](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)d’approbation.
>* La configuration de la cible d&#39;épreuve est expliquée dans [Définition d&#39;une cible](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)d&#39;épreuve spécifique.
>



Pour envoyer un BAT, procédez comme suit :

1. Assurez-vous que la cible d&#39;épreuve a été configurée comme décrit dans [Définition d&#39;une cible](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)d&#39;épreuve spécifique.
1. Cliquez sur **[!UICONTROL Send a proof]** la barre supérieure de l’assistant de remise.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Démarrer l&#39;analyse des messages. Voir [Analyse de la diffusion](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
1. Vous pouvez maintenant envoyer la livraison (voir [Envoi de la livraison](../../delivery/using/steps-sending-the-delivery.md)).

   Une fois la livraison envoyée, la preuve apparaît dans la liste de distribution et est automatiquement créée et numérotée. Il peut être modifié si vous souhaitez accéder à son contenu et à ses propriétés. Pour plus d’informations à ce propos, consultez [cette page](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Si plusieurs formats ont été créés pour la diffusion (HTML et Texte), vous pouvez choisir le format des messages à envoyer aux destinataires de la preuve dans la partie inférieure de la fenêtre.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

En fonction des remarques du groupe de validation qui reçoit le BAT, vous serez amené à modifier le contenu de la diffusion. Une fois vos modifications effectuées, vous devez relancer l&#39;analyse puis envoyer à nouveau un BAT. Chaque nouveau BAT est numéroté et consigné dans le journal de la diffusion.

Once the delivery has been analyzed, you can view the various proofs sent via the **[!UICONTROL Proofs]** sub-tab of the log (**[!UICONTROL Audit]** tab).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

Vous devez envoyer autant de BAT que nécessaire jusqu&#39;à ce que le contenu de votre diffusion soit finalisé. Dès lors, vous pouvez envoyer la diffusion à la cible principale et clore le cycle de validation.

L’ **[!UICONTROL Advanced]** onglet des propriétés de diffusion vous permet de définir les propriétés de la preuve. Si nécessaire, vous pouvez remplacer les règles d’exclusion des destinataires.

![](assets/s_ncs_user_wizard_email01_145.png)

Les options disponibles sont les suivantes :

* La première option permet de conserver les doublons du BAT.
* Les deux options suivantes vous permettent de conserver les adresses et les destinataires placés sur liste noire en quarantaine. Voir la description de ces options pour la cible principale dans [Personnalisation des paramètres](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings)d’exclusion. Contrairement à la cible d’une diffusion, où ces adresses sont exclues par défaut, elles sont conservées par défaut pour la cible d’une preuve.
* L&#39; **[!UICONTROL Keep the delivery code for the proof]** option vous permet de fournir à la preuve le même code de livraison que celui défini pour la livraison à laquelle elle se rapporte. Ce code est spécifié à la première étape de l’assistant de remise.
* Par défaut, l&#39;objet de la preuve est précédé du préfixe &quot;Preuve #&quot;, où # est le numéro de la preuve. Vous pouvez modifier ce préfixe dans le **[!UICONTROL Label prefix]** champ.

## Processus de validation avec des typologies {#validation-process-with-typologies}

Avant tout envoi, vous devez analyser la diffusion afin d&#39;en valider le contenu et le paramétrage. Les règles de vérification appliquées lors de la phase d&#39;analyse sont définies dans une **typologie**. Par défaut, pour les emails, l&#39;analyse porte sur les points suivants :

* validation de l&#39;objet,
* validation des URL et des images,
* validation des libellés des URL,
* validation du lien de désinscription,
* vérification de la taille des BAT,
* vérification de la durée de validité,
* vérification de la planification des vagues.

Pour chaque diffusion, la typologie à appliquer est sélectionnée dans l&#39;onglet **[!UICONTROL Typologies]** des paramètres de la diffusion.

Vous pouvez afficher et modifier les règles d’approbation, leur contenu, leur ordre d’exécution et leur description complète via le **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** noeud.

Vous pouvez créer de nouvelles règles et définir de nouvelles typologies depuis ce noeud. Ces opérations sont toutefois réservées à des utilisateurs experts, maîtrisant le langage JavaScript.

To edit the current typology, click the **[!UICONTROL Edit link]** icon to the right of the **[!UICONTROL Typology]** field.

![](assets/s_ncs_user_email_del_typo_tab.png)

L’ **[!UICONTROL Rule]** onglet donne une liste des règles de typologie à appliquer. Sélectionnez une règle et cliquez sur l’ **[!UICONTROL Detail...]** icône pour afficher sa configuration :

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** les typologies sont utilisées dans le cadre de la gestion de la pression de vente. Voir à ce propos [cette section](../../campaign/using/about-marketing-resource-management.md).

## Changer le mode de validation {#changing-the-approval-mode}

L’ **[!UICONTROL Analysis]** onglet correspondant aux propriétés de remise vous permet de sélectionner le mode de validation. Si des avertissements sont générés au cours de l’analyse (par exemple, si certains caractères sont accentués dans l’objet de la diffusion, etc.), vous pouvez configurer la diffusion pour qu’elle définisse si elle doit être exécutée ou non. Par défaut, l’utilisateur doit confirmer l’envoi de messages à la fin de la phase d’analyse : c&#39;est une validation **manuelle** .

Vous pouvez choisir un autre mode de validation dans la liste déroulante du champ correspondant.

![](assets/s_ncs_user_email_del_validation_mode.png)

Les modes de validation possibles sont les suivants :

* **[!UICONTROL Manual]**: À la fin de la phase d’analyse, l’utilisateur doit confirmer la livraison pour commencer l’envoi. Pour ce faire, cliquez sur le **[!UICONTROL Start]** bouton pour lancer la diffusion.
* **[!UICONTROL Semi-automatic]**: Les envois démarrent automatiquement si la phase d&#39;analyse ne génère aucun message d&#39;avertissement.
* **[!UICONTROL Automatic]**: Les envois démarrent automatiquement à la fin de la phase d&#39;analyse, quel qu&#39;en soit le résultat.

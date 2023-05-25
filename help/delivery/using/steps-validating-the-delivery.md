---
product: campaign
title: Validation de la diffusion
description: Découvrez comment valider une diffusion
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability, Email Rendering, Proofs
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '1807'
ht-degree: 100%

---

# Validation de la diffusion {#validating-the-delivery}



Une fois la diffusion créée et paramétrée, vous devez la valider avant de l&#39;envoyer à la cible principale.

Pour cela :

1. **Analyser la diffusion** : cette étape permet de procéder à la préparation des messages à envoyer. [En savoir plus](#analyzing-the-delivery).

   Les règles appliquées pendant lʼanalyse sont présentées dans [cette section](#validation-process-with-typologies). Les modes de validation disponibles sont détaillés dans la section [Modification du mode de validation](#changing-the-approval-mode).

1. **Envoyer des BAT** : cette étape permet de contrôler le contenu, les adresses URL, la personnalisation, etc. Pour en savoir plus, consultez les sections [Envoyer un BAT](steps-validating-the-delivery.md#sending-a-proof) et [Définir une cible spécifique au BAT](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>Les deux étapes ci-dessus DOIVENT être exécutées après chaque modification du contenu du message.

## Analysez la diffusion {#analyzing-the-delivery}

L’analyse est l’étape servant au calcul de la population cible et à la préparation de la diffusion. Une fois la diffusion terminée, elle est prête à être envoyée.

### Lancer l’analyse {#launching-the-analysis}

1. Pour lancer l’analyse de diffusion, cliquez sur **[!UICONTROL Envoyer]**.
1. Sélectionnez **[!UICONTROL Diffuser dès que possible]**.

   ![](assets/s_ncs_user_email_del_send.png)

1. Cliquez sur **[!UICONTROL Analyser]** pour lancer l’analyse manuellement.

   La barre de progression indique la progression de l’analyse.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >Les règles de validation appliquées pendant l’analyse sont décrites dans la section [Processus de validation avec des typologies](steps-validating-the-delivery.md#validation-process-with-typologies).

1. Vous pouvez arrêter à tout moment l’analyse par le biais du bouton **[!UICONTROL Arrêter]**.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   Aucun message n’est envoyé pendant la phase de préparation. Vous pouvez donc démarrer ou annuler l’analyse sans risque.

   >[!IMPORTANT]
   >
   >Lors de l’exécution, l’analyse gèle la diffusion (ou le BAT). Toute modification apportée à la diffusion (ou au BAT) doit être suivie d’une autre analyse pour devenir applicable.

1. Attendez que l’analyse soit terminée.

   Une fois l’analyse terminée, la section supérieure de la fenêtre indique si la préparation de la diffusion est terminée ou si des erreurs se sont produites. Toutes les étapes de validation, les avertissements et les erreurs sont répertoriés. Les icônes colorées indiquent le type de message :
   * L’icône bleue indique un message informatif.
   * L’icône jaune indique une erreur de traitement non critique.
   * L’icône rouge indique une erreur critique qui empêche l’envoi de la diffusion.

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. Cliquez sur **[!UICONTROL Fermer]** pour corriger les erreurs, le cas échéant.

1. Après avoir effectué les modifications, redémarrez l’analyse en cliquant sur **[!UICONTROL Analyser]**.

Une fois le résultat de l’analyse vérifié, vous pourrez cliquer sur **[!UICONTROL Confirmer l’envoi]** pour envoyer le message à la cible spécifiée. Un message de confirmation permet de lancer la diffusion.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Cliquez sur le lien **[!UICONTROL Modifier la cible principale de la diffusion]** si le nombre de messages à envoyer ne correspond pas à votre paramétrage. Vous pourrez alors modifier la définition de la population ciblée et relancer l&#39;analyse.

### Paramètres d’analyse {#analysis-parameters}

L’onglet **[!UICONTROL Analyse]** des propriétés de la diffusion permet de définir un ensemble d’informations relatives à la préparation des messages lors de la phase d’analyse.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Cet onglet permet d&#39;accéder aux options suivantes :

* **[!UICONTROL Libellé et code diffusion]** : les options de cette section sont utilisées pour calculer les valeurs de ces champs pendant la phase d’analyse de diffusion. Le champ **[!UICONTROL Calculer le dossier d’exécution lors de l’analyse de la diffusion]** calcule le nom du dossier qui contiendra cette action de diffusion pendant la phase d’analyse.
* **[!UICONTROL Mode de validation]** : ce champ permet de définir une diffusion manuelle ou automatique, une fois l’analyse terminée. Les modes de validation sont présentés dans la section [Changer le mode de validation](#changing-the-approval-mode).
* **[!UICONTROL Préparer les fragments de diffusion dans la base de données]** : cette option vous permet d’améliorer les performances de l’analyse des diffusions. Voir à ce propos [cette section](#improving-delivery-analysis).
* **[!UICONTROL Préparer les données de personnalisation avec un workflow]** : cette option permet de préparer, dans un workflow automatique, les données de personnalisation contenues dans la diffusion, ce qui permet d’augmenter considérablement les performances d’exécution de la personnalisation. Pour plus d’informations à ce sujet, voir la section [Optimiser la personnalisation](personalization-fields.md#optimizing-personalization).
* **[!UICONTROL Lancer le traitement dans un processus détaché]** : cette option permet de lancer l’analyse de la diffusion dans un processus à part. Par défaut, la fonction d’analyse utilise le processus du serveur applicatif d’Adobe Campaign (nlserver web). En cochant cette option, vous êtes assuré que l’analyse sera menée à son terme, même en cas de défaillance du serveur applicatif.
* **[!UICONTROL Enregistrer les requêtes SQL générées pendant l’analyse dans le journal]** : cette option permet d&#39;ajouter les logs des requêtes SQL dans le journal de la diffusion lors de la phase d’analyse.
* **[!UICONTROL Ignorer les scripts de personnalisation lors de l’envoi]** : cette option permet de ne pas interpréter les directives JavaScript présentes dans les contenus HTML. Elles seront affichées telles quelles dans les contenus envoyés. Ces directives sont introduites par la balise **&lt;%=**.

### Améliorer les performances des analyses de diffusions {#improving-delivery-analysis}

Pour accélérer la préparation de la diffusion, vous pouvez cocher l’option **[!UICONTROL Préparer les fragments de diffusion dans la base de données]** avant de lancer l’analyse.

Lorsque cette option est activée, la préparation de la diffusion est effectuée directement dans la base de données, ce qui peut accélérer considérablement l’analyse.

Actuellement, cette option n’est disponible que si les conditions suivantes sont remplies :
* La diffusion doit être un email. Les autres canaux ne sont pas pris en charge pour l’instant.
* Vous ne devez pas utiliser de routage de mid-sourcing ou externe. Seul le type de routage de diffusion en masse est possible. Vous pouvez vérifier le routage utilisé dans l’onglet **[!UICONTROL Général]** des **[!UICONTROL Propriétés de la diffusion]**.
* Vous ne pouvez pas cibler une population provenant d’un fichier externe. Pour une diffusion unique, cliquez sur le lien **[!UICONTROL À]** dans les **[!UICONTROL Paramètres de l’e-mail]** et vérifiez que l’option **[!UICONTROL Définie depuis la base de données]** est sélectionnée. Pour une diffusion utilisée dans un workflow, vérifiez que les destinataires sont **[!UICONTROL Spécifiés par le ou les événements entrants]** dans l’onglet **[!UICONTROL Diffusion]**.
* Vous devez utiliser une base de données PostgreSQL.

### Configurer la priorité d’analyse {#analysis-priority-}

Lorsque votre diffusion fait partie d&#39;une campagne, l&#39;onglet **[!UICONTROL Avancé]** propose une option supplémentaire : celle-ci vous permet d&#39;organiser l&#39;ordre de traitement des diffusions d&#39;une même campagne.

Avant envoi, chaque diffusion est analysée. La durée d&#39;analyse dépend de la taille du fichier d&#39;extraction de la diffusion. Plus sa taille est importante, plus l&#39;analyse est longue, ce qui met en attente les diffusions suivantes.

Les options de la section **[!UICONTROL Préparation des messages par l’ordonnanceur]** vous permettent de prioriser l’analyse des diffusions d’un workflow de campagne.

![](assets/delivery_analysis_priority.png)

Si une diffusion est trop volumineuse, il est préférable de lui administrer une priorité basse afin de ne pas ralentir l’analyse des autres diffusions du workflow.

>[!NOTE]
>
>Pour vous assurer que l&#39;analyse des diffusions les plus volumineuses ne freine pas le déroulement de vos workflows, il vous est possible de différer leur exécution en cochant la case **[!UICONTROL Différer l&#39;exécution vers une plage horaire de faible activité]**.

## Envoi d&#39;un BAT {#sending-a-proof}

Afin de détecter les éventuelles erreurs de paramétrage de vos messages, Adobe recommande vivement de mettre en place un cycle de validation de vos diffusions. Pour cela, faites-en valider le contenu autant de fois que nécessaire en envoyant des bons à tirer auprès de destinataires test. Un BAT doit être envoyé afin de valider le contenu après chaque modification.

>[!NOTE]
>
>* Les modes de validation disponibles sont présentés dans la section [Changer le mode de validation](steps-validating-the-delivery.md#changing-the-approval-mode).
>* La configuration de la cible du BAT est expliquée dans la section [Définir une cible spécifique au BAT](steps-defining-the-target-population.md#defining-a-specific-proof-target).
>


Pour envoyer un BAT, procédez comme suit :

1. Vérifiez que la cible du BAT a été configurée comme décrit dans la section [Définir une cible spécifique au BAT](steps-defining-the-target-population.md#defining-a-specific-proof-target).
1. Cliquez sur **[!UICONTROL Envoyer un BAT]** dans la barre supérieure de l&#39;assistant de diffusion.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Lancez l’analyse des messages. Pour plus d&#39;informations, consultez la section [Analyser la diffusion](steps-validating-the-delivery.md#analyzing-the-delivery).
1. Vous pouvez maintenant envoyer la diffusion (voir la section [Envoyer la diffusion](steps-sending-the-delivery.md)).

   Une fois la diffusion envoyée, le BAT apparaît dans la liste de diffusion et est automatiquement créé et numéroté. Il peut être modifié si vous souhaitez accéder à son contenu et à ses propriétés. Voir à ce propos [cette page](about-delivery-monitoring.md).

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Si plusieurs formats ont été créés pour la diffusion (HTML et Texte), vous pouvez choisir le format des messages à envoyer aux destinataires du BAT. Pour cela, sélectionnez l’option correspondante dans la section inférieure de la fenêtre de sélection de la cible des BAT.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

En fonction des remarques du groupe de validation qui reçoit le BAT, vous serez amené à modifier le contenu de la diffusion. Une fois vos modifications effectuées, vous devez relancer l&#39;analyse puis envoyer à nouveau un BAT. Chaque nouveau BAT est numéroté et consigné dans le journal de la diffusion.

Une fois la diffusion analysée, vous pouvez en visualiser les différents BAT depuis le sous-onglet **[!UICONTROL Bons à tirer]** du journal (onglet **[!UICONTROL Suivi]**).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

Vous devez envoyer autant de BAT que nécessaire jusqu&#39;à ce que le contenu de votre diffusion soit finalisé. Dès lors, vous pouvez envoyer la diffusion à la cible principale et clore le cycle de validation.

L&#39;onglet **[!UICONTROL Avancé]** des propriétés de la diffusion permet de définir les propriétés du BAT et notamment de remplacer les règles d&#39;exclusion des destinataires.

![](assets/s_ncs_user_wizard_email01_145.png)

Les options disponibles sont les suivantes :

* La première option permet de conserver les doublons du BAT.
* Les deux options ci-dessous permettent de conserver les destinataires qui se trouvent sur la liste bloquée et les adresses en quarantaine. Voir la description de ces options pour la cible principale dans la section [Personnaliser les paramètres d’exclusion](steps-defining-the-target-population.md#customizing-exclusion-settings). Contrairement à la cible d’une diffusion, où ces adresses sont exclues par défaut, elles sont conservées par défaut pour la cible d’un BAT.
* L&#39;option **[!UICONTROL Conserver le code diffusion pour le BAT]** permet d&#39;attribuer au BAT le même code de diffusion que celui défini pour la diffusion à laquelle il correspond : ce code est spécifié dans la première étape de l&#39;assistant de diffusion.
* Par défaut, l&#39;objet du BAT est préfixé par &quot;BAT N°&quot;, où N° correspond au numéro du BAT. Vous pouvez modifier ce préfixe dans le champ **[!UICONTROL Préfixe du libellé]**.

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

Vous pouvez visualiser et éditer les règles de validation, leur contenu, leur ordre d&#39;exécution et leur description complète depuis le noeud **[!UICONTROL Administration > Gestion de campagnes > Gestion des typologies > Règles de typologies]**.

Vous pouvez créer de nouvelles règles et définir de nouvelles typologies depuis ce noeud. Ces opérations sont toutefois réservées à des utilisateurs experts, maîtrisant le langage JavaScript.

Pour plus d’informations sur les règles de typologie, consultez [cette page ](../../campaign-opt/using/about-campaign-typologies.md).

Vous pouvez également éditer la typologie courante en cliquant sur l&#39;icône **[!UICONTROL Editer le lien]** situé à droite du champ **[!UICONTROL Typologie]**.

![](assets/s_ncs_user_email_del_typo_tab.png)

L&#39;onglet **[!UICONTROL Règle]** propose la liste des règles de typologie à appliquer. Sélectionnez une règle et cliquez sur l&#39;icône **[!UICONTROL Détail...]** pour en visualiser le paramétrage :

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>Les typologies de type **[!UICONTROL Arbitrage]** sont utilisées dans le cadre de la gestion de la pression commerciale. Voir à ce sujet [cette section](../../mrm/using/about-marketing-resource-management.md).

## Changer le mode de validation {#changing-the-approval-mode}

L&#39;onglet **[!UICONTROL Analyse]** des propriétés de la diffusion vous permet de sélectionner le mode de validation. En effet, si des avertissements sont générés lors de l&#39;analyse (par exemple, si certains caractères sont accentués dans le sujet de la diffusion, etc.), vous pouvez paramétrer la diffusion afin de définir si elle doit toutefois être exécutée ou non. Par défaut, à la fin de la phase d&#39;analyse, l&#39;utilisateur doit valider l&#39;envoi des messages : il s&#39;agit d&#39;une validation **manuelle**.

Vous pouvez choisir un autre mode de validation dans la liste déroulante du champ correspondant.

![](assets/s_ncs_user_email_del_validation_mode.png)

Les modes de validation possibles sont les suivants :

* **[!UICONTROL Manuel]** : à la fin de la phase d’analyse, l’utilisateur doit confirmer la diffusion pour commencer l’envoi. Pour cela, cliquez sur le bouton **[!UICONTROL Démarrer]** afin de lancer la diffusion.
* **[!UICONTROL Semi-automatique]** : les envois démarrent automatiquement si la phase d’analyse ne génère aucun message d’avertissement.
* **[!UICONTROL Automatique]** : les envois démarrent automatiquement à la fin de la phase d’analyse, quel qu’en soit le résultat.

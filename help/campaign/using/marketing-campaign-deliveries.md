---
solution: Campaign Classic
product: campaign
title: Diffusions de campagnes marketing
description: En savoir plus sur les diffusions d'opérations marketing
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3076'
ht-degree: 94%

---


# Diffusions de campagnes marketing {#marketing-campaign-deliveries}

Les diffusions peuvent être créées depuis le tableau de bord d&#39;une opération, un workflow d&#39;opération ou directement à partir de la vue d&#39;ensemble des diffusions.

Une fois créées à partir d’une campagne, les diffusions sont liées à cette campagne et consolidées au niveau de la campagne.

![](assets/do-not-localize/how-to-video.png)[ Découvrez cette fonctionnalité en vidéo](#create-email-video)

## Créer des diffusions {#creating-deliveries}

Pour créer une diffusion associée à une opération, cliquez sur le lien **[!UICONTROL Ajouter une diffusion]** proposé dans le tableau de bord de l&#39;opération.

![](assets/campaign_op_add_delivery.png)

Les paramétrages proposés sont adaptés au type de diffusion : courrier, email, canaux mobiles. [En savoir plus](../../delivery/using/steps-about-delivery-creation-steps.md).

## Choisir la population cible {#selecting-the-target-population}

Pour chaque diffusion, vous pouvez définir :

* Audience - En savoir plus sur la [création de l’audience dans un processus](#building-the-main-target-in-a-workflow) et la [sélection de la population](#selecting-the-target-population)de cibles.
* Une Population témoin - En savoir plus sur la [définition d&#39;une Population témoin](#defining-a-control-group).
* Adresses de contrôle - En savoir plus dans [cette section](../../delivery/using/about-seed-addresses.md).

Some of this information can be inherited from the [template](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Pour créer la cible de diffusion, vous pouvez définir des critères de filtrage pour les destinataires de la base de données. Ce mode de sélection destinataire est présenté dans [cette section](../../delivery/using/steps-defining-the-target-population.md).

**Exemple : envoyer des messages à un groupe**

Vous pouvez par exemple importer une population dans une liste puis cibler cette liste dans les diffusions.

1. Pour cela, éditez la diffusion concernée et cliquez sur le lien **[!UICONTROL Pour]** afin de modifier la population ciblée.

1. Dans l&#39;onglet **[!UICONTROL Cible principale]**, choisissez l&#39;option **[!UICONTROL Définie depuis la base de données]** et cliquez sur **[!UICONTROL Ajouter]** pour sélectionner les destinataires.

![](assets/s_user_target_group_add.png)

1. Choisissez **[!UICONTROL Une liste de destinataires]** et cliquez sur **[!UICONTROL Suivant]** pour le sélectionner parmi les listes existantes.

![](assets/s_user_target_group_next.png)

### Création de l’audience dans un processus {#building-the-main-target-in-a-workflow}

La cible principale d&#39;une diffusion peut également être définie au travers d&#39;un workflow de ciblage : cet environnement graphique permet de construire une cible via des requêtes, des tests et des unions, déduplications, partages, etc. [En savoir plus](../../workflow/using/architecture.md).

>[!IMPORTANT]
>
>Vous ne pouvez pas créer plus de 28 workflows dans une campagne. Après cette limite, d’autres workflows ne sont pas visibles dans l’interface et peuvent générer des erreurs.

#### Création du processus {#creating-a-targeting-workflow}

Le ciblage peut être construit grâce à une combinaison de critères de filtrage, enchaînés graphiquement dans un workflow. Vous pouvez ainsi créer des populations et sous-populations qui seront ciblées selon vos besoins. Pour afficher l&#39;éditeur de workflows, cliquez sur l&#39;onglet **[!UICONTROL Ciblages et workflows]** dans le tableau de bord des campagnes.

![](assets/s_ncs_user_edit_op_wf_link.png)

La population cible est extraite de la base Adobe Campaign via une ou plusieurs requêtes qui sont positionnées dans un workflow. Pour découvrir comment construire une requête, consultez [cette section](../../workflow/using/query.md).

Il est possible de lancer des requêtes puis de partager les populations via des boîtes de type Union, Intersection, Partage, Exclusion, etc.

Sélectionnez les objets dans les listes situées à gauche de l&#39;espace de travail et enchaînez-les pour construire la cible.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

Dans le diagramme, reliez ainsi entre elles les requêtes de ciblage et d&#39;ordonnancement nécessaires à la construction de la cible : vous pouvez exécuter le ciblage en cours de construction afin de contrôler la population extraite de la base de données.

>[!NOTE]
>
>La procédure pour définir des requêtes est présentée avec des exemples dans [cette section](../../workflow/using/query.md).

La section gauche de l&#39;éditeur contient une bibliothèque d&#39;objets graphiques qui représentent des activités. Le premier onglet regroupe les activités de ciblage et le deuxième onglet regroupe les activités d&#39;ordonnancement, qui sont utilisées plus occasionnellement afin de coordonner les activités de ciblage.

La barre d&#39;outils de l&#39;éditeur de diagramme permet d&#39;accéder aux fonctions de mise en page et d&#39;exécution du workflow de ciblage.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>Les activités disponibles pour la construction du diagramme, ainsi que toutes les problématiques d&#39;affichage et de mise en page, sont présentées dans le guide [Automatiser avec des workflows](../../workflow/using/architecture.md).

Vous pouvez créer plusieurs workflows de ciblage pour une même opération. Pour ajouter un workflow :

1. Positionnez le pointeur de la souris dans la section supérieure gauche de la zone de création des workflows, cliquez avec le bouton droit et choisissez **[!UICONTROL Ajouter]**. Vous pouvez également utiliser le bouton **[!UICONTROL Nouveau]** situé au-dessus de cette zone.

   ![](assets/s_ncs_user_add_a_wf.png)

1. Sélectionnez le modèle de workflow **[!UICONTROL Nouveau workflow]** et nommez ce workflow.
1. Cliquez sur **[!UICONTROL Ok]** pour valider la création du workflow, puis créez le diagramme pour ce workflow.

#### Exécuter le processus {#executing-a-workflow}

Les workflows de ciblage peuvent être lancés manuellement via le bouton **[!UICONTROL Démarrer]** de la barre d&#39;outils, sous réserve que vous disposiez des droits adéquats.

Le ciblage peut être planifié afin de s&#39;exécuter automatiquement selon un planning (planificateur) ou un événement (signal externe, import d&#39;un fichier, etc.).

Les actions relatives à l&#39;exécution du workflow de ciblage (lancement, arrêt, pause, etc.) sont des processus **asynchrones** : la commande est enregistrée et sera effective dès que le serveur sera disponible pour l&#39;appliquer.

Les icônes de la barre d&#39;outils permettent d&#39;agir sur l&#39;exécution du workflow de ciblage.

* Démarrer ou redémarrer

   * L&#39;icône **[!UICONTROL Démarrer]** permet de lancer le workflow de ciblage. Lorsque vous cliquez sur cette icône, toutes les activités qui n&#39;ont pas de transition entrante sont activées (sauf les sauts de type &#39;arrivée&#39;).

      ![](assets/s_user_segmentation_start.png)

      La demande est prise en compte par le serveur, comme le notifie son état :

      ![](assets/s_user_segmentation_start_status.png)

      Puis le processus passe en état **[!UICONTROL Démarré]**.

   * Vous pouvez redémarrer le workflow de ciblage à partir de l&#39;icône correspondante de la barre d&#39;outils. Cette commande peut être utile si l&#39;icône **[!UICONTROL Démarrer]** n&#39;est pas disponible, par exemple lorsque l&#39;arrêt du workflow de ciblage est en cours. Dans ce cas, cliquez sur l&#39;icône **[!UICONTROL Redémarrer]** pour anticiper le démarrage. La demande est prise en compte par le serveur, comme le notifie son état :

      ![](assets/s_user_segmentation_restart_status.png)

      Puis le processus passe en état **[!UICONTROL Démarré]**.

* Arrêter ou suspendre

   * Les icônes de la barre d&#39;outils permettent d&#39;arrêter ou suspendre un workflow de ciblage en cours d&#39;exécution.

      Lorsque vous cliquez sur l&#39;icône **[!UICONTROL Pause]**, les opérations en cours **[!UICONTROL ne sont pas]** suspendues, mais aucune autre activité n&#39;est lancée jusqu&#39;à la prochaine reprise.

      ![](assets/s_user_segmentation_pause.png)

      La commande est prise en compte par le serveur, comme le notifie son état :

      ![](assets/s_user_segmentation_pause_status.png)

      Vous pouvez également suspendre automatiquement un workflow de ciblage lorsque l&#39;exécution arrive à une activité. Pour cela, cliquez avec le bouton droit sur l&#39;activité à partir de laquelle le workflow de ciblage sera suspendu et choisissez **[!UICONTROL Activer mais ne pas exécuter]**.

      ![](assets/s_user_segmentation_donotexecute.png)

      Une icône spécifique matérialise ce paramétrage.

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >Cette option est utile lors des phases de conception et de test d&#39;une opération de ciblage.

      Cliquez sur **[!UICONTROL Démarrer]** pour reprendre l&#39;exécution.

   * Cliquez sur l&#39;icône **[!UICONTROL Arrêter]** pour stopper l&#39;exécution en cours.

      ![](assets/s_user_segmentation_stop.png)

      La commande est prise en compte par le serveur, comme le notifie son état :

      ![](assets/s_user_segmentation_stop_status.png)
   Vous pouvez également arrêter automatiquement un workflow de ciblage lorsque l&#39;exécution arrive à une activité. Pour cela, cliquez avec le bouton droit sur l&#39;activité à partir de laquelle le workflow de ciblage sera suspendu et choisissez **[!UICONTROL Ne pas activer]**.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   Une icône spécifique matérialise ce paramétrage.

   >[!NOTE]
   >
   >Cette option est utile lors des phases de conception et de test d&#39;une opération de ciblage.

* Arrêt inconditionnel

   Dans l&#39;Explorateur, sélectionnez **[!UICONTROL Administration > Exploitation > Objets créés automatiquement > Workflows des opérations]** pour accéder aux workflows des opérations et agir sur ces derniers.

   Vous pouvez effectuer un arrêt conditionnel de votre workflow en cliquant sur l&#39;icône **[!UICONTROL Actions]** et en sélectionnant **[!UICONTROL Arrêt inconditionnel]**. Cette action arrête votre workflow d&#39;opération.

   ![](assets/s_user_segmentation_stop_unconditional.png)

### Définir une population témoin {#defining-a-control-group}

La population témoin est une population qui ne recevra pas la diffusion : elle est utilisée pour suivre les comportements après diffusion et l&#39;impact de la campagne, par comparaison du comportement de la population cible, qui, elle, a reçu la diffusion.

La population témoin peut être extraite de la cible principale et/ou issue d&#39;un groupe ou d&#39;une requête spécifique.

#### Activation de la population témoin pour une opération {#activating-the-control-group-for-a-campaign}

Vous pouvez définir une population témoin au niveau de l&#39;opération : elle sera alors appliquée à chaque diffusion de l&#39;opération concernée.

1. Éditez l&#39;opération concernée et cliquez sur l&#39;onglet **[!UICONTROL Edition]**.
1. Cliquez sur **[!UICONTROL Paramètres avancés de l&#39;opération...]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. Sélectionnez l&#39;option **[!UICONTROL Activer et éditer le paramétrage de la population témoin]**.
1. Cliquez sur **[!UICONTROL Editer...]** pour paramétrer la population témoin.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

La procédure de paramétrage est présentée dans les sections [Extraire la population témoin de la cible principale](#extracting-the-control-group-from-the-main-target) et [Ajouter une population témoin](#adding-a-population).

#### Activation de la population témoin pour une diffusion {#activating-the-control-group-for-a-delivery}

Vous pouvez définir une population témoin au niveau de la diffusion : elle sera alors appliquée à chaque diffusion de l&#39;opération concernée.

Par défaut, le paramétrage de la population témoin défini au niveau de l&#39;opération s&#39;applique pour chaque diffusion de cette opération. Vous pouvez toutefois adapter la population témoin unitairement pour une diffusion.

>[!NOTE]
>
>Si vous avez défini une population témoin au niveau d&#39;une opération et que vous la configurez également pour une diffusion liée à cette opération, seule la population témoin définie pour la diffusion sera appliquée.

1. Éditez la diffusion concernée et cliquez sur le lien **[!UICONTROL Pour]** de la section **[!UICONTROL Paramètres de l&#39;e-mail]**.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. Cliquez sur l&#39;onglet **[!UICONTROL Population témoin]**, puis sélectionnez **[!UICONTROL Activer et éditer le paramétrage de la population témoin]**.
1. Cliquez sur **[!UICONTROL Editer...]** pour paramétrer la population témoin.

La procédure de paramétrage est présentée dans les sections [Extraire la population témoin de la cible principale](#extracting-the-control-group-from-the-main-target) et [Ajouter une population témoin](#adding-a-population).

#### Extraire la population témoin de la cible principale {#extracting-the-control-group-from-the-main-target}

Vous pouvez extraire des destinataires de la cible principale de la diffusion : dans ce cas, les destinataires seront soustraits de la cible des actions de diffusion impactées par ce paramétrage. Cette extraction peut être aléatoire ou résulter d&#39;un tri sur les destinataires.

![](assets/s_ncs_user_extract_from_target_population.png)

Pour extraire une population témoin, activez la population témoin au niveau de l&#39;opération ou de la diffusion et choisissez une des options suivantes : **[!UICONTROL Activer le tirage aléatoire]** ou **[!UICONTROL Conserver les premiers suite à un tri]**.

* **[!UICONTROL Activer le tirage aléatoire]** : cette option applique un tirage aléatoire sur les destinataires présents dans la population ciblée. Si vous définissez ensuite une limite de 100, la population témoin sera composée de 100 destinataires choisis aléatoirement dans la population ciblée. Le tirage aléatoire appliqué dépend du moteur de base de données.
* **[!UICONTROL Conserver les premiers suite à un tri]** : cette option permet de définir une limitation suivant un ou plusieurs ordres de tri. Si vous choisissez le champ **[!UICONTROL Age]** comme critère de tri, et que vous définissez ensuite une limite de 100, la population témoin sera composée des 100 destinataires les moins âgés. Il peut être intéressant, par exemple, de définir comme population témoin, des contacts qui achètent peu, ou au contraire, qui achètent fréquemment, et de comparer leur comportement aux destinataires qui ont été contactés.

Cliquez sur **[!UICONTROL Suivant]** pour définir l&#39;ordre de tri (si besoin) et sélectionnez le mode de limitation des destinataires.

![](assets/s_ncs_user_edit_op_target_param.png)

Ce paramétrage correspond à celui d&#39;une activité de partage dans le workflow, qui permet d&#39;éclater une cible en plusieurs sous-ensembles. La population témoin correspond à l&#39;un de ces sous-ensembles. Pour plus d&#39;informations, consultez [cette section](../../workflow/using/architecture.md).

### Ajouter une population témoin {#adding-a-population}

Vous pouvez définir une nouvelle population qui sera utilisée comme population témoin. Cette population peut être issue d&#39;un groupe de destinataires ou construite via une requête spécifique.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Le requêteur d&#39;Adobe Campaign est présenté dans [cette section](../../workflow/using/query.md).

## Démarrer la diffusion {#starting-a-delivery}

Une fois que toutes les validations ont été accordées, la diffusion est prête à démarrer. La procédure dépend alors du type de diffusion. For email or mobile channel deliveries, see [Starting an online delivery](#starting-an-online-delivery), and for direct mail deliveries, see [Starting an offline delivery](#starting-an-offline-delivery).

### Démarrer une diffusion online {#starting-an-online-delivery}

Une fois toutes les demandes de validation approuvées, la diffusion passe à l&#39;état **[!UICONTROL A confirmer]**, et peut être démarrée par un opérateur. Le cas échéant, l&#39;opérateur Adobe Campaign (ou le groupe d&#39;opérateurs) désigné comme validant pour le démarrage de la diffusion est alors notifié qu&#39;une diffusion est prête à être démarrée.

>[!NOTE]
>
>Si un opérateur spécifique ou groupe d&#39;opérateurs est désigné pour le démarrage de la diffusion dans les propriétés de cette dernière, vous pouvez également permettre à l&#39;opérateur en charge de la diffusion de confirmer l&#39;envoi. Pour cela activez l&#39;option **NMS_ActivateOwnerConfirmation** en indiquant comme valeur **1**. Les options sont gérées depuis le noeud **[!UICONTROL Administration]** > **[!UICONTROL Plate-forme]****[!UICONTROL Options]** de l&#39;explorateur Adobe Campaign.
>  
>Pour désactiver cette option, indiquez **0** comme valeur. Le processus de confirmation des envois fonctionnera alors comme par défaut : seul l&#39;opérateur ou le groupe d&#39;opérateurs désigné pour l&#39;envoi (ou un administrateur) dans les propriétés de la diffusion pourra confirmer et effectuer l&#39;envoi.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

L&#39;information est également remontée au niveau du tableau de bord de l&#39;opération. Le lien **[!UICONTROL Confirmer l&#39;envoi]** permet de lancer la diffusion.

![](assets/s_ncs_user_edit_del_to_start.png)

Un message de confirmation permet de sécuriser cette action.

### Démarrer une diffusion offline {#starting-an-offline-delivery}

Lorsque toutes les validations ont été acceptées, la diffusion passe à l&#39;état **[!UICONTROL En attente d&#39;extraction]**. Les fichiers d&#39;extraction sont créés via un workflow spécifique qui, dans une configuration par défaut, démarre automatiquement lorsqu&#39;une diffusion courrier est en attente d&#39;extraction. Lorsqu&#39;un traitement est en cours, il est affiché dans le tableau de bord : il peut être édité depuis son lien.

>[!NOTE]
>
>Les workflows techniques relatifs aux processus d&#39;opérations sont présentés dans la section [Liste des workflows de processus d&#39;opérations](../../workflow/using/campaign.md).

**Etape 1 - Valider le fichier**

Une fois le workflow d&#39;extraction exécuté correctement, le fichier d&#39;extraction doit être validé (sous réserve que la validation du fichier d&#39;extraction ait été sélectionnée dans le paramétrage de la diffusion).

Pour plus d&#39;informations, reportez-vous à la section [Valider un fichier d&#39;extraction](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**Etape 2 - Valider le message au prestataire**

* Une fois la validation du fichier d&#39;extraction acceptée, vous pouvez générer le BAT de l&#39;email de notification au routeur. Cet email est construit via un modèle de diffusion. Il doit être validé.

   >[!NOTE]
   >
   >Cette étape n&#39;est proposée que si l&#39;envoi et la validation des BAT ont été activés à partir de la fenêtre des validations.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Cliquez sur le bouton **[!UICONTROL Envoyer un BAT]** pour lancer la création des BAT.

   La cible des BAT doit avoir été préalablement définie.

   Vous pouvez créer autant de BAT que nécessaire. Ils sont accessibles à partir du lien **[!UICONTROL Courriers...]** du détail de la diffusion.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* La diffusion est alors à l&#39;état **[!UICONTROL A soumettre]**. Le bouton **[!UICONTROL Soumettre les BAT]** lance le processus de validation des BAT.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* La diffusion passe à l&#39;état **[!UICONTROL BAT à valider]** et un bouton permet d&#39;accepter ou refuser la validation.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   Vous pouvez alors accepter ou refuser cette validation, ou revenir à l&#39;étape d&#39;extraction

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* Puis le fichier d&#39;extraction est envoyé au routeur et la diffusion est terminée.

### Calcul des coûts et des stocks {#calculation-of-costs-and-stocks}

L&#39;extraction du fichier lance deux opérations : le calcul des budgets et le calcul des stocks. Les lignes budgétaires sont mises à jour.

* Au niveau de l&#39;opération, l&#39;onglet **[!UICONTROL Budget]** permet de gérer les budgets. Le cumul des lignes de coût est repris dans le champ **[!UICONTROL Coût calculé]** de l&#39;onglet principal de l&#39;opération et du programme auquel elle appartient. Les montants sont également répercutés au niveau du budget de l&#39;opération.

   Le coût réel sera calculé au final en fonction des informations fournies par le routeur : seuls les courriers réellement envoyés sont facturés.

* Les stocks sont définis dans le noeud **[!UICONTROL Administration > Gestion de campagne > Stocks]** de l&#39;arborescence, et les structures de coût, dans le noeud **[!UICONTROL Administration > Gestion de campagne > Prestataires]**.

   Au niveau des stocks, vous pouvez visualiser les lignes de stocks. Pour définir le stock initial, vous devez ouvrir une ligne de stock. Le stock est décrémenté au fur et à mesure des diffusions. Vous pouvez définir un niveau d&#39;alerte et des notifications.

>[!NOTE]
>
>Pour plus d&#39;informations sur le calcul des coûts et la gestion des stocks, voir la section [Prestataires, stocks et budgets](../../campaign/using/providers--stocks-and-budgets.md).

## Gérer les documents associés {#managing-associated-documents}

Vous pouvez associer différents documents à une opération : rapport, photo, page web, schéma, etc. Ces documents peuvent être dans n&#39;importe quel format (Microsoft Word, Powerpoint, PNG, JPG, Acrobat PDF, etc.). Pour attacher des documents à une opération, reportez-vous à la section [Ajouter des documents](#adding-documents).

>[!IMPORTANT]
>
>Ce mode d&#39;échange est réservé à des documents de faible volume (quelques Mo maximum).

Vous pouvez également référencer dans les opérations des éléments externes, créés dans l&#39;entreprise, tels que des coupons promotionnels, des offres spécifiques à une agence ou à un magasin, etc. Regroupés dans une composition, ces éléments peuvent être associés à une diffusion courrier. Voir à ce sujet la section [Associer et structurer les ressources liées via une composition](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Si vous utilisez MRM, vous pouvez également gérer une bibliothèque de ressources marketing sur lesquelles plusieurs intervenants peuvent agir dans un mode collaboratif. Voir à ce sujet la section [Gérer les ressources marketing](../../campaign/using/managing-marketing-resources.md).

### Ajouter des documents {#adding-documents}

Des documents peuvent être associés au niveau de l&#39;opération (documents contextuels) ou au niveau du programme (documents généraux).

L&#39;onglet **[!UICONTROL Documents]** contient :

* la liste de tous les documents nécessaires au contenu (maquette, images, etc.) qui pourront être téléchargés en local par les opérateurs Adobe Campaign possédant les droits adéquats,
* les documents contenant des informations destinées au routeur, s&#39;ils existent.

Les documents sont rattachés au programme ou à l&#39;opération via leur onglet **[!UICONTROL Edition > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

Vous pouvez également ajouter un document dans une opération via le lien proposé dans son tableau de bord.

![](assets/add_a_document_in_op.png)

Cliquez sur l&#39;icône **[!UICONTROL Détails]** pour visualiser le contenu d&#39;un fichier et ajouter des informations complémentaires :

![](assets/s_ncs_user_op_add_document_details.png)

Au niveau du tableau de bord, les documents associés à l&#39;opération sont regroupés dans la section **[!UICONTROL Document(s)]**, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_op_edit_document.png)

Ils peuvent également être édités et modifiés depuis cette vue.

### Associer et structurer les ressources liées via une composition {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Les compositions sont exclusivement utilisées dans le cadre d&#39;opérations courrier.

Une composition désigne un ensemble structuré d&#39;éléments (documents, agences/magasins, coupons promotionnels, etc.) créés dans l&#39;entreprise et pour une opération particulière.

Ces éléments sont regroupés dans des compositions, et telle ou telle composition sera associée à une diffusion : elle sera référencée dans le fichier d&#39;extraction transmis au **prestataire** afin d&#39;être jointe à la diffusion. Vous pouvez par exemple créer une composition qui référence une agence et les brochures marketing qu&#39;elle utilise.

Les compositions permettent, au niveau de l&#39;opération, de structurer des éléments externes qui seront associés à la diffusion en fonction de certains critères : agence de rattachement, offre promotionnelle accordée, invitation à un événement local, etc.

#### Créer une composition {#creating-an-outline}

Pour créer une composition, cliquez sur le sous-onglet **[!UICONTROL Compositions de diffusions]** proposé dans l&#39;onglet **[!UICONTROL Edition > Documents]** de l&#39;opération concernée.

>[!NOTE]
>
>Si cet onglet n&#39;est pas présent, alors cette fonctionnalité n&#39;est pas prise en compte pour cette opération. Reportez-vous à la configuration du modèle d&#39;opération.
>   
>Voir à ce sujet la section [modèles d&#39;opération](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Cliquez ensuite sur **[!UICONTROL Ajouter une composition de diffusion]** et créez l&#39;arborescence des compositions pour l&#39;opération :

1. Cliquez avec le bouton droit sur la racine de l&#39;arborescence et choisissez **[!UICONTROL Nouveau > Compositions de diffusion]**.
1. Cliquez avec le bouton droit de la souris sur la composition que vous venez de créer et choisissez **[!UICONTROL Nouveau > Article]** ou **[!UICONTROL Nouveau > Champs de personnalisation]**.

![](assets/s_ncs_user_op_add_composition.png)

Une composition peut contenir des articles, des champs de personnalisation, des ressources et des offres :

* Les articles sont par exemple des documents physiques qui sont ici référencés et décrits, et seront joints à la diffusion.
* Les champs de personnalisation permettent de créer des éléments de personnalisation relatifs aux diffusions et non aux destinataires. Ainsi, il est possible de créer des valeurs qui seront utilisées dans les diffusions pour une cible spécifique (offre de bienvenue, pourcentage de réduction, etc.) Ils sont créés dans Adobe Campaign et importés dans la composition, via le lien **[!UICONTROL Importer des champs de personnalisation...]**.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   Ils peuvent également être créés directement dans la composition, en cliquant sur l&#39;icône **[!UICONTROL Ajouter]** située à droite de la zone de liste.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Les ressources sont des ressources marketing qui sont gérées dans le tableau de bord des ressources marketing accessible à partir du lien **[!UICONTROL Ressources]** de l&#39;univers **[!UICONTROL Campagnes]**.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Pour plus d&#39;informations sur les ressources marketing, voir la section [Gérer les ressources marketing](../../campaign/using/managing-marketing-resources.md).

#### Sélectionner une composition {#selecting-an-outline}

Pour chaque diffusion, vous pouvez sélectionner la composition à associer à partir de la section réservée à la configuration de l&#39;extraction, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_op_select_composition.png)

La composition sélectionnée est alors affichée dans la section inférieure de la fenêtre. Elle peut être éditée à partir de l&#39;icône située à droite du champ ou modifiée en utilisant la liste déroulante :

![](assets/s_ncs_user_op_select_composition_b.png)

L&#39;onglet **[!UICONTROL Résumé]** de la diffusion affiche également cette information :

![](assets/s_ncs_user_op_select_composition_c.png)

#### Résultat de l&#39;extraction {#extraction-result}

Dans le fichier extrait et transmis au prestataire, le nom de la composition et éventuellement ses caractéristiques (coût, description, etc.) sont ajoutés au contenu, selon les informations présentes dans le modèle d&#39;export associé au prestataire.

Dans l&#39;exemple suivant, le libellé, le coût prévisionnel estimé et la description de la composition associée à la diffusion seront ajoutés dans le fichier d&#39;extraction.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Le modèle d&#39;export doit être associé au prestataire sélectionné pour la diffusion concernée. Voir à ce sujet la section [Créer les prestataires et leurs structures de coûts](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures). 

>[!NOTE]
>
>Pour plus d&#39;informations sur les exports, reportez-vous à la section [Prise en main](../../platform/using/generic-imports-and-exports.md).

#### Comment créer un email dans une campagne {#create-email-video}

Cette vidéo explique comment créer une campagne et un email dans Adobe Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

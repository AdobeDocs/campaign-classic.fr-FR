---
product: campaign
title: Prestataires, stocks et budgets
description: Prestataires, stocks et budgets
role: User
feature: Budget Management, Campaigns
hide: true
exl-id: c60c4f86-a957-4c44-a0fe-39b6e3f0e5d6
TQID: https://experienceleague.adobe.com/0yoC9sZaXdvq9iEqK6NLnXBSS-B7aB9RisW5l8uJqtI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: afa4204e-6d08-4e29-bc35-26aafb656d48
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: f863efa9-030c-4466-a2b8-a52aea6b722c
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 2017
ht-degree: 100%

---

# Prestataires, stocks et budgets{#providers-stocks-and-budgets}

Adobe Campaign vous permet de définir des prestataires qui seront impliqués dans les traitements réalisés dans les campagnes.Les informations relatives aux prestataires et les structures de coûts qui leur sont associées sont définies par l’administrateur ou l’administratrice Adobe Campaign, à partir de la vue principale.Le prestataire est référencé au niveau de la diffusion et ses structures de coûts permettent le calcul des coûts associés à cette diffusion ainsi que la gestion des stocks concernés.

## Créer les prestataires et leurs structures de coûts {#creating-service-providers-and-their-cost-structures}

Chaque prestataire est enregistré dans une fiche avec ses coordonnées, ses modèles de prestation et les traitements associés.

Les prestataires sont paramétrés dans le noeud **[!UICONTROL Administration > Gestion de campagne > Prestataires]** de l&#39;arborescence.

Les traitements réalisés dans les diffusions sont assurés par des prestataires, notamment pour les canaux publipostage direct et mobile.Ces prestataires peuvent par exemple être impliqués dans l’impression ou la distribution de messages.Ces traitements impliquent des configurations et des coûts spécifiques à chaque prestataire.La configuration des prestataires se déroule en quatre étapes :

1. Création du prestataire dans Adobe Campaign.

   Voir [Ajouter un prestataire](#adding-a-service-provider).

1. Définition des postes et structures de coûts des modèles de prestation qui lui sont associés

   Voir [Définir les postes de coût](#defining-cost-categories) et [Définir la structure de coûts](#defining-the-cost-structure).

1. Configuration des traitements

   Voir [Paramétrer les traitements associés à la prestation](#configuring-processes-associated-with-a-service).

1. Référencement du prestataire au niveau des opérations

   Voir [Associer une prestation à une campagne](#associating-a-service-with-a-campaign).

### Création d&#39;un prestataire et de ses postes de coûts {#creating-a-service-provider-and-its-cost-categories}

#### Ajouter un prestataire {#adding-a-service-provider}

Vous pouvez créer autant de prestataires que nécessaire pour vos diffusions.Pour ajouter un prestataire, les étapes sont les suivantes :

1. Cliquez avec le bouton droit dans la liste des prestataires et choisissez **[!UICONTROL Nouveau]**, ou cliquez sur le bouton **[!UICONTROL Nouveau]** situé au-dessus de la liste des prestataires.
1. Dans la section inférieure de la fenêtre, indiquez son nom et ses coordonnées.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. Cliquez sur le bouton **[!UICONTROL Enregistrer]** pour ajouter le prestataire dans la liste.

#### Définir les postes de coût {#defining-cost-categories}

Vous devez associer des modèles de service à chaque prestataire.Dans ces modèles, vous devez d&#39;abord identifier les postes de coûts et, au besoin, le stock concerné. Vous devez ensuite créer les règles de calcul des coûts pour chaque poste, via les structures de coûts.

>[!NOTE]
>
>Voir à ce sujet la section [Définir la structure de coûts](#defining-the-cost-structure).

Un poste de coût est une entité contenant un ensemble de coûts éligibles pour un type de diffusion (e-mail, publipostage direct, etc.)ou pour une tâche.Les postes de coûts sont regroupés dans les modèles de prestations associés aux fournisseurs. Chaque fournisseur peut référencer un ou plusieurs modèles de prestation.

Pour créer un modèle de prestation et définir son contenu, les étapes sont les suivantes :

1. Dans l&#39;onglet **[!UICONTROL Prestations]** du prestataire, cliquez sur le bouton **[!UICONTROL Ajouter]** et nommez le modèle de prestation.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. Créez les catégories de coûts pour chaque type de traitement (diffusion par courrier/e-mail/etc. ou tâche). Pour ce faire, cliquez sur l’onglet **[!UICONTROL Catégories de coûts]**, puis sur le bouton **[!UICONTROL Ajouter]** et renseignez les paramètres de chaque catégorie de coût.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * Saisissez un libellé pour ce poste de coût et sélectionnez le type de traitement concerné : diffusion par **[!UICONTROL Courrier]**, **[!UICONTROL E-mail]**, **[!UICONTROL Mobile]**, **[!UICONTROL Téléphone]** ou **[!UICONTROL Tâche]**.
   * Cliquez sur le bouton **[!UICONTROL Ajouter]** pour définir les types de coûts associés à ce poste.
   * Au besoin, associez une ligne de stock à chaque type de coût afin de reporter automatiquement les quantités utilisées sur les stocks existant.

     >[!NOTE]
     >
     >Les lignes de stock sont définies dans le noeud **[!UICONTROL Gestion des stocks]**.\
     >Voir à ce sujet la section [Gestion des stocks et des commandes](#stock-and-order-management).

1. Vous pouvez présélectionner une valeur pour ce poste de coût. Elle sera proposée par défaut dans les postes de coût des prestataires (au lieu d&#39;une valeur vide). Pour ce faire, sélectionnez l’option dans la colonne **[!UICONTROL Sélectionné]** pour le type de poste concerné :

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   Au niveau de la diffusion, la valeur sera sélectionnée par défaut :

   ![](assets/s_ncs_user_supplier_default_cost.png)

### Définir la structure de coûts {#defining-the-cost-structure}

Une structure de coûts indique, pour chaque type de coût, les règles de calcul à appliquer.

Cliquez sur l’onglet **[!UICONTROL Structure de coûts]** pour configurer le calcul des coûts pour chaque catégorie et type de coût. Cliquez sur **[!UICONTROL Ajouter]** et saisissez la structure de coûts.

![](assets/s_ncs_user_supplier_node_04.png)

* Pour créer la structure de coûts, sélectionnez dans les listes déroulantes le type de message et la catégorie de coût concerné, ainsi que le type de coût auquel s’appliquera la règle de calcul. Le contenu de ces listes déroulantes reprend les informations renseignées à partir de l’onglet **[!UICONTROL Catégories de coût]**.

  Vous devez attribuer un libellé à la structure de coûts. Par défaut, elle présente la composition de diffusion suivante : **Catégorie de coût - Type de coût**.

  Vous pouvez toutefois le renommer : saisissez alors directement la valeur souhaitée dans le champ **[!UICONTROL Libellé]**.

* La formule de calcul du coût est définie dans la section inférieure de la fenêtre.

  Cette formule peut être fixe (quel que soit le nombre de message), ou calculée en fonction du nombre de messages.

  Lorsqu&#39;elle dépend du nombre de messages, la structure de calcul du coût peut être **[!UICONTROL Linéaire]**, **[!UICONTROL Linéaire par seuil]** ou **[!UICONTROL Constant par seuil]**.

#### Structure linéaire {#linear-structure}

Si le montant est toujours le même, pour un message (ou un lot de messages), et ce, quel que soit le nombre de messages total, sélectionnez un type de structure **[!UICONTROL Linéaire]** et saisissez le coût de chaque message.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

Si ce montant s&#39;applique à un lot de messages, indiquez le nombre de messages concernés dans le champ **[!UICONTROL pour]**.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### Structure linéaire par seuil {#linear-structure-by-threshold}

Si le montant s’applique par seuil pour chaque message, vous devez définir une structure de calcul **[!UICONTROL Linéaire par seuil]**.Dans ce type de structure de coûts, chaque message coûtera 0,13, par exemple, si le nombre total de messages se situe entre 1 et 100, puis coûtera 0,12 entre 100 et 1 000 messages envoyés, et 0,11 au-delà de 1 000 messages.

Le paramétrage sera le suivant :

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

Pour ajouter un seuil, cliquez sur le bouton **[!UICONTROL Ajouter]** situé à droite de la liste.

#### Structure constante par seuil {#constant-structure-by-threshold}

Enfin, vous pouvez configurer un calcul des coûts en fonction du nombre total de messages. Pour ce faire, sélectionnez une structure de calcul **[!UICONTROL Constante par seuil]**. Par exemple, le coût sera fixé à 12 pour 1 à 100 messages ; à 100 pour une diffusion de 101 à 1000 messages, et à 500 pour toute diffusion de plus de 1 000 messages, quel que soit le nombre total.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### Paramétrer les traitements associés à la prestation {#configuring-processes-associated-with-a-service}

Vous pouvez associer des informations sur les traitements liés à une prestation depuis l&#39;onglet **[!UICONTROL Traitements]**.

Pour cela, cliquez sur l&#39;onglet **[!UICONTROL Traitements]** pour paramétrer l&#39;envoi des informations au routeur.

![](assets/s_ncs_user_supplier_node_02.png)

* La section **[!UICONTROL Extraction de fichier]** indique le modèle d’export utilisé pour la diffusion lorsque cette prestation est sélectionnée. Vous pouvez indiquer le nom du fichier de sortie dans le champ **[!UICONTROL Fichier d’extraction]**. Le bouton situé à droite du champ permet d’insérer des variables.

  ![](assets/s_ncs_user_supplier_node_02a.png)

* La section **[!UICONTROL E-mail de notification]** vous permet d’indiquer le modèle de notification aux prestataires après l’envoi des fichiers.Sélectionnez le modèle utilisé pour créer le message d’alerte et le groupe de personnes destinataires.

  Par défaut, les modèles de diffusion pour les messages de notification sont enregistrés sous le noeud **[!UICONTROL Administration > Gestion de campagne > Modèles des diffusions techniques]**, accessible depuis la vue globale.

* La section **[!UICONTROL Post-traitement]** vous permet de sélectionner le workflow à lancer une fois la diffusion approuvée.Si un modèle de workflow est entré, une instance de workflow est automatiquement créée, puis lancée dès que la validation prend effet.Ce workflow peut, par exemple, envoyer le fichier d’extraction à un prestataire externe pour traitement.

### Associer une prestation à une opération {#associating-a-service-with-a-campaign}

Les services sont associés aux campagnes via les diffusions ou les tâches.Les prestataires sont liés aux modèles de diffusion afin de proposer leurs services dans les diffusions créées à l’aide de ce modèle.

Lorsqu’un service est sélectionné, les postes de coûts correspondant au type de diffusion (publipostage direct, e-mail, etc.)sont automatiquement indiqués dans le tableau central, ainsi que les options de traitement qui ont été définies.

>[!NOTE]
>
>Si aucune catégorie de coût n’est affichée lorsqu’une prestation est sélectionnée, cela signifie qu’aucune catégorie de coût n’a été définie pour ce type de traitement. Par exemple, pour une diffusion e-mail, si aucun type de catégorie de coût **[!UICONTROL E-mail]** n’a été défini, aucune catégorie ne s’affichera et la sélection du service n’aura aucun effet.

* Pour une diffusion courrier, vous pouvez sélectionner le service à partir de la fenêtre de configuration.

  ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* Pour une diffusion sur canaux mobiles ou par téléphone, le mode de sélection est le même.
* Pour une diffusion par email, la prestation est sélectionnée à partir de l&#39;onglet **[!UICONTROL Avancé]** des propriétés de la diffusion, comme dans l&#39;exemple ci-dessous :

  ![](assets/s_ncs_user_supplier_email_delivery_select.png)

La colonne **[!UICONTROL Montant à surcharger]** permet d&#39;ajouter un coût pour ce poste dans le contexte de la diffusion ou de la tâche concernée.

Vous pouvez rendre obligatoire la sélection d&#39;un type de coût lors de la définition des postes de coût au niveau d&#39;une diffusion : Pour ce faire, sélectionnez **[!UICONTROL Un type de coût doit être sélectionné]**.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## Gestion des stocks et des commandes {#stock-and-order-management}

Les types de coûts peuvent être associés à des lignes de stocks afin de gérer les alertes, suivre les approvisionnements et lancer des commandes.

Pour mettre en place la gestion des stocks et des commandes dans Adobe Campaign, et alerter les opérateurs en cas d&#39;approvisionnement insuffisant pour la réalisation d&#39;une diffusion, les étapes sont les suivantes :

1. Création des stocks et référencement des prestataires associés.

   Voir [Créer un stock](#creating-a-stock).

1. Ajouter les lignes de stocks

   Voir [Ajouter les lignes de stock](#adding-stock-lines).

1. Notification des opérateurs en cas d&#39;alerte

   Voir [Alerter les opérateurs](#alerting-operators).

1. Commandes et approvisionnement

   Voir [Commandes](#orders).

### Gestion des stocks {#stock-management}

Adobe Campaign peut alerter un groupe d’opérateurs et d’opératrices si le stock est épuisé ou a atteint un seuil minimum. Les niveaux de stock sont accessibles via le lien **[!UICONTROL Stocks]** de l’onglet **[!UICONTROL Campagnes]** à partir du lien **[!UICONTROL Autres choix]** dans la zone de navigation.

![](assets/s_ncs_user_stocks_view.png)

#### Créer un stock {#creating-a-stock}

Pour créer un nouveau stock, les étapes sont les suivantes :

1. Cliquez sur le bouton **[!UICONTROL Créer]** situé au-dessus de la liste des stocks.
1. Saisissez le libellé du stock et sélectionnez dans la liste déroulante le prestataire auquel il est associé.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >Voir à ce sujet la section [Créer les prestataires et leurs structures de coûts](#creating-service-providers-and-their-cost-structures).

#### Ajouter les lignes de stocks {#adding-stock-lines}

Un stock comprend différentes lignes de stock.Une ligne de stock contient une quantité initiale de ressources qui seront consommées par les diffusions.Chaque ligne de stock indique la quantité consommée, la quantité en stock et la quantité commandée.

Lorsque vous créez un stock, cliquez sur l&#39;onglet **[!UICONTROL Lignes de stock]** pour ajouter des lignes de stocks.

![](assets/s_ncs_user_stocks_display_line.png)

Une fois le stock créé, cliquez sur un stock pour l&#39;éditer et utilisez son tableau de bord pour créer et visualiser les lignes de stock.

Cliquez sur le bouton **[!UICONTROL Créer]** pour définir les paramètres du stock.

![](assets/s_ncs_user_stocks_new_line.png)

* Indiquez la quantité initialement en stock dans le champ **[!UICONTROL Stock initial]**. Les champs **[!UICONTROL Consommé]** et **[!UICONTROL En stock]** sont calculés automatiquement et mis à jour au fil des campagnes.

  ![](assets/s_ncs_user_stocks_create_line.png)

* Indiquez, dans le champ **[!UICONTROL Niveau d’alerte]**, le seuil à partir duquel il faudra alerter les opérateurs et opératrices pour le renouvellement.Lorsque le niveau d’alerte est atteint, un message d’avertissement est affiché dans la fenêtre de validation des diffusions qui utilisent ce stock.

#### Associer un stock à des postes de coûts {#associating-a-stock-with-cost-categories}

Au niveau du prestataire, dans une prestation, une ligne de stock peut être référencée par l&#39;un de ses postes de coûts, comme ci-dessous :

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Tracking des stocks {#stock-tracking}

#### Alerter les opérateurs {#alerting-operators}

Une alerte s’affiche lorsqu’un stock référencé dans une diffusion est insuffisant.Par exemple, l’alerte suivante s’affiche lors de l’approbation d’un fichier d’extraction :

![](assets/s_ncs_user_stocks_valid_alert.png)

#### Les commandes {#orders}

Le sous-onglet **[!UICONTROL Commandes]** permet de visualiser les commandes en cours et d&#39;enregistrer de nouvelles commandes.

![](assets/s_ncs_user_stocks_edit_from_board.png)

Pour enregistrer une commande, éditez la ligne de stock visée, cliquez sur le bouton **[!UICONTROL Ajouter]** et indiquez la date de livraison et la quantité commandée.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>Une fois la date de diffusion atteinte, la ligne de stock en commande disparaît automatiquement et la quantité renseignée dans le champ **[!UICONTROL Volume en commande]** passe dans l’onglet **[!UICONTROL Tracking]**.Cette quantité est automatiquement ajoutée au volume de stock.

![](assets/s_ncs_user_stocks_node_08.png)

L’onglet **[!UICONTROL Consommations]** contient le volume consommé par campagne.Les informations de cet onglet sont automatiquement renseignées en fonction des diffusions réalisées.Cliquez sur le bouton **[!UICONTROL Modifier]** pour ouvrir la campagne concernée.

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## Calcul des budgets {#calculating-budgets}

### Principe {#principle}

Les coûts sont gérés pour les diffusions et les campagnes.En fonction de l’état d’avancement, ces coûts seront répercutés sur les budgets.

Les coûts de diffusion d’une opération sont consolidés au niveau de la campagne et les coûts de toutes les campagnes d’un programme sont répercutées au niveau du programme auquel elles sont associées.Les rapports dédiés permettent de suivre les budgets pour l’ensemble de la plateforme ou pour chaque plan et chaque programme.

### Mise en œuvre {#implementation}

Dans une campagne, lorsque vous sélectionnez le budget, vous devez saisir le montant initial.Les coûts calculés seront mis à jour automatiquement en fonction du degré d’engagement des montants renseignés (dépenses réalisées, prévues, réservées, engagées).Voir [Calcul des montants](../../mrm/using/controlling-costs.md#calculating-amounts).

>[!NOTE]
>
>La procédure de création de budgets est présentée dans [Créer un budget](../../mrm/using/controlling-costs.md#creating-a-budget).

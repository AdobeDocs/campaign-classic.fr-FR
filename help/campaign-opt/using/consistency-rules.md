---
product: campaign
title: Règles de cohérence
description: Découvrez comment utiliser les règles de cohérence dans Adobe Campaign
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Typology Rules, Campaigns
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: ht
source-wordcount: '830'
ht-degree: 100%

---

# Règles de cohérence{#consistency-rules}

## À propos des règles de cohérence {#about-consistency-rules}

Adobe Campaign permet d&#39;assurer la cohérence des communications au travers d&#39;un ensemble de règles regroupées dans des typologies de campagne. Ces règles ont pour objectif d&#39;assurer un contrôle sur les diffusions envoyées aux destinataires, leur volume, leur nature, leur pertinence, etc.

Des règles de **capacité** peuvent par exemple éviter de surcharger la plateforme concernée par la diffusion. Par exemple, une offre spéciale contenant un lien de téléchargement ne doit pas s’adresser au même moment à une population trop nombreuse afin de ne pas saturer le serveur, une campagne téléphonique ne doit pas excéder la capacité de traitement du centre d’appels, etc. Pour plus dʼinformations, consultez la section [Contrôle de la capacité](#controlling-capacity).

## Contrôle de la capacité {#controlling-capacity}

Avant de diffuser des messages, vous devez vous assurer que votre organisation a la capacité de gérer l&#39;envoi (infrastructure matérielle), les réponses que la diffusion peut générer (messages entrants), le nombre d&#39;appels à assurer pour contacter les abonnés (capacités de traitement du centre d&#39;appels), etc.

Pour cela, vous devez créer des règles de typologie de type **[!UICONTROL Capacité]**.

Dans l&#39;exemple suivant, nous allons créer une règle de typologie pour une campagne de fidélisation par téléphone. Elle permettra de limiter le nombre de messages à 20 par jour, c&#39;est-à-dire la capacité de traitement des appels par un centre d&#39;appels. Cette règle sera ensuite appliquée à deux diffusions afin de suivre son effet par le biais des logs.

Pour créer une règle de capacité, procédez comme suit :

1. Sous le nœud **[!UICONTROL Administration > Gestion de campagne > Gestion des typologies > Règles de typologie]**, cliquez sur **[!UICONTROL Nouveau]**.
1. Sélectionnez un type de règle **[!UICONTROL Capacité]**.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Dans l&#39;onglet **[!UICONTROL Capacité]**, créez les lignes de disponibilité : dans notre exemple, elles correspondent à des périodes pendant lesquelles les appels peuvent être passés. Sélectionnes 24 heures et saisissez 150 dans la quantité initiale, ce qui indique que le centre d&#39;appels peut traiter 150 appels par jour.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Les lignes de disponibilité n&#39;ont qu&#39;un caractère indicatif. Si vous devez exclure des messages lorsque la limite de capacité est atteinte, reportez-vous à [cette section](#exclude-messages-when-capacity-limit-reached).

1. Associez cette règle à une typologie, puis référencez cette typologie au niveau de la diffusion pour appliquer cette règle de capacité. Pour plus d&#39;informations, consultez [cette section](applying-rules.md#applying-a-typology-to-a-delivery).
1. Vous pouvez suivre la consommation dans les onglets **[!UICONTROL Consommations]** et **[!UICONTROL Capacité]**.

   Lorsqu&#39;une règle est utilisée dans une diffusion, les colonnes **[!UICONTROL Consommé]** et **[!UICONTROL Restant]** indiquent la charge utilisée, comme dans l&#39;exemple ci-dessous :

   ![](assets/campaign_opt_create_capacity_03.png)

   Pour plus d’informations, consultez [cette section](#monitoring-consumption).

## Définition de la charge maximale {#defining-the-maximum-load}

Pour définir la charge maximale, vous devez définir les lignes de disponibilité. Pour ce faire, deux options sont disponibles : vous pouvez créer manuellement une ou plusieurs lignes de disponibilité (consultez la section [Ajout de lignes de disponibilité une par une](#adding-availability-lines-one-by-one)) ou créer des plages de disponibilité. Il est possible d’automatiser la fréquence de ces périodes (consultez la section [Ajout dʼun ensemble de lignes de disponibilité](#add-a-set-of-availability-lines)).

### Ajout de lignes de disponibilité une par une {#adding-availability-lines-one-by-one}

Pour créer unitairement une ligne de disponibilité, cliquez sur le bouton **[!UICONTROL Ajouter]** et sélectionnez l&#39;option **[!UICONTROL Ajouter une ligne de disponibilité]**. Renseignez la plage de disponibilité et la charge disponible.

![](assets/campaign_opt_create_capacity_02.png)

Vous pouvez ajouter autant de lignes que nécessaires pour correspondre à votre capacité de traitement.

### Ajouter un ensemble de lignes de disponibilité {#add-a-set-of-availability-lines}

Pour définir des plages de disponibilité sur une période donnée, cliquez sur le bouton **[!UICONTROL Ajouter]** et sélectionnez l&#39;option **[!UICONTROL Ajouter un ensemble de lignes de disponibilité]**. Indiquez la durée de chaque plage et le nombre de plages à créer.

Pour automatiser la fréquence de création des plages, cliquez sur le bouton **[!UICONTROL Changer]** et définissez la planification des plages.

![](assets/campaign_opt_create_capacity_07.png)

Par exemple, nous allons définir un planning afin de créer les plages de disponibilité pour tous les jours ouvrés, pour 10 appels par heure, entre 9h et 17h. Pour cela, les étapes de configuration sont les suivantes :

1. Sélectionnez le type de périodicité et les jours et heures de validité :

   ![](assets/campaign_opt_create_capacity_08.png)

1. Indiquez les dates de validité :

   ![](assets/campaign_opt_create_capacity_09.png)

1. Vérifiez ce planning avant de le valider :

   ![](assets/campaign_opt_create_capacity_10.png)

Le workflow **[!UICONTROL Prévisionnel]** crée automatiquement toutes les lignes correspondantes.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>Il est recommandé de créer les lignes de disponibilité à partir d&#39;un import de fichier. Cet onglet permet alors de visualiser et contrôler les lignes de consommation.

## Exclure des messages lorsque la limite de capacité est atteinte {#exclude-messages-when-capacity-limit-reached}

Les lignes de disponibilité n&#39;ont qu&#39;un caractère indicatif. Pour exclure les messages excédentaires, cochez l&#39;option **[!UICONTROL Exclure de la cible les messages en sur-capacité]**. Dans ce cas, la capacité ne pourra pas être dépassée. Pour la même population que dans l&#39;exemple précédent, la consommation et la capacité restante ne pourront pas excéder la quantité initiale :

![](assets/campaign_opt_create_capacity_04.png)

Le nombre de messages à traiter est réparti proportionnellement sur la totalité de la plage de disponibilité définie. C&#39;est le cas notamment pour les centres d&#39;appels dont le nombre maximum d&#39;appels par jour est plafonné. Dans le cas des diffusions email, l&#39;option **[!UICONTROL Ne pas limiter la capacité instantanée de diffusion]** permet d&#39;ignorer cette plage de disponibilité et d&#39;envoyer vos emails en masse au même moment.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>En cas de surcharge, les messages conservés sont sélectionnés selon la formule définie au niveau des propriétés de la diffusion.

![](assets/campaign_opt_create_capacity_06.png)

## Suivi de la consommation {#monitoring-consumption}

Par défaut, les règles de capacité n&#39;ont qu&#39;un caractère indicatif. Sélectionnez l&#39;option **[!UICONTROL Exclure de la cible les messages en sur-capacité]** pour que la charge définie ne puisse pas être dépassée. Dans ce cas, les messages excédentaires seront automatiquement exclus des diffusions utilisant cette règle de typologie.

Pour suivre les consommations, consultez les valeurs affichées dans la colonne **[!UICONTROL Consommé]** de l&#39;onglet **[!UICONTROL Capacité]** de la règle de typologie.

![](assets/campaign_opt_create_capacity_04.png)

Pour visualiser les lignes de consommation, cliquez sur l&#39;onglet **[!UICONTROL Consommations]** de la règle.

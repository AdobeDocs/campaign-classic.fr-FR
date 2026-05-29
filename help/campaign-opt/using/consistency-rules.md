---
product: campaign
title: Règles de cohérence
description: Découvrez comment utiliser les règles de cohérence dans Adobe Campaign
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
TQID: https://experienceleague.adobe.com/rkCdxvBXQAvuM0hpIt2nQ35lxDBK2XpS-0tHN7NzQVI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: e5fb657f-3c0a-4fcc-9980-3589a23ab4de
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 830
ht-degree: 69%

---

# Règles de cohérence{#consistency-rules}

## À propos des règles de cohérence {#about-consistency-rules}

Adobe Campaign garantit la cohérence des communications grâce à un ensemble de règles contenues dans les typologies de campagne. Leur objectif est de contrôler les diffusions envoyées aux destinataires, comme le volume, la nature, la pertinence, etc.

Les règles **Capacité** par exemple peuvent éviter de surcharger la plateforme concernée par la diffusion des messages. Par exemple, les offres spéciales contenant un lien de téléchargement ne doivent pas être envoyées à un trop grand nombre de personnes à la fois, afin d’éviter de saturer le serveur ; les campagnes téléphoniques ne doivent pas dépasser la capacité de traitement des centres d’appels, etc. Pour plus d&#39;informations, consultez la section [Contrôler la capacité](#controlling-capacity).

## Contrôle de la capacité {#controlling-capacity}

Avant de diffuser des messages, vous devez vous assurer que votre organisation a la capacité de gérer l&#39;envoi (infrastructure matérielle), les réponses que la diffusion peut générer (messages entrants), le nombre d&#39;appels à assurer pour contacter les abonnés (capacités de traitement du centre d&#39;appels), etc.

Pour cela, vous devez créer des règles de typologie de type **[!UICONTROL Capacité]**.

Dans l’exemple suivant, nous créons une règle de typologie pour une campagne de fidélité téléphonique. Nous limitons le nombre des messages à 20 par jour, ce qui correspond à la capacité de traitement quotidienne d’un centre d’appel. Une fois la règle appliquée à deux diffusions, nous pouvons suivre la consommation via les logs.

Pour créer une règle de capacité, procédez comme suit :

1. Sous le nœud **[!UICONTROL Administration > Gestion de campagne > Gestion des typologies > Règles de typologie]**, cliquez sur **[!UICONTROL Nouveau]**.
1. Sélectionnez un type de règle **[!UICONTROL Capacité]**.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Dans l&#39;onglet **[!UICONTROL Capacité]**, créez les lignes de disponibilité : dans notre exemple, il s&#39;agit des périodes temporelles pendant lesquelles des appels peuvent être effectués. Sélectionnez une période de 24 heures et saisissez la quantité initiale de 150, ce qui signifie que le centre d’appels peut traiter 150 appels par jour.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Les lignes de disponibilité n&#39;ont qu&#39;un caractère indicatif. Si vous devez exclure des messages lorsque la limite de capacité est atteinte, reportez-vous à [cette section](#exclude-messages-when-capacity-limit-reached).

1. Associez cette règle à une typologie, puis référencez cette typologie au niveau de la diffusion pour appliquer cette règle de capacité. Pour plus d’informations, consultez [cette section](applying-rules.md#applying-a-typology-to-a-delivery).
1. Vous pouvez suivre la consommation dans les onglets **[!UICONTROL Consommations]** et **[!UICONTROL Capacité]**.

   Lorsqu&#39;une règle est utilisée dans une diffusion, les colonnes **[!UICONTROL Consommé]** et **[!UICONTROL Restant]** indiquent la charge utilisée, comme dans l&#39;exemple ci-dessous :

   ![](assets/campaign_opt_create_capacity_03.png)

   Pour plus d’informations, consultez [cette section](#monitoring-consumption).

## Définition de la charge maximale {#defining-the-maximum-load}

Pour définir la charge maximale, vous devez définir les lignes de disponibilité. Pour ce faire, deux options sont disponibles : vous pouvez créer manuellement une ou plusieurs lignes de disponibilité (consultez la section [Ajout de lignes de disponibilité une par une](#adding-availability-lines-one-by-one)) ou créer des plages de disponibilité. Il est possible d’automatiser la fréquence de ces périodes (consultez la section [Ajout dʼun ensemble de lignes de disponibilité](#add-a-set-of-availability-lines)).

### Ajout de lignes de disponibilité une par une {#adding-availability-lines-one-by-one}

Pour créer une ligne de disponibilité, cliquez sur le bouton **[!UICONTROL Ajouter]** et sélectionnez **[!UICONTROL Ajouter une ligne de disponibilité]**. Entrez la période de disponibilité et la charge disponible.

![](assets/campaign_opt_create_capacity_02.png)

Vous pouvez ajouter autant de lignes que nécessaires pour correspondre à votre capacité de traitement.

### Ajouter un ensemble de lignes de disponibilité {#add-a-set-of-availability-lines}

Pour définir les périodes de disponibilité pour une plage de disponibilité donnée, cliquez sur le bouton **[!UICONTROL Ajouter]** et sélectionnez l&#39;option **[!UICONTROL Ajouter un ensemble de lignes de disponibilité]**. Indiquez une durée pour chaque période et le nombre de périodes à créer.

Pour automatiser la fréquence de création des plages, cliquez sur le bouton **[!UICONTROL Changer]** et définissez la planification des plages.

![](assets/campaign_opt_create_capacity_07.png)

Par exemple, définissons un planning pour créer des périodes de disponibilité pour tous les jours ouvrés à raison de 10 appels par heure entre 9h et 17h. Pour cela, les étapes sont les suivantes :

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
>Nous vous recommandons de créer des lignes de disponibilité via des imports de fichiers. Cet onglet permet de visualiser et vérifier les lignes de consommation.

## Exclure des messages lorsque la limite de capacité est atteinte {#exclude-messages-when-capacity-limit-reached}

Les lignes de disponibilité n’ont qu’un caractère indicatif. Pour exclure les messages excédentaires, cochez l’option **[!UICONTROL Exclure de la cible les messages en sur-capacité]**. Dans ce cas, la capacité ne pourra pas être dépassée. Pour la même population que dans l’exemple précédent, la consommation et la capacité restante ne pourront pas excéder la quantité initiale :

![](assets/campaign_opt_create_capacity_04.png)

Le nombre maximum de messages qui peuvent être traités est réparti proportionnellement sur l’ensemble de la plage de disponibilité définie. Cela est particulièrement adapté aux centres d’appels, car leur nombre maximum d’appels par jour est limité. Dans le cas de diffusions par e-mail, l’option **[!UICONTROL Ne pas limiter la capacité instantanée de diffusion]** vous permet d’ignorer cette plage de disponibilité et d’envoyer vos e-mails en même temps.

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

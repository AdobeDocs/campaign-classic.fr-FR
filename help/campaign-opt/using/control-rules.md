---
product: campaign
title: Règles de contrôle
description: Découvrez comment utiliser les règles de contrôle dans Adobe Campaign
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
TQID: https://experienceleague.adobe.com/zeKJZ7Y-qtGpPtZ6tUPN42ISVU6Fh6wpOuhfcXDsyAA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
subfeature_v2: id: e5fb657f-3c0a-4fcc-9980-3589a23ab4de
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 397
ht-degree: 82%

---

# Règles de contrôle{#control-rules}

## Analyse et règles de contrôle d’arbitrage {#analysis-and-arbitration-control-rules}

Les règles de contrôle permettent de s&#39;assurer de la validité et la qualité des messages avant leur diffusion : bon affichage des caractères, taille des SMS, format des adresses, etc.

Un ensemble de règles d&#39;usine permet d&#39;effectuer les contrôles usuels. Ces contrôles (affichés en gras dans l’interface) sont les suivants :

* **[!UICONTROL Validation du sujet]** (email) : vérifie que le sujet et l&#39;adresse de l&#39;expéditeur du message ne contiennent pas de caractères spéciaux, susceptibles de poser des problèmes sur certains agents mail.
* **[!UICONTROL Validation des libellés d&#39;URL]** (email) : vérifie la présence d&#39;un libellé pour chaque URL de tracking.
* **[!UICONTROL Validation des URL]** (email) : vérifie les URL de tracking (présence du caractère &quot;&amp;&quot;).
* **[!UICONTROL Validation de la taille du message]** (mobile) : vérifie la taille des messages SMS.
* **[!UICONTROL Vérification de la durée de validité]** (email) : vérifie que la durée de validité de la diffusion est suffisante pour l&#39;envoi de tous les messages.
* **[!UICONTROL Vérification de la taille des BAT]** (tous les canaux) : génère un message d&#39;erreur si la population cible d&#39;un BAT dépasse 100 destinataires.
* **[!UICONTROL Vérification de la planification des vagues]** (email) : vérifie que la dernière vague d&#39;envoi est planifiée avant la fin de validité de la diffusion, lorsque la diffusion est envoyée en plusieurs vagues.
* **[!UICONTROL Validation du lien de désinscription]** (email) : vérifie la présence d&#39;au moins une URL de désinscription (URL de type opt-out) dans chacun des contenus (HTML et Texte).

## Créer une règle de contrôle {#creating-a-control-rule}

Afin de répondre à vos besoins, vous pouvez définir de nouvelles règles de contrôle. Pour cela, créez une règle de typologie de type **[!UICONTROL Contrôle]** et saisissez la formule de contrôle en SQL dans l&#39;onglet **[!UICONTROL Code]**.

**Exemple:**

Dans l&#39;exemple suivant, nous allons créer une règle pour empêcher l&#39;envoi d&#39;une offre SMS à plus de 100 destinataires. Cette règle sera associée à une typologie de campagne, puis aux diffusions SMS pour lesquelles l&#39;offre concernée est disponible.

Les étapes sont les suivantes :

1. Créez une règle de typologie de type **[!UICONTROL Contrôle]**. Sélectionnez un niveau d&#39;alerte de type Avertissement (**[!UICONTROL Warning]**).

   ![](assets/campaign_opt_create_control_01.png)

1. Dans l&#39;onglet **[!UICONTROL Code]**, saisissez le script permettant d&#39;appliquer la limite souhaitée, comme dans l&#39;exemple suivant :

   ![](assets/campaign_opt_create_control_02.png)

   Ce script permet de générer un avertissement lorsque la cible de la diffusion excède 100 contacts :

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. Associez cette règle à une typologie de campagne et référencez cette typologie dans la diffusion SMS concernée.

   ![](assets/campaign_opt_create_control_03.png)

1. Lors de la phase d&#39;analyse de la diffusion, la règle est appliquée et un avertissement est généré, s&#39;il y a lieu.

   ![](assets/campaign_opt_create_control_04.png)

   La diffusion est toutefois prête à être envoyée.

   Si vous augmentez le niveau d&#39;alerte, la diffusion ne pourra pas être démarrée.

   ![](assets/campaign_opt_create_control_05.png)

   A la fin de l&#39;analyse, le bouton **[!UICONTROL Confirmer l&#39;envoi]** ne sera pas disponible.

   ![](assets/campaign_opt_create_control_06.png)

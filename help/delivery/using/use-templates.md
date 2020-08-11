---
title: Utiliser des modèles de diffusion
seo-title: Utiliser des modèles de diffusion
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 44%

---


# Utilisez les modèles {#use-templates}

Les modèles de diffusion accroissent l&#39;efficacité en offrant des configurations prêtes à l&#39;emploi pour les types d&#39;activité les plus courants. Grâce aux modèles, les marketeurs peuvent déployer plus rapidement de nouvelles campagnes avec une personnalisation minimale.

Learn more about delivery templates in [this section](../../delivery/using/creating-a-delivery-template.md).

## Commencer avec les modèles de diffusion {#gs-templates}

A [delivery template](../../delivery/using/creating-a-delivery-template.md) enables you to define once a set of technical and functional properties that suit your needs and that can be reused for future deliveries. Vous pouvez ensuite gagner du temps et normaliser les diffusions si nécessaire.

Si vous gérez plusieurs marques dans Adobe Campaign, Adobe recommande de disposer d’un sous-domaine par marque. Une banque peut, par exemple, avoir plusieurs sous-domaines qui correspondent à chacune de ses agences régionales. Si une banque possède le domaine bluebank.com, ses sous-domaines peuvent être @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Disposer d’un modèle de diffusion par sous-domaine vous permet de toujours utiliser les paramètres préconfigurés adéquats pour chaque marque et d’éviter ainsi des erreurs tout en gagnant du temps.

**Conseil**:  Pour éviter les erreurs de configuration dans le Campaign Standard, nous vous recommandons de duplicata d’un modèle natif et de modifier ses propriétés plutôt que de créer un nouveau modèle.

## Configurer les adresses

* L&#39;adresse de l&#39;expéditeur est obligatoire pour permettre l&#39;envoi d&#39;un email.

* Certains FAI vérifient la validité de l’adresse de l’expéditeur avant d’accepter les messages.

* Une adresse erronée peut causer un refus de la part du serveur receveur. Vous devez vous assurer qu’une adresse correcte est bien renseignée.

* L&#39;adresse doit identifier explicitement l&#39;expéditeur. Le domaine doit appartenir à l&#39;expéditeur et être enregistré auprès de lui.

* Adobe recommande de créer des comptes email qui correspondent aux adresses indiquées pour les envois et les réponses. Parlez-en avec votre administrateur du système de messagerie.

Pour configurer les adresses dans l’interface Campaign, procédez comme suit :

1. In the [delivery template](../../delivery/using/creating-a-delivery-template.md), click the **[!UICONTROL From]** link. Dans la fenêtre **[!UICONTROL Paramètres d&#39;en-tête email]**, renseignez les champs suivants :

   ![](assets/d_best_practices_email_header.png)

1. Dans le champ Adresse **[!UICONTROL de l’]** expéditeur, assurez-vous que le domaine d’adresse est identique au sous-domaine que vous avez délégué à l’Adobe. Vous pouvez modifier la partie qui précède le signe « @ », mais pas l’adresse du domaine.

1. Dans le champ **[!UICONTROL De]** , utilisez un nom facilement identifiable par les destinataires, tel que le nom de votre marque, pour augmenter le taux d’ouverture de vos diffusions. Pour améliorer davantage l&#39;expérience du destinataire, vous pouvez ajouter le nom d&#39;une personne, par exemple &quot;Emma from Megastore&quot;.

1. Dans les champs de texte **[!UICONTROL d&#39;adresse de]** réponse, l&#39;adresse de l&#39;expéditeur est utilisée par défaut pour les réponses. Toutefois, l’Adobe recommande d’utiliser une adresse réelle existante, telle que l’assistance clientèle de votre marque. Ainsi, si un destinataire envoie une réponse, l’assistance clientèle sera en mesure de la traiter.

### Configurer une population témoin

Une fois que la diffusion est envoyée, vous pouvez comparer le comportement des destinataires exclus à celui des destinataires qui ont reçu la diffusion. Vous pouvez ensuite mesurer l&#39;efficacité de vos campagnes. En savoir plus sur les Populations témoins [cette section](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Pour configurer une Population témoin, cliquez sur le lien **[!UICONTROL À]** . In the **[!UICONTROL Select target]** window, select the **[!UICONTROL Control group]** tab. Vous pouvez extraire une partie de la cible, par exemple un échantillon aléatoire de 5 %.

![](assets/d_best_practices_control_group.png)

## Utiliser des typologies pour appliquer des filtres ou des règles de contrôle

Une typologie contient les règles de vérification qui sont appliquées lors de la phase d&#39;analyse, avant tout envoi.

In the **[!UICONTROL Typology]** tab of the template&#39;s properties, change the default typology according to your needs.

Par exemple, pour mieux contrôler le trafic sortant, vous pouvez définir les adresses IP à utiliser en définissant une affinité par sous-domaine et en créant une typologie par affinité. Les affinités sont définies dans le fichier de configuration de l’instance. Contactez votre administrateur Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

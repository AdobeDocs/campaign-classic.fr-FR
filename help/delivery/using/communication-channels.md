---
product: campaign
title: Canaux de communication
description: Création de diffusions pour envoyer des messages personnalisés sur différents canaux
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 100%

---

# Canaux de communication{#communication-channels}

![](../../assets/common.svg)

Avec Adobe Campaign, vous pouvez réaliser des campagnes cross-canal, y compris sous forme d’emails, SMS, messages LINE, notifications push et courrier, et mesurer leur efficacité à l’aide de différents [rapports](../../reporting/using/delivery-reports.md) dédiés. Ces messages sont conçus et envoyés à l&#39;aide de diffusions, et peuvent être personnalisés pour chaque destinataire.

Les principales fonctionnalités comprennent le ciblage, la définition et la personnalisation des messages, la mise en œuvre des communications et les rapports opérationnels connexes. Le principal point d&#39;accès fonctionnel est l&#39;assistant de diffusion. Ce point d’accès permet d’accéder à de multiples fonctionnalités proposées par Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign offre un ensemble d’outils destinés à surveiller votre délivrabilité et à optimiser l’envoi d’emails. En savoir plus dans [cette section](about-deliverability.md).

L&#39;envoi d&#39;une diffusion peut être automatisé en préparant la diffusion ou en l&#39;envoyant par le biais d&#39;un workflow. Pour plus d&#39;informations sur les activités de type diffusion dans les workflows, consultez [cette section](../../workflow/using/about-action-activities.md).

Les canaux de diffusion proposés par Adobe Campaign sont les suivants :

1. **Canal email** : les diffusions email permettent d&#39;adresser des messages électroniques personnalisés à la population cible. Voir [À propos du canal email](about-email-channel.md).
1. **Canal courrier** : les diffusions courrier permettent de générer un fichier d&#39;extraction contenant les données relatives à la population cible. Voir [À propos du canal courrier](about-direct-mail-channel.md).
1. **Canal mobile** : les diffusions sur canaux mobiles permettent d&#39;adresser des SMS ou des messages LINE personnalisés à la population cible. Voir [Canal SMS](sms-channel.md).
1. **Canal des applications mobiles** : les diffusions par applications mobiles permettent d&#39;envoyer des notifications sur des systèmes iOS et Android. Voir [Canal des applications mobiles](about-mobile-app-channel.md).

   Les autres canaux sont présentés dans [cette page](steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >Le nombre de canaux disponibles dépend de votre contrat. Veuillez vérifier votre contrat de licence.

Les diffusions peuvent être **on-line** (via email, un des canaux mobiles et les notifications push) et **off-line** (canal courrier).

Selon le canal, les modes de diffusion peuvent être les suivants :

* Envoi en masse directement via Adobe Campaign (mode par défaut pour le canal Email).
* Envoi en externe, via un opérateur spécialisé, auquel est fourni le fichier de sortie généré par l&#39;assistant de diffusion (mode par défaut pour le canal Courrier).

Les comptes externes sont paramétrés depuis le nœud **[!UICONTROL Administration > Plateforme > Comptes externes]**. Ce paramétrage est réservé à des utilisateurs experts.

## Diffusions Email {#email-deliveries}

Le [canal Email](about-email-channel.md) est l&#39;un des principaux canaux dans Adobe Campaign. Il vous permet de planifier et d&#39;envoyer des emails personnalisés à des cibles spécifiques.

Vous pouvez envoyer différents types d&#39;emails :

* Emails uniques : emails que vous pouvez envoyer une fois à une cible définie. Ils sont généralement utilisés pour promouvoir un contenu spécifique qui ne sera préparé et envoyé qu&#39;une seule fois (newsletter, email promotionnel, etc.).
* Emails récurrents : dans une campagne, envoyez un même email régulièrement et agrégez chaque envoi et ses rapports de façon périodique. Un même email est envoyé, mais généralement à une cible différente, selon la cible éligible pour le jour de l&#39;envoi. Un exemple courant est un email d&#39;anniversaire. Pour plus d&#39;informations, consultez la section [Diffusions récurrentes](../../workflow/using/recurring-delivery.md).
* Emails transactionnels : emails unitaires qui sont déclenchés en fonction du comportement de vos clients. Pour plus d&#39;informations, consultez la section [Messages transactionnels](../../message-center/using/about-transactional-messaging.md).

Pour plus d&#39;informations sur l&#39;utilisation des diffusions et les recommandations relatives à celles-ci, consultez [Bonnes pratiques de diffusion](delivery-best-practices.md) de Campaign.

Pour plus d&#39;informations sur les différents types de diffusion, consultez [cette section](#types-of-deliveries).

## Diffusions sur des mobiles {#mobile-deliveries}

Adobe Campaign permet de diffuser des [SMS](sms-channel.md) et des messages [LINE](line-channel.md) sur des mobiles.

Pour les SMS, vous pouvez créer, modifier et personnaliser des messages au format texte uniquement. Vous pouvez également prévisualiser les SMS avant leur envoi.

Pour les messages LINE, vous pouvez envoyer du texte ou des images et des liens.

Pour diffuser des SMS ou des messages LINE vers un téléphone mobile, il vous faut :

* un compte externe paramétré sur le canal **[!UICONTROL Mobile (SMS)]** ou **[!UICONTROL LINE]**,
* un modèle de diffusion SMS ou LINE correctement lié à ce compte externe.

## Notifications push {#push-notifications}

Adobe Campaign vous permet d&#39;envoyer des [notifications push](about-mobile-app-channel.md) personnalisées et segmentées sur des appareils mobiles iOS et Android via des applications dédiées. Une fois les procédures de configuration et d&#39;intégration effectuées, les diffusions sur iOS et Android peuvent être créées et envoyées. Vous pouvez également concevoir des notifications enrichies avec des images et des vidéos.

## Courrier {#direct-mail}

[Le canal Courrier est un canal off-line qui vous permet de personnaliser et de générer le fichier requis par les opérateurs de services postaux. Il vous offre la possibilité de mélanger des canaux off-line et on-line dans les parcours client.](about-direct-mail-channel.md)

Les canaux on-line vous permettent de créer vos messages (email, SMS, diffusion sur des applications mobiles, etc.) et de les envoyer à votre audience directement depuis Adobe Campaign. Les canaux off-line fonctionnent différemment. Lors de la préparation d&#39;une diffusion courrier, Adobe Campaign génère un fichier comprenant tous les profils ciblés et les informations de contact sélectionnées (adresse postale, par exemple). Vous pouvez ensuite envoyer ce fichier à votre opérateur de services postaux qui se chargera de l&#39;envoi.

## Autres canaux {#other-channels}

Adobe Campaign offre le modèle de diffusion Téléphone qui est utilisé pour créer des diffusions externes. L&#39;utilisation de ce canal implique la configuration de méthodologies dédiées pour traiter les fichiers de sortie. Les étapes de configuration sont identiques à celles du [canal Courrier](about-direct-mail-channel.md).

>[!NOTE]
>
>Le canal Téléphone n&#39;est pas disponible en standard. Sa mise en œuvre nécessite la participation d&#39;Adobe Consulting ou d&#39;un partenaire Adobe. Pour plus d&#39;informations, contactez votre représentant Adobe.

De plus, les diffusions de type Autre utilisent un modèle technique spécifique qui n&#39;exécute aucun processus. Elles permettent ainsi notamment de gérer dans Adobe Campaign des actions marketing exécutées en dehors de la plateforme.

Ce canal n&#39;a aucun mécanisme spécifique. Il s&#39;agit d&#39;un canal générique qui possède une option de routage de compte externe, un type de modèle de diffusion et une activité de workflow d&#39;opération, tout comme n&#39;importe quel autre canal de communication disponible dans Adobe Campaign.

Ce canal a été conçu à des fins de description uniquement, pour définir par exemple les diffusions pour lesquelles vous souhaitez conserver une trace de la cible d&#39;une campagne effectuée dans un outil autre qu&#39;Adobe Campaign.

## Types de diffusions{#types-of-deliveries}

Campaign contient trois types d&#39;objets de diffusion :

### Diffusion unique {#single-delivery}

Une **diffusion** est un objet de diffusion autonome exécuté une seule fois. Elle peut être dupliquée et préparée à nouveau. Toutefois, tant qu&#39;elle se trouve dans un état final (annulée, arrêtée, terminée), elle ne peut pas être réutilisée.

Les diffusions peuvent être créées à partir de la liste de diffusions ou au sein d&#39;un workflow via une activité [Diffusion](../../workflow/using/delivery.md).

 Les workflows fournissent également des activités de diffusion spécifiques selon le type de canal que vous souhaitez utiliser. Pour plus d&#39;informations sur ces activités, voir [cette section](../../workflow/using/cross-channel-deliveries.md).

### Diffusion récurrente {#recurring-delivery}

Une **diffusion récurrente** permet de créer une diffusion à chaque exécution de l&#39;activité. Ainsi, vous n&#39;avez pas à créer de diffusion pour les tâches récurrentes.

Par exemple, si vous exécutez ce type d&#39;activité une fois par mois, vous obtiendrez 12 diffusions au bout d&#39;un an.

Les diffusions récurrentes sont créées dans des workflows par le biais de l&#39;activité [](../../workflow/using/recurring-delivery.md)Diffusion récurrente. Un exemple d&#39;utilisation de cette activité est présenté dans la section suivante : [Créer une diffusion récurrente dans un workflow de ciblage](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Diffusion au fil de l&#39;eau {#continuous-delivery}

Une **diffusion au fil de l&#39;eau** permet d&#39;ajouter de nouveaux destinataires à une diffusion existante, ce qui évite d&#39;avoir à créer une diffusion à chaque exécution.

Si des informations liées à diffusion changent (contenu, nom, etc.), un nouvel objet de diffusion est créé lors de l&#39;exécution de la diffusion. Si aucune information n&#39;a été modifiée, le même objet de diffusion est réutilisé, et les logs de diffusion et de tracking sont ajoutés au même objet.

Par exemple, si vous exécutez ce type d&#39;activité une fois par mois, vous obtiendrez une seule diffusion au bout d&#39;un an (à condition que vous n&#39;ayez apporté aucune modification à la diffusion).

Les diffusions au fil de l&#39;eau sont créées dans des workflows via l&#39;activité [Diffusion au fil de l&#39;eau](../../workflow/using/continuous-delivery.md).

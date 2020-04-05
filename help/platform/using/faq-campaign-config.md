---
title: FAQ sur les paramètres de Campaign
seo-title: Comment configurer Campaign
description: FAQ sur Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c5a9823b2feb6e2f721a2ad15dc08c1abe672054

---


# FAQ sur les paramètres de Campaign {#settings-faq}

Découvrez les principales configurations afin de définir votre instance Campaign en fonction de vos besoins.

## Puis-je changer la langue de l&#39;interface de Campaign ? {#can-i-change-the-language-of-campaign-interface-}

La langue de Campaign est sélectionnée lors de la création de l&#39;instance. Vous ne pouvez pas la changer par la suite. Voir à ce propos [cette section](../../installation/using/creating-an-instance-and-logging-on.md).

L&#39;interface utilisateur d&#39;Adobe Campaign est disponible en 4 langues : anglais, français, allemand et japonais. La console cliente et le serveur doivent être configurés avec la même langue. Chaque instance de Campaign ne peut s&#39;exécuter que dans une seule langue.

Pour l&#39;anglais, lors de l&#39;installation de Campaign, vous pouvez sélectionner l&#39;anglais américain ou l&#39;anglais britannique : les formats de date et d&#39;heure sont différents. Pour plus d&#39;informations sur ces différences, consultez [cette section](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## Est-il possible d&#39;utiliser Campaign Classic avec d&#39;autres solutions Adobe ? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Vous pouvez combiner les fonctionnalités de diffusion et de gestion de campagnes avancées d&#39;Adobe Campaign avec un ensemble de solutions conçues pour vous aider à personnaliser l&#39;expérience de vos utilisateurs.

Cliquez ici pour découvrir [comment utiliser d&#39;autres solutions Adobe](../../integrations/using/about-campaign-integrations.md) et [comment configurer IMS dans Campaign](../../integrations/using/about-adobe-id.md).

## Comment configurer les fonctionnalités de tracking sur mon instance Campaign ? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

En tant qu&#39;utilisateur expert, vous pouvez configurer les fonctionnalités de tracking sur votre instance Campaign.

[Pour en savoir plus, cliquez ici](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Comment configurer la délivrabilité des emails ? {#how-to-configure-email-deliverability-}

En plus du [guide de prise en main sur la délivrabilité](https://docs.adobe.com/content/help/en/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html), consultez la section sur la configuration de la délivrabilité des emails pour configurer votre instance afin d&#39;optimiser les fonctionnalités d&#39;envoi de Campaign.

[Pour en savoir plus, cliquez ici](../../installation/using/email-deliverability.md).

## Comment mettre en place la validation du contenu ? {#how-can-i-implement-content-approval-}

Grâce à Campaign, vous pouvez mettre en place des processus de validation des principales étapes d’une campagne marketing, dans un mode collaboratif. Au niveau de chaque opération, vous pouvez valider la cible des diffusions, leur contenu et les coûts engendrés. Les opérateurs Adobe Campaign chargés de validation peuvent être notifiés par email et accepter ou refuser la validation à partir de la console ou via une connexion web.

[Cliquez ici pour en savoir plus](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) et découvrir les étapes pour mettre en place la validation du contenu de vos diffusions dans Campaign.

## Comment accéder aux données stockées dans une base de données externe ? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign propose l&#39;option Federated Data (FDA) Access afin d&#39;exploiter des informations stockées dans une ou plusieurs bases de données externes : vous pouvez accéder à des données externes sans modifier la structure des données d&#39;Adobe Campaign.

[Pour en savoir plus, cliquez ici](../../platform/using/connecting-to-database.md).

## À quelles bases de données externes est-il possible de connecter Campaign ? {#which-external-databases-can-i-connect-campaign-to-}

Les bases de données externes compatibles avec Campaign via FDA (Federated Data Access) sont répertoriées dans la [matrice de compatibilité](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

## Adobe Campaign peut-il s&#39;intégrer avec LDAP ? {#can-adobe-campaign-integrate-with-ldap-}

En tant que client on-premise/hybride, vous pouvez intégrer Campaign Classic avec votre annuaire LDAP.

[Cliquez ici pour découvrir comment](../../installation/using/connecting-through-ldap.md).

## Comment configurer les connecteurs CRM dans Campaign ? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign propose différents connecteurs CRM pour relier votre plateforme Adobe Campaign à vos systèmes tiers. Ces connecteurs CRM permettent par exemple de synchroniser les contacts, les comptes, les commandes, les achats, etc. Ils simplifient l&#39;intégration de votre application avec vos différentes applications tierces et métiers.

Ces connecteurs permettent d&#39;intégrer rapidement et simplement les données : Adobe Campaign propose un assistant dédié pour collecter et sélectionner parmi les tables disponibles dans le CRM. Ils permettent une synchronisation bidirectionnelle des informations afin que les données client soient à jour simultanément sur les différents systèmes.

Consultez l&#39;article [Configurer les connecteurs CRM](../../platform/using/crm-connectors.md) pour apprendre à synchroniser votre outil CRM avec Adobe Campaign. Regardez cette vidéo de cas pratique concernant l&#39;[intégration d&#39;Adobe Campaign avec Microsoft Dynamics 365](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## Comment effectuer un effacement de la mémoire cache douce lorsque les problèmes sont spécifiques à la machine ou à l’utilisateur ? {#perform-soft-cache-clear}

Si vous rencontrez des problèmes tels que le reflet correct des nouveaux logos, afin de pouvoir exporter avec succès les données spécifiques à l’ordinateur ou à l’utilisateur, vous devrez peut-être effectuer une suppression du cache logiciel avec Windows (Windows 7, Windows XP, Windows 10).

Une fois connecté, accédez à **[!UICONTROL Fichier]** > **[!UICONTROL Effacer le cache]** local. Ensuite, déconnectez-vous et reconnectez-vous.

![](assets/faq_soft_cache.png)

Si cela ne vous aide toujours pas, essayez d&#39;effacer le cache dur en suivant les étapes ci-dessous.

## Comment effectuer l&#39;effacement du cache dur lorsque les problèmes sont spécifiques à la machine ou à l&#39;utilisateur ? {#perform-hard-cache-clear}

Si vous rencontrez des problèmes tels que le reflet correct des nouveaux logos, afin de pouvoir exporter avec succès les données spécifiques à l’ordinateur / à l’utilisateur, vous devrez peut-être effectuer une suppression du cache disque avec Windows (Windows 7, Windows XP, Windows 10).

1. Dans la console client, choisissez **[!UICONTROL Fichier]** > **[!UICONTROL Effacer le cache]** local.

1. Déconnectez-vous et fermez la console client (client riche).

1. Accédez aux emplacements suivants, en fonction de la version de votre système d’exploitation :

   * Windows 7 : C:\Users\&lt; Nom d’utilisateur > \AppData\Roaming\Neolane\NL_5\
   * Windows XP : C:\Documents and Settings\&lt; Nom d’utilisateur >\Application Data\Neolane\NL_5
   Vous verrez ici de nombreux fichiers xml nommés nlclient-config-&lt; valeur alphanumérique >.xml.

1. Supprimez ces fichiers XML et les dossiers associés.

   >[!CAUTION]
   >
   >Ne supprimez pas le fichier nlclient_cnx.xml.

1. Connectez-vous à la console client.
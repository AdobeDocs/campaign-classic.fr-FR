---
title: Tracking anonyme
seo-title: Tracking anonyme
description: Tracking anonyme
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Tracking anonyme{#anonymous-tracking}

Adobe Campaign permet d&#39;associer les informations de tracking Web collectées à un destinataire lorsqu&#39;il navigue anonymement sur votre site. En effet, lorsqu&#39;un internaute navigue sur les pages tagguées de votre site web, ses informations de navigation sont collectées. Lorsqu&#39;il clique dans un email envoyé via Adobe Campaign, il est identifié et les informations lui sont automatiquement rattachées.

>[!IMPORTANT]
>
>La mise en place du tracking anonyme sur un site peut entraîner la collecte de très nombreux logs de tracking, et affecter le bon fonctionnement de la base de données. Il doit être configuré avec précaution sur votre site.\
>Les logs de tracking sont enregistrés dans la base de données jusqu&#39;à la purge des données de tracking. Les délais de purge sont paramétrés au travers de l&#39;assistant de déploiement. Consultez à ce propos [cette section](../../installation/using/deploying-an-instance.md#purging-data)

Pour activer le tracking Web anonyme sur votre instance, les éléments suivants doivent être configurés :

* Le paramètre **trackWebVisitors** de l’élément **redirection** du fichier **serverConf.xml** du serveur de tracking doit être réglé sur ‘**true**’, afin de poser un cookie permanent (**uuid230**) dans le navigateur des internautes inconnus qui visitent les pages du site.
* Le mode **Tracking Web anonyme** doit être sélectionné dans la fenêtre de configuration du tracking de l&#39;assistant de déploiement.

   ![](assets/webtracking_anonymous_set.png)

* Les formulaires Web et questionnaires doivent être publiés et exécutés sur le serveur de tracking. L&#39;option correspondante doit être sélectionnée dans l&#39;assistant de déploiement.

   ![](assets/webtracking_publication_set_for_webapps.png)


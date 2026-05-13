---
product: campaign
title: Tracking anonyme
description: Découvrez comment configurer le tracking anonyme
feature: Configuration, Instance Settings
role: Developer
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
TQID: https://experienceleague.adobe.com/jQ4x9zONaJacdqaNqRL--oeMUAyn53Rk-u3jOvKv-20
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 212
ht-degree: 50%

---

# Tracking anonyme{#anonymous-tracking}

Adobe Campaign permet d&#39;associer les informations de tracking Web collectées à un destinataire lorsqu&#39;il navigue anonymement sur votre site. Lorsqu’un utilisateur parcourt les pages balisées de votre site web, ses informations de navigation sont collectées. Lorsqu’il clique dans un e-mail envoyé par Adobe Campaign, il est identifié et les informations lui sont automatiquement liées.

>[!IMPORTANT]
>
>La configuration du tracking anonyme sur un site web peut déclencher la collecte d&#39;une quantité importante de logs de tracking, ce qui impacte le fonctionnement de la base de données. Configurez-le avec soin.\
>Les logs de tracking sont enregistrés dans la base de données jusqu’à la purge des données de tracking. Utilisez l’assistant de déploiement pour configurer la fréquence de purge. Voir à ce propos [cette section](../../installation/using/deploying-an-instance.md#purging-data).

Pour activer le tracking Web anonyme sur votre instance, les éléments suivants doivent être configurés :

* Le paramètre **trackWebVisitors** de l’élément **redirection** du fichier **serverConf.xml** du serveur de tracking doit être réglé sur ‘**true**’, afin de poser un cookie permanent (**uuid230**) dans le navigateur des internautes inconnus qui visitent les pages du site.
* Le mode **Tracking Web anonyme** doit être sélectionné dans la fenêtre de configuration du tracking de l’assistant de déploiement.

  ![](assets/webtracking_anonymous_set.png)

* Les formulaires web doivent être publiés et exécutés sur le serveur de tracking. L&#39;option correspondante doit être sélectionnée dans l&#39;assistant de déploiement.

  ![](assets/webtracking_publication_set_for_webapps.png)

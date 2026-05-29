---
product: campaign
title: Collecte de toutes les visites
description: Collecte de toutes les visites
feature: Configuration, Instance Settings
role: Developer
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
TQID: https://experienceleague.adobe.com/EdEX0IPygnmmYAqewEpX2jRqrCZ723itOEW6DhnMSl8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 51%

---

# Collecter toutes les visites{#collecting-all-visits}

Le module de webtracking fourni par Adobe Campaign permet de collecter les visites de certaines pages du site effectuées par un destinataire dans le cadre du tracking de site suite à un clic dans un message.

Toutefois, vous avez la possibilité de configurer votre plateforme de façon à ce qu&#39;elle collecte toutes les visites des pages ayant une balise de tracking Web, lorsqu&#39;elles sont visitées par un utilisateur connu de la plateforme.

Un utilisateur connu de la plateforme est un destinataire qui a déjà été ciblé par une diffusion et qui a cliqué au moins une fois dans un des messages reçus. Un cookie permanent est utilisé pour identifier ce destinataire.

>[!IMPORTANT]
>
>La plateforme Adobe Campaign n’est pas destinée à être utilisée en tant qu’outil de tracking de site web, hors du cadre de la visite du site suite à un clic dans un message. Lorsque cette option est activée, elle peut entraîner une utilisation très élevée des ressources sur les machines hébergeant vos serveurs (redirection, application et base de données). Nous vous conseillons de vous assurer que votre architecture matérielle peut prendre en charge cette charge et d&#39;éviter de placer des balises de tracking Web sur les pages les plus visitées, comme la page d&#39;accueil.

## Configuration du serveur {#server-configuration}

La configuration des serveurs se fait en surchargeant certains éléments du fichier **serverConf.xml**. Ces fichiers sont enregistrés dans le sous-répertoire **conf** du répertoire d’installation d’Adobe Campaign.

### Serveur de redirection {#redirection-server}

Pour le serveur de redirection, vous devez passer l&#39;attribut **trackWebVisitors** de l&#39;élément **redirection** à **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configurer une campagne de rattachement par défaut {#configuring-a-default-matching-campaign}

Afin de consulter les informations de tracking depuis votre console cliente, vous devez :

* créer une **diffusion factice**, dite &#39;diffusion balai&#39; (le mapping de la diffusion doit être identique au mapping du schéma cible),
* renseigner le **nom interne** de cette diffusion dans l&#39;option **NmsTracking_WebTrackingDelivery**.

Toutes les informations de tracking de site qui ne font pas directement suite à un clic dans un e-mail sont consultables au niveau de la diffusion factice créée.

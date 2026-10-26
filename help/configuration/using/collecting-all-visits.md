---
product: campaign
title: Collecte de toutes les visites
description: Collecte de toutes les visites
feature: Configuration, Instance Settings
role: Developer
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
TQID: 'https://experienceleague.adobe.com/EdEX0IPygnmmYAqewEpX2jRqrCZ723itOEW6DhnMSl8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: ht
source-wordcount: '296'
ht-degree: 100%
---
# Collecter toutes les visites{#collecting-all-visits}

Le module de webtracking fourni par Adobe Campaign permet de collecter les visites de certaines pages du site effectuées par un destinataire dans le cadre du tracking de site suite à un clic dans un message.

Toutefois, vous avez la possibilité de configurer votre plateforme de façon à ce qu&#39;elle collecte toutes les visites des pages ayant une balise de tracking Web, lorsqu&#39;elles sont visitées par un utilisateur connu de la plateforme.

Une personne connue de la plateforme est une personne destinataire qui a déjà été ciblée par une diffusion et qui a cliqué au moins une fois dans un des messages reçus. Un cookie permanent est utilisé pour identifier cette personne destinataire.

>[!IMPORTANT]
>
>La plateforme Adobe Campaign n’est pas destinée à être utilisée en tant qu’outil de tracking de site web, hors du cadre de la visite du site suite à un clic dans un message. Lorsque cette option est activée, elle peut entraîner une utilisation très élevée des ressources sur les machines hébergeant vos serveurs (redirection, application et base de données). Nous vous conseillons de vous assurer que votre architecture matérielle peut supporter cette charge et d’éviter de placer des balises de tracking web sur les pages les plus visitées, comme la page d’accueil.

## Configuration du serveur {#server-configuration}

La configuration des serveurs se fait en surchargeant certains éléments du fichier **serverConf.xml**. Ce fichier est enregistré dans le sous-répertoire **conf** du répertoire d’installation d’Adobe Campaign.

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

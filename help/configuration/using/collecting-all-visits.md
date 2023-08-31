---
product: campaign
title: Collecter toutes les visites
description: Collecter toutes les visites
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 100%

---

# Collecte de toutes les visites{#collecting-all-visits}

Le module de webtracking fourni par Adobe Campaign permet de collecter les visites de certaines pages du site effectuées par un destinataire dans le cadre du tracking de site suite à un clic dans un message.

Toutefois, vous avez la possibilité de configurer votre plateforme de façon à ce qu&#39;elle collecte toutes les visites des pages ayant une balise de tracking Web, lorsqu&#39;elles sont visitées par un utilisateur connu de la plateforme.

Un utilisateur connu de la plateforme est un destinataire qui a déjà été ciblé par une diffusion et qui a cliqué au moins une fois dans un des mails reçus : un cookie permanent est utilisé pour identifier ce destinataire.

>[!IMPORTANT]
>
>La plateforme Adobe Campaign n&#39;a pas vocation à servir d&#39;outil de tracking de site web, hors du cadre de la visite du site suite à un clic dans un message. L&#39;activation de cette option peut provoquer une consommation très importante de ressources sur les machines hébergeant vos différents serveurs (redirection, applicatif et base de données). Nous vous conseillons de vous assurer que vous disposez d&#39;une architecture matérielle suffisamment performante, et de ne pas insérer de balises de tracking Web sur les pages du site les plus fréquentées, par exemple sur la page d&#39;accueil.

## Configuration du serveur {#server-configuration}

La configuration des serveurs se fait en surchargeant certains éléments du fichier **serverConf.xml**. Ce fichier est enregistré dans le sous-répertoire **conf** du répertoire d&#39;installation d&#39;Adobe Campaign.

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

---
product: campaign
title: Configuration supplémentaire
description: Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: ht
source-wordcount: '168'
ht-degree: 100%

---

# Configuration {#configuration}



## Changement du port d&#39;écoute du module syslogd {#changing-the-syslogd-listening-port}

Par défaut, le port d&#39;écoute du module **syslogd** est le 666 (udp). Vous pouvez cependant modifier le port d&#39;écoute à l&#39;aide d&#39;une variable d&#39;environnement.

Une fois paramétrée, cette variable est prise en compte par tous les modules Adobe Campaign.

### Sous Linux {#in-linux}

Vous devez modifierle fichier **customer.sh** et ajouter la ligne suivante :

```
export TRACE_ADDR=localhost:<listening port>
```

### Sous Windows {#in-windows}

Vous devez créer la variable d&#39;environnement **TRACE_ADDR** avec la valeur **localhost** : **`<listening port="" />`**.

>[!IMPORTANT]
>
>Nous vous recommandons de procéder à des tests afin de vérifier le bon fonctionnement de votre plateforme après avoir créé cette variable d&#39;environnement.

## Configuration de zones de sécurité {#configuring-security-zones}

Chaque opérateur doit être associé à une zone pour se connecter à une instance et l&#39;adresse IP de l&#39;opérateur doit faire partie des adresses ou des plages d&#39;adresses définies dans la zone de sécurité. La configuration technique des zones est effectuée dans le fichier de configuration du serveur Adobe Campaign. L&#39;association d&#39;un opérateur à une zone de sécurité doit être défini dans la console (noeud **[!UICONTROL Administration > Gestion des accès > Opérateurs]**).

>[!NOTE]
>
>Pour plus d’informations sur le paramétrage des zones de sécurité, consultez [cette section](../../installation/using/security-zones.md).

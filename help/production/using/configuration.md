---
product: campaign
title: Configuration supplémentaire
description: Configuration
feature: Monitoring, Configuration
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
TQID: https://experienceleague.adobe.com/gzcQquM9q71NIOt8mScgRpLtwffxvopslrrpLxxIang
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: efa38731-2723-4334-8d8b-a778af834835
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 66%

---

# Configuration{#configuration}



## Changement du port d&#39;écoute du module syslogd {#changing-the-syslogd-listening-port}

Par défaut, le port d’écoute **syslogd** est 666 (udp). Vous pouvez la modifier à l’aide d’une variable d’environnement si nécessaire.

Une fois paramétrée, cette variable est prise en compte par tous les modules Adobe Campaign.

### Sous Linux {#in-linux}

Vous devez modifierle fichier **customer.sh** et ajouter la ligne suivante :

```sql
export TRACE_ADDR=localhost:<listening port>
```

### Sous Windows {#in-windows}

Vous devez créer la variable d&#39;environnement **TRACE_ADDR** avec la valeur **localhost** : **`<listening port="" />`**.

>[!IMPORTANT]
>
>Nous vous recommandons de procéder à des tests afin de vérifier le bon fonctionnement de votre plateforme après avoir créé cette variable d&#39;environnement.

## Configuration de zones de sécurité {#configuring-security-zones}

Chaque opérateur doit être associé à une zone pour se connecter à une instance et l&#39;adresse IP de l&#39;opérateur doit faire partie des adresses ou des plages d&#39;adresses définies dans la zone de sécurité. La configuration technique des zones est effectuée dans le fichier de configuration du serveur Adobe Campaign. L&#39;association d&#39;un opérateur à une zone de sécurité doit être défini dans la console (noeud **[!UICONTROL Administration > Gestion des accès > Opérateurs]**).

>[!NOTE]
>
>Pour plus d’informations sur le paramétrage des zones de sécurité, consultez [cette section](../../installation/using/security-zones.md).

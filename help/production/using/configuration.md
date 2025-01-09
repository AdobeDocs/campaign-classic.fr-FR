---
product: campaign
title: Configuration supplémentaire
description: Configuration
feature: Monitoring, Configuration
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Configuration{#configuration}



## Changement du port d&#39;écoute du module syslogd {#changing-the-syslogd-listening-port}

Par défaut, le port d&#39;écoute du module **syslogd** est le 666 (udp). Vous pouvez cependant modifier le port d&#39;écoute à l&#39;aide d&#39;une variable d&#39;environnement.

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

Chaque opérateur doit être associé à une zone pour se connecter à une instance et son adresse IP doit faire partie des adresses ou des plages d&#39;adresses définies dans la zone de sécurité. La configuration d’une zone technique est effectuée dans le fichier de configuration du serveur Adobe Campaign. L&#39;association d&#39;un opérateur à une zone de sécurité doit être défini dans la console (noeud **[!UICONTROL Administration > Gestion des accès > Opérateurs]**).

>[!NOTE]
>
>Pour plus d’informations sur le paramétrage des zones de sécurité, consultez [cette section](../../installation/using/security-zones.md).

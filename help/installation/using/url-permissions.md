---
product: campaign
title: Configurer les autorisations d’URL
description: Découvrez comment configurer les autorisations d’URL
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
TQID: 'https://experienceleague.adobe.com/5F4SRt978KzXMI06t3rNt3YRnYI-EWwSkQIrAd0oDq8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
  - id: fb2a841f-c522-491f-9901-a1b939d252df
    internal-label: Security
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
    internal-label: Permissions
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 100%
---
# Configuration des autorisations d’URL (On-premise){#url-permissions}



La liste par défaut des URL pouvant être appelées par des codes JavaScript (workflows, etc.) par vos instances Campaign Classic est limitée. Il s’agit des URL qui permettent à vos instances de fonctionner correctement.

Par défaut, les instances ne sont pas autorisées à se connecter à des URL externes. Cependant, il est possible d’ajouter des URL externes à la liste des URL autorisées afin que votre instance puisse s’y connecter. Vous pouvez ainsi connecter vos instances Campaign à des systèmes externes, comme des serveurs SFTP ou des sites Web, afin d’activer le transfert de fichiers et/ou de données.

>[!NOTE]
>
>Cette procédure est limitée aux déploiements **On-premise**.
>
>En tant que client **hébergé**, si vous pouvez accéder au [Panneau de contrôle Campaign](https://experienceleague.adobe.com/fr/docs/control-panel/using/control-panel-home.html?lang=fr), vous pouvez utiliser l’interface en libre-service des autorisations d’URL. [En savoir plus](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=fr)
>
>Les autres clients **hybrides/hébergés** doivent contacter l’équipe d’assistance d’Adobe pour ajouter une adresse IP à la liste autorisée.
>

Pour les déploiements **hybride** et **On-premise**, l’administrateur doit référencer une nouvelle **urlPermission** dans le fichier **serverConf.xml**.


Trois modes de protection de la connexion sont disponibles :

* **Blocage** : toutes les URL qui ne figurent pas sur la liste autorisée sont bloquées et un message d&#39;erreur s&#39;affiche. Il s&#39;agit du mode par défaut après un postupgrade.
* **Permissif** : toutes les URL qui ne figurent pas sur la liste autorisée sont autorisées.
* **Avertissement** : toutes les URL qui ne figurent pas sur la liste autorisée sont autorisées, mais l&#39;interpréteur JS émet un avertissement pour que l&#39;administrateur puisse les collecter. Ce mode ajoute des messages d’avertissement JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Par défaut, les nouvelles implémentations utilisent le mode **Blocage**.
>
>En tant que client existant issu d’une migration, vous pouvez temporairement utiliser le mode **Avertissement**. Analysez le trafic sortant avant d’autoriser les URL. Une fois la liste des URL autorisées définie, vous pouvez ajouter des URL à la liste autorisée et activer le mode **Blocage**.

Pour plus d’informations, consultez les sections suivantes :

* [Documentation relative au Panneau de contrôle](https://experienceleague.adobe.com/fr/docs/control-panel/using/control-panel-home.html?lang=fr)
* [Modèles d&#39;hébergement](hosting-models.md)
* [Configuration du serveur Campaign](configuring-campaign-server.md)
* [Paramètres du fichier de configuration du serveur Campaign](the-server-configuration-file.md)
* [Liste de contrôle relative à la sécurité et à la confidentialité](get-started-security-privacy.md)

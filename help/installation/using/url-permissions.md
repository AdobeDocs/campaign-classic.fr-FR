---
product: campaign
title: Configurer les autorisations d’URL
description: Découvrez comment configurer les autorisations d’URL
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814,6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 99%

---

# Configuration des autorisations d’URL (On-premise){#url-permissions}

La liste par défaut des URL pouvant être appelées par des codes JavaScript (workflows, etc.) de vos instances Campaign Classic est limitée. Il s’agit des URL qui permettent à vos instances de fonctionner correctement.

Par défaut, les instances ne sont pas autorisées à se connecter à des URL externes. Cependant, il est possible d’ajouter des URL externes à la liste des URL autorisées afin que votre instance puisse s’y connecter. Vous pouvez ainsi connecter vos instances Campaign à des systèmes externes, comme des serveurs SFTP ou des sites Web, afin d’activer le transfert de fichiers et/ou de données.

>[!NOTE]
>
>Cette procédure est limitée aux déploiements **On-premise**.
>
>En tant que client **hébergé**, si vous pouvez accéder au [Panneau de contrôle Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr), vous pouvez utiliser l’interface en libre-service des autorisations d’URL. [En savoir plus](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=fr)
>
>Les autres clients **hybrides/hébergés** doivent contacter l’équipe d’assistance d’Adobe pour ajouter une adresse IP à la liste autorisée.


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

* [Documentation relative au Panneau de contrôle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Modèles d&#39;hébergement](hosting-models.md)
* [Paramétrage du serveur Campaign](configuring-campaign-server.md)
* [Paramétrage du serveur Campaign paramètres de fichier](the-server-configuration-file.md)
* [Liste de contrôle relative à la sécurité et à la confidentialité](get-started-security-privacy.md)

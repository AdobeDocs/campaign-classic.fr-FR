---
solution: Campaign Classic
product: campaign
title: Configuration des autorisations d’URL
description: Découvrez comment configurer les autorisations d’URL
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 67%

---


# Configurer les autorisations d&#39;URL {#url-permissions}

La liste par défaut des URL pouvant être appelées par des codes JavaScript (workflows, etc.) de vos instances Campaign Classic est limitée. Il s’agit des URL qui permettent à vos instances de fonctionner correctement.

Par défaut, les instances ne sont pas autorisées à se connecter à des URL externes. Cependant, il est possible d’ajouter des URL externes à la liste des URL autorisées afin que votre instance puisse s’y connecter. Vous pouvez ainsi connecter vos instances Campaign à des systèmes externes, comme des serveurs SFTP ou des sites web, afin d’activer le transfert de fichiers et/ou de données.

Pour les déploiements **Hybrid** et **Sur site**, l’administrateur doit référencer un nouveau **urlPermission** dans le fichier **serverConf.xml**.

Trois modes de protection de connexion sont disponibles :

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
>En tant que client existant provenant d’une migration, vous pouvez temporairement utiliser le mode **Avertissement**. Analysez le trafic sortant avant d’autoriser les URL. Une fois la liste des URL autorisées définie, vous pouvez ajouter les URL à la liste autorisée et activer le mode **Blocage**.

Pour plus d’informations, consultez les sections suivantes :

* [Documentation relative au Panneau de contrôle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr)
* [Modèles d&#39;hébergement](hosting-models.md)
* [Configuration du serveur Campaign](configuring-campaign-server.md)
* [Paramètres du fichier de configuration du serveur Campaign](the-server-configuration-file.md)
* [Liste de contrôle relative à la sécurité et à la confidentialité](get-started-security-privacy.md)
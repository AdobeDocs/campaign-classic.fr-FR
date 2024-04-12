---
product: campaign
title: Configuration du serveur web
description: En savoir plus sur les bonnes pratiques clés de configuration d'un serveur web
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# Configuration du serveur web {#web-server-configuration}



Vous trouverez ci-dessous quelques bonnes pratiques clés relatives à la configuration du serveur web (Apache/IIS).

* Modifiez les pages d’erreur par défaut.

* Désactivez l’ancienne version de SSL et les chiffrements :

  **Sur Apache**, modifiez le fichier /etc/apache2/mods-available/ssl.conf. Voici un exemple :

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **Sur IIS** (voir la [documentation](https://support.microsoft.com/en-us/kb/245030)), effectuez la configuration suivante :

   * Ajoutez la sous-clé de registre dans HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Pour que le système puisse utiliser les protocoles qui ne seront pas négociés par défaut (tels que TLS 1.2), remplacez les données de la valeur DWORD de la valeur DisabledByDefault par 0x0 dans les clés de registre suivantes sous la clé **Protocols** :

     SCHANNEL\Protocols\TLS 1.2\Client

     SCHANNEL\Protocols\TLS 1.2\Server

  **Désactivez SSL x.0**

  SCHANNEL\Protocols\SSL 3.0\Client : DisabledByDefault : valeur DWORD (32 bits) sur 1

  SCHANNEL\Protocols\SSL 3.0\Server : Enabled : valeur DWORD (32 bits) sur 0

* Supprimez la méthode **TRACE** :

  **Sur Apache**, modifiez le fichier /etc/apache2/conf.d/security : TraceEnable **Off**.

  **Sur IIS** (voir la [documentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), effectuez la configuration suivante :

   * Assurez-vous que la fonctionnalité ou le service de rôle **Filtrage des requêtes** est installé.
   * Dans le volet **Filtrage des requêtes**, cliquez sur l’onglet Verbes HTTP, puis sur Refuser un verbe. Dans le volet Actions, saisissez TRACE dans la boîte de dialogue ouverte.

* Supprimez la bannière :

  **Sur Apache**, modifiez le fichier /etc/apache2/conf.d/security :

   * ServerSignature **Off**
   * ServerTokens **Prod**

  **Sur IIS**, effectuez la configuration suivante :

   * Installez **URLScan**.
   * Modifiez le fichier **Urlscan.ini** afin d’obtenir **RemoveServerHeader=1**.

* Limitez la taille des requêtes pour empêcher le téléchargement de fichiers volumineux :

  **** Sur Apache, ajoutez la directive **LimitRequestBody** (taille en octets) dans le répertoire /.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **Sur IIS** (voir la [documentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), définissez la valeur **maxAllowedContentLength** (longueur de contenu maximale autorisée) dans les options de filtrage de contenu.

Rubriques connexes :

* [Vue d’ensemble de la conformité d’Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Vue d’ensemble de la sécurité d’Adobe Campaign](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)

---
solution: Campaign Classic
product: campaign
title: Configuration du serveur web
description: En savoir plus sur les principales pratiques de configuration des serveurs Web.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 40%

---

# Configuration du serveur web {#web-server-configuration}

Vous trouverez ci-dessous quelques-unes des meilleures pratiques liées à la configuration du serveur Web (Apache/IIS).

* Modifiez les pages d&#39;erreur par défaut.

* Désactivez l&#39;ancienne version de SSL et les chiffrements :

   **Sur Apache**, modifiez /etc/apache2/mods-available/ssl.conf. En voici un exemple :

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **Sous IIS**  (voir la  [documentation](https://support.microsoft.com/en-us/kb/245030)), effectuez la configuration suivante :

   * Ajoutez la sous-clé de registre dans HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Pour permettre au système d’utiliser les protocoles qui ne seront pas négociés par défaut (tels que TLS 1.2), modifiez les données de valeur DWORD de la valeur DisabledByDefault en 0x0 dans les clés de Registre suivantes sous la clé **Protocoles** :

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **Désactiver SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client : DisabledByDefault : valeur DWORD (32 bits) sur 1

   SCHANNEL\Protocols\SSL 3.0\Server : Enabled : valeur DWORD (32 bits) sur 0

* Supprimez la méthode **TRACE** :

   **Sur Apache**, modifiez la page /etc/apache2/conf.d/security: TraceEnable  **Off**

   **Sous IIS**  (voir la  [documentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), effectuez la configuration suivante :

   * Vérifiez que la fonctionnalité ou le service de rôle **Filtrage des demandes** est installé.
   * Dans le volet **Filtrage des demandes**, cliquez sur l&#39;onglet   Verbes HTTP, puis sur   Refuser un verbe. Dans le volet Actions, saisissez   TRACE dans la boîte de dialogue ouverte.

* Supprimez la bannière :

   **Sur Apache**, modifiez /etc/apache2/conf.d/security:

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **Sous IIS**, effectuez la configuration suivante :

   * Installez **URLScan**.
   * Editez le fichier **Urlscan.ini** afin d&#39;obtenir **RemoveServerHeader=1**.


* Limitez la taille des requêtes pour empêcher le téléchargement de fichiers volumineux :

   **Sur Apache**, ajoutez la directive  **** LimitRequestBodydirective (taille en octets) dans le répertoire /.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **Sur IIS**  (voir la  [documentation](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), définissez la  **valeur maxAllowedContentLength**  (longueur de contenu maximale autorisée) dans les options de filtrage de contenu.

Rubriques connexes :

* [Présentation](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf)  de la conformité Adobe Marketing Cloud (PDF)
* [Aperçu](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf)  de la sécurité Adobe Campaign (PDF)

---
title: Interaction - Mémoire tampon
seo-title: Interaction - Mémoire tampon
description: Interaction - Mémoire tampon
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Interaction - Mémoire tampon{#interaction-data-buffer}

>[!NOTE]
>
>Certains paramétrages côté serveur ne peuvent être réalisés que par Adobe pour les déploiements hébergés par Adobe, par exemple pour accéder aux fichiers de configuration de l&#39;instance et du serveur. Pour plus d&#39;informations sur les différents déploiements, reportez-vous à la section [Modèles d&#39;hébergement](../../installation/using/hosting-models.md) ou à [cet article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

Dans Adobe Campaign, une **zone de mémoire tampon** a été introduite dans le module Interaction. Elle permet **d&#39;augmenter les performances** d&#39;Interaction entrant en désynchronisant le calcul des propositions, du stockage.

Il concerne uniquement interaction entrant, soit pour un appel (avec ou sans données d&#39;appel), soit pour une mise à jour de statut (updateStatus).

Afin d&#39;éviter une file d&#39;attente lors de l&#39;écriture des propositions liées à un destinataire, un nouveau processus génère une **zone de mémoire tampon** qui permet l&#39;**écriture asynchrone** des propositions. Cette zone de mémoire de tampon est lue et vidée de façon périodique. La période par défaut correspond environ à une seconde. Par conséquent, l&#39;écriture des propositions est regroupée.

Le **paramétrage** de la zone de mémoire tampon est à effectuer dans le fichier de configuration propre à l&#39;instance (config-Instance.xml).

>[!NOTE]
>
>Tout changement effectué sur la configuration demande un redémarrage du serveur web (Apache / IIS) et des processus Adobe Campaign.\
>Lors du paramétrage de la zone de mémoire tampon, veillez à disposer d&#39;une configuration matériel adaptée (quantité de mémoire vive).

Lors du paramétrage de la zone de mémoire tampon, veillez à disposer d&#39;une configuration matériel adaptée (quantité de mémoire vive).

La définition du démon d’écriture (processus nommé : interactiond) est la suivante :

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Si vous utilisez Interaction Entrant, l&#39;attribut @autoStart doit être à &quot;true&quot; pour démarrer automatiquement le process au lancement du serveur Adobe Campaign.

Détails des arguments :

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```


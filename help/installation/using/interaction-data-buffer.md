---
product: campaign
title: Interaction - Mémoire tampon
description: Interaction - Mémoire tampon
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
TQID: https://experienceleague.adobe.com/VzejoXfvy4j-bthB0FrSB-iSipA-oGLd0BmqP2niNrg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 301
ht-degree: 100%

---

# Interaction - Mémoire tampon{#interaction-data-buffer}



Vous pouvez configurer une zone de mémoire tampon pour augmenter les performances d’Interaction en entrée en désynchronisant les calculs des propositions d’offre.Cette configuration doit être effectuée dans le fichier de configuration propre à l’instance (config-Instance.xml).

Dans Adobe Campaign, une **zone de mémoire tampon** a été introduite dans le module Interaction. Elle permet **d&#39;augmenter les performances** d&#39;Interaction entrant en désynchronisant le calcul des propositions, du stockage.

Il concerne uniquement interaction entrant, soit pour un appel (avec ou sans données d&#39;appel), soit pour une mise à jour de statut (updateStatus).

Afin d’éviter une file d’attente lors de l’écriture des propositions liées à une personne destinataire, un nouveau processus génère une **zone de mémoire tampon** qui permet l’**écriture asynchrone** des propositions.Cette zone de mémoire tampon est lue et vidée de façon périodique.La période par défaut correspond environ à une seconde.Par conséquent, l’écriture des propositions est regroupée.

>[!NOTE]
>
>Ce paramètre est indispensable si vous utilisez Interaction avec une architecture distribuée.

La **configuration** de la zone de mémoire tampon est à effectuer dans le fichier de configuration propre à l’instance (config-Instance.xml).

>[!CAUTION]
>
>Certaines configurations ne peuvent être exécutées que par Adobe pour les déploiements hébergés par Adobe.Par exemple, pour accéder aux fichiers de configuration du serveur et de l’instance.Pour en savoir plus sur les différents déploiements, consultez la section [Modèles d&#39;hébergement](../../installation/using/hosting-models.md) ou [cette page](../../installation/using/capability-matrix.md).
>
>Toute modification apportée à la configuration nécessite un redémarrage du serveur web (Apache:IIS) et des processus Adobe Campaign.\
>Après avoir configuré la zone de mémoire tampon, veillez à disposer d’une configuration matériel adaptée(quantité de mémoire présente).


Après avoir configuré la zone de mémoire tampon, veillez à disposer d’une configuration matériel adaptée(quantité de mémoire présente).

La définition du démon d’écriture (processus nommé : interactiond) est la suivante :

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Si vous utilisez Interaction Entrant, l&#39;attribut @autoStart doit être à &quot;true&quot; pour démarrer automatiquement le process au lancement du serveur Adobe Campaign.

Détails des arguments :

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

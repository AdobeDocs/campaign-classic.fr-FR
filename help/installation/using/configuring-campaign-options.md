---
product: campaign
title: Paramétrer les options de Campaign
description: Découvrez comment paramétrer les options de Campaign
feature: Installation, Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '4015'
ht-degree: 100%

---

# Liste des options de Campaign Classic{#configuring-campaign-options}

Le nœud **[!UICONTROL Administration / Plateforme / Options]** vous permet de paramétrer les options d&#39;Adobe Campaign. Certaines d&#39;entre elles sont intégrées lors de l&#39;installation de Campaign et d&#39;autres peuvent être ajoutées manuellement en cas de besoin. Les options disponibles varient en fonction des packages installés avec votre instance.


>[!CAUTION]
>
>* Les options non répertoriées dans cette page sont exclusivement internes et **ne doivent pas être modifiées**.
>
>* La modification ou la mise à jour des options d’Adobe Campaign ne peut être effectuée que par des utilisateurs experts.

## Diffusion {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Date du dernier broadLogMsg récupéré à partir de l'instance de délivrabilité.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Date du dernier broadLogMsg récupéré envoyé à l'instance de délivrabilité.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identifiant pour les rapports de délivrabilité. Merci de contacter le support pour obtenir votre identifiant.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Liste des schémas pour lesquels vous souhaitez utiliser des adresses de test pour l'Inbox Rendering (les noms des éléments sont séparés par des virgules). Par exemple : custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> Adresse e-mail en Cci à laquelle le MTA amélioré enverra une copie brute des e-mails envoyés. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Permet d’autoriser l’opérateur en charge de la diffusion à confirmer l’envoi, si un opérateur ou un groupe spécifique d’opérateurs est désigné pour démarrer une diffusion dans les propriétés de la diffusion.</p><p> Pour ce faire, activez l'option en saisissant "1" comme valeur. Pour désactiver cette option, entrez "0".</p><p> Le processus de confirmation des envois fonctionnera alors comme par défaut : seul l'opérateur ou le groupe d'opérateurs désigné pour l'envoi (ou un administrateur) dans les propriétés de la diffusion pourra confirmer et effectuer l'envoi. Voir <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">cette section</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign utilise une variable globale "Nms_DefaultRcpSchema" pour dialoguer avec la base de destinataires par défaut (nms:recipient).<br /> La valeur de l'option doit correspondre au nom du schéma qui correspond à la table de destinataires externe.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Nombre minimum de destinataires pour qu'une diffusion soit considérée comme principale dans le rapport de facturation.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Prestataire de routage par défaut pour les nouveaux modèles.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Taille minimale du lot (nombre de lignes) pour l’insertion des broadLogs lors de la préparation d’une diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Seuil de durée du lot (nombre de millisecondes) sous lequel la taille du lot pour l’insertion des broadLogs est doublée lors de la préparation d’une diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Taille des groupements de fragments de diffusion lors des analyses en mode mid-sourcing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Période de diffusion par défaut pour une diffusion (en secondes).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Expressions régulières de normalisation des messages de diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Entrer la valeur "1" permet d’exclure les destinataires qui ne souhaitent plus être contactés.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Entrer la valeur "1" permet de supprimer automatiquement les doublons.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> Permet de définir la syntaxe de l'adresse d'erreur utilisée lors de la réponse à un message.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> Permet de définir la syntaxe de l'adresse d'expéditeur utilisée lors de la réponse à un message.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Permet de définir un délai d’expiration (en secondes) pour obtenir une réponse du serveur lors de la récupération d’une image téléchargée à partir d’une URL personnalisée et jointe à un email. Si cette valeur de délai d’expiration est dépassée, le message ne peut pas être envoyé. La valeur par défaut est de 60 secondes.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Permet de définir la taille maximale (en octets) autorisée pour une image téléchargée à partir d’une URL personnalisée et jointe à un email. La valeur par défaut est de 100 000 octets (100 Ko). Lors de l’envoi d’un BAT et du téléchargement des images pour traiter l’email, si la taille d’une image dépasse cette valeur ou si un problème de téléchargement se produit, une erreur s’affiche dans les logs de diffusion et la diffusion du BAT échoue.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Permet de définir un nombre maximal de pièces jointes à un email ou dans un modèle d’email transactionnel. Si cette valeur est dépassée, un avertissement s’affiche dans les logs d’analyse des diffusions ou lors de la publication du modèle d’email transactionnel. La valeur par défaut est de 1 pièce jointe.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Nombre maximum de réessais lors de l'analyse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Script de publication.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Désactiver le comptage broadLogMsg pour les messages push.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Afficher le poids du message dans l'assistant de diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Adresse email 'erreur' par défaut au niveau de l'instance utilisée pour la diffusion de l'email si l'utilisateur l'a laissée vide.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Adresse email 'expéditeur' par défaut au niveau de l'instance utilisée pour la diffusion de l'email si l'utilisateur l'a laissée vide.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Adresse e-mail 'répondre' par défaut au niveau de l’instance utilisée pour la diffusion de l’e-mail si l’utilisateur ou l’utilisatrice l’a laissée vide.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nom usuel du client. Utilisé dans certains messages d’avertissement affichés aux destinataires.<br /> "Vous recevez ce message, car vous avez été en contact avec 'Organization' ou une société affiliée. Pour ne plus recevoir de messages de 'Organization' <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Libellé de l'email 'expéditeur' par défaut au niveau de l'instance utilisée pour la diffusion de l'email si l'utilisateur l'a laissé vide.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Libellé de l’e-mail 'répondre' par défaut au niveau de l’instance utilisée pour la diffusion de l’e-mail si l’utilisateur ou l’utilisatrice l’a laissé vide.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Période entre deux reprises d'un email (en secondes).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Période des reprises pour les emails.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formule de calcul du poids d'un message d'une diffusion prévisionnelle.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Liste des adresses email de transfert autorisées (à partir du module de traitement du courrier entrant). Les adresses doivent être séparées par des virgules (ou * pour les autoriser toutes). Par exemple, xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Clé AES utilisée dans la servlet 'lineImage' pour encoder les URL (canal LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Sur le canal "email" (utiliser par défaut) : nombre maximum d'erreurs accepté, pour les erreurs SOFT lors de l'envoi avant de mettre le destinataire en quarantaine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Sur le canal "email" (utiliser par défaut) : période minimum à respecter à partir de la précédente erreur SOFT référencée, avant de prendre en compte une nouvelle erreur SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Sur le canal "mobile" : nombre maximum d'erreurs accepté, pour les erreurs SOFT lors de l'envoi avant de mettre le destinataire en quarantaine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Sur le canal "mobile" : période minimum à respecter à partir de la précédente erreur SOFT référencée, avant de prendre en compte une nouvelle erreur SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Permet de spécifier une période maximum (exprimée en heures) afin de limiter le nombre de broadlogs récupérés à chaque exécution du workflow de synchronisation.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Nombre maximum d'appels dans une session MidSourcing, qui peuvent être exécutés en parallèle (3 par défaut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Délai personnalisé (en minutes) après lequel une diffusion est considérée 'retardée'. La valeur par défaut est de 30 minutes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Cette option est utilisée par le workflow technique <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> pour le comptage du nombre de diffusions en cours.</p>Elle vous permet de définir le nombre de jours au-delà desquels les diffusions dont le statut est incohérent seront exclues du nombre de diffusions en cours.</p><p>Par défaut, la valeur est définie sur « 7 », ce qui signifie que les diffusions incohérentes remontant à plus de 7 jours seront exclues.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Ligne 1 de l'adresse de l'expéditeur.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Ligne 3 de l'adresse de l'expéditeur.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Ligne 4 de l'adresse de l'expéditeur.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Ligne 6 de l'adresse de l'expéditeur.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Ligne 7 de l'adresse de l'expéditeur.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> URL du serveur de page miroir (par défaut, elle devrait être identique à NmsTracking_ServerUrl).<br /> Il s'agit de la valeur par défaut des diffusions par email lorsque l'URL n'est pas spécifiée dans la définition de routage.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Paramètres des SMS envoyés : information transmise à la passerelle SMS pour indiquer la priorité du message.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Nombre de reprises lors de l'envoi de messages SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Période pendant laquelle les reprises de messages SMS seront réalisées.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Date de la dernière consolidation pour les statistiques <span class="uicontrol">NmsUserAgent</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nom de l'option qui contient les segments web et leurs états.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Activer/désactiver la prise en charge des caractères spéciaux pour Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Caractères valides pour une adresse email.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Ajoutez cette option avec la valeur "0" pour désactiver l’édition du code XML des diffusions (cliquez avec le bouton droit sur <span class="uicontrol">Éditer le XML source</span> ou utilisez le raccourci <span class="uicontrol">CTRL + F4</span>).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Ressources {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Emplacement des ressources pour la publication dans la console cliente d'Adobe Campaign. Voir <a href="../../delivery/using/formatting.md#image-referencing">cette section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Emplacement des ressources pour la prévisualisation dans la console cliente d'Adobe Campaign. Voir <a href="../../delivery/using/formatting.md#image-referencing">cette section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Liste des masques d’URL pour les images ignorées lors du chargement.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Paramétrage du chargement des images. Les valeurs peuvent être aucun/tracking/script/liste (elles peuvent être remplacées par les paramètres facultatifs de l’opérateur). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Dossier dans lequel vont être stockées les images sur le serveur.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Emplacement pour l'affichage des logos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Répertoire utilisé comme racine pour les publications.<br /> Pour plus d’informations sur la génération du contenu HTML et Texte, consultez <a href="../../delivery/using/using-a-content-template.md">cette section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Permet de définir le serveur sur lequel les images utilisées dans les diffusions sont stockées pour permettre au navigateur de les obtenir.<br /> Pour les versions de build &lt;= 5098, nous utilisons l’URL des images téléchargées sur l’instance.<br /> Pour les versions de build &gt; 5098, nous utilisons à la place l’URL publique de la diffusion ou l’URL de l’option <span class="uicontrol">XtkFileRes_Public_URL</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Permet de paramétrer le nom de l’instance pour le chargement des images.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Permet de paramétrer le mot de passe pour le chargement des images.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Permet de paramétrer la ou les URL médias pour le chargement des images.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Durée de validité par défaut des ressources en ligne d'une diffusion (en secondes).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Nouvelle URL des fichiers de ressource publique.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Gestion des campagnes et workflows {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Durée en mois au-delà de laquelle l'historique de marketing ignore les informations.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Durée de validité par défaut d’une opération (en secondes).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Nombre maximum de traitements de diffusions/workflows/hypothèses/simulations pouvant être exécutés en même temps, démarrés par le workflow operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Vous permet de surveiller l’exécution du workflow technique <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Si ce paramètre est activé (avec la valeur "1"), les informations d’exécution sont consignées dans les logs d’audit du workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Plage horaire pour les conditions de lancement des ciblages et des extractions en mode différé.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Nombre d'enregistrements modifiés à partir duquel une mise à jour des statistiques sera déclenchée automatiquement.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo à afficher en haut à droite des rapports exportés.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Nombre de jours à patienter entre les vérifications pour les workflows en pause.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Activez la validation des diffusion par le propriétaire de l'opération en entrant "1" comme valeur. Pour désactiver cette option, entrez "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Bibliothèque JS complémentaire à charger dans l'activité de workflow "Notification des ressources marketing".<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sécurité {#security}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBSchema</span> <br /> </td> 
   <td> (à compter de la version 21.1.3) Si 1 est sélectionné (valeur par défaut), cette option désactive l'édition des schémas intégrés.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (à compter de la version 21.1.3) Si 1 est sélectionné (valeur par défaut), cette option désactive l’édition des codes JavaScript intégrés.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Installer le mode de compatibilité : build&gt;6000) Lorsqu’elle est activée (valeur « 1 »), cette option permet l’utilisation d’anciens mots de passe stockés dans la base de données pour la connexion aux comptes externes ou à l’instance.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Cette clé est utilisée pour chiffrer la plupart des mots de passe dans la base de données (comptes externes, mot de passe LDAP...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Si 1 est sélectionné, cette option autorise privilegeEscalation dans JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Si 1 est sélectionné, cette option désactive les contrôles ACL lors du téléchargement d’un fichier (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Si 1 est sélectionné, cette option désactive le mode sandbox pour les fichiers en JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Si elle est définie sur "true", elle autorise les opérateurs non administrateurs à mettre à jour les valeurs xtkOption via l'assistant de déploiement.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Si 1 est sélectionné, cette option permet d'utiliser decryptString pour déchiffrer certains mots de passe.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Entrez la valeur "1" pour tracer la suppression des éléments avec les informations de piste de suivi dans le mData, via la modification de son champ "modifié par" avant la suppression de l'enregistrement.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Message Center {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> Bibliothèque JavaScript à personnaliser pour l'enrichissement des événements. Doit contenir l'implémentation de ces deux fonctions :<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : enrichit et enregistre les événements dans la base de données (où <span class="uicontrol">aiEventId</span> correspond à la table des événements temps réel traités).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : enrichit et enregistre les événements dans la base de données (où <span class="uicontrol">aiEventId</span> correspond à la table des ID des événements batch traités).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Date de la dernière mise à jour du statut des événements depuis les logs de diffusion.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> Bibliothèque JavaScript à personnaliser pour le routage des événements. Doit contenir l'implémentation de ces deux fonctions :<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> : renvoie le nom interne du message transactionnel sélectionné pour traiter l'événement temps réel (où <span class="uicontrol">iEventId</span> correspond à l'ID du traitement temps réel traité).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : renvoie le nom interne du message transactionnel sélectionné pour traiter l'événement batch (où <span class="uicontrol">iEventId</span> correspond à l'ID du traitement batch traité).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Seuil d'alerte du temps moyen d'envoi des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Seuil d’avertissement du temps moyen d’envoi des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Seuil d'alerte de durée moyenne de traitement des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Seuil d'avertissement de durée moyenne de traitement des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Seuil d'alerte de la moyenne d'événements temps réel en file d'attente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Seuil d'alerte du temps moyen des événements temps réel dans la file.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Seuil d'avertissement du temps moyen des événements temps réel dans la file.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Seuil d'avertissement de la moyenne d'événements temps réel en file d'attente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Seuil d'alerte des erreurs de traitement des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Seuil d'avertissement des erreurs de traitement des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Seuil d'alerte du maximum d'événements temps réel en file<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Seuil d'avertissement du maximum d'événements temps réel en file.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Seuil d'alerte du minimum d'événements temps réel en file.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Seuil d'avertissement du minimum d'événements temps réel en file.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Seuil avant alerte de la file d'événements temps réel en attente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Seuil avant warning de la file d'événements temps réel en attente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Seuil d'alerte de débit des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Seuil d'avertissement de débit des événements temps réel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Taille du regroupement pour le routage des événements.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Mettre à jour le pointeur du statut RtEvent (dernière date jusqu'à ce que les données aient été récupérées).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> URL du serveur Message Center pour envoyer les messages de bienvenue (canal LINE).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Base de données {#database}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Définit la dernière fois que le processus de nettoyage a été exécuté.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permet de définir le délai après lequel le broadlog est effacé de la base de données.</p><p>Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Permet de définir le délai après lequel l'historique des événements est effacé de la base de données.</p><p>
   Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Permet de définir le délai après lequel les événements sont effacés de la base de données.</p><p>Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Permet de définir le délai après lequel les statistiques d'événement sont effacées de la base de données.</p><p>Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Permet de définir le délai après lequel les propositions sont effacées de la base de données.</p><p> Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Permet de définir le délai après lequel les quarantaines sont effacées de la base de données.</p><p> Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Permet de définir le délai après lequel les diffusions recyclées sont effacées de la base de données.</p><p> Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Permet de définir le délai après lequel les rejets sont effacés de la base de données.</p><p>Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permet de définir le délai après lequel les logs de tracking sont effacés de la base de données.</p><p>Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Permet de définir le délai après lequel les statistiques de tracking sont effacées de la base de données.</p><p> Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Permet de définir le délai après lequel les visiteurs sont effacés de la base de données.</p><p> Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Permet de définir le délai après lequel les résultats de workflow sont effacés de la base de données.</p><p> Cette option est automatiquement créée une fois que le délai est modifié dans l'interface. Si vous modifiez la valeur de la liste d'options, elle doit être exprimée en secondes.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Options du connecteur Azure SQL Datawarehouse.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Permet d’affecter le comportement Arrêt inconditionnel à tous les workflows et requêtes de base de données PostgreSQL avec les valeurs potentielles suivantes :<ul>
    <li><p>0 – default : arrête le processus du workflow, sans impact sur la base de données<p></li>
    <li><p>1 -  pg_cancel_backend : arrête le processus du workflow et annule la requête dans la base de données<p></li>
    <li><p>2 – pg_terminate_backend : arrête le processus du workflow et interrompt la requête dans la base de données<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nom du tablespace destiné à contenir les données des tables ootb d’Adobe Campaign.<br />Voir la section <a href="../../installation/using/creating-and-configuring-the-database.md">Création et paramétrage de la base de données</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nom du tablespace destiné à contenir les index des tables ootb d’Adobe Campaign.<br />Voir la section <a href="../../installation/using/creating-and-configuring-the-database.md">Création et paramétrage de la base de données</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nom du tablespace destiné à contenir les données des tables de travail d'Adobe Campaign.<br />Voir la section <a href="../../installation/using/creating-and-configuring-the-database.md">Création et paramétrage de la base de données</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nom du tablespace destiné à contenir les index des tables de travail d'Adobe Campaign.<br />Voir la section <a href="../../installation/using/creating-and-configuring-the-database.md">Création et paramétrage de la base de données</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Permet de configurer une base de données distincte pour les tables de travail sous Microsoft SQL Server, afin d’optimiser les sauvegardes et la réplication. L’option correspond au nom de la base de données temporaire : les tables de travail seront écrites dans cette base de données en cas de spécification. Exemple : 'tempdb.dbo.' (notez que le nom doit se terminer par un point). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">En savoir plus</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Fuseau horaire de l’instance Adobe Campaign. Pour plus d'informations, consultez la section <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuration</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Les champs de chaîne de la base de données sont-ils définis avec NChar ?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Les champs 'datetime" de la base de données stockent-ils les informations de fuseau horaire ?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID de la base de données. Commence par 'u' pour la Base Unicode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Préfixe ajouté devant les noms internes générés automatiquement.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Nombre maximum de résultats renvoyés par une requête sur xtk:schema et xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Tous les schémas personnalisés créés après cette période et qui comprennent autopk="true", mais pas l’attribut "pkSequence", obtiendront une séquence générée automatiquement "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Pendant la migration, la structure arborescente est automatiquement réorganisée selon les standards de la nouvelle version.<br /> Cette option vous permet de désactiver la migration automatique de l'arbre de navigation. Si vous l'utilisez, après la migration vous devrez supprimer les dossiers obsolètes, ajouter les nouveaux dossiers et effectuer toutes les vérifications nécessaires.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Type de données :</span> entier</p> </li> 
     <li> <p> <span class="uicontrol">Valeur (texte)</span> : 1 </p> </li> 
    </ul> Cette option devrait uniquement être utilisée si l'arbre de navigation d'usine a subi un trop grand nombre de modifications.<br /> Voir à ce propos <a href="../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11">cette section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Date du dernier traitement de nettoyage de la table <span class="uicontrol">NmsEmailErrorStat</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informations relatives à l’erreur survenue dans le postupgrade, selon la syntaxe ci-dessous :<br /> <strong>{numéro de build}:{mode: pre/post/...}:{La valeur 'lessThan'/'greaterOrEquelThan' où l’erreur s’est produite + sous-étape}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Entrez la valeur "1" afin que la mise à jour des statistiques ne soit pas effectuée via le workflow de nettoyage.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Intégration {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Types de ressources AEM qui peuvent être utilisés dans Adobe Campaign. Les valeurs doivent être séparées par des virgules.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Permet de paramétrer les Triggers Experience Cloud. Le type de données est "texte long" et doit être au format JSON. Voir <a class="anchorLink" href="https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Utilisation des Triggers Experience Cloud avec Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Cette option est utilisée lors de l’importation de données à partir d’un système tiers via un connecteur CRM. En l’activant, vous pouvez collecter uniquement les objets modifiés depuis la dernière importation. Cette option doit être créée manuellement et remplie comme ci-dessous : 
    <ul> 
     <li> <p> <span class="uicontrol">Nom interne</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Valeur (champ)</span>:mm: : date de la dernière importation au format aaaa/mm/jj hh:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Serveur Adobe Target utilisé pour l'intégration. Cette option est déjà renseignée par défaut. Cette valeur correspond au Server Domain Adobe Target, suivie de la valeur /m2. Par exemple : tt.omtrdc.net/m2.<br /> Reportez-vous à <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">cette section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Nom de l'organisation Adobe Target. Cette valeur correspond au nom du Client Adobe Target.<br /> Reportez-vous à <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">cette section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Option utilisée pour l'intégration avec Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Option utilisée pour l'intégration avec Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Options du connecteur Teradata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Options du connecteur Hive.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Offres {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Nombre de coupons qui sont mis à jour par transaction SQL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [schéma de la proposition] + "_" + extAccountSource.@executionInstanceId + [schéma de la proposition] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [schéma de la proposition] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Tracking des workflows de synchronisation.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Activer/désactiver l'écriture de proposition asynchrone ("0" pour désactiver, "1" pour activer).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Permet d'activer les coupons.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Serveur {#server}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Identifiant de l'instance d'exécution.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Identifiant client utilisé pour l'envoi du rapport de facturation<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> URL de base du serveur applicatif interne.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Numéro de build de l'instance AC avant la dernière mise à niveau.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL de base du serveur d'application web public.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Permet de continuer à utiliser les anciennes fonctions SQL non déclarées après la migration. Nous vous recommandons fortement de ne pas utiliser cette option en raison des risques de sécurité qu'elle présente.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracking {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Permet d'activer le tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Script de calcul des URL suivies.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Permet de définir le compte externe du serveur de tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Permet de définir le nom de l'instance du serveur de tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Dernière fois que les informations sur le tracking ont été consolidées avec de nouvelles données.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Script de calcul de l'URL d'ouverture.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Mot de passe du serveur de tracking<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> Le pointeur effectue le suivi des derniers événements de messages qui ont été traités via leur identifiant et date.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> URL sécurisée du serveur de tracking frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL du serveur de tracking frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Liste des URL des différents serveurs de tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Jeu de règles pour l'identification des navigateurs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script de calcul des balises de tracking web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Nom de la diffusion virtuelle destinée à la gestion du tracking web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Permet de définir le mode de tracking web.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Confidentialité {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> Si l'option 1 est sélectionnée, vous devez confirmer manuellement, dans une seconde étape, la suppression dans l'interface utilisateur. Sinon, les données seront supprimées sans confirmation.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> Délai entre l'attente de la confirmation de suppression par la demande et l'annulation de la demande.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Nombre d'erreurs maximum autorisé lors du traitement/de la suppression d'une demande d'accès à des informations personnelles.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> Délai entre la création de la demande dans la file d'attente et la suppression des données de la demande.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Activer l'utilisation d'un serveur LDAP afin d'authentifier les utilisateurs et éventuellement de fournir les autorisations des utilisateurs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Login applicatif afin de contacter le serveur pour les diverses recherches.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Mot de passe chiffré du login applicatif.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Activer la création automatique d'utilisateurs et de leurs droits dans Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Formule de calcul de l'identifiant utilisateur LDAP (DN) en fonction de son login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Activer la recherche de l'identifiant utilisateur dans l'annuaire.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> Base de la recherche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> Filtre permettant la recherche de l'identifiant.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> Étendue de la recherche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> Type d'authentification utilisé pour contacter le serveur LDAP (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Activer la synchronisation des autorisations ou groupes définis dans l'annuaire LDAP vers les droits nommés Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> Attribut LDAP contenant le nom de l'autorisation.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Base de la recherche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Filtres de recherche des autorisations données à un utilisateur.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Expression permettant d'extraire les noms des droits Adobe Campaign à partir du nom des autorisations LDAP.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Étendue de la recherche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> Adresse du serveur LDAP (possibilité de préciser un port en utilisant ':' comme séparateur).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Formulaires web {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Nom de l'option </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> La définition de la valeur sur 1 permet l'ajout de la barre de défilement aux formulaires de détail.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instance à utiliser pour l'invalidation des formulaires web en mode 'autre(s) serveur(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Mot de passe de l'instance à utiliser pour l'invalidation des formulaires web en mode 'autre(s) serveur(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Option permettant de préciser le mode d'invalidation des formulaires web : local par défaut, utilise les serveurs de tracking si l'option est 'tracking' et utilise une liste personnalisée avec l'option 'autre(s) serveur(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Liste personnalisée des adresses des serveurs à contacter pour l'invalidation des formulaires web (mode 'Autre(s) serveur(s)').<br /> </td> 
  </tr> 
 </tbody> 
</table>

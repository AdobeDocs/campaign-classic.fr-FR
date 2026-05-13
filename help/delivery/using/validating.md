---
product: campaign
title: Validation
description: Validation
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Direct Mail
hide: true
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
TQID: https://experienceleague.adobe.com/I31u-kAqMRpzti-bOtfYjrGbwvmsfeEPwWU7kCFLzcQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 277
ht-degree: 64%

---

# Validation{#validating}



Les concepts généraux de validation d&#39;une diffusion sont présentés dans [cette section](steps-validating-the-delivery.md).

Le fichier de sortie d&#39;une diffusion par courrier est généré pendant l&#39;analyse de la diffusion. Le contenu du fichier dépend des colonnes de sortie sélectionnées (voir la section [Fichier d&#39;extraction](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>La phase d&#39;analyse est détaillée dans la section [Analyser la diffusion](steps-validating-the-delivery.md#analyzing-the-delivery).

Lors de la phase d’analyse, le fichier est généré mais les informations relatives aux destinataires (c’est-à-dire les logs de diffusion) ne sont pas mises à jour. Vous pouvez donc annuler ce traitement sans courir de risque.

Vérifiez le résultat de l&#39;analyse et le contenu du fichier de sortie avant de cliquer sur **[!UICONTROL Confirmer la diffusion]**. Un message de confirmation permet de lancer la diffusion.

La confirmation de l&#39;envoi lance l&#39;extraction des données dans le fichier spécifié.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Vous pouvez ensuite fermer l’assistant et consulter les logs de diffusion depuis l’onglet **[!UICONTROL Diffusion]** accessible à partir du détail de cette diffusion.

Vous pouvez paramétrer le mode de récupération des logs de diffusion à partir de l&#39;onglet **[!UICONTROL Analyse]** des Propriétés de la diffusion.

Deux modes sont proposés :

* **[!UICONTROL Les messages sont considérés envoyés suite à la validation]** (mode par défaut) : dans ce mode de fonctionnement, tous les broadlogs sont mis à jour lorsque l&#39;opérateur confirme l&#39;envoi (leur statut passe de &#39;En attente de diffusion&#39; à &#39;Envoyé&#39;) et le statut de la diffusion devient automatiquement **[!UICONTROL Terminé]**.
* **[!UICONTROL Un fichier de résultats détermine les messages envoyés et en échec]** : ce mode permet de mettre à jour les broadlogs via un fichier externe transmis par le prestataire. Dans ce cas, un workflow pour traiter ces informations doit être utilisé afin de mettre à jour le statut du broadlog.

  >[!NOTE]
  >
  >Dans ce cas, l&#39;utilisateur doit aussi modifier l&#39;état de la diffusion en **[!UICONTROL Terminé]** dès que les broadlogs sont mis à jour.

---
title: Résolution des problèmes liés à ACS Connector
seo-title: Résolution des problèmes liés à ACS Connector
description: Résolution des problèmes liés à ACS Connector
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Résolution des problèmes liés à ACS Connector{#troubleshooting-the-acs-connector}

Selon votre mise en œuvre, vous pouvez rencontrer quelques problèmes courants.

* **Quelles sont les différences d&#39;interface utilisateur entre Campaign Standard et Campaign v7 ?**

   Le mode de fonctionnement de Campaign Standard et Campaign v7 est très similaire. La plupart des concepts sont identiques, mais certains peuvent être légèrement différents. Voici quelques concepts qui peuvent être différents dans le contexte d&#39;ACS Connector :

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> destinataires (ou tout autre dimension de profil)<br /> </td> 
   <td> profils<br /> </td> 
  </tr> 
  <tr> 
   <td> liste<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> workflows de campagne, workflows de ciblage<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> opérations<br /> </td> 
   <td> campagnes<br /> </td> 
  </tr> 
  <tr> 
   <td> applications web<br /> </td> 
   <td> landing pages<br /> </td> 
  </tr> 
  <tr> 
   <td> table personnalisée et extension de schéma<br /> </td> 
   <td> ressource personnalisée et extension de ressource<br /> </td> 
  </tr> 
  <tr> 
   <td> membres des adresses de contrôle<br /> </td> 
   <td> profils de test<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **Les destinataires de mon instance de Campaign v7 ne sont pas synchronisés ou visibles dans Campaign Standard.**

   Cette situation peut se produire pour plusieurs raisons :

   * Les destinataires ont été créés ou mis à jour très récemment dans Campaign v7. Comme la synchronisation a lieu toutes les 15 minutes, les destinataires mis à jour ou nouvellement créés seront visibles dans Campaign Standard après la prochaine synchronisation.
   * Votre mise en œuvre peut avoir été définie pour ne synchroniser que les destinataires de dossiers spécifiques. Les destinataires des autres dossiers ne sont pas synchronisés.
   * Les destinataires peuvent être synchronisés mais non visibles dans Campaign Standard. Vérifiez le mapping des dossiers.

* **Je ne trouve pas les champs de profil dont j&#39;ai besoin pour ma requête dans Campaign Standard.**

   Par défaut, 20 champs de la table nms:recipient sont synchronisés avec Campaign Standard. Consultez la liste détaillée des champs synchronisés. Les champs supplémentaires que vous devez récupérer dans Campaign Standard doivent être associés et configurés par votre consultant.

   To make sure the field you want to use is available, you can check the profile resource definition from **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   De plus, toutes les données associées aux destinataires et stockées dans les tables liées à nms:recipients ne sont pas synchronisées par défaut dans Campaign Standard.

   To still be able to use related data, you can perform your targeting in Campaign v7 and add additional data as explained in the [Synchronizing audiences](../../integrations/using/synchronizing-audiences.md) section, or you can refer to your consultant to explore customization possibilities.

* **J&#39;utilise une autre dimension de profil que la table nms:recipient par défaut dans Campaign v7. Comment synchroniser les profils avec Campaign Standard ?**

   Campaign Standard utilise une ressource de ciblage unique appelée **profils**. La mise en œuvre de base de la fonctionnalité ACS Connector fournit un mapping par défaut entre les destinataires de Campaign v7 et les profils de Campaign Standard.

   Si vous utilisez une autre dimension de profil dans Campaign v7 ou si vous en utilisez plusieurs, elles doivent toutes être associées aux profils de Campaign Standard. Contactez votre consultant pour aborder ce besoin spécifique.

* **Je souhaite partager une liste de profils avec Campaign Standard par le biais d&#39;un workflow, mais je ne trouve pas mon audience dans Campaign Standard**.

   Les audiences se trouvent dans le **[!UICONTROL Audiences]** menu de Campaign Standard. L’étiquette est spécifiée dans l’ **[!UICONTROL List update]** activité dans votre flux de travail Campaign v7. Ils sont soumis au mappage de dossiers défini lors de l’implémentation.

   La première chose à vérifier est de savoir si le flux de travail s’est terminé sans erreur. Si vous constatez une erreur sur l’ **[!UICONTROL List update]** activité, cela signifie que la synchronisation avec Campaign Standard a peut-être échoué. Pour plus d’informations sur ce qui s’est passé, accédez à **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Ce dossier contient les processus de synchronisation déclenchés par l’exécution de l’ **[!UICONTROL List update]** activité.

   Also, make sure that the **[!UICONTROL Share with ACS]** option is checked in the **[!UICONTROL List update]** activity and that the workflow was correctly executed.

   Les profils des destinataires contenus dans la liste doivent avoir été synchronisés avec Campaign Standard avant l&#39;exécution du workflow. Lorsqu&#39;ils sont partagés avec Campaign Standard, les destinataires de la liste sont réconciliés avec les profils Campaign Standard, ce qui implique qu&#39;ils doivent s&#39;y trouver. Les destinataires de la liste qui ne peuvent pas être réconciliés avec les profils de Campaign Standard sont ignorés.

   Si vous partagez une liste composée de profils qu&#39;aucun d&#39;entre eux n&#39;est synchronisé avec Campaign Standard, une audience de type requête vide est créée dans Campaign Standard. Celle-ci ne peut pas être utilisée.

* **Une notification m&#39;informe qu&#39;un workflow de synchronisation est en erreur. Que dois-je faire ?**

   Vérifiez la configuration du compte externe dans Campaign Standard et Campaign v7 en testant la connexion :

   * **[!UICONTROL acsDefaultRelayAccount]** dans Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** dans Campaign v7.

* **Aucun groupe de sécurité n&#39;est disponible lors du mapping des dossiers entre Campaign v7 et Campaign Standard.**

   Vous devez d&#39;abord synchroniser vos groupes de sécurité à partir de **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Cette action vérifie les groupes de sécurité disponibles dans Campaign Standard. Une fois synchronisée, vous pouvez trouver les groupes de sécurité lors de la configuration du mappage de dossiers.

* **Je ne peux pas éditer un profil, une audience ou une landing page dans Campaign Standard. Pourquoi ?**

   Les ressources synchronisées depuis Campaign v7 sont en lecture seule dans Campaign Standard pour garantir la cohérence des données. Si vous devez éditer l&#39;un de ces éléments, vous pouvez le faire dans Campaign v7 et répliquer ensuite la modification dans Campaign Standard.


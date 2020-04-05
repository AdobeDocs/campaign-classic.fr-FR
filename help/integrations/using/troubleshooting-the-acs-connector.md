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

   Pour vous assurer que le champ que vous souhaitez utiliser est disponible, vous pouvez vérifier la définition de la ressource de profil dans **[!UICONTROL Administration > Développement > Diagnostic > Schémas de données]**.

   De plus, toutes les données associées aux destinataires et stockées dans les tables liées à nms:recipients ne sont pas synchronisées par défaut dans Campaign Standard.

   Pour pouvoir continuer à utiliser les données associées, vous pouvez effectuer votre ciblage dans Campaign v7 et ajouter des données additionnelles comme décrit dans la section [Synchronisation des audiences](../../integrations/using/synchronizing-audiences.md). Vous pouvez également contacter votre consultant pour explorer les possibilités de personnalisation.

* **J&#39;utilise une autre dimension de profil que la table nms:recipient par défaut dans Campaign v7. Comment synchroniser les profils avec Campaign Standard ?**

   Campaign Standard utilise une ressource de ciblage unique appelée **profils**. La mise en œuvre de base de la fonctionnalité ACS Connector fournit un mapping par défaut entre les destinataires de Campaign v7 et les profils de Campaign Standard.

   Si vous utilisez une autre dimension de profil dans Campaign v7 ou si vous en utilisez plusieurs, elles doivent toutes être associées aux profils de Campaign Standard. Contactez votre consultant pour aborder ce besoin spécifique.

* **Je souhaite partager une liste de profils avec Campaign Standard par le biais d&#39;un workflow, mais je ne trouve pas mon audience dans Campaign Standard**.

   Les audiences figurent dans le menu **[!UICONTROL Audiences]** de Campaign Standard. Leur libellé est spécifié dans l&#39;activité **[!UICONTROL Mise à jour de liste]** du workflow de Campaign v7. Le mapping des dossiers défini pendant la mise en œuvre s&#39;applique aux audiences.

   Commencez par vérifier si le workflow s&#39;est terminé sans erreurs. Si vous remarquez une erreur dans l&#39;activité **[!UICONTROL Mise à jour de liste]**, cela signifie que la synchronisation avec Campaign Standard ne s&#39;est peut-être pas effectuée correctement. Pour déterminer ce qui s&#39;est passé, accédez à **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Traitement]** > **[!UICONTROL Diagnostic]**. Ce dossier contient les workflows de synchronisation déclenchés par l&#39;exécution de l&#39;activité **[!UICONTROL Mise à jour de liste]**.

   Vérifiez également que l&#39;option **[!UICONTROL Partager avec ACS]** est cochée dans l&#39;activité **[!UICONTROL Mise à jour de liste]** et que le workflow a été exécuté correctement.

   Les profils des destinataires contenus dans la liste doivent avoir été synchronisés avec Campaign Standard avant l&#39;exécution du workflow. Lorsqu&#39;ils sont partagés avec Campaign Standard, les destinataires de la liste sont réconciliés avec les profils Campaign Standard, ce qui implique qu&#39;ils doivent s&#39;y trouver. Les destinataires de la liste qui ne peuvent pas être réconciliés avec les profils de Campaign Standard sont ignorés.

   Si vous partagez une liste composée de profils qu&#39;aucun d&#39;entre eux n&#39;est synchronisé avec Campaign Standard, une audience de type requête vide est créée dans Campaign Standard. Celle-ci ne peut pas être utilisée.

* **Une notification m&#39;informe qu&#39;un workflow de synchronisation est en erreur. Que dois-je faire ?**

   Vérifiez la configuration du compte externe dans Campaign Standard et Campaign v7 en testant la connexion :

   * **[!UICONTROL acsDefaultRelayAccount]** dans Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** dans Campaign v7.

* **Aucun groupe de sécurité n&#39;est disponible lors du mapping des dossiers entre Campaign v7 et Campaign Standard.**

   Vous devez d&#39;abord synchroniser vos groupes de sécurité dans **[!UICONTROL Administration > ACS Connector > Gestion des droits > Groupes de sécurité]**. Cette action vérifie les groupes de sécurité disponibles dans Campaign Standard. Une fois les groupes de sécurité synchronisés, vous pouvez les trouver lors de la configuration du mapping des dossiers.

* **Je ne peux pas éditer un profil, une audience ou une landing page dans Campaign Standard. Pourquoi ?**

   Les ressources synchronisées depuis Campaign v7 sont en lecture seule dans Campaign Standard pour garantir la cohérence des données. Si vous devez éditer l&#39;un de ces éléments, vous pouvez le faire dans Campaign v7 et répliquer ensuite la modification dans Campaign Standard.


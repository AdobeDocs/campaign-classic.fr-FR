---
product: campaign
title: Résolution des problèmes liés au connecteur ACS
description: Résolution des problèmes liés au connecteur ACS
feature: ACS Connector, Troubleshooting
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
TQID: https://experienceleague.adobe.com/hqQ4rSZpOoCMn9sA0yu2VsHFxTGEnwGwOMi6cu6e-1Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
  - id: bea9e610-36b4-4df2-94bb-0fb6fe46cb50
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 901
ht-degree: 59%

---

# Résolution des problèmes liés au connecteur ACS{#troubleshooting-the-acs-connector}



Selon votre mise en œuvre, vous pouvez rencontrer quelques problèmes courants.

* **Quelles sont les différences d&#39;interface utilisateur entre Campaign Standard et Campaign v7 ?**

  Campaign Standard et Campaign v7 fonctionnent de manière très similaire. La plupart des concepts sont identiques, mais dans certains cas, l’approche peut être légèrement différente. Voici quelques-uns des concepts qui peuvent différer dans le contexte d’ACS Connector :

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
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

* **Les destinataires de mon instance de Campaign v7 ne sont pas synchronisés ou visibles dans Campaign Standard.**

  Cette situation peut se produire pour plusieurs raisons :

   * Les destinataires viennent d&#39;être créés ou mis à jour dans Campaign v7. La synchronisation se déclenche toutes les 15 minutes. En d’autres termes, les destinataires mis à jour ou nouvellement créés seront visibles dans Campaign Standard après la prochaine synchronisation.
   * Votre implémentation peut avoir été définie pour synchroniser uniquement les destinataires de dossiers spécifiques. Les destinataires d&#39;autres dossiers ne sont pas synchronisés.
   * Le destinataire peut être synchronisé mais non visible dans Campaign Standard. Vérifiez le mappage des droits du dossier .

* **Je ne trouve pas les champs de profil dont j&#39;ai besoin pour ma requête dans Campaign Standard.**

  Par défaut, 20 champs du tableau nms:recipient sont synchronisés avec Campaign Standard. Consultez la liste détaillée des champs synchronisés. Les champs supplémentaires que vous devez récupérer dans Campaign Standard doivent être associés et configurés par votre consultant.

  Pour vous assurer que le champ que vous souhaitez utiliser est disponible, vous pouvez vérifier la définition de la ressource de profil dans **[!UICONTROL Administration > Développement > Diagnostic > Schémas de données]**.

  En outre, toutes les données associées aux destinataires et stockées dans les tables liées à nms:recipients ne sont pas synchronisées par défaut avec Campaign Standard.

  Pour pouvoir continuer à utiliser les données associées, vous pouvez effectuer votre ciblage dans Campaign v7 et ajouter des données additionnelles comme décrit dans la section [Synchronisation des audiences](../../integrations/using/synchronizing-audiences.md). Vous pouvez également contacter votre consultant pour découvrir avec lui les possibilités de personnalisation.

* **J&#39;utilise une autre dimension de profil que la dimension nms par défaut:recipient dans Campaign v7, comment synchroniser les profils avec Campaign Standard ?**

  Campaign Standard utilise une ressource de ciblage unique nommée **profils**. La mise en œuvre de base de la fonction Campaign Standard Connect fournit un mappage par défaut entre les destinataires de Campaign v7 et les profils de Campaign Standard.

  Si vous utilisez une autre dimension de profil dans Campaign v7, ou si vous en utilisez plusieurs, elles doivent toutes être associées à des profils Campaign Standard. Consultez votre consultant pour répondre à ce besoin particulier.

* **Je souhaite partager une liste de profils avec Campaign Standard par le biais d&#39;un workflow, mais je ne trouve pas mon audience dans Campaign Standard**.

  Les audiences figurent dans le menu **[!UICONTROL Audiences]** de Campaign Standard. Leur libellé est spécifié dans l&#39;activité **[!UICONTROL Mise à jour de liste]** du workflow de Campaign v7. Le mapping des dossiers défini pendant la mise en œuvre s&#39;applique aux audiences.

  Commencez par vérifier si le workflow s&#39;est terminé sans erreurs. Si vous remarquez une erreur dans l&#39;activité **[!UICONTROL Mise à jour de liste]**, cela signifie que la synchronisation avec Campaign Standard ne s&#39;est peut-être pas effectuée correctement. Pour déterminer ce qui s’est passé, accédez à **[!UICONTROL Administration]** > **[!UICONTROL Connecteur ACS]** > **[!UICONTROL Traitement]** > **[!UICONTROL Diagnostic]**. Ce dossier contient les workflows de synchronisation déclenchés par l&#39;exécution de l&#39;activité **[!UICONTROL Mise à jour de liste]**.

  Vérifiez également que l&#39;option **[!UICONTROL Partager avec ACS]** est cochée dans l&#39;activité **[!UICONTROL Mise à jour de liste]** et que le workflow a été exécuté correctement.

  Notez que les profils des destinataires contenus dans la liste doivent avoir été synchronisés avec Campaign Standard avant l’exécution du workflow. Une fois partagée avec Campaign Standard, les destinataires de la liste sont réconciliés avec les profils Campaign Standard, ce qui signifie qu’ils doivent y exister. Les destinataires de la liste qui ne peuvent pas être réconciliés avec des profils dans Campaign Standard sont ignorés.

  Si vous partagez une liste composée de profils qu&#39;aucun d&#39;entre eux n&#39;est synchronisé avec Campaign Standard, une audience de type requête vide est créée dans Campaign Standard. Celle-ci ne peut pas être utilisée.

* **Une notification m&#39;informe qu&#39;un workflow de synchronisation est en erreur. Que dois-je faire ?**

  Vérifiez la configuration du compte externe dans Campaign Standard et Campaign v7 en testant la connexion :

   * **[!UICONTROL acsDefaultRelayAccount]** dans Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** dans Campaign v7.

* **Aucun groupe de sécurité n&#39;est disponible lors du mapping des dossiers entre Campaign v7 et Campaign Standard.**

  Vous devez d&#39;abord synchroniser vos groupes de sécurité à partir de **[!UICONTROL Administration > ACS Connector > Gestion des droits > Groupes de sécurité]**. Cette action vérifie les groupes de sécurité disponibles dans Campaign Standard. Une fois la synchronisation effectuée, vous pouvez trouver les groupes de sécurité lors de la configuration du mappage des dossiers.

* **Je ne peux pas modifier un profil, une audience ou une page de destination dans Campaign Standard. Pourquoi ?**

  Les ressources synchronisées à partir de Campaign v7 sont en lecture seule dans Campaign Standard, afin d’assurer la cohérence des données. Si vous devez modifier l’un de ces éléments, vous pouvez le faire dans Campaign v7, puis répliquer la modification dans Campaign Standard.

* **Des erreurs se produisent dans le workflow [ACS] Réplication des logs de diffusion du profil. Que dois-je faire ?**

  Si des instances Campaign Classic et Campaign Standard sont utilisées pour envoyer des e-mails avec des URL trackées, un problème lié à des tagID d’URL en double peut se produire pendant la synchronisation. Dans le cas présent, le workflow **[ACS] Réplication des logs de diffusion du profil** (newRcpDeliveryLogReplication) échoue toujours en signalant l&#39;erreur suivante :

  ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

  Pour résoudre le problème et empêcher qu&#39;il se reproduise, mettez à jour l&#39;activité **Mise à jour des URL de tracking** (writerTrackingUrls) dans le workflow et ajoutez le préfixe « ACS » à l&#39;expression source @tagId.

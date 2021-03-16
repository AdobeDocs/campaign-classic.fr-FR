---
solution: Campaign Classic
product: campaign
title: Configuration et envoi de la diffusion
description: Configuration et envoi de la diffusion
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: ht
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: ht
source-wordcount: '1617'
ht-degree: 100%

---


# Configuration et envoi de la diffusion {#configuring-and-sending-the-delivery}

>[!NOTE]
>
>Seul le propriétaire d&#39;une diffusion peut démarrer cette dernière. Pour qu&#39;un autre opérateur (ou un groupe d&#39;opérateurs) puisse démarrer une diffusion, vous devez l&#39;ajouter comme validant au niveau du champ **[!UICONTROL Démarrage de la diffusion.]** Voir à ce sujet [cette section](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Paramètres supplémentaires de diffusion {#delivery-additiona-parameters}

Avant d&#39;envoyer la diffusion, vous pouvez définir les paramètres d&#39;envoi dans les propriétés de la diffusion, via l&#39;onglet **[!UICONTROL Diffusion]**.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Priorité de diffusion]** : cette option vous permet d’influencer l’ordre d’envoi des diffusions en indiquant leur niveau de priorité (normal, élevé ou faible). Vous pouvez ainsi privilégier l’envoi de certaines diffusions plus urgentes que d’autres.

* **[!UICONTROL Regrouper les messages par]** : cette option permet de définir le nombre de messages regroupés au sein d’un même package d’envoi XML. Si le paramètre est défini sur 0, les messages sont automatiquement regroupés. La taille du paquet est définie par le calcul `<delivery size>/1024`, avec un minimum de 8 messages et un maximum de 256 messages par package.

   >[!IMPORTANT]
   >
   >Lorsque la diffusion est dupliquée, le paramètre est remis à zéro.

* **[!UICONTROL Envoyer en plusieurs vagues]** : pour plus d’informations, voir la section [Envoyer en plusieurs vagues](#sending-using-multiple-waves).

* **[!UICONTROL Tester l’envoi par SMTP]** : cette option vous permet de tester l’envoi d’une diffusion via SMTP. La diffusion est traitée jusqu’à la connexion au serveur SMTP mais n’est pas envoyée.

   >[!NOTE]
   >
   >L&#39;utilisation de cette option est déconseillée dans le cas d&#39;une installation en mid-sourcing afin de ne pas faire appel au MTA. Pour plus d&#39;informations sur la configuration d&#39;un serveur SMTP, voir [cette section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* **[!UICONTROL Email Cci]** : permet de stocker les emails sur un système externe à l&#39;aide de l&#39;option BCC en ajoutant une adresse email en &quot;copie cachée&quot; (Cci, ou Bcc en anglais) à la cible des messages. Voir à ce propos [cette section](../../delivery/using/sending-messages.md#archiving-emails).

## Confirmation de l&#39;envoi des diffusions.{#confirming-delivery}

Une fois la diffusion configurée et prête à être envoyée, vérifiez que vous avez exécuté l’analyse de la diffusion.

Pour ce faire, cliquez sur **[!UICONTROL Envoyer]**, sélectionnez l’action souhaitée et cliquez sur **[!UICONTROL Analyser]**. Voir à ce propos la section [Lancement de l&#39;analyse](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Une fois que vous avez terminé, cliquez sur **[!UICONTROL Confirmer l’envoi]** pour lancer la diffusion des messages.

Vous pouvez ensuite fermer l&#39;assistant de diffusion et suivre l&#39;exécution de la diffusion depuis l&#39;onglet **[!UICONTROL Diffusion]** accessible à partir du détail de cette diffusion ou depuis la liste des diffusions.

Une fois les messages envoyés, vous pouvez effectuer le suivi et le tracking des diffusions.Voir à ce sujet les sections suivantes :

* [Contrôler une diffusion](../../delivery/using/about-delivery-monitoring.md)
* [Comprendre les diffusions en échec](../../delivery/using/understanding-delivery-failures.md)
* [A propos du tracking des messages](../../delivery/using/about-message-tracking.md)

## Planifier l&#39;envoi de diffusion {#scheduling-the-delivery-sending}

Vous pouvez différer la diffusion des messages pour planifier l&#39;envoi ou pour gérer la pression commerciale afin de ne pas sur-solliciter une population.

1. Cliquez sur le bouton **[!UICONTROL Envoyer]** et sélectionnez l’option **[!UICONTROL Différer la diffusion]**.

1. Indiquez une date de démarrage dans le champ **[!UICONTROL Date de contact]**.

![](assets/dlv_email_del_plan.png)

1. Vous pouvez ensuite lancer l’analyse de la diffusion, puis confirmer son envoi. Toutefois, cet envoi ne démarrera pas avant la date indiquée dans le champ **[!UICONTROL Date de contact]**.

>[!IMPORTANT]
>
>Une fois que vous avez lancé l&#39;analyse, la date de contact que vous avez définie est figée.Si vous modifiez cette date, veillez à relancer l&#39;analyse pour que vos modifications soient bien prises en compte.

![](assets/s_ncs_user_email_del_start_delayed.png)

Dans la liste des diffusions, la diffusion apparaît avec le statut **[!UICONTROL En attente]**.

![](assets/s_ncs_user_email_del_waiting.png)

La planification peut aussi être paramétrée en amont via le bouton **[!UICONTROL Planification]** de la diffusion.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Elle vous permet de différer la diffusion à une date ultérieure ou enregistrer la diffusion dans le calendrier prévisionnel.

* L&#39;option **[!UICONTROL Planifier la diffusion (pas d&#39;exécution automatique)]** permet de planifier une analyse prévisionnelle de la diffusion.

   Lorsque ce paramétrage est enregistré, la diffusion passe alors dans l&#39;état **[!UICONTROL Ciblage en attente]**.L&#39;analyse sera lancée à la date indiquée.

* L&#39;option **[!UICONTROL Planifier la diffusion (exécution automatique à la date prévue)]** permet d&#39;indiquer la date de contact.

   Cliquez sur le bouton **[!UICONTROL Envoyer]** et choisissez **[!UICONTROL Différer la diffusion]** puis lancez l&#39;analyse et confirmez l&#39;envoi. Une fois l&#39;analyse terminée, la cible de la diffusion est prête et les messages seront automatiquement envoyés à la date indiquée.

Les dates et heures sont entendues dans le fuseau horaire de l&#39;opérateur courant. La liste déroulante **[!UICONTROL Fuseau horaire]** située sous la zone de saisie de la date de contact permet d&#39;adapter automatiquement la date et l&#39;heure saisie dans le fuseau horaire sélectionné.

Ainsi, si vous planifiez une diffusion pour qu&#39;elle s&#39;exécute automatiquement à 8h heure de Londres, l&#39;heure est automatiquement convertie dans le fuseau sélectionné :

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Envoyer en plusieurs vagues {#sending-using-multiple-waves}

Pour équilibrer la charge, vous pouvez répartir les envois en plusieurs lots. Configurez le nombre de lots et leur proportion par rapport à l&#39;ensemble de la diffusion.

>[!NOTE]
>
>Vous pouvez uniquement définir la taille et le délai entre deux vagues consécutives. Le critère de sélection des destinataires pour chaque vague n&#39;est pas paramétrable.

1. Ouvrez la fenêtre des propriétés de la diffusion, puis cliquez sur l&#39;onglet **[!UICONTROL Diffusion]**.
1. Sélectionnez l&#39;option **[!UICONTROL Envoyer en plusieurs vagues]**, puis cliquez sur le lien **[!UICONTROL Définition des vagues...]**.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Pour configurer des vagues, vous pouvez effectuer l&#39;une des opérations suivantes :

   * Définissez la taille de chaque vague. Par exemple, si vous saisissez **[!UICONTROL 30 %]** dans le champ correspondant, chaque vague représentera 30 % des messages inclus dans l&#39;envoi, à l&#39;exception de la dernière vague qui représentera 10 % des messages.

      Dans le champ **[!UICONTROL Période]**, définissez le délai entre le démarrage de deux vagues consécutives. Par exemple, si vous saisissez **[!UICONTROL 2j]**, la première vague démarre immédiatement, la deuxième démarre dans deux jours, la troisième dans quatre jours, etc.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Définissez un calendrier pour l&#39;envoi de chaque vague.

      Dans la colonne **[!UICONTROL Démarrage]**, indiquez le délai entre le démarrage de deux vagues consécutives. Dans la colonne **[!UICONTROL Taille]**, saisissez un nombre fixe ou un pourcentage.

      Dans l&#39;exemple ci-dessous, la première vague représente 25 % du nombre total des messages inclus dans l&#39;envoi et démarre immédiatement. Les deux vagues suivantes terminent l&#39;envoi et sont définies pour démarrer à six heures d&#39;intervalle.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   Une règle de typologie spécifique, la **[!UICONTROL Vérification de la planification des vagues]**, garantit que la dernière vague est planifiée avant la limite de validité de la diffusion. Les typologies de campagne et leurs règles, paramétrées dans l’onglet **[!UICONTROL Typologie]** des propriétés d’une diffusion, sont présentées dans la section [Processus de validation avec des typologies](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Veillez à ce que les dernières vagues ne dépassent pas la date limite d&#39;envoi qui est définie dans l&#39;onglet **[!UICONTROL Validité]**.Sinon, certains messages peuvent ne pas être envoyés.
   >
   >Lors de la configuration des dernières vagues, veillez également à prévoir assez de temps pour les reprises. Reportez-vous à [cette section](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).

1. Pour suivre vos envois, accédez aux logs de diffusion. Voir à ce sujet [cette page](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

   Vous pouvez visualiser les diffusions qui ont déjà été envoyées dans les vagues traitées (statut **[!UICONTROL Envoyé]**) et celles à envoyer dans les vagues restantes (statut **[!UICONTROL En attente]**).

Les deux exemples ci-dessous constituent les cas d&#39;utilisation les plus fréquents de plusieurs vagues.

* **Lors de la phase de démarrage**

   Lorsque vous envoyez des emails à l&#39;aide d&#39;une nouvelle plate-forme, rien n&#39;est plus suspect pour un FAI (fournisseur d&#39;accès internet) que les adresses IP qui ne sont pas reconnues. Si des emails sont subitement envoyés en masse, le FAI les range souvent dans le courrier indésirable.

   Pour éviter que les emails soient marqués comme spam, vous pouvez augmenter progressivement le volume envoyé à l&#39;aide de vagues. Cela permet d&#39;entamer la phase de démarrage en douceur et de réduire le nombre total d&#39;adresses invalides.

   Pour ce faire, utilisez l&#39;option **[!UICONTROL Planifier les vagues selon un calendrier]**. Par exemple, définissez la première vague sur 10 %, la deuxième sur 15 %, etc.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagnes impliquant un centre d&#39;appels**

   Lorsque vous gérez une campagne téléphonique de fidélisation, votre entreprise a une capacité de traitement des appels limitée pour contacter les abonnés.

   Grâce aux vagues, vous pouvez limiter le nombre des messages à 20 par jour, ce qui correspond à la capacité de traitement quotidien d&#39;un centre d&#39;appels.

   Pour ce faire, sélectionnez l&#39;option **[!UICONTROL Planifier plusieurs vagues de même taille]**. Saisissez **[!UICONTROL 20]** pour la taille de la vague et **[!UICONTROL 1j]** dans le champ **[!UICONTROL Période]**.

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Paramétrer les reprises {#configuring-retries}

Les messages temporairement non diffusés en raison d&#39;une erreur **Soft** ou **Ignoré** sont soumis à une nouvelle reprise automatique. Les types et les raisons d&#39;échec de diffusion sont présentés dans cette [section](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué une mise à niveau vers le [MTA amélioré](../../delivery/using/sending-with-enhanced-mta.md), les paramètres de reprise de la diffusion ne sont plus utilisés par Campaign. Les reprises des erreurs soft et l’intervalle qui les sépare sont déterminés par le MTA amélioré en fonction du type et de la gravité des réponses des retours provenant du domaine d&#39;email du message.

Pour les installations on-premise et les installations hébergées/hybrides utilisant l’ancien MTA de Campaign, la section centrale de l’onglet **[!UICONTROL Diffusion]** pour les paramètres de diffusion indique le nombre de reprises à effectuer le lendemain de la diffusion et le délai minimal entre celles-ci.

![](assets/s_ncs_user_wizard_retry_param.png)

Par défaut, cinq reprises sont planifiées le premier jour de l’envoi, avec un intervalle minimum d’une heure, réparties sur les 24h de la journée. Après cela, une reprise est programmée chaque jour jusqu’à la date limite de diffusion, qui est définie dans l’onglet **[!UICONTROL Validité]** (voir la section [Définir la période de validité](#defining-validity-period)).

## Définir la période de validité {#defining-validity-period}

Une fois la diffusion lancée, les messages (et les éventuelles reprises) peuvent être envoyés jusqu&#39;à la limite de la diffusion. Elle est indiquée dans les propriétés de la diffusion, à partir de l&#39;onglet **[!UICONTROL Validité]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* Le champ **[!UICONTROL Durée de diffusion]** permet de saisir la limite pour des reprises globales de diffusion. Concrètement, Adobe Campaign diffuse les messages à partir de la date de lancement. Puis, pour les messages en erreur uniquement, des reprises régulières et paramétrables sont effectuées tant que la limite de diffusion n&#39;est pas atteinte.

   Vous pouvez également choisir de spécifier des dates.Pour cela, cochez l&#39;option **[!UICONTROL Fixer explicitement les dates de validité]**. Dans ce cas, les dates limites de diffusion et de validité permettent de préciser également l&#39;heure. Cette heure correspond par défaut à l&#39;heure courante mais peut être modifiée directement dans le champ de saisie.

   >[!IMPORTANT]
   >
   >Pour les installations hébergées ou hybrides, si vous avez effectué une mise à niveau vers le [MTA amélioré](../../delivery/using/sending-with-enhanced-mta.md), le paramètre **[!UICONTROL Durée de diffusion]** des diffusions Campaign ne sera utilisé que s’il est défini sur **3,5 jours ou moins**. Si vous définissez une valeur supérieure à 3,5 jours, elle ne sera pas prise en compte.

* **Limite de validité des ressources** : le champ **[!UICONTROL Limite de validité]** est utilisé pour les ressources téléchargées, principalement pour la page miroir et les images. Les ressources de cette page ont une durée de validité limitée (afin d&#39;économiser de l&#39;espace disque).

   Dans ce champ, les valeurs peuvent être exprimées dans les unités listées dans [cette section](../../platform/using/adobe-campaign-workspace.md#default-units).

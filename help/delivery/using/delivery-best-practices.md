---
title: Recommandations relatives à la diffusion Campaign
seo-title: Bonnes pratiques de diffusion
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f599bc5483779ae62dd4d5eb1936cbc2760639b5
workflow-type: tm+mt
source-wordcount: '4395'
ht-degree: 56%

---


# Bonnes pratiques de diffusion {#delivery-best-practices}

## Optimisez votre diffusion {#optimize-delivery}

Avant même de commencer à créer des diffusions, vous pouvez prendre des mesures pour sécuriser et optimiser le processus d&#39;envoi en amont.

La section suivante présente les bonnes pratiques et les procédures recommandées pour optimiser la configuration d&#39;Adobe Campaign. L&#39;application de ces pratiques permettra de limiter les problèmes que vous risquez de rencontrer en aval.

### Performances de la plate-forme

Plusieurs facteurs peuvent avoir une incidence directe sur les performances du serveur et ralentir la plate-forme :

* Nombre et type d’éléments de personnalisation : la personnalisation dans les courriers électroniques extrait les données de la base de données pour chaque destinataire. Si les éléments de personnalisation sont nombreux, la quantité de données nécessaire pour préparer la diffusion augmente.  Learn more about personalization in [this section](../../delivery/using/about-personalization.md)

* Chargement du serveur : lorsque le serveur marketing gère plusieurs tâches différentes en même temps, il peut ralentir les performances. Le serveur marketing doit coordonner toutes les données entrantes et sortantes pour toutes les diffusions afin de s’assurer que les données sont correctes et à temps.

   **CONSEIL** - Pour éviter cela, coordonnez la planification des diffusions avec les autres membres de votre équipe afin d’assurer les meilleures performances.

* Exécution du flux de travaux : la surveillance de vos workflows est essentielle pour éviter les problèmes de performances de la plate-forme. Suivez les directives énumérées [dans ce document](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* En tant que client hébergé, vous pouvez tirer parti des fonctionnalités [du panneau de contrôle](https://docs.adobe.com/content/help/fr-FR/control-panel/using/discover-control-panel/key-features.html) Campaign pour surveiller votre plateforme à l’aide des fonctionnalités de surveillance [des](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) performances.

### Vérifier la configuration du réseau {#network-config}

Pour optimiser une diffusion lors d&#39;un envoi en masse et éviter d&#39;être pris pour un spammeur, vérifiez que vous disposez d&#39;une configuration réseau correcte qui ne cherche pas à cacher des informations.

**Conseil**:  Utilisez une adresse d’expéditeur transparente correspondant au site Web de votre marque. Par exemple, la société TravelAgency gère la chaîne d&#39;hôtels Valentino. Elle possède le domaine valentino.com pour son site web. Pour promouvoir l’hôtel Valentino à Paris, elle utilise le sous-domaine paris.valentino.com. Une adresse d’expéditeur pertinente peut donc être hotel@paris.valentino.com.

### Gestion de la délivrabilité {#deliverability-management}

Pour que vos messages arrivent dans la boîte de réception de vos destinataires sans rebond et sans être marqués comme spam, vous devez en améliorer la délivrabilité.

* Qu’est-ce que la délivrabilité ?

   * La délivrabilité désigne les facteurs qui déterminent la capacité d’un email à être accepté par le serveur d’un destinataire. Les fournisseurs d’accès à Internet (FAI) filtrent les emails qu’ils identifient comme spam ou bloquent le téléchargement des images. S’ils déterminent qu’un domaine donné envoie un trop grand nombre d’emails, ils fixent une limite au nombre d’emails qu’ils acceptent de cet expéditeur.

   * Lorsque vous vérifiez la délivrabilité de votre email, vous devez vous concentrer sur quatre catégories principales : qualité des données, message et contenu, infrastructure d’envoi et réputation. Pour une plongée plus approfondie sur ce sujet, consultez [cette section](../../delivery/using/about-deliverability.md).

* Appliquez les recommandations détaillées [dans ce document](../../delivery/using/deliverability-key-points.md).

* Contactez votre représentant d&#39;Adobe pour obtenir de l&#39;aide.

### Gestion des quarantaines {#quarantine-management}

Vous avez tout intérêt à mettre en place et à conserver de bons processus de gestion des quarantaines.

Lorsque vous commencez à envoyer des emails sur une nouvelle plate-forme, vous pouvez utiliser une liste d’adresses qui ne sont pas entièrement qualifiées. Or l’envoi à des adresses non valides ou à des adresses pièges (boîtes mails créées dans le but de piéger les spammeurs) contribue à abaisser la réputation de la plate-forme. De bons processus de gestion des quarantaines aident à : maintenez la qualité de l&#39;adresse, évitez la liste bloquée des fournisseurs d&#39;accès internet et réduisez votre taux d&#39;erreur, en accélérant les diffusions et le débit.

**Conseils**

* If you have a list of invalid addresses, Adobe recommends importing it to the quarantine table, through **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Les destinataires dont l’adresse est en quarantaine sont par défaut exclus lors de l’analyse d’une diffusion : ils ne seront pas ciblés. Le taux d’erreur ayant une incidence importante sur la vitesse de diffusion, les envois sont ainsi accélérés. Une adresse email peut être mise en quarantaine par exemple lorsque la boîte de messagerie est pleine ou si l’adresse n’existe pas. [En savoir plus](#identifying-quarantined-addresses-for-a-delivery)

* Le mode de gestion des adresses en erreur par Adobe Campaign dépend du type d’erreur retourné. Voir à ce propos [cette section](../../delivery/using/understanding-quarantine-management.md).


* Certains fournisseurs d&#39;accès Internet considèrent automatiquement les emails comme du spam si le taux d&#39;adresses invalides est trop élevé. La quarantaine permet donc d’éviter d’être ajouté à une liste bloquée par ces fournisseurs.

* La gestion des Quarantaines aidera également à réduire les coûts d&#39;envoi de SMS en excluant les numéros de téléphone erronés des diffusions.

### Mécanisme de double opt-in {#double-opt-in}

Pour éviter d&#39;envoyer des messages à des adresses invalides, limiter les communications abusives et améliorer la réputation de l&#39;expéditeur, Adobe recommande de mettre en place un mécanisme de double opt-in pour une confirmation après inscription. Cela vous permet de vous assurer que le destinataire est bien à l&#39;origine de l&#39;abonnement.

Les détails de la mise en oeuvre de ce mécanisme sont décrits dans [cette section](../../web/using/use-cases--web-forms.md).

## Utilisez les modèles {#use-templates}

Les modèles de diffusion accroissent l&#39;efficacité en offrant des configurations prêtes à l&#39;emploi pour les types d&#39;activité les plus courants. Grâce aux modèles, les marketeurs peuvent déployer plus rapidement de nouvelles campagnes avec une personnalisation minimale.

Learn more about delivery templates in [this section](../../delivery/using/creating-a-delivery-template.md).

### Commencer avec les modèles de diffusion {#gs-templates}

A [delivery template](../../delivery/using/creating-a-delivery-template.md) enables you to define once a set of technical and functional properties that suit your needs and that can be reused for future deliveries. Vous pouvez ensuite gagner du temps et normaliser les diffusions si nécessaire.

Si vous gérez plusieurs marques dans Adobe Campaign, Adobe recommande de disposer d’un sous-domaine par marque. Une banque peut, par exemple, avoir plusieurs sous-domaines qui correspondent à chacune de ses agences régionales. Si une banque possède le domaine bluebank.com, ses sous-domaines peuvent être @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Disposer d’un modèle de diffusion par sous-domaine vous permet de toujours utiliser les paramètres préconfigurés adéquats pour chaque marque et d’éviter ainsi des erreurs tout en gagnant du temps.

**Conseil**:  Pour éviter les erreurs de configuration dans le Campaign Standard, nous vous recommandons de duplicata d’un modèle natif et de modifier ses propriétés plutôt que de créer un nouveau modèle.

**Configurer les adresses**

* L&#39;adresse de l&#39;expéditeur est obligatoire pour permettre l&#39;envoi d&#39;un email.

* Certains FAI vérifient la validité de l’adresse de l’expéditeur avant d’accepter les messages.

* Une adresse erronée peut causer un refus de la part du serveur receveur. Vous devez vous assurer qu’une adresse correcte est bien renseignée.

* L&#39;adresse doit identifier explicitement l&#39;expéditeur. Le domaine doit appartenir à l&#39;expéditeur et être enregistré auprès de lui.

* Adobe recommande de créer des comptes email qui correspondent aux adresses indiquées pour les envois et les réponses. Parlez-en avec votre administrateur du système de messagerie.

Pour configurer les adresses dans l’interface Campaign, procédez comme suit :

1. In the [delivery template](../../delivery/using/creating-a-delivery-template.md), click the **[!UICONTROL From]** link. Dans la fenêtre **[!UICONTROL Paramètres d&#39;en-tête email]**, renseignez les champs suivants :

   ![](assets/d_best_practices_email_header.png)

1. Dans le champ Adresse **[!UICONTROL de l’]** expéditeur, assurez-vous que le domaine d’adresse est identique au sous-domaine que vous avez délégué à l’Adobe. Vous pouvez modifier la partie qui précède le signe « @ », mais pas l’adresse du domaine.

1. Dans le champ **[!UICONTROL De]** , utilisez un nom facilement identifiable par les destinataires, tel que le nom de votre marque, pour augmenter le taux d’ouverture de vos diffusions. Pour améliorer davantage l&#39;expérience du destinataire, vous pouvez ajouter le nom d&#39;une personne, par exemple &quot;Emma from Megastore&quot;.

1. Dans les champs de texte **[!UICONTROL d&#39;adresse de]** réponse, l&#39;adresse de l&#39;expéditeur est utilisée par défaut pour les réponses. Toutefois, l’Adobe recommande d’utiliser une adresse réelle existante, telle que l’assistance clientèle de votre marque. Ainsi, si un destinataire envoie une réponse, l’assistance clientèle sera en mesure de la traiter.

**Configurer une population témoin**

Une fois que la diffusion est envoyée, vous pouvez comparer le comportement des destinataires exclus à celui des destinataires qui ont reçu la diffusion. Vous pouvez ensuite mesurer l&#39;efficacité de vos campagnes. En savoir plus sur les Populations témoins [cette section](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Pour configurer une Population témoin, cliquez sur le lien **[!UICONTROL À]** . In the **[!UICONTROL Select target]** window, select the **[!UICONTROL Control group]** tab. Vous pouvez extraire une partie de la cible, par exemple un échantillon aléatoire de 5 %.

![](assets/d_best_practices_control_group.png)

**Utiliser des typologies pour appliquer des filtres ou des règles de contrôle**

Une typologie contient les règles de vérification qui sont appliquées lors de la phase d&#39;analyse, avant tout envoi.

In the **[!UICONTROL Typology]** tab of the template&#39;s properties, change the default typology according to your needs.

Par exemple, pour mieux contrôler le trafic sortant, vous pouvez définir les adresses IP à utiliser en définissant une affinité par sous-domaine et en créant une typologie par affinité. Les affinités sont définies dans le fichier de configuration de l’instance. Contactez votre administrateur Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Concevez et personnalisez votre message {#design-and-personalize}

Lors de la conception du contenu de votre message, évitez les problèmes courants qui peuvent vous empêcher d’exécuter votre diffusion. La plupart du temps, les erreurs possibles sont liées à la [personnalisation](../../delivery/using/about-personalization.md), au [formatage](../../delivery/using/defining-the-email-content.md#message-content) et aux [images](../../delivery/using/defining-the-email-content.md#adding-images).

### Optimiser la personnalisation {#optimize-personalization}

Pour éviter des problèmes courants qui peuvent vous empêcher d’exécuter votre diffusion et d’améliorer l’expérience de vos destinataires, Adobe Campaign vous permet de personnaliser vos messages.

Vous pouvez utiliser les données destinataires stockées dans la base de données Adobe Campaign, ou collectées par le suivi, les landings page, les abonnements, etc.
Les principes de base de la personnalisation sont présentés dans [cette section](../../delivery/using/personalization-fields.md).

Vérifiez que le contenu de votre message est correctement conçu pour éviter les erreurs généralement liées à la personnalisation.

**Conseils**: Dans les champs de personnalisation provenant de fichiers externes fournis par des fournisseurs tiers, le contenu HTML externe peut être incorrect. Pour éviter ce problème, vérifiez la syntaxe, l’utilisation des balises, les caractères, etc. Par exemple, une balise de personnalisation Adobe Campaign présente toujours le formulaire suivant : &lt;%=table.field%>. Voir à ce propos [cette section](../../delivery/using/about-personalization.md).

L&#39;utilisation incorrecte des paramètres dans les blocs de personnalisation peut entraîner des problèmes. Par exemple, les variables en JavaScript doivent être utilisées comme suit :

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

For more on personalization blocks, refer to the [this section](../../delivery/using/personalization-blocks.md).

Vous pouvez préparer des données de personnalisation dans un processus afin d’améliorer l’analyse de préparation des diffusions. Ceci doit être utilisé spécialement si les données de personnalisation proviennent d&#39;une table externe via Federated Data Access (FDA). Cette option est décrite dans cette [section](../../delivery/using/personalization-fields.md#optimizing-personalization)

### Créer du contenu optimisé {#optimize-content}

Lorsque vous créez vos emails, tenez compte des bonnes pratiques générales présentées ci-dessous.

* Gardez le design de vos emails simple

* Gardez les utilisateurs d’appareils mobiles à l’esprit

* Évitez les emails basés entièrement sur des images

* Utilisez des polices sécurisées pour les emails

* Encodez les caractères spéciaux

**Objet** - Travaux sur la ligne [de](../../delivery/using/defining-the-email-content.md#message-content) sujet visant à améliorer les taux d&#39;ouverture :

* Évitez les objets trop longs. Utilisez 50 caractères au maximum

* Évitez de répéter des mots tels que « gratuit » ou « offre » qui peuvent être considérés comme des messages indésirables

* Évitez les majuscules et les caractères spéciaux tels que &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

**Page miroir** : incluez toujours un lien de page miroir. La partie supérieure de l’email constitue la position idéale. [En savoir plus](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**Lien** Désinscription - Le lien désinscription est essentiel. Il doit être visible et valide et le formulaire doit être fonctionnel. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Conseil**: Comme une erreur humaine est toujours possible, vérifiez que le lien d’exclusion fonctionne correctement avant chaque envoi. Par exemple, lors de l’envoi du BAT, assurez-vous que le lien est valide, que le formulaire est en ligne et que le champ Ne plus contacter ce destinataire est remplacé par Oui.

Découvrez comment insérer un lien d’exclusion [dans cette section](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

**Taille** du courrier électronique - Pour éviter des problèmes de performances ou de délivrabilité, la taille maximale recommandée d&#39;un courrier électronique est d&#39;environ **35 Ko**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Une fois le message généré, sa taille s&#39;affiche en haut à droite.

Pour maintenir la taille de l’email sous cette limite, tenez compte des possibilités suivantes :

* Suppression de styles redondants ou inutilisés

* Déplacer une partie du contenu du courrier électronique vers un landing page

* Minimiser votre code

Veillez à tester toutes les modifications avant l’envoi final

**Longueur des SMS**

Par défaut, le nombre de caractère d&#39;un SMS respecte la norme de téléphonie mobile GSM (Global System for Mobile Communications). Les SMS utilisant l&#39;encodage GSM sont limités à 160 caractères, ou 153 caractères par SMS pour les messages envoyés en plusieurs parties.

La translittération consiste à remplacer un caractère d&#39;un SMS par un autre lorsque ce caractère n&#39;est pas pris en charge par la norme GSM. Notez que l&#39;insertion de champs de personnalisation dans le contenu du SMS peut introduire des caractères non pris en charge par l&#39;encodage GSM. Vous pouvez autoriser la translittération des caractères en cochant la case correspondante dans l&#39;onglet des paramètres du canal SMPP du **[!UICONTROL Compte externe]** correspondant.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Conseils**:

* Pour conserver tous les caractères de vos SMS, afin de ne pas altérer les noms propres par exemple, n&#39;activez pas la translittération.

* En revanche, si vos SMS contiennent beaucoup de caractères qui ne sont pas pris en charge par la norme GSM, activez la translittération afin de limiter le coût de vos envois.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

### Travail sur le formatage {#formatting}

Pour éviter les erreurs de formatage courantes, tenez compte des éléments suivants :

* Correction de la mise en forme **des** dates : Adobe Campaign fournit des fonctions de formatage de date pour les modèles JavaScript et les feuilles de style XSL. [En savoir plus](../../delivery/using/formatting.md#date-display)

* Utilisation de caractères **** autorisés dans les courriers électroniques : la liste de caractères valides pour les adresses électroniques est définie dans l’option &quot;XtkEmail_Characters&quot;. Découvrez comment accéder aux options Campaign [dans cette section](../../installation/using/configuring-campaign-options.md). Pour gérer correctement les caractères spéciaux, Adobe Campaign doit être installé dans Unicode.

* Configuration de l’authentification **de** courriel : assurez-vous que les en-têtes de courrier électronique contiennent la signature DKIM. L’authentification DKIM (Domain Keys Identified Mail) permet au serveur de messagerie de réception de vérifier qu’un message a bien été envoyé par la personne ou l’entité revendiquant l’envoi et si le contenu du message a été modifié ou non entre le moment où il a été envoyé (et « signé » par DKIM) et celui où il a été reçu. Cette norme utilise généralement le domaine dans l’en-tête De ou Expéditeur. Voir à ce propos [cette section](../../delivery/using/technical-recommendations.md#dkim).

* **Le responsive design des emails permet de s’assurer que le rendu d’un email est optimal sur l’appareil sur lequel il est ouvert.**

   * Utilisez du code HTML en responsive design plutôt que du code HTML web.

   * Utilisez le mode Aperçu et envoyez des BAT pour tester le rendu sur le plus grand nombre d’appareils possible.

   * The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. En savoir plus [dans cet article](https://theblog.adobe.com/responsive-email-design-101/).



### Gestion des images {#manage-images}

Suivez les instructions ci-dessous pour l’utilisation des images.

* **Empêcher le blocage** des images : certains clients de messagerie bloquent les images par défaut et certains utilisateurs modifient leurs paramètres pour bloquer les images à des fins d’enregistrement sur l’utilisation des données. Par conséquent, si les images ne sont pas téléchargées, le message entier peut être perdu. Pour éviter cela :

   * Équilibrez le contenu entre image et texte. Évitez les emails basés entièrement sur des images.

   * Si le texte doit être contenu dans une image, utilisez du texte de titre et du texte alternatif pour vous assurer que votre message passe bien. Mettez en forme votre texte de titre et alternatif pour améliorer son aspect.

   * Évitez d’utiliser des images de fond, car elles ne sont pas prises en charge par certains clients de messagerie.

* **Rendre les images réactives** : essayez de rendre les images réactives et redimensionnables. Notez que ceci peut avoir un impact sur les coûts, car la création prend plus de temps.

* **Utiliser des références** d&#39;image absolues : pour être accessibles de l&#39;extérieur, les images utilisées dans les courriels et les ressources publiques liés aux campagnes doivent être présentes sur un serveur accessible en externe.

   * Vous pouvez vérifier si la configuration de l’instance permet la gestion des ressources publiques. [En savoir plus](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon. [En savoir plus](../../delivery/using/defining-the-email-content.md#adding-images)

   * Si les images ne sont pas affichées, vérifiez qu&#39;elles sont disponibles sur le serveur. Pour ce faire, cliquez sur l&#39;onglet Source de votre diffusion. Recherchez vos images, copiez l&#39;URL de chaque image et collez-la dans un navigateur web. Si les images ne sont toujours pas affichées, contactez votre administrateur informatique ou le fournisseur tiers du contenu de votre diffusion.

### Prévisualisez votre message {#preview-msg}

Adobe recommande de prévisualiser votre message afin de vérifier sa personnalisation et l’affichage de la diffusion par vos destinataires.

* Dans le volet diffusion, le sous-onglet **[!UICONTROL Prévisualisation]** vous permet de vue du rendu de chaque contenu pour un destinataire. Les champs de personnalisation et les éléments conditionnels du contenu sont remplacés par les informations correspondantes pour le profil sélectionné. [En savoir plus](../../delivery/using/defining-the-email-content.md#message-content)

* Une vérification anti-spam est automatiquement effectuée à chaque prévisualisation. Dans le sous-onglet **[!UICONTROL Prévisualisation]** , vérifiez le score de spam [SpamAssassin](../../delivery/using/spamassassin.md) .  Cliquez sur **[!UICONTROL Plus...]** pour en savoir plus sur l&#39;avertissement.  Avant de procéder, assurez-vous que SpamAssassin est correctement installé et configuré sur le serveur d&#39;applications Adobe Campaign. [En savoir plus](../../installation/using/configuring-spamassassin.md)

## Définir la cible appropriée {#define-the-right-target}

La population ciblée est essentielle : créez soigneusement vos listes, testez vos emails sur les clients de messagerie et les appareils mobiles les plus utilisés et vérifiez que vos listes email sont à jour (sans adresses inconnues ou obsolètes). Vous pouvez également envoyer des bons à tirer permettant de configurer un cycle de validation complet.

En savoir plus sur les populations de cibles [dans cette section](../../delivery/using/steps-defining-the-target-population.md)

### Cible de l&#39;audience appropriée {#target-the-right-audience}

Lorsque votre contenu est prêt, vous devez soigneusement définir qui recevra votre message.

Pour réussir votre diffusion, vous souhaitez envoyer le contenu personnalisé le plus pertinent aux bons destinataires. Adobe Campaign vous permet de créer la cible la plus précise qui soit : vous pouvez sélectionner les destinataires selon leur âge, leur emplacement géographique, leurs achats ou selon qu’ils ont cliqué ou non sur un lien dans une diffusion précédente, par exemple. Avec Adobe Campaign, vous pouvez également définir des profils de test, des Populations témoins et des adresses de contrôle pour vous assurer que votre cible est correcte.

### Mappings de ciblage {#target-mappings}

En Campaign Classic, par défaut, modèle de diffusion cible **Destinataires**. Adobe Campaign propose d’autres mappings de ciblage pour vos diffusions, que vous pouvez modifier selon vos besoins.

Vous pouvez, par exemple, diffuser des données aux visiteurs dont les profils ont été collectés via les réseaux sociaux ou aux visiteurs abonnés à un service d&#39;information.

Ces mappages sont présentés [dans cette section](../../delivery/using/selecting-a-target-mapping.md).

Vous pouvez également créer et utiliser un mapping de ciblage personnalisé. Voir à ce propos [cette section](../../configuration/using/target-mapping.md).

### Destinataires externes {#external-recipients}

Vous pouvez distribuer aux destinataires qui sont stockés dans un fichier externe plutôt que enregistrés dans la base de données. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### Envoyer à vos abonnés {#send-to-subscribers}

Pour envoyer des messages aux abonnés d&#39;un bulletin d&#39;information, vous pouvez directement les cible au service d&#39;information correspondant. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### Testez les destinataires et les adresses de contrôle {#test-recipients-seed-addresses}

Pour tester votre diffusion, utilisez des bons à tirer avant l&#39;envoi à la cible principale.

Veillez à sélectionner les destinataires BAT appropriés, car ils valident le formulaire et le contenu du message. Les étapes de définition des destinataires BAT sont présentées [dans cette section](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis afin de tester une diffusion avant l’envoi à la cible principale. Ils sont présentés [dans cette section](../../delivery/using/about-seed-addresses.md).

### Dédupliquez les adresses {#deduplicate-addresses}

Il est important d&#39;éviter d&#39;avoir des adresses email en double, car cela peut avoir un impact sur votre cible.

* Un même message peut être envoyé plusieurs fois lorsqu&#39;une une cible est partagée.

* Si une personne se désinscrit suite à la réception d&#39;un message, son profil en double recevra toujours les prochains messages.

Pour garantir votre réputation et assurer une bonne gestion des quarantaines, dédupliquez les adresses.

En savoir plus [sur ce cas](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)d&#39;utilisation.


### Adresse électronique d’index {#index-addresses}

Pour optimiser les performances des requêtes SQL utilisées dans l&#39;application, un index peut être déclaré à partir de l&#39;élément principal du schéma de données.

Les étapes permettant d’ajouter un index à l’adresse électronique sont présentées [dans cette section](../../configuration/using/database-mapping.md#indexed-fields).

## Effectuer toutes les vérifications avant d’envoyer {#perform-all-checks}

Une fois que votre message est prêt, vérifiez que le contenu s&#39;affiche correctement sur tous les appareils et qu&#39;il ne contient aucune erreur, comme des liens rompus ou une personnalisation incorrecte.

Avant d’envoyer votre message, vérifiez également que les paramètres et la configuration sont cohérents par rapport à la diffusion.

### La validation est essentielle {#validation-is-key}

Avant d&#39;envoyer une diffusion, vous devez vous assurer que vos destinataires recevront le message que vous souhaitez réellement leur envoyer. Pour cela, vous devez valider le contenu du message et les paramètres de diffusion.

Cette étape vous permet de détecter les éventuelles erreurs et de les corriger avant l’envoi à la cible principale.

Les étapes de validation d&#39;une diffusion sont présentées [dans cette section](../../delivery/using/steps-validating-the-delivery.md).

### Inbox rendering {#inbox-and-email-rendering}

L&#39;inbox rendering vous permet de prévisualiser vos messages sur les principaux clients de messagerie, de surveiller le contenu et votre réputation, et de découvrir comment les destinataires lisent vos messages.

**Conseils**:

* Vous pouvez visualiser l&#39;affichage du message envoyé dans les différents contextes de réception : webmail, service de messagerie, mobile, etc.

* Les fonctionnalités d&#39;inbox rendering sont essentielles pour déterminer si vos campagnes email réussissent à passer les filtres des principaux FAI et des services webmail. Les outils de ce type envoient une copie de vérification d&#39;un email à un réseau de boîtes de réception de test pour que vous puissiez voir comment le message s&#39;affichera à travers ces différents services. Ils peuvent également inclure des rapports et des options de correction de code qui vous permettent d&#39;identifier rapidement les problèmes et de les corriger afin d&#39;améliorer la délivrabilité.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

### Messages de BAT {#proof-messages}

L&#39;envoi de BAT permet de vérifier le lien de désinscription (opt-out), la page miroir et d&#39;autres liens, de valider le message, de vérifier le bon affichage des images, de détecter les erreurs possibles, etc. Vous souhaitez peut-être également vérifier votre conception et le rendu sur différents appareils.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Configurer des diffusions avec test A/B {#a-b-testing-deliveries}

Si vous disposez de plusieurs contenus pour une diffusion email, vous pouvez utiliser des tests A/B pour déterminer quelle version aura le plus d&#39;impact sur la population ciblée.

**Conseils**:

* Envoyez les différentes versions à une partie de vos destinataires

* Choisissez la version qui a eu le plus de succès et envoyez-la au reste de vos destinataires

Learn more [in this section](../../workflow/using/a-b-testing.md).

### Vérifiez que votre message est bien délivré {#make-sure-your-message-is-delivered}

En dernier lieu, tirez parti des fonctionnalités d’Adobe Campaign Classic et augmentez les chances que votre message soit délivré aux bons destinataires.

**Exécutez un processus** de validation : vous pouvez définir un processus de validation complet, impliquant des opérateurs et des groupes Adobe Campaign, pour valider la cible et le contenu du message. Cela permettra d&#39;assurer un suivi et un contrôle complets des divers processus de la campagne : ciblage, contenu, budget, extraction et envoi d’un BAT. En fonction de leurs permissions, les utilisateurs seront avertis, ils recevront les BAT et ils pourront valider ou refuser le message. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Utiliser le vagues** : vous pouvez augmenter progressivement le volume envoyé à l&#39;aide de vagues. Vous éviterez ainsi que vos messages ne soient signalés comme étant des messages indésirables ou que vous souhaitiez limiter le nombre de messages par jour. Grâce aux vagues, vous pouvez répartir les envois en plusieurs lots au lieu d’envoyer de gros volumes de messages en même temps. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Prioriser les messages** : vous pouvez définir l&#39;ordre d&#39;envoi de vos diffusions en indiquant le niveau de priorité. Pour ce faire :

1. Editez les propriétés de la diffusion et sélectionnez l&#39;onglet **[!UICONTROL Diffusion]**.

1. Définissez le niveau de priorité de la diffusion sur une échelle allant de **[!UICONTROL Très basse]** à **[!UICONTROL Très haute]**.

>[!NOTE]
>
>Il n&#39;est pas possible de définir l&#39;ordre d&#39;envoi des messages à partir d&#39;une diffusion.

**Configuration des Affinités** IP : pour mieux contrôler le trafic SMTP sortant, vous pouvez gérer les affinités en définissant les adresses IP spécifiques qui peuvent être utilisées pour chaque affinité. Ainsi, il est possible de limiter l’envoi d’emails pour des diffusions spécifiques, vers certaines machines ou adresses de sortie. Vous pouvez, par exemple, utiliser une affinité par pays ou sous-domaine. Vous pouvez ensuite créer une typologie par pays et associer chaque affinité à la typologie correspondante.

Vous pouvez ainsi :

* Définissez les affinités IP dans le fichier de configuration serverConf.xml. [En savoir plus](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Pour chaque élément IPAfinity, déclarez les adresses IP qui peuvent être utilisées. [En savoir plus](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In the [typology](../../campaign/using/about-campaign-typologies.md) of your choice, use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the delivery server (MTA) which manages the said affinity. [En savoir plus](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Une fois que l&#39;email a été envoyé, contrôlez l&#39;en-tête pour vérifier l&#39;adresse IP à partir de laquelle la diffusion a été envoyée. L&#39;administrateur de messagerie peut vous aider à obtenir les informations d&#39;en-tête.

>[!NOTE]
>
>La plupart de ces étapes ne peuvent être effectuées que par un utilisateur expert.

**Utiliser des typologies** : vous pouvez utiliser des règles de typologie pour exclure une partie de la cible en fonction de critères spécifiques. Elles permettent de s’assurer que les messages envoyés répondent le mieux possible aux attentes ou aux besoins du client, dans le respect des stratégies de communication de l’entreprise. Vous pouvez, par exemple, filtrer les destinataires mineurs du public cible de votre newsletter. En savoir plus [dans cet exemple](../../campaign/using/filtering-rules.md).

**Évitez les pièces jointes** - Les pièces jointes restent l&#39;un des vecteurs les plus courants de prolifération des logiciels malveillants, surtout lorsqu&#39;elles sont envoyées en vrac. Incluez un lien sécurisé vers le document au lieu de le joindre au message. Ceci garantit une couche supplémentaire de sécurité afin d’éviter une redistribution involontaire, et réduit considérablement les risques que le message soit rejeté sur les passerelles de messagerie entrantes pour des raisons de taille ou de sécurité du message.

## Trackez et suivez vos diffusions {#track-and-monitor}

Vous avez cliqué sur le bouton Envoyer ? Voyons maintenant ce qui se passe. Une fois la diffusion envoyée, Adobe Campaign vous permet de conserver une trace des messages envoyés et de découvrir la réaction des destinataires face à votre diffusion. Cela vous permettra d&#39;améliorer l&#39;envoi futur et d&#39;optimiser vos prochaines campagnes.

### Surveillance des diffusions {#monitoring-deliveries}

Pour contrôler vos campagnes, vous devez vérifier que le message a bien été délivré à vos destinataires.

Depuis le tableau de bord de diffusion Campaign, vous pouvez vérifier les messages traités et les journaux d&#39;audit des diffusions.
Vous pouvez également contrôler le statut des messages dans les logs de diffusion. [En savoir plus](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Que faire si les diffusions ne sont pas envoyées et restent dans un état **En attente** ?

* Le processus d&#39;exécution attend la disponibilité de certaines ressources. Le MTA n&#39;a peut-être pas été démarré.
Vérifiez que vos mta@instance de données sont lancés sur vos serveurs MTA et début le module MTA si nécessaire. [En savoir plus](../../production/using/administration.md).

* La diffusion peut utiliser une affinité qui n&#39;a pas été configurée sur l&#39;instance d&#39;envoi.
Conseil : Vérifiez la configuration relative à la gestion du trafic (affinité IP). Voir à ce propos la section Contrôle du trafic SMTP sortant.

>[!NOTE]
>
>Ces étapes ne peuvent être effectuées que par un utilisateur expert.

### Effectuer un tracking {#tracking-deliveries}

Pour mieux connaître le comportement de vos destinataires, vous pouvez suivre leur réaction à une diffusion : réception, ouverture, clics sur des liens, désinscriptions, etc. En Campaign Classic, ces informations s’affichent dans l’onglet Suivi des destinataires ciblés par la diffusion et dans l’onglet Suivi de la diffusion. En Campaign Standard, il s’affiche dans l’onglet Logs de tracking de la diffusion.

**Conseil**: Le suivi des messages est activé par défaut. Pour configurer les URL, sélectionnez l’option Afficher les URL dans la section inférieure de l’assistant de diffusion. Pour chaque URL du message, vous pouvez choisir d’activer ou non le suivi.

Pour plus d&#39;informations, reportez-vous à la section [Configuration du suivi](../../delivery/using/how-to-configure-tracked-links.md) et à la description des indicateurs [de](../../reporting/using/delivery-reports.md#tracking-indicators) suivi.

### Performances des diffusions {#delivery-performances}

Pour mesurer la vitesse à laquelle les messages sont diffusés, vous pouvez contrôler le débit de diffusion. Les critères constituent le nombre de messages diffusés par heure et la taille des messages, en bits par seconde. Voir à ce propos la section [Débit de diffusion](../../reporting/using/global-reports.md#delivery-throughput).

**Conseils**:

* Ne gardez pas les diffusions en échec sur l&#39;instance, car cela conserve les tables temporaires et a un impact sur les performances.

* Supprimez les diffusions qui ne sont plus nécessaires et les destinataires inactifs de la base pour conserver la qualité des adresses.

* N&#39;essayez pas de planifier des diffusions volumineuses ensemble. 5 à 10 minutes sont nécessaires pour répartir la charge uniformément sur le système.

## Dépannage de la Diffusion {#delivery-troubleshooting}

Des actions spécifiques peuvent être exécutées en cas de problème avec des diffusions :

* [Problèmes de délivrabilité](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problèmes liés à l’affichage des images](../../production/using/image-display-issues.md)

* [Problèmes de performances des diffusions](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problèmes](../../production/using/temporary-files.md) de fichiers temporaires - clients *sur site uniquement*

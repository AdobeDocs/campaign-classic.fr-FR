---
title: Créer du contenu personnalisé
seo-title: Créer du contenu personnalisé
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
source-git-commit: c804745ae58a9bded885ac5aef32f019f43e82be
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 55%

---


# Créer du contenu personnalisé {#build-personalized-content}

Lors de la conception du contenu de votre message, évitez les problèmes courants qui peuvent vous empêcher d’exécuter votre diffusion. La plupart du temps, les erreurs possibles sont liées à la [personnalisation](../../delivery/using/about-personalization.md), au [formatage](../../delivery/using/defining-the-email-content.md#message-content) et aux [images](../../delivery/using/defining-the-email-content.md#adding-images).

## Optimiser la personnalisation {#optimize-personalization}

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

## Créer du contenu optimisé {#optimize-content}

Lorsque vous créez vos emails, tenez compte des bonnes pratiques générales présentées ci-dessous.

* Gardez le design de vos emails simple

* Gardez les utilisateurs d’appareils mobiles à l’esprit

* Évitez les emails basés entièrement sur des images

* Utilisez des polices sécurisées pour les emails

* Encodez les caractères spéciaux

### Objet

Work on the [subject line](../../delivery/using/defining-the-email-content.md#message-content) to improve open rates:

* Évitez les objets trop longs. Utilisez 50 caractères au maximum

* Évitez de répéter des mots tels que « gratuit » ou « offre » qui peuvent être considérés comme des messages indésirables

* Évitez les majuscules et les caractères spéciaux tels que &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Page miroir

Incluez toujours un lien de page miroir. La partie supérieure de l’email constitue la position idéale. [En savoir plus](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Lien de désabonnement

The unsubscription link is essential. It must be visible and valid, and the form must be functional. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Conseil**: Comme une erreur humaine est toujours possible, vérifiez que le lien d’exclusion fonctionne correctement avant chaque envoi. Par exemple, lors de l’envoi du BAT, assurez-vous que le lien est valide, que le formulaire est en ligne et que le champ Ne plus contacter ce destinataire est remplacé par Oui.

Découvrez comment insérer un lien d’exclusion [dans cette section](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

### Taille des emails

Pour éviter des problèmes de performances ou de délivrabilité, la taille maximale recommandée d’un courrier électronique est d’environ **35 Ko**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Une fois le message généré, sa taille s&#39;affiche en haut à droite.

Pour maintenir la taille de l’email sous cette limite, tenez compte des possibilités suivantes :

* Suppression de styles redondants ou inutilisés

* Déplacer une partie du contenu du courrier électronique vers un landing page

* Minimiser votre code

Veillez à tester toutes les modifications avant l’envoi final

### Longueur des SMS

Par défaut, le nombre de caractère d&#39;un SMS respecte la norme de téléphonie mobile GSM (Global System for Mobile Communications). Les SMS utilisant l&#39;encodage GSM sont limités à 160 caractères, ou 153 caractères par SMS pour les messages envoyés en plusieurs parties.

La translittération consiste à remplacer un caractère d&#39;un SMS par un autre lorsque ce caractère n&#39;est pas pris en charge par la norme GSM. Notez que l&#39;insertion de champs de personnalisation dans le contenu du SMS peut introduire des caractères non pris en charge par l&#39;encodage GSM. Vous pouvez autoriser la translittération des caractères en cochant la case correspondante dans l&#39;onglet des paramètres du canal SMPP du **[!UICONTROL Compte externe]** correspondant.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Conseils**:

* Pour conserver tous les caractères de vos SMS, afin de ne pas altérer les noms propres par exemple, n&#39;activez pas la translittération.

* En revanche, si vos SMS contiennent beaucoup de caractères qui ne sont pas pris en charge par la norme GSM, activez la translittération afin de limiter le coût de vos envois.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

## Travail sur le formatage {#formatting}

Pour éviter les erreurs de formatage courantes, tenez compte des éléments suivants :

* Correction de la mise en forme **des** dates : adobe campaign fournit des fonctions de formatage de date pour les modèles JavaScript et les feuilles de style XSL. [En savoir plus](../../delivery/using/formatting.md#date-display)

* Utilisation de caractères **** autorisés dans les courriers électroniques : la liste de caractères valides pour les adresses électroniques est définie dans l’option &quot;XtkEmail_Characters&quot;. Découvrez comment accéder aux options Campaign [dans cette section](../../installation/using/configuring-campaign-options.md). Pour gérer correctement les caractères spéciaux, Adobe Campaign doit être installé dans Unicode.

* Configuration de l’authentification **de** courriel : assurez-vous que les en-têtes de courrier électronique contiennent la signature DKIM. L’authentification DKIM (Domain Keys Identified Mail) permet au serveur de messagerie de réception de vérifier qu’un message a bien été envoyé par la personne ou l’entité revendiquant l’envoi et si le contenu du message a été modifié ou non entre le moment où il a été envoyé (et « signé » par DKIM) et celui où il a été reçu. Cette norme utilise généralement le domaine dans l’en-tête De ou Expéditeur. Voir à ce propos [cette section](../../delivery/using/technical-recommendations.md#dkim).

### Conception réactive de courrier électronique

Le responsive design des emails permet de s’assurer que le rendu d’un est optimal sur l’appareil sur lequel il est ouvert.

* Utilisez du code HTML en responsive design plutôt que du code HTML web

* Utilisez le mode Aperçu et envoyez des BAT pour tester le rendu sur le plus grand nombre d’appareils possible

* The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. En savoir plus [dans cet article](https://theblog.adobe.com/responsive-email-design-101/)

## Gestion des images {#manage-images}

Suivez les instructions ci-dessous pour l’utilisation des images.

### Empêcher le blocage des images

Certains clients de messagerie bloquent les images par défaut, et certains utilisateurs modifient leurs paramètres pour bloquer les images afin de réduire l’utilisation des données. Par conséquent, si les images ne sont pas téléchargées, le message entier peut être perdu. Pour éviter cela :

* Équilibrez le contenu entre image et texte. Évitez les emails basés entièrement sur des images.

* Si le texte doit être contenu dans une image, utilisez du texte de titre et du texte alternatif pour vous assurer que votre message passe bien. Mettez en forme votre texte de titre et alternatif pour améliorer son aspect.

* Évitez d’utiliser des images de fond, car elles ne sont pas prises en charge par certains clients de messagerie.

### Rendre les images réactives

Essayez de rendre les images réactives et redimensionnables. Notez que ceci peut avoir un impact sur les coûts, car la création prend plus de temps.

### Utiliser des références d’image absolues

Pour être accessibles de l’extérieur, les images utilisées dans les courriels et les ressources publiques liés aux campagnes doivent être présentes sur un serveur accessible en externe.

* Vous pouvez vérifier si la configuration de l’instance permet la gestion des ressources publiques. [En savoir plus](../../installation/using/deploying-an-instance.md#managing-public-resources)

* From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon. [En savoir plus](../../delivery/using/defining-the-email-content.md#adding-images)

* Si les images ne sont pas affichées, vérifiez qu&#39;elles sont disponibles sur le serveur. Pour ce faire, cliquez sur l&#39;onglet Source de votre diffusion. Recherchez vos images, copiez l&#39;URL de chaque image et collez-la dans un navigateur web. Si les images ne sont toujours pas affichées, contactez votre administrateur informatique ou le fournisseur tiers du contenu de votre diffusion.

## Prévisualisez votre message {#preview-msg}

Adobe recommande de prévisualiser votre message afin de vérifier sa personnalisation et l’affichage de la diffusion par vos destinataires.

* Dans le volet diffusion, le sous-onglet **[!UICONTROL Prévisualisation]** vous permet de vue du rendu de chaque contenu pour un destinataire. Les champs de personnalisation et les éléments conditionnels du contenu sont remplacés par les informations correspondantes pour le profil sélectionné. [En savoir plus](../../delivery/using/defining-the-email-content.md#message-content)

* Une vérification anti-spam est automatiquement effectuée à chaque prévisualisation. Dans le sous-onglet **[!UICONTROL Prévisualisation]** , vérifiez le score de spam [SpamAssassin](../../delivery/using/spamassassin.md) .  Cliquez sur **[!UICONTROL Plus...]** pour en savoir plus sur l&#39;avertissement.  Avant de procéder, assurez-vous que SpamAssassin est correctement installé et configuré sur le serveur d&#39;applications Adobe Campaign. [En savoir plus](../../installation/using/configuring-spamassassin.md)

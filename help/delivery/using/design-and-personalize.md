---
product: campaign
title: Créer du contenu personnalisé
description: Découvrez comment créer du contenu personnalisé dans les diffusions Adobe Campaign
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Email Design, Personalization
role: User
hide: true
hidefromtoc: true
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 97%

---

# Créer du contenu personnalisé {#build-personalized-content}

Lors de la conception du contenu de votre message, évitez les problèmes courants qui peuvent vous empêcher d’exécuter votre diffusion. La plupart du temps, les erreurs possibles sont liées à la [personnalisation](about-personalization.md), au [formatage](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr#message-content){target="_blank"} et aux [images](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr#adding-images){target="_blank"}.

## Optimiser la personnalisation {#optimize-personalization}

Pour éviter des problèmes courants qui peuvent vous empêcher d&#39;exécuter votre diffusion et d&#39;améliorer l&#39;expérience de vos destinataires, Adobe Campaign vous permet de personnaliser vos messages.

Vous pouvez utiliser les données des destinataires stockées dans la base de données Adobe Campaign ou collectées par le biais du tracking, des landing pages, des inscriptions, etc.
Les principes de base de la personnalisation sont présentés dans [cette section](personalization-fields.md).

Vérifiez que le contenu de votre message est correctement conçu pour éviter les erreurs généralement liées à la personnalisation.

**Conseils** : dans les champs de personnalisation provenant de fichiers externes fournis par des prestataires tiers, le contenu HTML externe peut être incorrect. Pour éviter ce problème, vérifiez la syntaxe, l’utilisation des balises, les caractères, etc. Par exemple, une balise de personnalisation Adobe Campaign est toujours de la forme : &lt;%=table.champ%>. Voir à ce propos [cette section](about-personalization.md).

L&#39;utilisation incorrecte des paramètres dans les blocs de personnalisation peut entraîner des problèmes. Par exemple, les variables en JavaScript doivent être utilisées comme suit :

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Pour plus d&#39;informations sur les blocs de personnalisation, consultez [cette section](personalization-blocks.md).

Vous pouvez préparer les données de personnalisation dans un workflow afin d’améliorer l’analyse de préparation des diffusions. Vous devez effectuer cette opération tout particulièrement si les données de personnalisation proviennent d&#39;une table externe via Federated Data Access (FDA). Cette option est décrite dans [cette section](personalization-fields.md#optimizing-personalization)

## Créer du contenu optimisé {#optimize-content}

Lorsque vous créez vos e-mails, tenez compte des bonnes pratiques générales présentées ci-dessous.

* Gardez le design de vos e-mails simple

* Gardez les utilisateurs d&#39;appareils mobiles à l&#39;esprit

* Évitez les e-mails basés entièrement sur des images

* Utilisez des polices sécurisées pour les e-mails

* Encodez les caractères spéciaux

### Objet

Découvrez l’objet de la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr#sender){target="_blank"} pour améliorer les taux d’ouverture :

* Évitez les objets trop longs. Utilisez 50 caractères au maximum

* Évitez de répéter des mots tels que &quot;gratuit&quot; ou &quot;offre&quot; qui peuvent être considérés comme des messages indésirables

* Évitez les majuscules et les caractères spéciaux tels que &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Page miroir

Incluez toujours un lien de page miroir. La partie supérieure de l&#39;e-mail constitue la position idéale. [En savoir plus](sending-messages.md#generating-the-mirror-page)

### Lien de désabonnement

Le lien de désabonnement est indispensable. Il doit être visible, valide et le formulaire fonctionnel. Par défaut, une [règle de typologie](steps-validating-the-delivery.md#validation-process-with-typologies) vérifie au moment de l’analyse du message qu’un lien d’exclusion est bien présent dans le contenu d’une diffusion et génère un avertissement en cas d’absence.

**Conseil** : comme une erreur humaine est toujours possible, vérifiez du début à la fin le bon fonctionnement du lien de désabonnement avant chaque envoi. Par exemple, lors de l&#39;envoi du BAT, vérifiez que le lien est valide, que le formulaire est en ligne et que la valeur du champ Ne plus contacter cette personne est changée en Oui.

Découvrez comment insérer un lien d&#39;opt-out [dans cette section](personalization-blocks.md#personalization-blocks-example).

### Taille des emails

Pour éviter des problèmes de performances ou de délivrabilité, la taille maximale recommandée d’un email est d’environ **35 Ko**. Pour vérifier la taille du message, accédez à l’onglet **[!UICONTROL Aperçu]** et choisissez un profil de test. Une fois le message généré, sa taille s&#39;affiche en haut à droite.

Pour maintenir la taille de l’email sous cette limite, tenez compte des possibilités suivantes :

* Supprimer les styles redondants ou inutilisés

* Déplacer une partie du contenu de l’email vers une landing page

* Minimiser votre code

Veillez à tester toutes les modifications avant l’envoi final

### Longueur des SMS

Par défaut, le nombre de caractère d&#39;un SMS respecte la norme de téléphonie mobile GSM (Global System for Mobile Communications). Les SMS utilisant l&#39;encodage GSM sont limités à 160 caractères, ou 153 caractères par SMS pour les messages envoyés en plusieurs parties.

La translittération consiste à remplacer un caractère d’un SMS par un autre lorsque ce caractère n’est pas pris en charge par la norme GSM. Notez que l’insertion de champs de personnalisation dans le contenu de votre SMS peut introduire des caractères qui ne sont pas pris en charge par l’encodage GSM. Vous pouvez autoriser la translittération des caractères en cochant la case correspondante dans l’onglet Paramètres du canal SMPP du **[!UICONTROL compte externe]** correspondant.
En savoir plus dans [cette section](sms-set-up.md#creating-an-smpp-external-account).

**Conseils** :

* Pour conserver tous les caractères de vos SMS, afin de ne pas altérer les noms propres par exemple, n’activez pas la translittération.

* En revanche, si vos SMS contiennent beaucoup de caractères qui ne sont pas pris en charge par la norme GSM, activez la translittération afin de limiter le coût de vos envois.

En savoir plus dans [cette section](sms-set-up.md#about-character-transliteration).

## Travail sur le formatage {#formatting}

Pour éviter les erreurs de formatage courantes, tenez compte des éléments suivants :

* Correction du **formatage de la date** : Adobe Campaign fournit des fonctions de formatage de date pour les modèles JavaScript et les feuilles de style XSL. [En savoir plus](formatting.md#date-display)

* Utilisation de **carcatères autorisés** dans les emails : la liste des caractères valides pour les adresses email est définie dans l’option « XtkEmail_Characters ». Découvrez comment accéder aux options Campaign [dans cette section](../../installation/using/configuring-campaign-options.md). Pour gérer correctement les caractères spéciaux, Adobe Campaign doit être installé en Unicode.

* Configuration de l’**authentification des emails** : assurez-vous que les en-têtes d’email contiennent la signature DKIM. L’authentification DKIM (Domain Keys Identified Mail) permet au serveur de messagerie de réception de vérifier qu’un message a bien été envoyé par la personne ou l’entité revendiquant l’envoi et si le contenu du message a été modifié ou non entre le moment où il a été envoyé (et « signé » par DKIM) et celui où il a été reçu. Cette norme utilise généralement le domaine dans l’en-tête « De » ou « Expéditeur ». Pour plus d’informations à ce sujet, consultez le [Guide des bonnes pratiques relatives à la délivrabilité d’Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=fr#authentication).

### E-mail en responsive design

Le responsive design des e-mails permet de s&#39;assurer que le rendu d&#39;un est optimal sur l&#39;appareil sur lequel il est ouvert.

* Utilisez du code HTML en responsive design plutôt que du code HTML web

* Utilisez le mode Aperçu et envoyez des BAT pour tester le rendu sur le plus grand nombre d&#39;appareils possible

* Le module Digital Content Editor (DCE) Adobe Campaign Classic contient quelques modèles pour appareils mobiles en responsive design accessibles via **[!UICONTROL Ressources]** > **[!UICONTROL Modèles]** > **[!UICONTROL Modèles de contenu]**.

## Gestion des images {#manage-images}

Suivez les instructions ci-dessous pour l&#39;utilisation des images.

### Empêcher le blocage des images

Certains clients de messagerie bloquent les images par défaut, et certains utilisateurs modifient leurs paramètres pour bloquer les images afin de réduire l&#39;utilisation des données. Dans ce cas, si les images ne sont pas téléchargées, il est possible que l&#39;ensemble du message soit perdu. Pour éviter cela :

* Équilibrez le contenu entre image et texte. Évitez les e-mails basés entièrement sur des images.

* Si le texte doit être contenu dans une image, utilisez du texte de titre et du texte alternatif pour vous assurer que votre message passe bien. Mettez en forme votre texte de titre et alternatif pour améliorer son aspect.

* Évitez d’utiliser des images d’arrière-plan, car elles ne sont pas prises en charge par certains clients de messagerie.

### Rendre les images réactives

Essayez de rendre les images réactives et redimensionnables. Notez que cela peut avoir un impact sur les coûts, car la création prend plus de temps.

### Utiliser des références absolues pour l&#39;accès à l&#39;image

Pour être accessibles depuis l&#39;extérieur, les images utilisées dans les emails et les ressources publiques associées aux opérations doivent être présentes sur un serveur accessible de l&#39;extérieur.

* Vous pouvez vérifier si la configuration de l’instance permet la gestion des ressources publiques. [En savoir plus](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Depuis l’assistant de diffusion, vous pouvez importer une page HTML contenant des images ou insérer directement des images à l’aide de l’éditeur HTML via l’icône **[!UICONTROL Image]**  Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr#adding-images){target="_blank"}.

* Si les images ne sont pas affichées, vérifiez qu&#39;elles sont disponibles sur le serveur. Pour ce faire, cliquez sur l&#39;onglet Source de votre diffusion. Recherchez vos images, copiez l&#39;URL de chaque image et collez-la dans un navigateur web. Si les images ne sont toujours pas affichées, contactez votre administrateur informatique ou le fournisseur tiers du contenu de votre diffusion.

## Prévisualisez votre message {#preview-msg}

Adobe recommande de prévisualiser votre message afin de vérifier sa personnalisation et l&#39;affichage de la diffusion par vos destinataires.

* Dans l’assistant de diffusion, le sous-onglet **[!UICONTROL Prévisualisation]** vous permet de visualiser le rendu de chaque contenu pour une personne destinataire. Les champs de personnalisation et les éléments conditionnels du contenu sont remplacés par les informations correspondantes pour le profil sélectionné. Pour en savoir plus, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=fr#message-content){target="_blank"}.

* Une vérification anti-spam est automatiquement effectuée à chaque prévisualisation. Dans le sous-onglet **[!UICONTROL Aperçu]**, vérifiez le score de spam [SpamAssassin](spamassassin.md).  Cliquez sur **[!UICONTROL Autres choix...]** pour en savoir plus sur l’avertissement.  Avant de procéder, assurez-vous que SpamAssassin est correctement installé et configuré sur le serveur applicatif Adobe Campaign. [En savoir plus](../../installation/using/configuring-spamassassin.md)

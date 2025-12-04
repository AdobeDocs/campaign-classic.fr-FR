---
product: campaign
title: Limitation de l'affichage des PI
description: Découvrez comment limiter l'affichage des PI
feature: PI
role: Developer
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: ht
source-wordcount: '449'
ht-degree: 100%

---

# Limitation de l&#39;affichage des PI{#restricting-pii-view}

## Vue d&#39;ensemble {#overview}

Certains clients ont besoin que les utilisateurs marketing puissent accéder aux enregistrements de données, mais ne souhaitent pas qu’ils visualisent des informations d’identification personnelles (PII) telles que le prénom, le nom ou l’adresse e-mail. Adobe Campaign propose un moyen de protéger la confidentialité et d’empêcher toute utilisation abusive des données par des opérateurs standard de Campaign.

## Mise en œuvre {#implementation}

Un nouvel attribut pouvant être appliqué à n’importe quel élément ou attribut a été ajouté aux schémas. Il complète l’attribut **[!UICONTROL visibleIf]** existant et s’appelle **[!UICONTROL accessibleIf]**. Lorsqu’il contient une expression XTK liée au contexte utilisateur actuel, cet attribut peut utiliser des valeurs telles que **[!UICONTROL HasNamedRight]** ou **[!UICONTROL $(login)]**.

Vous trouverez ci-dessous un exemple d&#39;extension de schéma de destinataire qui illustre cette utilisation :

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

Les principales propriétés sont les suivantes :

* **[!UICONTROL visibleIf]** : cache les champs des métadonnées. Ils ne sont donc pas accessibles dans la vue d&#39;un schéma, la sélection de colonnes ou l&#39;édition d&#39;expressions. Cette propriété ne masque toutefois aucune donnée. Si le nom du champ est saisi manuellement dans une expression, la valeur s&#39;affiche.
* **[!UICONTROL accessibleIf]** : masque les données (en les remplaçant par des valeurs vides) de la requête obtenue. Si visibleIf est vide, il obtient la même expression que l’attribut **[!UICONTROL accessibleIf]**.

Les conséquences de l&#39;utilisation de cet attribut dans Adobe Campaign sont les suivantes :

* Les données ne sont pas affichées dans le requêteur générique de la console.
* Les données ne sont pas visibles dans les listes d&#39;aperçu et la liste des enregistrements (console).
* Les données sont en lecture seule dans la vue détaillée.
* Les données ne peuvent être utilisées que dans des filtres (ce qui signifie qu&#39;il est toujours possible de deviner les valeurs à l&#39;aide de stratégies de dichotomie).
* Les expressions qui sont construites à l&#39;aide d&#39;un champ restreint sont aussi restreintes : lower(@email) devient autant accessible que @email.
* Dans un workflow, vous pouvez ajouter la colonne restreinte à la population ciblée en tant que colonne supplémentaire de la transition, mais elle reste inaccessible aux utilisateurs d&#39;Adobe Campaign.
* Lors du stockage de la population ciblée dans un groupe (liste), les caractéristiques des champs stockés sont identiques à celles de la source de données.
* Par défaut, les données ne sont pas accessibles par les codes JavaScript.

>[!IMPORTANT]
>
>L’utilisation de l’attribut **accessibleIf** sur des paramètres critiques (tels que ceux des clés composites) peut entraîner des erreurs pour les personnes qui ne sont pas autorisées à lire les données en raison de données masquées. Cela peut entraîner des échecs de requête ou un comportement inattendu. Assurez-vous que les paramètres essentiels sont accessibles pour éviter les perturbations.

## Recommandations {#recommendations}

Dans chaque diffusion, les adresses email sont copiées dans les tables de **[!UICONTROL broadLog]** et **[!UICONTROL forecastLog]** : ces champs doivent donc être aussi protégés.

Vous trouverez ci-dessous un exemple d’extension de table de logs pour mettre cela en œuvre :

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Cette restriction s’applique aux utilisateurs n’ayant pas de connaissances techniques : un utilisateur technique, avec les autorisations associées, sera en mesure de récupérer les données. Cette méthode n’est donc pas entièrement sûre.

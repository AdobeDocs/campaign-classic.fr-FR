---
solution: Campaign Classic
product: campaign
title: Base de données des listes bloquées
description: Base de données des listes bloquées
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: ht
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: ht
source-wordcount: '392'
ht-degree: 100%

---


# Base de données des listes bloquées{#denylist-databases}

Plusieurs organisations recensent les adresses IP et les domaines réputés pour être des spammeurs. La consultation de ces sites peut aider à comprendre la raison de certains rejets de messages comme spam. Il est généralement possible de demander le retrait d&#39;une adresse injustement recensée dans ces listes.

Ces bases sont appelées RBL (Real-time Blackhole List) et leur consultation repose sur le mécanisme du DNS. On distingue trois types de RBL :

* Par adresse IP : recense les adresses IP émettrices de spam ou susceptibles de relayer du spam.
* Par domaine d&#39;envoi : recense les domaines d&#39;envoi (domaine complet de l&#39;adresse de mails rebonds) émetteurs de spam ou présentant un défaut de configuration.
* Par domaine web : recense les domaines (domaines de haut niveau tels qu&#39;enregistrés auprès des registrars) trouvés dans les URL des liens et des images des spams. Dans Adobe Campaign, le domaine à considérer est généralement le domaine utilisé pour le tracking.

La liste qui suit répertorie les listes RBL les plus utilisées. Pour obtenir une liste plus complète, consultez la page [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

   Consultez la page [https://www.spamhaus.org/](https://www.spamhaus.org/)

   La base de données est plus importante. Être classé dans cette liste est généralement une situation grave. Si cela se produit, vous devez agir IMMÉDIATEMENT et avertir les services commerciaux, les services chargés de la délivrabilité et l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

   Consultez la page [https://www.spamcop.net/](https://www.spamcop.net/)

   Une des bases les plus connues. Si l&#39;une de vos adresses IP est répertoriée sur cette liste, cela signifie généralement que les utilisateurs de SpamCom ont déclaré vos messages comme étant des spams ou que vous avez envoyé des messages dans les pièges à spam de SpamCop.

* **URIBL**

   Consultez la page [https://www.uribl.com/](https://www.uribl.com/)

   Cette liste identifie les domaines qui apparaissent régulièrement dans les messages déclarés comme étant des spams. Si votre domaine s’affiche dans cette liste, cela peut avoir une incidence significative sur votre délivrabilité. Vous devez informer immédiatement les services chargés de la délivrabilité et l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SURBL**

   Consulter la page [http://www.surbl.org/](http://www.surbl.org/)

   SURBL identifie les sites web qui apparaissent régulièrement dans les spams. Si votre domaine s’affiche dans cette liste, cela peut avoir une incidence significative sur votre délivrabilité. Vous devez informer immédiatement les services chargés de délivrabilité et l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **iX Manitu**

   Cette liste recense des IP et est très utilisée en Allemagne, voir la page [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
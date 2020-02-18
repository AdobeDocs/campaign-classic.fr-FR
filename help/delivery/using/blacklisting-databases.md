---
title: Bases de blacklistage
seo-title: Bases de blacklistage
description: Bases de blacklistage
seo-description: null
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ac3a0ca00591943d79563e9fd4d85d71fa0ba81a

---


# Bases de blacklistage{#blacklisting-databases}

Plusieurs organisations recensent les adresses IP et les domaines réputés pour être des spammeurs. La consultation de ces sites peut aider à comprendre la raison de certains rejets de messages comme spam. Il est généralement possible de demander le retrait d&#39;une adresse injustement recensée dans ces listes.

Ces bases sont appelées RBL (Real-time Blackhole List) et leur consultation repose sur le mécanisme du DNS. On distingue trois types de RBL :

* Par adresse IP : recense les adresses IP émettrices de spam ou susceptibles de relayer du spam.
* Par domaine d&#39;envoi : recense les domaines d&#39;envoi (domaine complet de l&#39;adresse de mails rebonds) émetteurs de spam ou présentant un défaut de configuration.
* Par domaine web : recense les domaines (domaines de haut niveau tels qu&#39;enregistrés auprès des registrars) trouvés dans les URL des liens et des images des spams. Dans Adobe Campaign, le domaine à considérer est généralement le domaine utilisé pour le tracking.

Vous trouverez ci-dessous une liste des listes de révocation des certificats les plus utilisées. Pour obtenir une liste plus exhaustive, consultez le formulaire [https://www.dnsstuff.com/](https://tools.dnsstuff.com/) (&quot;Recherche de liste noire de messages indésirables&quot;).

* **Spamhaus**

   Consultez la page [https://www.spamhaus.org/](https://www.spamhaus.org/)

   La base la plus importante. Etre répertorié sur cette liste est généralement une situation grave. Si cela se produit, vous devez réagir IMMEDIATEMENT et avertir les services commerciaux, délivrabilité et support d&#39;Adobe Campaign.

* **SpamCop**

   Consultez la page [https://www.spamcop.net/](https://www.spamcop.net/)

   Une des bases les plus connues. Si l&#39;une de vos adresses IP est répertoriée sur cette liste, cela signifie généralement que les utilisateurs de SpamCom ont déclaré vos messages comme étant des spams ou que vous avez envoyé des messages dans les pièges à spam de SpamCop.

* **URIBL**

   Consultez la page [https://www.uribl.com/](https://www.uribl.com/)

   Cette liste recense les domaines qui apparaissent régulièrement dans les messages déclarés en spam. Si votre domaine apparaît dans cette liste, cela peut affecter considérablement votre délivrabilité. Avertissez immédiatement les services délivrabilité et support d&#39;Adobe Campaign.

* **SURBL**

   Consultez la page [https://www.surbl.org/](https://www.surbl.org/)

   SURBL recence les sites web qui sont apparus dans des messages non sollicités. Si votre domaine apparaît dans cette liste, cela peut affecter considérablement votre délivrabilité. Avertissez immédiatement les services délivrabilité et support d&#39;Adobe Campaign.

* **iX Manitu**

   Cette liste recense des IP et est très utilisée en Allemagne, voir la page [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
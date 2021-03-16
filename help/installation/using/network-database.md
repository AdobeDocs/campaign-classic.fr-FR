---
solution: Campaign Classic
product: campaign
title: Réseau, base de données et SSL/TLS
description: En savoir plus sur les meilleures pratiques de configuration du réseau, de la base de données et du protocole SSL/TLS.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 63b2e6b95812f1649e636580984a1f0dcc9c5c53
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 78%

---


# Réseau, base de données et SSL/TLS {#network-database}

## Configuration réseau

Le [paramétrage du réseau](../../installation/using/network-configuration.md) est un élément très important que vous devez vérifier lorsque vous déployez un type d’architecture on-premise. Vérifiez que le serveur Tomcat N&#39;EST PAS directement accessible en dehors du serveur :

* Fermez le port Tomcat (8080) sur les adresses IP externes (doit fonctionner sur localhost).
* Ne mappez pas le port HTTP standard (80) sur le port Tomcat (8080).

Si possible, utilisez un canal sécurisé : POP3S au lieu de POP3 (ou POP3 sur TLS).

## Base de données

Vous devez appliquer les meilleures pratiques de sécurité du moteur de base de données.

## Configuration SSL/TLS

Pour vérifier le certificat, vous pouvez utiliser openssl. Pour contrôler les chiffrements actifs, vous pouvez avoir recours à nmap :

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

Vous pouvez également utiliser un script Python [sslyze](https://github.com/nabla-c0d3/sslyze/releases) qui effectue les deux vérifications.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```

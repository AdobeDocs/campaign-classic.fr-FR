---
product: campaign
title: Réseau, base de données et SSL/TLS
description: En savoir plus sur les bonnes pratiques en matière de configuration du réseau, de la base de données et du protocole SSL/TLS
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 100%

---

# Réseau, base de données et SSL/TLS {#network-database}

## Configuration réseau

La [configuration du réseau](../../installation/using/network-configuration.md) est un élément très important à vérifier lorsque vous déployez un type d’architecture On-premise. Assurez-vous que le serveur Tomcat N’EST PAS directement accessible en dehors du serveur :

* Fermez le port Tomcat (8080) sur les adresses IP externes (doit fonctionner sur localhost).
* Ne mappez pas le port HTTP standard (80) sur le port Tomcat (8080).

Si possible, utilisez un canal sécurisé : POP3S au lieu de POP3 (ou POP3 sur TLS).

## Base de données

Vous devez appliquer les bonnes pratiques en matière de sécurité au moteur de votre base de données.

## Configuration de SSL/TLS

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

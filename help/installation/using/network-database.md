---
product: campaign
title: Réseau, base de données et SSL/TLS
description: En savoir plus sur les bonnes pratiques en matière de configuration du réseau, de la base de données et du protocole SSL/TLS
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
TQID: 'https://experienceleague.adobe.com/PLGVcm4QYeU0A1uEhlDEfweZ275xpxtxo91r4aidr1I'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: ht
source-wordcount: '138'
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

Pour vérifier le certificat, vous pouvez utiliser openssl. Pour vérifier les chiffrements actifs, vous pouvez avoir recours à nmap :

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

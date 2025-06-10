---
product: campaign
title: Nouvelles fonctions basées sur GCM
description: Nouvelles fonctions basées sur GCM
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: ht
source-wordcount: '578'
ht-degree: 100%

---

# Fonctions basées sur GCM {#new-functions}

Pour améliorer la sécurité, nous avons abandonné l’utilisation de l’algorithme AES (Advanced Encryption Standard) avec le mode CBC (Cipher Block Chaining) pour les opérations cryptographiques. De nouvelles fonctions de chiffrement ont été introduites. Ces fonctions utilisent AES avec le mode Galois/Counter Mode (AES-GCM), offrant une alternative plus sécurisée. Ces fonctions sont disponibles dans JavaScript, JSP, les API SOAP et les schémas XML, ce qui permet aux clientes et clients de passer de CBC à GCM pour le chiffrement et le déchiffrement.

Cette documentation répertorie les nouvelles fonctions AES-GCM et les fonctions basées sur CBC qui sont en train d’être abandonnées.

Nouvelles fonctions :

* [Fonction de l’API EncryptString](#encryptString-api-xtk)
* [Fonction de l’API EncryptStringWithServerPassword](#EncryptStringWithServerPassword-api-xtk)
* [Fonction JavaScript encryptString](#encryptString-javascript)

Fonctions héritées pouvant être utilisées pour GCM :

* [Fonction JavaScript DecryptString](#decryptString-javascript)
* [Fonction JavaScript DecryptPassword](#decryptPassword-javascript)

[Fonctions obsolètes](#depracated-functions)

## Fonctions API

### EncryptString {#encryptString-api-xtk}

Chiffre la chaîne de caractères avec la clé de l’instance en utilisant l’algorithme AES en mode GCM.

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**Paramètres** : texte déchiffré

**Valeur(s) renvoyée(s)** : chiffrée(s)

**Schéma** : xtk:session

**Statique** : oui

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Chiffre la chaîne de caractères avec la clé du serveur en utilisant l’algorithme AES en mode GCM.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Paramètres** : déchiffrés

**Valeur(s) renvoyée(s)** : chiffrée(s)

**Schéma** : xtk:session

**Statique** : oui

## Fonctions JavaScript

### encryptString() {#encryptString-javascript}

Chiffre une chaîne de caractères avec la clé de l’instance ou toute autre clé.

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**Paramètres** :

* str : chaîne de caractères à chiffrer.
* key : la clé de chiffrement AES est codée en base 64 : 256 bits si la longueur de la clé est 32 ; 192 bits si la longueur de la clé est 24 ; 128 bits si la longueur de la clé est 16 ou si aucune clé n’est spécifiée.
* useSalt : utilisez un sel des données à chiffrer. True par défaut.

**Valeur renvoyée** : renvoie la chaîne de caractères chiffrée.

**Remarques**

Le chiffrement se fait selon la méthode suivante : 

* La chaîne de caractères unicode est transformée en chaîne UTF-8.
* Un caractère de vérification est ajouté dans le texte de chiffrement à la fin.
* Cette chaîne est chiffrée à l’aide de l’algorithme AES en mode Galois/Counter Mode (GCM) en utilisant le sel avec un vecteur d’initialisation de 12 octets et une balise de 16 octets. Si aucune clé n’est fournie en tant que paramètre, la clé d’instance est utilisée.
* Le texte de chiffrement contiendra la balise et le vecteur d’initialisation.
* Le bloc chiffré est alors converti en base 64.

Le déchiffrement est effectué à l’aide de la fonction decryptString.

**Fonctionnalités**

Disponible dans :

* Gestion de contenu
* Propriétés de la diffusion
* Message de diffusion
* Règle de typologie
* Import
* JSSP
* Méthode SOAP
* WebApp
* Workflow

### decryptString() {#decryptString-javascript}

Déchiffre une chaîne de caractères à l’aide de la clé de l’instance ou de toute autre clé. Cette fonction héritée peut être utilisée avec GCM. Elle est obsolète pour le déchiffrement du texte chiffré à l’aide du mode AES-CBC.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Paramètres** :

* str : chaîne de caractères à déchiffrer.
* key : la clé de chiffrement AES est codée en base 64 : 256 bits si la longueur de la clé est 32 ; 192 bits si la longueur de la clé est 24 ; 128 bits si la longueur de la clé est 16 ou si aucune clé n’est spécifiée.
* useSalt : utilisez un sel des données pour déchiffrer. True par défaut.

**Valeur renvoyée** : renvoie la chaîne de caractères déchiffrée.

**Avertissement** : les mots de passe stockés dans la base de données (options/comptes externes) ne peuvent plus être déchiffrés à l’aide de cette méthode. Pour cela, utilisez [decryptPassword](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Déchiffre un mot de passe stocké dans un compte externe. Cette fonction héritée peut être utilisée avec GCM. Elle est obsolète pour le déchiffrement du texte chiffré à l’aide du mode AES-CBC.

```
            decryptPassword (str)
         
```

**Paramètres** :

* str : chaîne de caractères à déchiffrer.

**Valeur renvoyée** : renvoie le mot de passe en texte brut.

**Remarques**

Cette fonction ne peut pas être appelée dans les workflows, les applications web, les rapports ou les diffusions. Elle peut être appelée dans les implémentations d’appels JSSP ou SOAP. Exemple :

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Fonctions obsolètes {#depracated-functions}

Les fonctions suivantes sont totalement obsolètes :

* cryptString
* Chiffrer
* EncryptServerPassword

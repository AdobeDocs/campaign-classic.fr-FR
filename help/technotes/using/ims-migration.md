---
title: Migration des utilisateurs et utilisatrices techniques vers Adobe Developer Console
description: Découvrez comment migrer les opérateurs et opératrices techniques Campaign vers un compte technique sur Adobe Developer Console.
feature: Technote
role: Admin
exl-id: 1a409daf-57be-43c9-a3d9-b8ab54c88068
source-git-commit: af811b2df325efcaee38a967252b6952e67680d1
workflow-type: tm+mt
source-wordcount: '1779'
ht-degree: 100%

---

# Migration des opérateurs et opératrices techniques Campaign vers Adobe Developer Console {#migrate-tech-users-to-ims}

Dans le cadre des efforts visant à renforcer le processus de sécurité et d’authentification, à partir de Campaign Classic v7.3.5, le processus d’authentification de Campaign Classic est en cours d’amélioration. Les opérateurs et opératrices techniques doivent à présent utiliser [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} pour se connecter à Campaign. Pour en savoir plus sur le nouveau processus d’authentification serveur à serveur, consultez la [documentation d’Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}. **Adobe recommande d’effectuer cette migration dans Campaign v7 afin de pouvoir migrer en douceur vers Campaign v8.**

Un opérateur ou une opératrice technique est un profil utilisateur de Campaign qui a été explicitement créé pour l’intégration de l’API. Cet article décrit les étapes à suivre pour migrer un opérateur ou une opératrice technique vers un compte technique par le biais de l’Adobe Developer Console.

## Cela vous concerne-t-il ?{#ims-impacts}

Si vous effectuez des appels API depuis un système externe à Campaign vers l’instance de marketing ou l’instance de Message Center en temps réel de Campaign, Adobe recommande vivement de migrer les opérateurs et opératrices techniques vers les comptes techniques par le biais de l’Adobe Developer Console, comme décrit ci-dessous.

Cette modification s’applique à partir de Campaign Classic v7.3.5 (et des dernières [versions compatibles avec la migration IMS](ac-ims.md#ims-versions)). Elle est **obligatoire** pour passer à Adobe Campaign v8.

## Processus de migration {#ims-migration-procedure}

Suivez les étapes ci-dessous pour créer des comptes techniques dans l’Adobe Developer Console, puis utilisez ces comptes nouvellement créés pour pouvoir modifier les méthodes d’authentification de tous vos systèmes externes qui effectuent des appels API dans Adobe Campaign.

Voici une vue d’ensemble des étapes :

* Créer un projet dans Adobe Developer Console
* Affecter les API appropriées au projet nouvellement créé
* Affecter les profils de produit Campaign nécessaires au projet
* Mettre à jour vos API pour utiliser les informations d’identification du compte technique nouvellement créé
* Supprimer les opérateurs et opératrices techniques hérités de votre instance Campaign


### Prérequis pour la migration{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Clientes et clients Campaign hébergés et Managed Services

  Pour les appels d’API dans les instances Message Center, il faut que le profil de produit (mentionné ci-dessous) ait été créé lors de la mise à niveau vers Campaign v7.4.1 (ou une autre [version compatible avec la migration IMS](ac-ims.md#ims-versions)) ou lors de l’approvisionnement de l’instance. Si vous ne voyez pas le profil de produit, contactez votre gestionnaire de transition ou le service clientèle pour obtenir le profil de produit créé avant de démarrer la migration IMS. Ce profil de produit est nommé :

  `campaign - <your campaign marketing instance> - messagecenter`

  Si vous avez déjà utilisé l’authentification IMS pour l’accès des utilisateurs et utilisatrices à Campaign, les profils de produit requis pour les appels API doivent donc déjà exister dans l’Admin Console. Si vous utilisez un groupe d’opérateurs et d’opératrices personnalisé dans Campaign pour les appels API vers l’instance Marketing, vous devez créer ce profil de produit dans l’Admin Console.

  Dans d’autres cas, vous devez contacter la personne responsable de votre transition Adobe (pour les utilisateurs et utilisatrices d’un environnement Managed Services) ou le service clientèle d’Adobe (pour les utilisateurs et utilisatrices d’un environnement hébergé) afin que les équipes techniques d’Adobe puissent migrer vos groupes d’opérateurs et d’opératrices existants et vos droits nommés vers les profils de produit dans l’Admin Console.

* Clientes et clients de Campaign On-Premise et hybride

  Pour les appels d’API dans les instances de Message Center, vous devez créer un profil de produit nommé :

  `campaign - <your campaign instance> - messagecenter`

  Si vous avez déjà utilisé l’authentification IMS pour l’accès des utilisateurs et utilisatrices à Campaign, les profils de produit requis pour les appels API doivent donc déjà exister dans l’Admin Console. Si vous utilisez un groupe d’opérateurs et d’opératrices personnalisé dans Campaign pour les appels API vers l’instance Marketing, vous devez créer ce profil de produit dans l’Admin Console.

  Vous pouvez en savoir plus sur les profils de produit dans l’Adobe Console dans la [documentation de l’Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.


### Étape 1 : créer votre projet Campaign dans l’Adobe Developer Console {#ims-migration-step-1}

Les intégrations sont créées dans le cadre d’un **Projet** dans Adobe Developer Console. En savoir plus sur les projets dans la [documentation d’Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

Vous pouvez utiliser n’importe quel projet précédemment créé par vous ou créer un nouveau projet. Les étapes de création d’un projet sont détaillées dans la [documentation d’Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. Vous trouverez ci-dessous les étapes clés.

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

Pour créer un projet, cliquez sur **Créer un projet** dans l’écran principal de l’Adobe Developer Console.

![](assets/New-Project.png)

Vous pouvez utiliser le bouton **Modifier le projet** pour renommer ce projet.


### Étape 2 : ajouter des API à votre projet {#ims-migration-step-2}

Dans l’écran du projet nouvellement créé, ajoutez les API nécessaires pour pouvoir utiliser ce projet comme compte technique pour vos appels API à Adobe Campaign.

Pour ajouter des API à votre projet, procédez comme suit :

1. Cliquez sur **Ajouter une API** pour sélectionner les API à ajouter à votre projet.
   ![](assets/do-not-translate/ims-updates-01.png)
1. Sélectionnez l’API Adobe Campaign et ajoutez-la à votre projet en cochant la case située dans le coin supérieur droit de la carte Adobe Campaign qui s’affiche lorsque vous pointez sur la carte.
   ![](assets/do-not-translate/ims-updates-02.png)
1. Cliquez sur **Suivant** au bas de l’écran.

### Étape 3 : sélectionner le type d’authentification  {#ims-migration-step-3}

Dans l’écran **Configurer l’API**, sélectionnez le type d’authentification nécessaire. L’authentification **OAuth serveur à serveur** est requise pour ce projet. Assurez-vous qu’elle est sélectionnée, puis cliquez sur **Suivant** au bas de l’écran.

![](assets/do-not-translate/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### Étape 4 : sélectionner les profils de produit {#ims-migration-step-4}

Comme décrit dans la section des conditions préalables, vous devez attribuer les profils de produit appropriés à utiliser par le projet. Dans cette étape, vous devez sélectionner le ou les profils de produit à utiliser par le compte technique en cours de création.

Si ce compte technique est utilisé pour effectuer des appels d’API vers l’instance Message Center, veillez à sélectionner le profil de produit Adobe, se terminant par messagecenter, pour l’instance marketing associée à Message Center.

Pour les appels d’API aux instances marketing, sélectionnez le profil de produit correspondant à l’instance et au groupe d’opérateurs et d’opératrices. Par exemple, `campaign - <your campaign marketing instance> - Admin`.

Une fois les profils de produit nécessaires sélectionnés, cliquez sur **Enregistrer l’API configurée** au bas de l’écran.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### Étape 5 : ajouter l’API de gestion I/O à votre projet {#ims-migration-step-5}


Dans l’écran du projet, cliquez sur le bouton **[!UICONTROL + Ajouter au projet]** et choisissez **[!UICONTROL API]** dans le coin supérieur gauche de l’écran pour pouvoir ajouter l’API de gestion I/O à ce projet.

![](assets/do-not-translate/ims-updates-04.png)

Dans l’écran **Ajouter une API**, faites défiler l’écran vers le bas pour trouver la carte **API de gestion I/O**. Sélectionnez-la en cochant la case qui s’affiche lorsque vous pointez sur la carte. Cliquez ensuite sur **Suivant** au bas de l’écran.

![](assets/do-not-translate/ims-updates-05.png)


Dans l’écran **Configurer l’API**, l’authentification OAuth serveur à serveur existe déjà. Cliquez sur **Enregistrer l’API configurée** au bas de l’écran.


![](assets/do-not-translate/ims-updates-06.png)

Vous revenez alors à l’écran Projet dans l’API de gestion I/O du projet nouvellement créé. Cliquez sur le nom du projet dans les barres de navigation en haut de l’écran pour revenir à la page principale Détails du projet.


### Étape 6 : vérifier la configuration du projet {#ims-migration-step-6}

Vérifiez votre projet pour vous assurer qu’il ressemble à ce qui suit, avec l’**API de gestion I/O** et l’**API Adobe Campaign** visibles dans la section Produits et services et **OAuth serveur à serveur** dans la section Informations d’identification.

![](assets/do-not-translate/ims-updates-07.png)


### Étape 7 : valider votre configuration {#ims-migration-step-7}

Pour tester la connexion, procédez comme décrit dans le [guide des informations d’identification de l’Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} pour générer un jeton d’accès et copier la commande Sample cURL fournie. Vous pouvez créer un appel SOAP à l’aide de ces informations d’identification pour vérifier que vous pouvez vous authentifier et vous connecter correctement aux instances Adobe Campaign. Nous vous recommandons d’effectuer cette validation avant d’apporter toutes les modifications aux intégrations d’API tierces.

### Étape 8 : mettre à jour les intégrations d’API tierces {#ims-migration-step-8}

Vous devez maintenant mettre à jour les intégrations d’API qui effectuent des appels dans Adobe Campaign pour utiliser le compte technique nouvellement créé.

Pour plus d’informations sur les étapes d’intégration de l’API, reportez-vous aux exemples de code ci-dessous.

Lors de l’utilisation de l’authentification Adobe Identity Management System (IMS), pour générer un fichier WSDL, vous devez ajouter l’autorisation : Bearer &lt;IMS_Technical_Token_Token> dans l’appel postman :

```
curl --location --request POST 'https://<instance_url>/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent' \--header 'Authorization: Bearer <Technical account access token>'
```

>[!BEGINTABS]

>[!TAB Appel SOAP]

```
curl --location --request POST 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp' \
--header 'Content-Type: text/xml; charset=utf-8' \
--header 'SOAPAction: xtk:queryDef#ExecuteQuery' \
--header 'Authorization: Bearer eyJhw' \
--data-raw '<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'
```

>[!TAB  SampleCode Java]

```javascript
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import com.google.gson.Gson;
import com.google.gson.JsonObject;
 
import com.google.gson.JsonSyntaxException;
import org.apache.hc.client5.http.classic.methods.HttpPost;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;
import org.apache.hc.client5.http.impl.classic.HttpClients;
import org.apache.hc.core5.http.HttpEntity;
import org.apache.hc.core5.http.io.entity.StringEntity;
 
 
public class TAAccessToken {
    public static void main(String[] args) throws IOException {
        String accessToken = null;
        CloseableHttpClient httpClient = HttpClients.createDefault();
        try {
            HttpPost httpPost = new HttpPost("https://ims-na1.adobelogin.com/ims/token/v3");
 
            // Request headers
            httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded");
 
            String clientId = "<client_id>";
            String clientSecret = "<client_secret>";
            String scopes = "<scopes>";
 
            // Define the request body
            String requestBody = "client_id="+clientId+"&client_secret="+clientSecret+"&grant_type=client_credentials&scope="+scopes+"";
            StringEntity requestEntity = new StringEntity(requestBody);
            httpPost.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClient.execute(httpPost);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
                int responseCode = response.getCode();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String lineImsToken;
                    StringBuilder responseImsToken = new StringBuilder();
                    while ((lineImsToken = bufferedReader.readLine()) != null) {
                        responseImsToken.append(lineImsToken);
                    }
 
                    String jsonString = responseImsToken.toString();
 
                    try {
                        Gson gson = new Gson();
                        JsonObject jsonObject = gson.fromJson(jsonString, JsonObject.class);
 
                        // Get the value of a specific key
                        accessToken = jsonObject.get("access_token").getAsString();
                    }
                    catch (JsonSyntaxException | NullPointerException e) {
                        System.err.println("Error parsing JSON: " + e.getMessage());
                        e.printStackTrace();
                    }
                    System.out.println("Response Code: " + responseCode);
                    System.out.println("Response Body: " + accessToken);
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClient.close();
        }
 
        CloseableHttpClient httpClientSoap = HttpClients.createDefault();
        try {
            HttpPost httpPostSoap = new HttpPost("https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp");
 
            // Request headers
            httpPostSoap.addHeader("Content-Type", "text/xml; charset=utf-8");
            httpPostSoap.addHeader("SOAPAction", "xtk:queryDef#ExecuteQuery");
            httpPostSoap.addHeader("Authorization", "Bearer "+accessToken);
 
            // Request body
            String xmlData = "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n" +
                    "<soap:Envelope xmlns:soap=\"http://schemas.xmlsoap.org/soap/envelope/\">\n" +
                    "  <soap:Body>\n" +
                    "    <ExecuteQuery xmlns=\"urn:xtk:queryDef\">\n" +
                    "            <sessiontoken></sessiontoken>\n" +
                    "            <entity>\n" +
                    "                <queryDef schema=\"nms:recipient\" operation=\"select\">\n" +
                    "                    <!-- fields to retrieve -->\n" +
                    "                    <select>\n" +
                    "                        <node expr=\"@lastName\"/>\n" +
                    "                        <node expr=\"@email\"/>\n" +
                    "                        <node expr=\"@firstName\"/>\n" +
                    "                    </select>\n" +
                    "                    <!-- condition on email -->\n" +
                    "                    <!-- <where><condition expr=\"@email= '\''joh@com.com'\''\"/>\n" +
                    "                </where> -->\n" +
                    "                </queryDef>\n" +
                    "            </entity>\n" +
                    "        </ExecuteQuery>\n" +
                    "  </soap:Body>\n" +
                    "</soap:Envelope>";
            StringEntity requestEntity = new StringEntity(xmlData);
            httpPostSoap.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClientSoap.execute(httpPostSoap);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String line;
                    while ((line = bufferedReader.readLine()) != null) {
                        System.out.println(line);
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClientSoap.close();
        }
 
    }
}
```

>[!TAB SampleCodePython]

```python
import requests
 
oauth_url = 'https://ims-na1.adobelogin.com/ims/token/v3'
data = {
    'grant_type': 'client_credentials',
    'scope': '<scopes>',
    'client_id': '<client_id>',
    'client_secret': '<client_secret>'
}
 
headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
}
response = requests.post(oauth_url, data=data, headers=headers)
response = response.json()
access_token = response['access_token']
 
 
url = 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp'
headers = {
    'Content-Type': 'text/xml; charset=utf-8',
    'SOAPAction': 'xtk:queryDef#ExecuteQuery',
    'Authorization': 'Bearer '+access_token
}
xml_data = '''<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'''
response = requests.post(url, headers=headers, data=xml_data)
```

>[!ENDTABS]

Pour plus d’informations, consultez la [documentation d’authentification d’Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

Vous trouverez ci-dessous des exemples d’appels SOAP indiquant les appels avant et après la migration pour les systèmes tiers.

Une fois le processus de migration réalisé et validé, les appels Soap sont mis à jour comme indiqué ci-dessous :

* Avant la migration : le jeton d’accès au compte technique n’est pas pris en charge.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* Après la migration : le jeton d’accès au compte technique est pris en charge. Le jeton d’accès doit être fourni dans l’en-tête `Authorization` comme jeton du porteur. L’utilisation du jeton de session doit être ignorée ici, comme illustré dans l’exemple d’appel SOAP ci-dessous.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### Étape 9 : (facultatif) mettre à jour l’opérateur ou opératrice du compte technique dans la console cliente Campaign {#ims-migration-step-9}

Cette étape est facultative et disponible uniquement dans la ou les instances marketing, et non dans une instance Message Center, et si des autorisations de dossiers spécifiques ou des droits nommés ont été définis pour l’opérateur ou l’opératrice technique, et non par le ou les groupes d’opérateurs et d’opératrices attribués. Vous devez maintenant mettre à jour l’utilisateur ou utilisatrice du compte technique nouvellement créé dans l’Admin Console pour accorder les autorisations de dossier ou les droits nommés requis.

Notez que l’utilisateur ou l’utilisatrice du compte technique n’existera PAS dans Adobe Campaign tant qu’au moins un appel API n’aura pas été effectué vers l’instance Campaign. À ce moment-là, IMS créera l’utilisateur ou l’utilisatrice dans Campaign. Si vous ne parvenez pas à localiser les utilisateurs et utilisatrices techniques dans Campaign, vérifiez que vous avez bien réussi à envoyer un appel API comme indiqué [à l’étape 7](#ims-migration-step-7).

1. Pour appliquer les modifications nécessaires au nouvel utilisateur ou à la nouvelle utilisatrice du compte technique, procédez à sa localisation dans la console cliente Campaign avec son adresse e-mail. Cette adresse e-mail a été créée lors des étapes de création et d’authentification du projet ci-dessus.

   Vous pouvez localiser cette adresse e-mail en cliquant sur le titre **OAuth serveur à serveur** dans la section **Informations d’identification** du projet.

   ![](assets/do-not-translate/ims-updates-07.png)

   Dans l’onglet **Informations d’identification**, faites défiler l’écran vers le bas pour localiser l’**adresse e-mail du compte technique**, puis cliquez sur le bouton **Copier**.

   ![](assets/do-not-translate/ims-updates-08.png)

1. Vous devez maintenant mettre à jour l’opérateur technique nouvellement créée ou l’opératrice technique nouvellement créée dans la console cliente Adobe Campaign. Vous devez appliquer les autorisations de dossier des opérateurs et opératrices techniques existants au nouvel opérateur ou à la nouvelle opératrice technique.

   Pour mettre à jour cet opérateur ou cette opératrice, procédez comme suit :

   1. Dans l’explorateur de la console cliente Campaign, accédez à **Administration > Gestion des accès > Opérateurs**.
   1. Accédez à l’opérateur ou opératrice technique existant(e) utilisé(e) pour les API.
   1. Accédez aux autorisations de dossier et vérifiez les droits.
   1. Appliquez les mêmes autorisations à l’opérateur ou opératrice technique nouvellement créé(e). L’adresse e-mail de cet opérateur ou de cette opératrice est la valeur de l’**e-mail du compte technique** copiée précédemment.
   1. Enregistrez vos modifications.


>[!CAUTION]
>
>Le nouvel opérateur ou la nouvelle opératrice technique doit avoir effectué au moins un appel API à ajouter à la console cliente Campaign.
>

### Étape 10 : supprimer l’ancien opérateur ou l’ancienne opératrice technique d’Adobe Campaign {#ims-migration-step-10}

Une fois que vous avez migré tous les systèmes tiers pour utiliser le nouveau compte technique avec l’authentification IMS, vous pouvez supprimer l’ancien opérateur ou l’ancienne opératrice technique de la console cliente Campaign.

Pour ce faire, connectez-vous à la console cliente Campaign, accédez à **Administration > Gestion des accès > Opérateurs et opératrices**, recherchez les anciens utilisateurs et les anciennes utilisatrices techniques et supprimez-les.


>[!MORELIKETHIS]
>
>* [Migration des utilisateurs et utilisatrices finaux vers IMS](migrate-users-to-ims.md)
>* [Mettre à jour de l’interface de Campaign après la migration IMS](impact-ims-migration.md)
>* [Dernières notes de mise à jour d’Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Présentation d’Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}


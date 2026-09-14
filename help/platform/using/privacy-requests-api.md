<?xml version="1.0" encoding="UTF-8"?>
<xliff xmlns="urn:oasis:names:tc:xliff:document:1.2" xmlns:okp="okapi-framework:xliff-extensions" xmlns:its="http://www.w3.org/2005/11/its" xmlns:itsxlf="http://www.w3.org/ns/its-xliff/" version="1.2" its:version="2.0">
<file original="help/platform/using/privacy-requests-api.md.mdsc" source-language="en-US" target-language="en-XX" datatype="x-text/markdown">
<body>
<trans-unit id="tu17" xml:space="preserve">
<source xml:lang="en-US">https://experienceleague.adobe.com/fr/tools/campaign-api</source>
<target xml:lang="en-XX">https://experienceleague.adobe.com/fr/tools/campaign-api</target>
</trans-unit>
<trans-unit id="tu1" restype="x-YAML_METADATA_HEADER_VALUE" xml:space="preserve">
<source xml:lang="en-US">Automatic Privacy request process</source>
<target xml:lang="en-XX">Processus automatique de demande d'accès à des informations personnelles</target>
</trans-unit>
<trans-unit id="tu2" restype="x-YAML_METADATA_HEADER_VALUE" xml:space="preserve">
<source xml:lang="en-US">Learn how to setup an automatic Privacy request process</source>
<target xml:lang="en-XX">Découvrez comment configurer un processus automatique de demande d’accès à des informations personnelles.</target>
</trans-unit>
<trans-unit id="tu3" xml:space="preserve">
<source xml:lang="en-US">Automatic Privacy request process</source>
<target xml:lang="en-XX">Processus automatique de demande d'accès à des informations personnelles</target>
</trans-unit>
<trans-unit id="tu4" xml:space="preserve">
<source xml:lang="en-US">Adobe Campaign provides an <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>API<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> which allows you to setup an automatic Privacy request process.</source>
<target xml:lang="en-XX">Adobe Campaign fournit une <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>API<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> qui permet de configurer un processus automatique de demande d'accès à des informations personnelles.</target>
</trans-unit>
<trans-unit id="tu5" xml:space="preserve">
<source xml:lang="en-US">With the API, the general Privacy process is the same as <ph id="1" ctype="x-LINK">[</ph>using the interface<ph id="2" ctype="x-LINK">](privacy-requests-ui.md)</ph>. The only difference is the creation of the Privacy request. Instead of creating the request in Adobe Campaign, a POST containing the request information is sent to Campaign. For every request, a new entry is added in the <ph id="3" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Privacy Requests<ph id="5" ctype="x-LINK_REF">]**</ph> screen. The Privacy technical workflows then process the request, the same way as for a request added using the interface.</source>
<target xml:lang="en-XX">Avec l'API, le processus général d'accès à des informations personnelles est identique à <ph id="1" ctype="x-LINK">[</ph>celui de l'interface<ph id="2" ctype="x-LINK">](privacy-requests-ui.md)</ph>. La seule différence est la création de la demande d'accès à des informations personnelles. Au lieu de créer la demande dans Adobe Campaign, une instruction POST contenant les informations de la demande est envoyée à Campaign. Pour chaque demande, une nouvelle entrée est ajoutée dans l'écran <ph id="3" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Demandes d'accès à des informations personnelles<ph id="5" ctype="x-LINK_REF">]**</ph>. Les workflows techniques d'accès à des informations personnelles traitent ensuite la demande, de la même manière que pour une demande ajoutée à l'aide de l'interface.</target>
</trans-unit>
<trans-unit id="tu6" xml:space="preserve">
<source xml:lang="en-US">If you're using the API to submit Privacy requests, we recommend that you leave the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>2-step process<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> activated for the first Delete requests, in order to test the returned data. When your tests are finished, you can deactivate the 2-step process so that the Delete request process can run automatically.</source>
<target xml:lang="en-XX">Si vous utilisez l'API pour soumettre des demandes d'accès à des informations personnelles, il est recommandé de conserver l'option <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>Processus en 2 étapes<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> activée pour les premières demandes de suppression, afin de tester les données renvoyées. Une fois vos tests terminés, vous pouvez désactiver le processus en 2 étapes de façon à ce que le processus de demande de suppression puisse s'exécuter automatiquement.</target>
</trans-unit>
<trans-unit id="tu7" xml:space="preserve">
<source xml:lang="en-US">The <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> JS API is defined as follows.</source>
<target xml:lang="en-XX">L'API JS <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> est définie comme suit.</target>
</trans-unit>
<trans-unit id="tu8" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu9" xml:space="preserve">
<source xml:lang="en-US">If you were using the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>gdprRequest<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> API, you can still use it but it is recommended to use the new <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>privacyRequest<ph id="4" ctype="x-STRONG_EMPHASIS">**</ph> API.</source>
<target xml:lang="en-XX">Si vous utilisiez l'API <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>gdprRequest<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, vous pouvez la conserver, mais il est recommandé d'utiliser la nouvelle API <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>privacyRequest<ph id="4" ctype="x-STRONG_EMPHASIS">**</ph>.</target>
</trans-unit>
<trans-unit id="tu10" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!IMPORTANT">[!IMPORTANT]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!IMPORTANT">[!IMPORTANT]</ph></target>
</trans-unit>
<trans-unit id="tu11" xml:space="preserve">
<source xml:lang="en-US">The <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Privacy Data Right<ph id="3" ctype="x-LINK_REF">]**</ph> named right is required to use the API.</source>
<target xml:lang="en-XX">Le droit nommé <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Droit relatif aux données personnelles<ph id="3" ctype="x-LINK_REF">]**</ph> est nécessaire pour utiliser l'API.</target>
</trans-unit>
<trans-unit id="tu12" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu13" xml:space="preserve">
<source xml:lang="en-US">The 'regulation' field is only available if you are using Campaign Classic 20.2 (build 9178+).</source>
<target xml:lang="en-XX">Le champ "règlement" n'est disponible que si vous utilisez Campaign Classic 20.2 (build 9178+).</target>
</trans-unit>
<trans-unit id="tu14" xml:space="preserve">
<source xml:lang="en-US">If you are migrating to 20.2 and if you were already using the API, you must add the ‘regulation’ field as shown above. If you are using a previous build, you can continue to use the API without the ‘regulation’ field.</source>
<target xml:lang="en-XX">Si vous effectuez une migration vers la version 20.2 et que vous utilisiez déjà l'API, vous devez ajouter ce champ comme illustré ci-dessus. Si vous avez recours à un build précédent, vous pouvez continuer à utiliser l'API sans le champ «règlement».</target>
</trans-unit>
<trans-unit id="tu15" xml:space="preserve">
<source xml:lang="en-US">Invoking the API externally</source>
<target xml:lang="en-XX">Appel de l'API en externe</target>
</trans-unit>
<trans-unit id="tu16" xml:space="preserve">
<source xml:lang="en-US">Here is an example of how you can invoke the API externally (authentication via the API and details about the Privacy API specifically). For more information on the Privacy API, consult the <ph id="1" ctype="x-LINK">&lbrack;</ph>API documentation<ph id="2" ctype="x-LINK">[#$tu17]</ph>. You can also consult the <ph id="3" ctype="x-LINK">[</ph>Web service calls documentation<ph id="4" ctype="x-LINK">](../../configuration/using/web-service-calls.md)</ph>.</source>
<target xml:lang="en-XX">Voici un exemple d'appel externe de l'API (authentification via l'API et détails spécifiques sur l'API de protection des données). Pour en savoir plus sur l'API de protection des données, consultez la <ph id="1" ctype="x-LINK">&lbrack;</ph>documentation de l'API<ph id="2" ctype="x-LINK">[#$tu17]</ph>. Vous pouvez également consulter la <ph id="3" ctype="x-LINK">[</ph>documentation sur les appels Web Service<ph id="4" ctype="x-LINK">](../../configuration/using/web-service-calls.md)</ph>.</target>
</trans-unit>
<trans-unit id="tu18" xml:space="preserve">
<source xml:lang="en-US">First of all, you need to perform the authentication via the API:</source>
<target xml:lang="en-XX">Tout d'abord, vous devez effectuer l'authentification par le biais de l'API :</target>
</trans-unit>
<trans-unit id="tu19" xml:space="preserve">
<source xml:lang="en-US">Download the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>xtk<ph id="2" ctype="x-inline-directive">:session**</ph> WSDL via this url: <ph id="4" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=xtk<ph id="6" ctype="x-inline-directive">:session**</ph>.</source>
<target xml:lang="en-XX">Téléchargez le WSDL <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>xtk<ph id="2" ctype="x-inline-directive">:session**</ph> via cette URL : <ph id="4" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=xtk<ph id="6" ctype="x-inline-directive">:session**</ph>.</target>
</trans-unit>
<trans-unit id="tu20" xml:space="preserve">
<source xml:lang="en-US">Use the "Logon" method and pass in a username and password as parameters in the request. You will get a response containing a session token. Here is an example using SoapUI.</source>
<target xml:lang="en-XX">Utilisez la méthode « Logon » et transmettez un nom d’utilisateur ou d’utilisatrice et un mot de passe en tant que paramètres dans la demande. Vous obtiendrez une réponse contenant un jeton de session. Voici un exemple utilisant SoapUI.</target>
</trans-unit>
<trans-unit id="tu21" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api.png)</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api.png)</ph></target>
</trans-unit>
<trans-unit id="tu22" xml:space="preserve">
<source xml:lang="en-US">Use the returned Session Token as the authentication for all subsequence API calls. It expires after 24 hours.</source>
<target xml:lang="en-XX">Utilisez le jeton de session renvoyé comme authentification pour tous les appels API suivants. Il expire au bout de 24 heures.</target>
</trans-unit>
<trans-unit id="tu23" xml:space="preserve">
<source xml:lang="en-US">Then invoke the Privacy API:</source>
<target xml:lang="en-XX">Vous pouvez ensuite appeler l'API de protection des données :</target>
</trans-unit>
<trans-unit id="tu24" xml:space="preserve">
<source xml:lang="en-US">Download the WSDL from this URL: <ph id="1" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=nms<ph id="3" ctype="x-inline-directive">:privacyRequest**</ph>.</source>
<target xml:lang="en-XX">Téléchargez le WSDL à partir de cette URL : <ph id="1" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=nms<ph id="3" ctype="x-inline-directive">:privacyRequest**</ph>.</target>
</trans-unit>
<trans-unit id="tu25" xml:space="preserve">
<source xml:lang="en-US">Use <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> to create a specific Privacy request.</source>
<target xml:lang="en-XX">Utilisez <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> pour créer une demande d'accès à des informations personnelles spécifique.</target>
</trans-unit>
<trans-unit id="tu26" xml:space="preserve">
<source xml:lang="en-US">Here is an example using the <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph>. Note how we use the session token provided above as authentication. The response is the ID of the created request.</source>
<target xml:lang="en-XX">Voici un exemple utilisant <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph>. Remarquez comment nous utilisons le jeton de session fourni ci-dessus pour l'authentification. La réponse est l'identifiant de la demande créée.</target>
</trans-unit>
<trans-unit id="tu27" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api-2.png)</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api-2.png)</ph></target>
</trans-unit>
<trans-unit id="tu28" xml:space="preserve">
<source xml:lang="en-US">To help you perform the steps above, consider the following:</source>
<target xml:lang="en-XX">Pour vous aider à effectuer les étapes ci-dessus, tenez compte des points suivants :</target>
</trans-unit>
<trans-unit id="tu29" xml:space="preserve">
<source xml:lang="en-US">You can use a <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> on the <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequest**</ph> schema to check the status of the Access request.</source>
<target xml:lang="en-XX">Vous pouvez utiliser une <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> sur le schéma <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequest**</ph> pour vérifier le statut de la demande d’accès.</target>
</trans-unit>
<trans-unit id="tu30" xml:space="preserve">
<source xml:lang="en-US">You can use a <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> on the <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequestData**</ph> schema to get the result of the Access request.</source>
<target xml:lang="en-XX">Vous pouvez utiliser une <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> sur le schéma <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequestData**</ph> pour obtenir le résultat de la demande d’accès.</target>
</trans-unit>
<trans-unit id="tu31" xml:space="preserve">
<source xml:lang="en-US">To be able to download the XML file from <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>"$(serverUrl)'/nms/gdpr.jssp?id='@id"<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, you must be logged in and accessing it from an IP that is included in the allowlist. To do this, create a web application allowing you to access the file generated by the JSSP.</source>
<target xml:lang="en-XX">Pour pouvoir télécharger le fichier XML à partir de <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>"$(serverUrl)'/nms/gdpr.jssp?id='@id"<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, vous devez être connecté et y accéder à partir d’une adresse IP placée sur la liste autorisée. Pour ce faire, créez une application web vous permettant d'accéder au fichier généré par le JSSP.</target>
</trans-unit>
<trans-unit id="tu32" xml:space="preserve">
<source xml:lang="en-US">Invoking the API from a JS</source>
<target xml:lang="en-XX">Appel de l'API depuis un script JS</target>
</trans-unit>
<trans-unit id="tu33" xml:space="preserve">
<source xml:lang="en-US">Here is an example of how you can invoke the API from a JS within Campaign Classic.</source>
<target xml:lang="en-XX">Vous trouverez ci-dessous un exemple d'appel de l'API depuis un script JS dans Campaign Classic.</target>
</trans-unit>
<trans-unit id="tu34" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu35" xml:space="preserve">
<source xml:lang="en-US">The 'regulation' field is only available if you are using Campaign Classic 20.2 (build 9178+).</source>
<target xml:lang="en-XX">Le champ "règlement" n'est disponible que si vous utilisez Campaign Classic 20.2 (build 9178+).</target>
</trans-unit>
<trans-unit id="tu36" xml:space="preserve">
<source xml:lang="en-US">If you are migrating to 20.2 and if you were already using the API, you must add the ‘regulation’ field. If you are using a previous build, you can continue to use the API without the ‘regulation’ field.</source>
<target xml:lang="en-XX">Si vous effectuez une migration vers la version 20.2 et que vous utilisiez déjà l'API, vous devez ajouter ce champ. Si vous avez recours à un build précédent, vous pouvez continuer à utiliser l'API sans le champ «règlement».</target>
</trans-unit>
<trans-unit id="tu37" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>using a previous build (with GDPR package)<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, you can continue to use the API without the ‘regulation’ field as shown below:</source>
<target xml:lang="en-XX">Si <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>vous utilisez une version précédente (avec le package RGPD)<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, vous pouvez continuer à utiliser l'API sans le champ 'regulation' comme illustré ci-dessous :</target>
</trans-unit>
<trans-unit id="tu38" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>migrating to 20.2<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> and if you were already using the API, you must add the ‘regulation’ field as shown below:</source>
<target xml:lang="en-XX">Si vous effectuez une <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>migration vers la version 20.2<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> et que vous utilisiez déjà l'API, vous devez ajouter ce champ comme illustré ci-dessous :</target>
</trans-unit>
<trans-unit id="tu39" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>using Campaign Classic 20.2 (build 9178+) or above<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, the 'regulation' field is optional, as shown below:</source>
<target xml:lang="en-XX">Si <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>vous utilisez Campaign Classic 20.2 (version 9178+) ou une version ultérieure<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, le champ 'regulation' est facultatif, comme illustré ci-dessous :</target>
</trans-unit>
</body>
</file>
</xliff>
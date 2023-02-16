---
product: campaign
title: Intégration du SDK Campaign
description: Découvrez comment intégrer le SDK Campaign à votre application mobile
feature: Mobile SDK Integration, Push
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 0ae52b00f69298e001596583fe166771faddead2
workflow-type: ht
source-wordcount: '1012'
ht-degree: 100%

---

# Intégration du SDK Campaign à votre application {#integrating-campaign-sdk-into-the-mobile-application}

![](../../assets/common.svg)

Les SDK Campaign pour iOS et Android sont des composants du module Canal des applications mobiles.

>[!NOTE]
>
>Pour obtenir le SDK Campaign (anciennement connu sous le nom de SDK Neolane), contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

L’intérêt du SDK est de faciliter l’intégration d’une application mobile à la plateforme Adobe Campaign.

Pour plus d’informations sur les différentes versions Android et iOS prises en charge, consultez la [matrice de compatibilité](../../rn/using/compatibility-matrix.md#MobileSDK).

>[!NOTE]
>
>Vous pouvez également utiliser le SDK mobile Adobe Experience Platform en configurant l’extension Adobe Campaign dans Adobe Launch. [En savoir plus dans la documentation relative à Adobe Experience Platform](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.
>
>Découvrez comment configurer et installer le SDK mobile Adobe Experience Platform [dans cette vidéo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/configure-push-using-aep-mobile-sdk.html?lang=fr){target="_blank"}.

## Charger le SDK Campaign {#loading-campaign-sdk}

* **Sous Android** : le fichier **neolane_sdk-release.aar** doit être lié au projet.

   L’autorisation suivante permet l&#39;accès au serveur Adobe Campaign :

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
   ```

   La permisson suivante permet de récupérer un identifiant unique par téléphone :

   ```
   <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   ```

   A partir de la version 1.0.24 du SDK, cette autorisation est uniquement utilisée pour les versions antérieures à Android 6.0.

   A partir de la version 1.0.26 du SDK, cette autorisation n&#39;est plus utilisée.

* **Sous iOS** : les fichiers **libNeolaneSDK.a** et **Neolane_SDK.h** doivent être liés au projet. A partir de la version 1.0.24 du SDK, l&#39;option **ENABLE_BITCODE** est activée.

   >[!NOTE]
   >
   >Pour la version 1.0.25 du SDK, les quatre architectures sont disponibles dans le fichier **Neolane_SDK.h**.

## Déclarer les paramètres d&#39;intégration {#declaring-integration-settings}

Afin d&#39;intégrer le SDK Campaign dans l&#39;application mobile, l&#39;administrateur fonctionnel doit fournir au développeur les informations suivantes :

* **Une clé d&#39;intégration** permettant à la plateforme Adobe Campaign d&#39;identifier l&#39;application mobile.

   >[!NOTE]
   >
   >Cette clé d&#39;intégration est renseignée dans la console Adobe Campaign, dans l&#39;onglet **[!UICONTROL Informations]** du service dédié à l&#39;application mobile. Pour plus d&#39;informations, consultez la section [Paramétrage de l’application mobile dans Adobe Campaign](configuring-the-mobile-application.md).

* **Une URL de tracking** correspondant à l&#39;adresse du serveur de tracking Adobe Campaign.
* **Une URL marketing** permettant de collecter les abonnements.

* **Sous Android** :

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
   ```

* **Sous iOS** :

   ```
   Neolane_SDK *nl = [Neolane_SDK getInstance];
   [nl setMarketingHost:strMktHost];
   [nl setTrackingHost:strTckHost];
   [nl setIntegrationKey:strIntegrationKey];
   ```

## Fonction d&#39;enregistrement {#registration-function}

La fonction d&#39;enregistrement permet :

* d&#39;envoyer l&#39;identifiant de notification ou push id (deviceToken pour iOS et registrationID pour Android) à Adobe Campaign.
* de récupérer la clé de réconciliation ou userKey (par exemple l&#39;adresse email ou le numéro de compte)

* **Sous Android** :

   ```
   void registerInNeolane(String registrationId, String userKey, Context context)
   {
    try{
     Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
    } catch (NeolaneException e){
     //...
    } catch (IOException e){
     //...
    }
   }
   ```

   Si vous utilisez FCM (Firebase Cloud Messaging), nous vous conseillons d&#39;utiliser la fonction **registerDevice** lors de l&#39;appel de la fonction **onTokenRefresh** pour notifier Adobe Campaign du changement de token de l&#39;appareil mobile de l&#39;utilisateur.

   ```
   public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
     @Override
     public void onTokenRefresh() {
       String registrationToken = FirebaseInstanceId.getInstance().getToken();
       NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
       ...
       ...
       // Neolane Registration
       neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
       public void onComplete(String e, Object state) { ... }
       public void onNeolaneException(NeolaneException e, Object state) { ... }
       public void onIOException(IOException e, Object state) { ... }
       });
       ...
       ...
     }
   }
   ```

* **Sous iOS** :

   ```
   // Callback called on successful registration to the APNs
   - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
   {
       // Pass the token to Adobe Campaign
       Neolane_SDK *nl = [Neolane_SDK getInstance];
       [nl registerDevice:tokenString:self.userKey:dic];
   }
   ```

## Fonction de tracking {#tracking-function}

* **Sous Android** :

   Les fonctions de tracking permettent de tracker l&#39;affichage de la notification (impression sur écran) et l&#39;activation des notifications (ouvertures).

   Pour tracker l&#39;affichage d&#39;une notification (réalisé via l&#39;appel de la fonction **notifyReceive** du SDK),suivez l&#39;implémentation ci-après. Si vous utilisez FCM (Firebase Cloud Messaging), nous vous conseillons d&#39;utiliser la fonction **notifyReceive** lors de l&#39;appel de la fonction **onMessageReceived** par le système Android.

   ```
   package com.android.YourApplication;
   
   import android.content.Context;
   import android.content.SharedPreferences;
   import android.os.Bundle;
   import android.util.Log;
   
   import com.google.firebase.messaging.FirebaseMessagingService;
   import com.google.firebase.messaging.RemoteMessage;
   
   import java.util.Iterator;
   import java.util.Map;
   import java.util.Map.Entry;
   
   public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
     private static final String TAG = "MyFirebaseMsgService";
   
     @Override
     public void onMessageReceived(RemoteMessage message) {
       Log.d(TAG, "Receive message from: " + message.getFrom());
       Map<String,String> payloadData = message.getData();
       final Bundle extras = new Bundle();
       final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
       while(iter.hasNext())
       {
         final Entry<String, String>  entry =iter.next();
         extras.putString(entry.getKey(), entry.getValue());
       }
   
       SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
       String mesg = payloadData.get("_msg");
       String title = payloadData.get("title");
       String url = payloadData.get("url");
       String messageId = payloadData.get("_mId");
       String deliveryId = payloadData.get("_dId");
       YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
     }
   }
   ```

   ```
   public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
       if( message == null ) message = "No Content";
       if( title == null )   title = "No title";
       if( url == null )     url = "https://www.tripadvisor.fr";
       int iconId = R.drawable.notif_neotrip;
   
     // notify Neolane that a notification just arrived
     SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
     Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
     Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
     Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
   
     NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
     nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
       public void onNeolaneException(NeolaneException arg0, Object arg1) {}
       public void onIOException(IOException arg0, Object arg1) {}
       public void onComplete(String arg0, Object arg1){}
     });
     if (yourApplication.isActivityVisible())
       {
         Log.i("INFO", "The application has the focus" );
         ...
       }
       else
       {
         // notification creation :
         NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
         Notification notification;
   
         // Activity to start :
         Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
         notifIntent.putExtra("notificationText", message);
         notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
         notifIntent.putExtra("_dId", deliveryId);
         notifIntent.putExtra("_mId", messageId);
         notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
         PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
   
         notification = new Notification.Builder(context)
                 .setContentTitle(title)
                 .setContentText(message)
                 .setSmallIcon(iconId)
                 .setContentIntent(contentIntent)
                 .build();
   
         // launch the notification :
         notification.flags |= Notification.FLAG_AUTO_CANCEL;
         notificationManager.notify(Integer.valueOf(messageId), notification);
       }
   }
   ```

   Voici un exemple d&#39;implémentation pour le tracking de l&#39;ouverture d&#39;une notification (réalisé via l&#39;appel de la fonction **notifyOpening** du SDK). La classe **NotificationActivity** correspond à celle utilisée pour créer l&#39;objet **notifIntent** dans l&#39;exemple précédent.

   ```
   public class NotificationActivity extends Activity {
   public void onCreate(Bundle savedBundle) {
     [...]
     Bundle extra = getIntent().getExtras();
     if (extra != null) {
       // reinit the acc sdk
       SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
       Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
       Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
       Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
   
       // Get the messageId and the deliveryId to do the tracking
       String deliveryId = extra.getString("_dId");
       String messageId = extra.getString("_mId");
       if (deliveryId != null && messageId != null) {
         try {
           Neolane.getInstance().notifyOpening(Integer.valueOf(messageId), Integer.valueOf(deliveryId));
         } catch (NeolaneException e) {
           // ...
         } catch (IOException e) {
           // ...
         }
       }
     }
    }
   }
   ```

* **Sous iOS** :

   La fonction de tracking permet de tracker l&#39;activation des notifications (ouvertures).

   ```
   (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
   fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
   {
   if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
   *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
   ...  
   completionHandler(UIBackgroundFetchResultNoData);
   }
   ```

   >[!NOTE]
   >
   >À partir de la version 7.0, une fois la fonction **application:didReceiveRemoteNotification:fetchCompletionHandler** mise en œuvre, le système d&#39;exploitation appelle uniquement cette fonction. La fonction **application:didReceiveRemoteNotification** n&#39;est donc pas appelée.

## Suivi des notifications silencieuses {#silent-notification-tracking}

iOS permet d&#39;envoyer des notifications silencieuses, des notifications ou des données qui seront directement envoyées à une application mobile sans les afficher. Adobe Campaign vous permet de les tracker.

Pour suivre votre notification silencieuse, suivez l&#39;exemple ci-après.

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

### Délégué RegisterDeviceStatus {#registerdevicestatus-delegate}

>[!NOTE]
>
>Ceci s&#39;applique exclusivement à iOS.

Sous iOS, le protocole délégué vous permet d’obtenir le résultat de l’appel de **registerDevice** et peut être utilisé pour déterminer si une erreur s’est produite pendant l’enregistrement.

Le prototype de **registerDeviceStatus** est le suivant :

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

Le **Statut** vous permet de déterminer si un enregistrement a été effectué avec succès ou si une erreur s’est produite.

**ErrorReason** fournit des informations supplémentaires sur les erreurs qui se sont produites. Pour en savoir plus sur les erreurs disponibles et leur description, reportez-vous au tableau ci-dessous.

<table> 
 <thead>
  <tr>
   <th> Status<br /> </th>
   <th> Description<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Succès de l'enregistrement<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> Le nom d'hôte du serveur marketing ACC est vide ou non défini.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> La clé d'intégration est vide ou non définie.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> Problème de connexion lié à ACC<br /> </td>
   <td> Informations supplémentaires (dans la langue actuelle du système d'exploitation)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> L'UUID indiqué (clé d'intégration) est inconnu.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> Une erreur inattendue a été retournée au serveur ACC.<br /> </td>
   <td> Message d'erreur retourné à ACC.<br /> </td>
  </tr>
 </tbody>
</table>

Le protocole **Neolane_SDKDelegate** et la définition du délégué **registerDeviceStatus** sont les suivants :

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

Pour implémenter le délégué **registerDeviceStatus**, procédez comme suit :

1. Implémentez **setDelegate** pendant l&#39;initialisation du SDK.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings
   
    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];
   
    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. Ajoutez le protocole à l&#39;**@interface** de votre classe.

   ```
   //  AppDelegate.h
   
   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"
   
   @class LandingPageViewController;
   
   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. Implémentez le délégué dans **AppDelegate**.

   ```
   //  AppDelegate.m
   
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);
   
       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);
   
       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

## Variables {#variables}

Les variables vous permettent de définir le comportement de l&#39;application mobile après réception d&#39;une notification. Ces variables doivent être définies dans le code de l&#39;application mobile et dans la console Adobe Campaign, dans l&#39;onglet **[!UICONTROL Variables]** du service d&#39;applications mobiles dédié (voir la section [Paramétrage de l&#39;application mobile dans Adobe Campaign](configuring-the-mobile-application.md)). Voici un exemple de code qui permet à une application mobile de collecter toutes les variables ajoutées dans une notification. Dans notre exemple, nous utilisons la variable &quot;VAR&quot;.

* **Sous Android** :

   ```
   public void onReceive(Context context, Intent intent) {
        ...
       String event = intent.getStringExtra("VAR");
        ...
   }
   ```

* **Sous iOS** :

   ```
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
       ....
       if( launchOptions )
       {
           // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
           NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
           if( localLaunchOptions )
           {
            ...
            [localLaunchOptions objectForKey:@"VAR"];
           ...
           }
      }
   }
   
   // Callback called when the application is already launched (whether the application is running foreground or background)
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
   {
       if( launchOptions )
       {
        ...
           [launchOptions objectForKey:@"VAR"];
       }
   }
   ```

>[!CAUTION]
>
>Adobe recommande de choisir des noms de variables courts car la taille des notifications est limitée : 4 ko pour iOS et Android.

## Extension du service de notification {#notification-service-extension}

**Pour iOS**

Le média doit être téléchargé au niveau de l&#39;extension du service de notification.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

## Extension du contenu de notification {#notification-content-extension}

**Pour iOS**

A ce niveau, vous devez effectuer les opérations suivantes :

* Associer votre extension de contenu à la catégorie envoyée par Adobe Campaign :

   Si vous souhaitez que l&#39;application mobile affiche une image, définissez la valeur de la catégorie dans Adobe Campaign, par exemple &quot;image&quot;. Dans l&#39;application mobile, vous créez une extension de notification avec le paramètre **UNNotificationExtensionCategory** ayant pour valeur &quot;image&quot;. Lorsque la notification push est reçue sur l&#39;appareil, l&#39;extension est appelée selon la valeur de la catégorie définie.

* Définir le style de la notification

   Vous devez définir le style avec les widgets adéquats. Pour une image, c&#39;est le widget **UIImageView**.

* Afficher le contenu multimédia

   Vous devez ajouter du code pour alimenter le widget avec les données multimédia. Voici un exemple de code pour une image :

   ```
   #import "NotificationViewController.h"
   #import <UserNotifications/UserNotifications.h>
   #import <UserNotificationsUI/UserNotificationsUI.h>
   
   @interface NotificationViewController () <UNNotificationContentExtension>
   
   @property (strong, nonatomic) IBOutlet UIImageView *imageView;
   @property (strong, nonatomic) IBOutlet UILabel *notifContent;
   @property (strong, nonatomic) IBOutlet UILabel *label;
   
   @end
   
   @implementation NotificationViewController
   
   - (void)viewDidLoad {
       [super viewDidLoad];
       // Do any required interface initialization here.
   }
   
   - (void)didReceiveNotification:(UNNotification *)notification {
       self.label.text = notification.request.content.title;
       self.notifContent.text = notification.request.content.body;
       UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
       if ([attachment.URL startAccessingSecurityScopedResource])
       {
         NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
         self.imageView.image =[UIImage imageWithData: imageData];
         [attachment.URL stopAccessingSecurityScopedResource];
       }
   }
   @end
   ```

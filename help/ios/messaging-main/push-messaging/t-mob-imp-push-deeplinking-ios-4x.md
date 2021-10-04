---
description: Nadat u de deep linking-URL hebt geconfigureerd in de gebruikersinterface van Adobe Mobile Services, bevindt deze URL zich in de pushlading met de adb_deplink-toets.
title: Implementeer Push Messaging met Deep Linking
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
exl-id: c9ca955c-506f-45fe-82d6-fad2f9a80130
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 1%

---

# Push messaging implementeren met deep linking {#implement-push-messaging-with-deep-linking}

Nadat u de deep linking-URL hebt geconfigureerd in de gebruikersinterface van Adobe Mobile Services, bevindt deze URL zich in de pushlading met de `adb_deeplink`-toets.

1. In AppDelegate, kunt u diepe verbinding URL terug krijgen en het behandelen op uw eigen plaats in de volgende plaatsen:

   * In `application:didFinishLaunchingWithOptions`:

      Als de app niet wordt uitgevoerd wanneer er een push-klik plaatsvindt, kunt u de pushlading ophalen vanuit `launchOptions` en de deep link URL in het payload-woordenboek wordt geplaatst door de `adb_deeplink`-toets.

   * De afgevaardigde methodes voor Verre Bericht

      In de `didReceiveRemoteNotification:` toepassing of in `didReceiveRemoteNotification:fetchCompletionHandler:` toepassing, kunt u URL krijgen door tot het `userInfo` woordenboek met `adb_deeplink` sleutel toegang te hebben.

   * De gedelegeerde methoden voor `UNUserNotificationCenter`

      In de `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` methode, kunt u duw lading van `userInfo` woordenboek, in `adb_deeplink` sleutel krijgen.

Bijvoorbeeld:

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```

---
description: Vanaf WatchOS 2 worden de WatchKit Extensions uitgevoerd op een Apple Watch-apparaat. Toepassingen die in deze omgeving worden uitgevoerd, vereisen het WatchConnectivity-framework om gegevens te delen met de bijbehorende iOS-app.
seo-description: Vanaf WatchOS 2 worden de WatchKit Extensions uitgevoerd op een Apple Watch-apparaat. Toepassingen die in deze omgeving worden uitgevoerd, vereisen het WatchConnectivity-framework om gegevens te delen met de bijbehorende iOS-app.
seo-title: Apple Watch-implementatie met WatchOS 2
solution: Marketing Cloud,Analytics
title: Apple Watch-implementatie met WatchOS 2
topic: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Apple Watch-implementatie met WatchOS 2{#apple-watch-implementation-with-watchos}

Vanaf WatchOS 2 kunnen uw WatchKit Extensions worden uitgevoerd op een Apple Watch. Toepassingen die in deze omgeving worden uitgevoerd, vereisen dat het `WatchConnectivity` framework gegevens deelt met de bijbehorende iOS-app.

>[!TIP]
>
>Vanaf `AdobeMobileLibrary` v4.6.0 wordt `WatchConnectivity` dit ondersteund.

## Nieuwe release van Adobe Experience Platform Mobile SDK

Op zoek naar informatie en documentatie over de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via het [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar Adobe Experience Platform Launch.
* Ga naar [Github om te zien wat er in de repositories van Experience Platform SDK staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aan de slag {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Zorg ervoor dat u een project hebt met minstens de volgende doelstellingen:
>
>* De bevattende app
>* De app WatchKit
>* De extensie WatchKit
>



Raadpleeg [de Watch App Architecture](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)voor meer informatie over het ontwikkelen van WatchKit-apps.

## De bevattende app configureren {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de `AdobeMobileLibrary` map naar uw project.
1. Zorg ervoor dat het `ADBMobileConfig.json` bestand lid is van het doel van de bevattende app.
1. In the **[!UICONTROL Build Phases]** tab of your containing app’s target, expand the **[!UICONTROL Link Binary with Libraries]** section and add the following libraries:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. In uw klasse die het `UIApplicationDelegate` protocol uitvoert, voeg het `WCSessionDelegate` protocol toe.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. Importeer het bestand `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Voordat u de `ADBMobile` bibliotheek aanroept, configureert u uw gedelegeerde `application:didFinishLaunchingWithOptions:` app `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Implementeer de methoden `session:didReceiveMessage:` `session:didReceiveUserInfo:` en methoden in uw gedelegeerde app.

   `syncSettings:` wordt aangeroepen in de `ADBMobile` bibliotheek, die een bool retourneert die aangeeft of het woordenboek is bedoeld voor gebruik door de `ADBMobile` bibliotheek. Als het bericht wordt geretourneerd, is het niet vanuit de SDK van Adobe gestart. `No`

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## De extensie WatchKit configureren {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Zorg ervoor dat het `ADBMobileConfig.json` bestand lid is van het doel van de extensie WatchKit.
1. In the **[!UICONTROL Build Phases]** tab of your WatchKit extension’s target, expand the **[!UICONTROL Link Binary with Libraries]** section and add the following libraries:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In uw klasse die het `WKExtensionDelegate` protocol uitvoert, voer `WatchConnectivity` en voeg het `WCSessionDelegate` protocol toe.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Importeer het bestand `AdobeMobileLibrary`in het implementatiebestand van de gedelegeerde extensie.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` van uw uitbreidingsafgevaardigde, vorm uw `WCSession` alvorens om het even welke vraag aan de `ADBMobile` bibliotheek te maken.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Start in `applicationDidFinishLaunching` het geval van uw gedelegeerde extensie de app watch voor de SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In uw uitbreidingsafgevaardigde, voer de `session:didReceiveMessage:` `session:didReceiveUserInfo:` en de methodes uit.

   `syncSettings:` wordt aangeroepen in de `ADBMobile` bibliotheek, die een bool retourneert die aangeeft of het woordenboek is bedoeld voor gebruik door de `ADBMobile` bibliotheek. Als het bericht wordt geretourneerd, is het niet vanuit de SDK van Adobe gestart. `NO`

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Aanvullende informatie {#section_7BCDB5CF0D424DCA97883753D1881233}

De volgende informatie onthouden:

* Voor WatchKit-apps wordt `a.RunMode` ingesteld op `Extension`.
* Aangezien WatchKit-apps worden uitgevoerd op de watch, worden hun namen correct gerapporteerd in `a.AppID`.
* Er wordt geen levenscyclusaanroep geactiveerd voor WatchOS2-apps.


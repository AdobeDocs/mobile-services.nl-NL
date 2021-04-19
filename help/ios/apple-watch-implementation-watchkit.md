---
description: Vanaf WatchOS 2 worden de WatchKit Extensions uitgevoerd op een Apple Watch-apparaat. Toepassingen die in deze omgeving worden uitgevoerd, vereisen het WatchConnectivity-framework om gegevens te delen met de bijbehorende iOS-app.
seo-description: Vanaf WatchOS 2 worden de WatchKit Extensions uitgevoerd op een Apple Watch-apparaat. Toepassingen die in deze omgeving worden uitgevoerd, vereisen het WatchConnectivity-framework om gegevens te delen met de bijbehorende iOS-app.
seo-title: Apple Watch-implementatie met WatchOS 2
solution: Experience Cloud,Analytics
title: Apple Watch-implementatie met WatchOS 2
topic-fix: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
exl-id: 9fc9b799-1081-42e4-acf3-569fdeb07aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Apple Watch-implementatie met WatchOS 2{#apple-watch-implementation-with-watchos}

Vanaf WatchOS 2 kunnen uw WatchKit Extensions worden uitgevoerd op een Apple Watch. Voor toepassingen die in deze omgeving worden uitgevoerd, moet het `WatchConnectivity`-framework gegevens delen met de bijbehorende iOS-app.

>[!TIP]
>
>Vanaf `AdobeMobileLibrary` v4.6.0 wordt `WatchConnectivity` ondersteund.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aan de slag {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Zorg ervoor dat u een project hebt met minstens de volgende doelstellingen:
>
>* De bevattende app
>* De app WatchKit
>* De extensie WatchKit

>



Zie [De architectuur van de app controleren](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1) voor meer informatie over het ontwikkelen van WatchKit-apps.

## De bevattende app {#section_0A2A3995575B4E2ABD12E426BA06AEFF} configureren

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de `AdobeMobileLibrary` omslag in uw project.
1. Zorg ervoor dat het `ADBMobileConfig.json`-bestand lid is van het doel van de bevattende app.
1. Vouw op het tabblad **[!UICONTROL Build Phases]** van het doel van de bevattende app de sectie **[!UICONTROL Link Binary with Libraries]** uit en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. In uw klasse die `UIApplicationDelegate` protocol uitvoert, voeg `WCSessionDelegate` protocol toe.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. Importeer `AdobeMobileLibrary` in het implementatiebestand van de gedelegeerde klasse voor de app.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Voordat u een oproep doet naar de `ADBMobile`-bibliotheek, moet u `WCSession` in `application:didFinishLaunchingWithOptions:` van uw gedelegeerde app configureren.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Implementeer de methoden `session:didReceiveMessage:` en `session:didReceiveUserInfo:` in uw gedelegeerde toepassing.

   `syncSettings:` wordt aangeroepen in de  `ADBMobile` bibliotheek, die een bool retourneert die aangeeft of het woordenboek is bedoeld voor gebruik door de  `ADBMobile` bibliotheek. Als het `No` terugkeert, werd het bericht niet in werking gesteld van Adobe SDK.

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

## De WatchKit-extensie {#section_5ADE31741E514330A381F2E3CFD4A814} configureren

1. Zorg ervoor dat het `ADBMobileConfig.json`-bestand lid is van het doel van de extensie WatchKit.
1. Vouw op het tabblad **[!UICONTROL Build Phases]** van het doel van de extensie WatchKit de sectie **[!UICONTROL Link Binary with Libraries]** uit en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. Importeer `WatchConnectivity` in de klasse die het `WKExtensionDelegate`-protocol implementeert en voeg het `WCSessionDelegate`-protocol toe.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. In het implementatiedossier van uw klasse van de uitbreidingsafgevaardigde, voer `AdobeMobileLibrary` in.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` van uw uitbreidingsafgevaardigde, vorm uw `WCSession` alvorens om het even welke vraag aan `ADBMobile` bibliotheek te maken.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Start in `applicationDidFinishLaunching` van uw gedelegeerde extensie de app watch voor de SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In uw uitbreidingsafgevaardigde, voer `session:didReceiveMessage:` en `session:didReceiveUserInfo:` methodes uit.

   `syncSettings:` wordt aangeroepen in de  `ADBMobile` bibliotheek, die een bool retourneert die aangeeft of het woordenboek is bedoeld voor gebruik door de  `ADBMobile` bibliotheek. Als het `NO` terugkeert, werd het bericht niet in werking gesteld van Adobe SDK.

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

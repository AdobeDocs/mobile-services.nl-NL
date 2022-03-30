---
description: Vanaf WatchOS 2 worden uw WatchKit Extensions uitgevoerd op een Apple Watch-apparaat. Toepassingen die in deze omgeving worden uitgevoerd, vereisen dat het WatchConnectivity-framework gegevens deelt met de bijbehorende iOS-app.
solution: Experience Cloud Services,Analytics
title: Apple Watch Implementation met WatchOS 2
topic-fix: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
exl-id: 9fc9b799-1081-42e4-acf3-569fdeb07aff
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# Apple Watch-implementatie met WatchOS 2{#apple-watch-implementation-with-watchos}

Vanaf WatchOS 2 kunnen uw WatchKit Extensions worden uitgevoerd op een Apple Watch. Toepassingen die in deze omgeving worden uitgevoerd, vereisen `WatchConnectivity` -framework om gegevens te delen met de bijbehorende iOS-app.

>[!TIP]
>
>Beginnen met `AdobeMobileLibrary` v4.6.0 `WatchConnectivity` wordt ondersteund.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aan de slag {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Zorg ervoor dat u een project hebt met minstens de volgende doelstellingen:
>
>* De bevattende app
>* De app WatchKit
>* De extensie WatchKit
>


Ga voor meer informatie over het ontwikkelen van WatchKit-apps naar [De App Architectuur van de Controle](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## De bevattende app configureren {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de `AdobeMobileLibrary` in uw project.
1. Zorg ervoor dat de `ADBMobileConfig.json` is een lid van het doel van de bevattende app.
1. In de **[!UICONTROL Build Phases]** tabblad van het doel van de bevattende app, vouwt u de **[!UICONTROL Link Binary with Libraries]** en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. In uw klasse die het `UIApplicationDelegate` protocol, voeg toe `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. Importeer in het implementatiebestand van de gedelegeerde klasse van uw app de klasse `AdobeMobileLibrary`.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Voordat u een aanroep naar de `ADBMobile` bibliotheek, in `application:didFinishLaunchingWithOptions:` van uw toepassingsafgevaardigde, vorm uw `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Implementeer in uw app-gedelegeerde de `session:didReceiveMessage:` en `session:didReceiveUserInfo:` methoden.

   `syncSettings:` wordt aangeroepen in het dialoogvenster `ADBMobile` bibliotheek, die een bool retourneert die aangeeft of het woordenboek voor gebruik door de `ADBMobile` bibliotheek. Als het terugkeert `No`, is het bericht niet vanuit de Adobe SDK geïnitieerd.

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

1. Zorg ervoor dat de `ADBMobileConfig.json` Dit bestand is een lid van het doel van de extensie WatchKit.
1. In de **[!UICONTROL Build Phases]** tabblad van het doel van de extensie WatchKit vouwt u de **[!UICONTROL Link Binary with Libraries]** en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In uw klasse die het `WKExtensionDelegate` protocol, importeren `WatchConnectivity` en voeg de `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Importeer in het implementatiebestand van de gedelegeerde extensie de klasse `AdobeMobileLibrary`.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. In `applicationDidFinishLaunching` van uw uitbreidingsafgevaardigde, vorm uw `WCSession` alvorens om het even welke vraag te maken aan `ADBMobile` bibliotheek.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In `applicationDidFinishLaunching` initialiseer de app watch voor de SDK van uw gedelegeerde extensie.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In uw uitbreidingsafgevaardigde, voer uit `session:didReceiveMessage:` en `session:didReceiveUserInfo:` methoden.

   `syncSettings:` wordt aangeroepen in het dialoogvenster `ADBMobile` bibliotheek, die een bool retourneert die aangeeft of het woordenboek voor gebruik door de `ADBMobile` bibliotheek. Als het terugkeert `NO`, is het bericht niet vanuit de Adobe SDK geïnitieerd.

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

* Voor WatchKit-apps, `a.RunMode` wordt ingesteld op `Extension`.
* Omdat WatchKit-apps worden uitgevoerd via de watch, worden hun namen correct gerapporteerd in `a.AppID`.
* Er wordt geen levenscyclusaanroep geactiveerd voor WatchOS2-apps.

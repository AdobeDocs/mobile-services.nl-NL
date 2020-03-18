---
description: Met deze informatie kunt u in-app berichten gebruiken in uw iOS-apps.
seo-description: Met deze informatie kunt u in-app berichten gebruiken in uw iOS-apps.
seo-title: In-app berichten
solution: Marketing Cloud,Analytics
title: In-app berichten
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# In-app berichten {#in-app-messaging}

Met deze informatie kunt u in-app berichten gebruiken in uw iOS-apps.

Als u in-app berichten wilt gebruiken, **moet** u SDK versie 4.2 of hoger hebben.

Enkele informatie die u moet onthouden:

* Berichten en de regels die bepalen wanneer de berichten worden getoond worden gecreeerd in de diensten van Adobe Mobile. Zie Een bericht [in de app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)maken voor meer informatie.
* De updates die in deze sectie worden beschreven moeten aan SDK worden gemaakt om in-app berichten te tonen.

   >[!TIP]
   >
   >U kunt deze stappen zelfs uitvoeren als er geen berichten zijn gedefinieerd. Nadat u berichten hebt gedefinieerd, worden deze dynamisch aan uw app geleverd en zonder update van de App Store weergegeven.

## In-app-berichten inschakelen {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/requirements.md)voor meer informatie.

1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Controleer of het `ADBMobileConfig.json` bestand de vereiste instellingen voor In-App-berichten bevat.
1. Als u wilt dat in-app-berichten tijdens het starten dynamisch worden bijgewerkt, moet het `remotes` object aanwezig zijn en correct zijn geconfigureerd:

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` of `remotes` is vereist.

   Als deze objecten niet zijn geconfigureerd, downloadt u een bijgewerkt `ADBMobileConfig.json` bestand van Adobe Mobile-services. Zie [Core Implementation en Lifecycle](/help/ios/getting-started/requirements.md)voor meer informatie.

## In-app berichten bijhouden {#section_B85CDF6929564AAEA79338B55E5CB1E8}

De SDK&#39;s van iOS Mobile Services volgen de volgende meetgegevens voor uw in-app-berichten:

* Voor volledig scherm en waakzame stijl binnen-app berichten:

   * **[!UICONTROL Impressions]**: wanneer de gebruiker een bericht in de app activeert.
   * **[!UICONTROL Click throughs]**: wanneer de gebruiker op de **[!UICONTROL Click-through]** knop drukt.
   * **[!UICONTROL Cancels]**: wanneer de gebruiker op de **[!UICONTROL Cancel]** knop drukt.

* Voor aangepaste, volledig scherm in-app berichten moet de HTML-inhoud in het bericht de juiste code bevatten om de SDK een melding te geven van de volgende knoppen:

   * **[!UICONTROL Click-through]** (omleiden) voorbeeld bijhouden: `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Cancel]** (close) voorbeeld tracking: `adbinapp://cancel`

* Voor lokale (externe) meldingen:

   * **[!UICONTROL Impressions]**: wanneer de gebruiker het bericht activeert.
   * **[!UICONTROL Opens]**: wanneer de gebruiker de toepassing opent vanuit het bericht.
   Hier volgt een voorbeeld van de manier waarop u open tracking kunt opnemen:

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Lokale fallback-afbeelding {#section_DEACC1CE549B4573B556A44A52409941}

Als u een volledig-schermbericht maakt in Adobe Mobile-services, kunt u desgewenst een fallback-afbeelding opgeven. Als uw bericht de bedoelde afbeelding niet van het web kan ophalen, probeert de SDK de afbeelding met dezelfde naam uit uw toepassingsbundel te laden. Op deze manier kunt u uw bericht in de oorspronkelijke vorm weergeven, zelfs als de gebruiker offline is of als de vooraf ingestelde afbeelding onbereikbaar is.

De naam van het fallback-afbeeldingselement wordt opgegeven bij het configureren van het bericht in Adobe Mobile-services.

>[!IMPORTANT]
>
>U moet ervoor zorgen dat de opgegeven bron beschikbaar is.


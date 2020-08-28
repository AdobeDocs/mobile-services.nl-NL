---
description: Hier volgt een lijst met methoden die worden geleverd door de iOS-bibliotheek.
seo-description: Hier volgt een lijst met methoden die worden geleverd door de iOS-bibliotheek.
seo-title: Configuratiemethoden
solution: Marketing Cloud,Analytics
title: Configuratiemethoden
topic: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: 527f93ae4ec910d1d1ea3637eb3a62d749a14397
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 21%

---


# Configuratiemethoden {#configuration-methods}

Hier volgt een lijst met methoden die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service.

* **setAppExtensionType**

   Vormt de Adobe Mobile SDK-instelling om te bepalen welk type extensie momenteel wordt uitgevoerd.

   Stel een van de volgende waarden in:
   * `ADBMobileAppExtensionTypeRegular` - de extensie wordt gebundeld met een bevattende app.
   * `ADBMobileAppExtensionTypeStandAlone` - de extensie wordt niet gebundeld met een bevattende app.

   >[!TIP]
   >
   >Deze methode mag **alleen** worden gebruikt als uw app een extensie heeft of een zelfstandige extensie is. Zie *ADBMobileAppExtensionType* hieronder voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **versie**

   Retourneert de huidige versie van de Adobe Mobile-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(NSString*) version;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   Retourneert de numerieke representatie van de privacystatus voor de huidige gebruiker:

   * `ADBMobilePrivacyStatusOptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut` - treffers worden genegeerd.
   * `ADBMobilePrivacyStatusUnknown` - Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (vervolgens worden treffers verzonden) of Afmelden (vervolgens worden treffers verwijderd). Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.
De standaardwaarde wordt ingesteld in het `ADBMobileConfig.json` bestand.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   Hiermee stelt u de privacystatus voor de huidige gebruiker in `status`.

   Stel een van de volgende waarden in:

   * `ADBMobilePrivacyStatusOptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut` - treffers worden genegeerd.
   * `ADBMobilePrivacyStatusUnknown` - Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (vervolgens worden treffers verzonden) of Afmelden (vervolgens worden treffers verwijderd). Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifeValue**

   Retourneert de levensduurwaarde van de huidige gebruiker. De standaardwaarde is `0`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   Retourneert de automatisch gegenereerde bezoeker-id. Dit is een unieke bezoekersidentiteitskaart app-specifiek die door de servers van Adobe wordt geproduceerd. Als Adobe niet kunnen worden bereikt op het moment dat ze worden gegenereerd, wordt de id gegenereerd met de CFUID van Apple. De waarde wordt gegenereerd bij de eerste keer dat de toepassing wordt gestart en wordt vanaf dat punt opgeslagen en gebruikt. Deze id blijft bewaard tussen upgrades van apps, wordt opgeslagen en hersteld tijdens het back-upproces van de standaardtoepassing en wordt verwijderd bij het verwijderen.

   >[!TIP]
   >
   >Als uw app van de Experience Cloud 3.x naar de 4.x-SDK upgradet, wordt de vorige aangepaste of automatisch gegenereerde bezoeker-id opgehaald en opgeslagen als de aangepaste gebruikers-id. Zie de `userIdentifier` rij hieronder voor meer informatie. Op deze manier blijven bezoekersgegevens behouden tussen SDK-upgrades. Voor nieuwe installaties op 4.x SDK, is het gebruikersherkenningsteken `nil` en het volgen herkenningsteken wordt gebruikt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   Als een aangepaste id is ingesteld, wordt de gebruikers-id geretourneerd. Als er geen aangepaste id is ingesteld, wordt deze `nil` geretourneerd. De standaardwaarde is `nil`.

   >[!TIP]
   >
   >Als uw app upgradet van de SDK van Experience Cloud 3.x naar 4.x, wordt de vorige aangepaste of automatisch gegenereerde bezoeker-id opgehaald en opgeslagen als de aangepaste gebruikers-id. Op deze manier blijven bezoekersgegevens behouden tussen upgrades van de SDK.

   Voor nieuwe installaties op 4.x SDK, is het gebruikersherkenningsteken `nil` tot reeks.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   Hiermee stelt u de gebruikers-id in op `identifier`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   Retourneert de huidige voorkeur voor foutopsporing. De standaardwaarde is `NO`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   Hiermee stelt u de voorkeur voor foutopsporing in op `debug`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   Wijst aan SDK erop dat uw volgende hervat van achtergrond geen nieuwe zitting, ongeacht de waarde van de tijd van de levenscycluszitting in uw configuratiedossier zou moeten beginnen.

   >[!TIP]
   >
   >Deze methode is bedoeld voor toepassingen die zich registreren voor meldingen op de achtergrond en mag alleen worden aangeroepen vanuit de code die wordt uitgevoerd terwijl de toepassing op de achtergrond wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectionLifecycleData**

   Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/ios/metrics.md)voor meer informatie.

   >[!TIP]
   >
   >De voorkeurslocatie voor het aanroepen van deze methode is in `application:didFinishLaunchingWithOptions:`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   Hiermee kunt u aanvullende gegevens doorgeven bij het verzamelen van levenscyclusmetriek.

   Deze methode moet worden aangeroepen vanaf het ingangspunt van uw app. Indien van toepassing, kan dit één of allebei van de methodes `application:didFinishLaunchingWithOptions:` en/of `applicationWillEnterForeground:` in uw klasse AppDelegate omvatten.

   >[!IMPORTANT]
   >
   >Gegevens die via `collectLifecycleDataWithAdditionalData:` de SDK aan de SDK worden doorgegeven, blijven in de SDK behouden `NSUserDefaults`. De SDK verwijdert waarden in de `NSDictionary` parameter die niet van het type `NSString` of `NSNumber`zijn. U kunt alleen `collectLifecycleDataWithAdditionalData:`gebruiken met SDK- **versie 4.4** of hoger.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   Gebruik deze API om de verzameling van levenscyclusgegevens te pauzeren. Zie [Levenscyclusstatistieken](/help/ios/metrics.md)voor meer informatie.

   >[!IMPORTANT]
   >
   >In de `applicationDidEnterBackground` afgevaardigde methode, moet u de `pauseCollectingLifecycleData` methode eerst roepen.
   >
   >De API is bedoeld om het probleem op iPhone7/7s- of oudere apparaten met iOS 13 te verhelpen, waarbij de meting voor de sessielengte abnormaal werd. Dit was het gevolg van enkele onbekende wijzigingen die zijn opgetreden in iOS 13, waarbij iOS niet genoeg tijd verlaat om de achtergrondtaak te voltooien wanneer u de toepassing ondergronds maakt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   Hiermee kunt u een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart. De verschillende configuratie wordt gebruikt tot de toepassing wordt gesloten.

   >[!IMPORTANT]
   >
   >SDK-versie 4.2 of hoger is vereist `overrideConfigPath`om te kunnen gebruiken.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   Hiermee stelt u het apparaattoken voor pushberichten in.

   >[!IMPORTANT]
   >
   >Deze methode mag alleen in de `application:didRegisterForRemoteNotificationsWithDeviceToken:` methode worden gebruikt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   Hiermee stelt u de IDFA in de SDK in. Als de IDFA is ingesteld in de SDK, wordt de IDFA verzonden in de levenscyclus. Het kan ook in Signals (Postbacks) worden betreden.

   >[!TIP]
   >
   >Haal de IDFA **alleen** van Apple API&#39;s op als u een advertentieservice gebruikt. Als u IDFA ophaalt en deze niet correct gebruikt, wordt uw app mogelijk afgewezen.
   >
   >Als voor uw toepassing IDFA is vereist, controleert u de documentatie [van](https://developer.apple.com/documentation/adsupport) Apple om de gebruikersvoorkeuren voor Advertentie te raadplegen en de IDFA-waarde op te halen.
   >
   >Voor iOS 14+ moet het nieuwe [app Tracking Transparency framework](https://developer.apple.com/documentation/apptrackingtransparency) worden geïmplementeerd om de IDFA-waarde te kunnen ophalen.
   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```


---
description: Met deze informatie kunt u diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden met de Adobe Mobile iOS SDK.
solution: Experience Cloud,Analytics
title: Diepkoppelingen bijhouden
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
exl-id: a8b20233-d800-4318-ad4f-39229d8b3a5e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Diepkoppelingen bijhouden{#tracking-deep-links}

Met deze informatie kunt u diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden met de Adobe Mobile iOS SDK.

Voor meer informatie over hoe de marketers diep het verbinden in hun toepassingen gebruiken, zie [Verwerving](/help/ios/acquisition-main/acquisition.md) in de Mobiele documentatie van de Diensten.

## Diepkoppelingen bijhouden

1. Voeg de SDK toe aan uw project en implementeer levenscyclusmetriek.

   Zie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en LiveCycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
1. Registreer de toepassing voor het afhandelen van inter-App-communicatie of voor het ondersteunen van Universal Links.

   Zie [Communicatie tussen toepassingen](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) of [Universele koppelingen ondersteunen](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html) voor meer informatie

1. Diepe koppeling bijhouden in openURL.

   Hier volgt een voorbeeld van de diepe koppeling naar de track:

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

De Adobe Mobile SDK kan sleutel- en waardeparen gegevens parseren die aan een diepe of Universal Link zijn toegevoegd, op voorwaarde dat de koppeling een sleutel bevat met een `a.deeplink.id`-label en een corresponderende, niet-null en door de gebruiker gegenereerde waarde. Alle sleutel- en waardeparen gegevens die aan de koppeling worden toegevoegd, worden geparseerd, gekoppeld aan een levenscyclushit en verzonden naar Adobe Analytics, op voorwaarde dat de koppeling de sleutel en waarde `a.deeplink.id` bevat.

U zou ook kunnen verkiezen om één of meerdere van de volgende gereserveerde sleutels (met user-generated waarden) aan de diepe of Universele Verbinding toe te voegen:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Deze toetsen zijn vooraf toegewezen variabelen voor rapportage in Adobe Analytics. Voor meer informatie over afbeelding en verwerkingsregels, zie [Regels en Context Data](/help/ios/getting-started/proc-rules.md) verwerken.

### Uitgestelde diepe koppelingen bijhouden

1. Registreer Adobe-gegevenscallback.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Verwerk `ADBMobileDataEventDeepLink` binnen `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Openbare informatie dieper koppelen {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### Methoden

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### Constanten

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```

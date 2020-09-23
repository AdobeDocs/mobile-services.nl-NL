---
description: Met deze informatie kunt u diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden met de Adobe Mobile iOS SDK.
seo-description: Met deze informatie kunt u diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden met de Adobe Mobile iOS SDK.
seo-title: Diepkoppelingen bijhouden
solution: Experience Cloud,Analytics
title: Diepkoppelingen bijhouden
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Diepkoppelingen bijhouden{#tracking-deep-links}

Met deze informatie kunt u diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden met de Adobe Mobile iOS SDK.

Voor meer informatie over hoe de marketers diep het verbinden in hun toepassingen gebruiken, zie [Verwerving](/help/ios/acquisition-main/acquisition.md) in de Mobiele documentatie van de Diensten.

## Diepkoppelingen bijhouden

1. Voeg de SDK toe aan uw project en implementeer levenscyclusmetriek.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. Registreer de toepassing voor het afhandelen van inter-App-communicatie of voor het ondersteunen van Universal Links.

   Voor meer informatie, zie [Communicatie](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) inter-App of de Universele Verbindingen van de [Steun](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

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

De mobiele SDK van Adobe kan sleutel en waardeparen gegevens ontleden die aan om het even welke diepe of Universele Verbinding worden toegevoegd, op voorwaarde dat de verbinding een sleutel met een `a.deeplink.id` etiket en een overeenkomstige niet-krachteloze en gebruiker geproduceerde waarde bevat. Alle sleutel- en waardeparen gegevens die aan de koppeling worden toegevoegd, worden geparseerd, gekoppeld aan een levenscyclushit en verzonden naar Adobe Analytics, op voorwaarde dat de koppeling de `a.deeplink.id` sleutel en waarde bevat.

U zou ook kunnen verkiezen om één of meerdere van de volgende gereserveerde sleutels (met user-generated waarden) aan de diepe of Universele Verbinding toe te voegen:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Deze toetsen zijn vooraf toegewezen variabelen voor rapportage in Adobe Analytics. Voor meer informatie over afbeelding en verwerkingsregels, zie de Regels van de [Verwerking en de Gegevens](/help/ios/getting-started/proc-rules.md)van de Context.

### Uitgestelde diepe koppelingen bijhouden

1. Registreer Adobe-gegevenscallback.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Handgreep `ADBMobileDataEventDeepLink` binnen `AdobeDataCallback`.

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


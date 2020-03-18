---
description: Gebruik de iOS SDK om het bijhouden van uitgebreide koppelingen van derden te implementeren.
seo-description: Gebruik de iOS SDK om het bijhouden van uitgebreide koppelingen van derden te implementeren.
seo-title: Het volgen van derde Uitgestelde Diepe Verbindingen
title: Het volgen van derde Uitgestelde Diepe Verbindingen
uuid: 5525b609-e926-44b9-b0f5-38e9dd7c9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# Uitgestelde diepe koppelingen van derden bijhouden {#tracking-third-party-deferred-deep-links}

Gebruik de iOS SDK om het bijhouden van uitgebreide koppelingen van derden te implementeren.

## Klassieke Adobe Mobile SDK, diep koppelen {#section_D114FA1EB9664EAA82E036A990694B26}

De SDK van Adobe Mobile ondersteunt momenteel diepe koppelingen, waarbij de ontwikkelaar van de app naar verwachting de `trackAdobeDeepLink` API aanroept en de deep linking-URL doorgeeft. Dit is de vingerprinter-URL die tijdens de configuratie in Adobe Mobile Services wordt gegenereerd. De SDK pingelt de vingerprinter om aanschafgegevens te verkrijgen en voegt deze toe aan de analytische gegevens voor installeren/starten en roept contextgegevens aan als onderdeel van de levenscyclus. Daarnaast voegt de SDK ook de gegevens van de deplink-URL-parameters toe. Voor meer informatie bij diepe verbinding, zie het [Volgen Diepe Verbindingen](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Een maker van een advertentie kan een advertentie op Facebook maken als een diepe koppeling. Wanneer gebruikers op de advertentie op Facebook klikken, gaat het rechtstreeks naar de informatie waarin ze geïnteresseerd zijn in de app. De diepe koppeling is **geen** vingerprinter-URL. Tijdens de configuratie van de advertentie is er echter een optie om een diepe koppeling-URL van derden op te geven. Een toepassingsontwikkelaar die de Experience Cloud Mobile SDK&#39;s en services gebruikt, moet de door Mobile Services geconfigureerde vingerprinter-URL in dit veld invoeren. Als alles correct is ingesteld, geeft de SDK van Facebook deze URL door aan de toepassing wanneer de app wordt geïnstalleerd of gestart.

## SDK&#39;s instellen {#section_834CD3109175432B8173ECB6EA7DE315}

1. Stel de SDK van Facebook in.

   Raadpleeg de volgende secties voor meer informatie:

   * [Aan de slag met de SDK van Facebook voor iOS](https://developers.facebook.com/docs/ios/getting-started)
   * [Setup deplinken](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. Als u de SDK wilt instellen, roept u de URL aan `trackAdobeDeepLink` en geeft u deze door aan de SDK&#39;s:

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >Zorg ervoor dat de diepe verbinding URL een sleutel met de naam heeft `a.deeplink.id`. Er worden geen URL-parameters aan de contextgegevens toegevoegd als de URL de `a.deeplink.id` parameter heeft overgeslagen.

Als de toepassing is ingesteld zoals hierboven beschreven, werkt de huidige AMSDK-versie goed en voegt u de diepgaande koppelingsgegevens toe om de analytische aanroepen correct te installeren/starten.

## De functie in een voorbeeldtoepassing inschakelen {#section_64C15E269E89424B8E3D029F88094620}

1. Registreer een URL-schema.

   Zorg ervoor dat u een URL-schema hebt geregistreerd. Dit is hetzelfde als de diepe koppeling-URL.

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. Koppel de SDK&#39;s van Facebook.

   ![Facebook-middelen](assets/link-fb-sdk.jpg)

1. Bewerken `AppDelegate`.

   1. Importeer de kopteksten.

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. Voeg de handgreep voor uitgestelde diepe koppelingen toe.

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. Roep de `trackAdobeDeepLink` API aan en geef de diepe verbinding URL aan SDK door.

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```


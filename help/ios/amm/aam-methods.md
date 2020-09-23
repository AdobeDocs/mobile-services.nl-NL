---
description: Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de iOS-bibliotheek.
seo-description: Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de iOS-bibliotheek.
seo-title: Methoden van Audience Manager
solution: Experience Cloud,Analytics
title: Methoden van Audience Manager
topic: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 22%

---


# Methoden van Audience Manager {#audience-manager-methods}

Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service. De methoden worden vooraf bepaald volgens de oplossing en de Audience Manager wordt voorgefixeerd met &quot; `audience`.&quot;

Als Audience Manager in uw JSON-bestand is geconfigureerd, wordt een signaal met levenscyclusmetriek verzonden `application:didFinishLaunchingWithOptions:`.

* **publiekVisitorProfile**

   Retourneert het bezoekersprofiel dat het laatst is verkregen en retourneert, als er geen signaal is verzonden, `null`. Het bezoekersprofiel wordt opgeslagen in `NSUserDefaults` zodat u eenvoudig toegang hebt tot meerdere startpagina&#39;s van uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Hier volgt het codevoorbeeld voor dit menu:

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **publiekDpid**

   Retourneert de huidige DPID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **publiekDpuuid**

   Retourneert de huidige DPUUID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **publiekSetDpid: &#x200B; puuid:**

   Hiermee stelt u de DPID en DPUUID in. Wanneer reeks, allebei zal aan elk signaal worden toegevoegd.

   * Identiteitskaart van de Leverancier van **Gegevens (DPID)** is identiteitskaart van de gegevenspartner die door Audience Manager wordt toegewezen.
   * De unieke gebruikersnaam van de **gegevensaanbieder (DPUUID)** is de unieke id van de gegevensaanbieder voor de gebruiker.

      >[!IMPORTANT]
      >
      >Vóór versie 4.13.x werd DPUUID niet automatisch gecodeerd. Vanaf versie 4.13.x decodeert de SDK eerst de waarde die is doorgegeven en codeert deze waarde vervolgens opnieuw. Dit proces zorgt ervoor dat de SDK de compatibiliteit met oudere versies niet breekt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **publiekReset**

   Hiermee wordt de UUID van de Audience Manager opnieuw ingesteld en wordt het huidige bezoekersprofiel gewist.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(void) audienceReset;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **publiekSignalWithData: &#x200B; callback:**

   Verzendt publieksbeheer een signaal met eigenschappen en krijgt de passende segmenten die in een blokcallback zijn teruggekeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## Voorbeeld

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```

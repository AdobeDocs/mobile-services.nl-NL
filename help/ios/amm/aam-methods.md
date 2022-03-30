---
description: Hier volgt een lijst met de methoden van de Audience Manager die worden geleverd door de iOS-bibliotheek.
solution: Experience Cloud Services,Analytics
title: Methoden van Audience Manager
topic-fix: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
exl-id: b843a52f-2b83-4e19-9f43-895bd582d4ef
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 24%

---

# Methoden van Audience Manager {#audience-manager-methods}

Hier volgt een lijst met de methoden van de Audience Manager die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service. De methoden worden vooraf bepaald volgens de oplossing en de Audience Manager wordt voorafgegaan door &quot; `audience`.&quot;

Als Audience Manager in uw JSON-bestand is geconfigureerd, wordt een signaal met levenscyclusmetriek verzonden met `application:didFinishLaunchingWithOptions:`.

* **publiekVisitorProfile**

   Retourneert het bezoekersprofiel dat het laatst is verkregen en retourneert, als er geen signaal is verzonden `null`. Het bezoekersprofiel is opgeslagen in `NSUserDefaults` voor eenvoudige toegang bij meerdere startpagina&#39;s van uw app.

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

   * De **Data Provider ID (DPID)** is identiteitskaart van de gegevenspartner die door Audience Manager wordt toegewezen.
   * De **Unieke gebruikersnaam gegevensaanbieder (DPUUID)** is de unieke id van de gegevensaanbieder voor de gebruiker.

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

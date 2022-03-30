---
description: Hier volgt een lijst met Adobe Analytics-methoden die worden geleverd door de iOS-bibliotheek.
solution: Experience Cloud Services,Analytics
title: Analysemethoden
topic-fix: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
exl-id: 327ec44a-be15-47af-a2c8-a373124999ad
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 33%

---

# Analysemethoden {#analytics-methods}

Hier volgt een lijst met Adobe Analytics-methoden die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service. Methoden worden vooraf bepaald volgens de oplossing. Experience Cloud ID-methoden beginnen met `track`.

Elk van deze methoden wordt gebruikt om gegevens naar uw Adobe Analytics-rapportenpakket te verzenden.

* **trackState: &#x200B; gegevens:**

   Frames zijn de weergaven die beschikbaar zijn in uw app, zoals `home dashboard`, `app settings`, `cart`, enzovoort. Deze statussen lijken op pagina&#39;s op een website, en `trackState` roept stijgende paginameningen. Indien `state` is leeg, wordt weergegeven als *app name app version (build)* in verslagen. Als u deze waarde in rapporten ziet, zorg ervoor u plaatst `state` in elke `trackState` vraag.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction: &#x200B; gegevens:**

   Tracks an action in your app. Handelingen die u wilt meten, zoals `logons`, `banner taps`, `feed subscriptions`en andere meetgegevens, vindt u in uw app.

   >[!TIP]
   >
   >Als u code hebt die kan worden uitgevoerd terwijl de toepassing zich op de achtergrond bevindt (bijvoorbeeld een ophaalbewerking voor achtergrondgegevens), gebruikt u `trackActionFromBackground` in plaats daarvan.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   Haalt de id voor het bijhouden van analyses op.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground: &#x200B; gegevens:**

   Tracks an action that occurred in the background, which suppresses lifecycle events from firing in certain scenario&#39;s.

   >[!TIP]
   >
   >Deze methode mag alleen worden aangeroepen in code die wordt uitgevoerd terwijl de toepassing op de achtergrond wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation: &#x200B; gegevens:**

   Verzendt de huidige x y-coördinaten. Gebruikt ook aandachtspunten die in `ADBMobileConfig.json` bestand om te bepalen of de locatie die als parameter wordt opgegeven zich in een van uw POI&#39;s bevindt. Als de huidige coördinaten zich in een gedefinieerde POI bevinden, wordt een contextgegevensvariabele gevuld en verzonden met de `trackLocation` vraag.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon: &#x200B; gegevens:**

   Tracks wanneer een gebruiker nabijheid van een baken ingaat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   Wist beacons gegevens nadat een gebruiker de nabijheid van het baken verlaat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease: &#x200B; gegevens:**

   Toevoegingen `amount` naar de levensduurwaarde van de gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart: &#x200B; gegevens:**

   Een getimede actie met naam starten `action`. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate: &#x200B; gegevens:**

   Doorgeven in `data` om de contextgegevens bij te werken die bij het gegeven horen `action`. De `data` die wordt doorgegeven, wordt toegevoegd aan de bestaande gegevens voor de actie en als dezelfde sleutel al is gedefinieerd voor `action`, overschrijft de gegevens.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd: &#x200B; logica:**

   Een getimede actie beëindigen. Als u `block`, hebt u toegang tot de uiteindelijke tijdwaarden en kunt u `data` voordat de laatste treffer wordt verzonden.

   >[!TIP]
   >
   >Als u `block`, u moet terugkeren `YES` om een hit te verzenden. Passend in `nil` for `block` verzendt de laatste hit.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   Retourneert of een getimede actie wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   Vereist SDK 4.1. Ongeacht het aantal treffers dat momenteel in de wachtrij wordt geplaatst, dwingt de bibliotheek alle treffers in de offline wachtrij te verzenden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   Hiermee wordt het aantal treffers opgehaald dat momenteel in de offline wachtrij staat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   Wist alle treffers van de off-line rij.

   >[!CAUTION]
   >
   >Wees voorzichtig wanneer u de wachtrij handmatig wist. Dit proces kan niet ongedaan worden gemaakt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   Tracks a push message click-through.

   >[!IMPORTANT]
   >
   >Met deze methode worden de paginaweergaven niet vergroot.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```

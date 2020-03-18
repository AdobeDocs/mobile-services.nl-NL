---
description: iOS-methoden voor Xamarin-componenten voor Experience Cloud-oplossingen 4.x SDK.
keywords: Xamarin
seo-description: iOS-methoden voor Xamarin-componenten voor Experience Cloud-oplossingen 4.x SDK.
seo-title: iOS-methoden
solution: Marketing Cloud,Developer
title: iOS-methoden
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
translation-type: tm+mt
source-git-commit: f53953831e6471ea64eb2ae06ddae16ca0eab6f6

---


# iOS-methoden{#ios-methods}

iOS-methoden voor Xamarin-componenten voor Experience Cloud-oplossingen 4.x SDK.

## Configuratiemethoden {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/ios/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **DebugLogging**

   Retourneert de huidige voorkeur voor foutopsporing. De standaardwaarde is `false`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   Hiermee stelt u de voorkeur voor foutopsporing in op ingeschakeld.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **LifetimeValue**

   Retourneert de levensduurwaarde van de huidige gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static double LifetimeValue();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **PrivacyStatus**

   Retourneert de opsomming van de privacystatus voor de huidige gebruiker.
   * `ADBMobilePrivacyStatus.OptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatus.OptOut` - treffers worden genegeerd.
   * ADBMobilePrivacyStatus.Unknown - Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de status van de privacy verandert in opt-in (dan worden treffers verzonden) of opt-out (dan worden treffers genegeerd). Als offline bijhouden is uitgeschakeld, worden treffers verwijderd totdat de privacystatus verandert in aanmelden.
   De standaardwaarde wordt ingesteld in [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **SetPrivacyStatus**

   Hiermee stelt u de privacystatus voor de huidige gebruiker in op status. Stel een van de volgende waarden in:
   * `ADBMobilePrivacyStatus.OptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatus.OptOut` - treffers worden genegeerd.
   * `ADBMobilePrivacyStatus.Unknown`  - Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (vervolgens worden treffers verzonden) of Afmelden (vervolgens worden treffers verwijderd). Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   Retourneert de aangepaste gebruikers-id als er een aangepaste id is ingesteld. Retourneert null als er geen aangepaste id is ingesteld. De standaardwaarde is `null`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   Retourneert de aangepaste gebruikers-id als er een aangepaste id is ingesteld. Retourneert null als er geen aangepaste id is ingesteld. De standaardwaarde is `null`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static string UserIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   Hiermee wordt de bibliotheekversie opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static string Version();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive (alleen iOS)**

   Wijst aan SDK erop dat uw volgende hervat van achtergrond geen nieuwe zitting, ongeacht de waarde van de tijd van de levenscycluszitting in uw configuratiedossier zou moeten beginnen.

   >[!TIP]
   >
   >Deze methode is bedoeld voor toepassingen die zich registreren voor meldingen op de achtergrond en mag alleen worden aangeroepen vanuit uw code die wordt uitgevoerd terwijl de toepassing op de achtergrond wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analysemethoden {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Haalt de id voor het bijhouden van analyses op.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;titelscherm&#39;, &#39;niveau 1&#39;, &#39;onderbreken&#39; enzovoort. Deze statussen zijn vergelijkbaar met die van pagina&#39;s op een website en `TrackState` roepen increment paginaweergaven aan. Als de status leeg is, wordt deze weergegeven als &#39;app name app version (build)&#39; in rapporten. Als u deze waarde in rapporten ziet, zorg ervoor u staat in elke `TrackState` vraag plaatst.

   [!TIP]
   >Dit is de enige volgende vraag die de paginameningen verhoogt.
   >
   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   Tracks an action in your app. Acties zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;sterfte&#39;, &#39;aangewonnen niveau&#39;, &#39;abonnementen voor diervoeders&#39; en andere maatstaven.

   >[!TIP]
   Als u code hebt die kan worden uitgevoerd terwijl de toepassing zich op de achtergrond bevindt (bijvoorbeeld het ophalen van achtergrondgegevens), gebruikt u `trackActionFromBackground` deze.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (alleen iOS)**

   Tracks an action that occurred in the background. Dit onderdrukt levenscyclusgebeurtenissen van het vuren in bepaalde scenario&#39;s.

   >[!TIP]
   Deze methode mag alleen worden aangeroepen in code die wordt uitgevoerd terwijl de toepassing op de achtergrond wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Verzendt de huidige breedte- en lengtecoördinaten. Gebruikt ook aandachtspunten die in het `ADBMobileConfig.json` bestand zijn gedefinieerd om te bepalen of de locatie die als parameter wordt opgegeven zich binnen een van uw POI-taken bevindt. Als de huidige coördinaten zich binnen bepaalde POI bevinden, wordt een variabele van contextgegevens bevolkt en verzonden met de `TrackLocation` vraag.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   Tracks wanneer een gebruiker nabijheid van een baken ingaat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   Wist beacons gegevens nadat een gebruiker de nabijheid van het baken verlaat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Hiermee voegt u de waarde toe aan de levensduur van de gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      public nbsp;static void TrackLifetimeValueIncrease(dubbele hoeveelheid, NSDictionary-gegevens);

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Een getimede actie starten met een naamactie. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Geef gegevens door om de contextgegevens bij te werken die aan de opgegeven actie zijn gekoppeld. De gegevens die worden doorgegeven, worden toegevoegd aan de bestaande gegevens voor de opgegeven handeling en overschrijft de gegevens als dezelfde toets al voor de handeling is gedefinieerd.

   >[!TIP]
   Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Een getimede actie beëindigen.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      });
      ```

* **TrackingTimedActionExists**

   Retourneert of een getimede actie wordt uitgevoerd (of niet).

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   Hiermee dwingt u de bibliotheek alle treffers in de offline wachtrij te verzenden, ongeacht het aantal dat momenteel in de wachtrij staat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Wist alle treffers van de off-line rij.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Hiermee wordt het aantal treffers opgehaald dat momenteel in de offline wachtrij staat.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Ervaar de methoden van Cloud ID {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   Haalt de Experience Cloud ID op van de ID-service.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Met de Experience Cloud-id kunt u aanvullende klant-id&#39;s instellen die aan elke bezoeker worden gekoppeld. De bezoeker-API accepteert meerdere Customer ID&#39;s voor dezelfde bezoeker, samen met een id voor het klanttype om het bereik van de verschillende klant-id&#39;s te scheiden. Deze methode komt overeen met setCustomerIDs in de JavaScript-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Doelmethoden {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Verzendt verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een `Action<NSDictionary>` callback wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
      Console.WriteLine  (context); 
      });
      ```

* **TargetCreateRequest**

   Een gebruiksvriendelijke constructor om een `ADBTargetLocationRequest` object met de opgegeven parameters te maken.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   Maakt een `ADBTargetLocationRequest`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   Wist doelcookies uit uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Auditiebeheer {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   Retourneert het bezoekersprofiel dat het laatst is verkregen. Retourneert nul als er nog geen signaal is verzonden. Bezoekersprofiel wordt opgeslagen in `NSUserDefaults` zodat u eenvoudig toegang hebt tot meerdere startpagina&#39;s van uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   Retourneert de huidige DPID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static string AudienceDpid ();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   Retourneert de huidige DPUUID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   Hiermee stelt u de dpid en de dpuuid in. Als dpid en dpuuid zijn ingesteld, worden ze samen met elk signaal verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Verzendt publieksbeheer een signaal met eigenschappen en krijgt de passende segmenten die in een `Action<NSDictionary>` callback zijn teruggekeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Hiermee wordt de UUID van publieksmanager opnieuw ingesteld en wordt het huidige bezoekersprofiel leeggemaakt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void AudienceReset ();
      ```

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Zie [Video Analytics](/help/ios/getting-started/dev-qs.md)voor meer informatie.

* **MediaCreateSettings**

   Retourneert een `ADBMediaSettings` object met opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   Retourneert een `ADBMediaSettings` object voor gebruik bij het bijhouden van een advertentievideo.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   Hiermee opent u een `ADBMediaSettings` object dat u wilt bijhouden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   Sluit het media-item genaamd name.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   Hiermee wordt het media-item met de naam name afgespeeld bij de opgegeven verschuiving (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   Markeer het media-item handmatig als voltooid bij de opgegeven verschuiving (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   Hiermee wordt aan de mediamodule gemeld dat de video bij de opgegeven verschuiving is gestopt of gepauzeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   Hiermee wordt aan de mediamodule gemeld dat op het media-item is geklikt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   Hiermee wordt een aanroep van een handeling track verzonden (geen paginaweergave) voor de huidige mediastatus.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```

---
description: Android-methoden voor Xamarin-componenten voor Experience Cloud-oplossingen 4.x SDK.
keywords: Xamarin
seo-description: Android-methoden voor Xamarin-componenten voor Experience Cloud-oplossingen 4.x SDK.
seo-title: Methoden van Android
solution: Marketing Cloud,Developer
title: Methoden van Android
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Methoden van Android{#android-methods}

Android-methoden voor Xamarin-componenten voor Experience Cloud-oplossingen 4.x SDK.

## Configuratiemethoden {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   Retourneert de huidige voorkeur voor foutopsporing en de standaardwaarde is false.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static Boolean DebugLogging;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   Retourneert de levensduurwaarde van de huidige gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   Retourneert de opsomming van de privacystatus voor de huidige gebruiker.
   * `ADBMobilePrivacyStatus.OptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatus.OptOut` - treffers worden genegeerd.
   * `ADBMobilePrivacyStatus.Unknown` - Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (vervolgens worden treffers verzonden) of Afmelden (vervolgens worden treffers verwijderd). Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.
   De standaardwaarde wordt ingesteld in het bestand [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) .

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   Als een aangepaste id is ingesteld, wordt deze id geretourneerd. Als een aangepaste id niet is ingesteld, wordt null geretourneerd. De standaardwaarde is `null`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static UserIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **Versie**

   Hiermee wordt de bibliotheekversie opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string Version;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   Geeft aan de SDK aan dat de app is gepauzeerd, zodat de levenscycluswaarden correct worden berekend. Bij pauzeren wordt bijvoorbeeld een tijdstempel verzameld om de duur van de vorige sessie te bepalen. Hierdoor wordt ook een vlag ingesteld zodat de levenscyclus correct weet dat de app niet vastloopt. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Activiteit)**

   (4.2 of hoger) Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activiteit)**

   (4.2 of hoger) Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 of hoger) Hiermee kunt u een ander `ADBMobile JSON` configuratiebestand laden wanneer de toepassing wordt gestart. De verschillende configuratie wordt gebruikt tot de toepassing wordt gesloten.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   (4.2 of hoger) Hiermee stelt u het grote pictogram in dat wordt gebruikt voor meldingen die door de SDK worden gemaakt. Dit pictogram is de primaire afbeelding die wordt weergegeven wanneer de gebruiker het volledige bericht ziet in het meldingscentrum.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 of hoger) Hiermee stelt u het kleine pictogram in dat wordt gebruikt voor meldingen die door de SDK worden gemaakt. Dit pictogram wordt weergegeven op de statusbalk en is de secundaire afbeelding die wordt weergegeven wanneer de gebruiker het volledige bericht ziet in het meldingscentrum.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analysemethoden {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Retourneert de automatisch gegenereerde id voor Analytics. Dit is een unieke id die specifiek is voor de toepassing en die wordt gegenereerd bij de eerste keer dat de toepassing wordt gestart en die vanaf dat moment wordt opgeslagen en gebruikt. Deze id blijft behouden tussen upgrades van apps en wordt verwijderd bij het verwijderen.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string TrackingIdentifier;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Traceert een toepassingsstatus met optionele contextgegevens. `States` Dit zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;titelscherm&#39;, &#39;niveau 1&#39;, &#39;onderbreken&#39; enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `TrackState` roepen paginaweergaven met meer pagina&#39;s aan. Als de status leeg is, wordt deze weergegeven als &quot;app name app version (build)&quot; in rapporten. Als u deze waarde in rapporten ziet, zorg ervoor u staat in elke `TrackState` vraag plaatst.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   Tracks an action in your app. Acties zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;sterfte&#39;, &#39;aangewonnen niveau&#39;, &#39;abonnementen voor diervoeders&#39; en andere maatstaven.

   >[!TIP]
   >
   >
   >Als u code hebt die kan worden uitgevoerd terwijl de toepassing zich op de achtergrond bevindt (bijvoorbeeld het ophalen van achtergrondgegevens), gebruikt u `trackActionFromBackground` deze.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   Verzendt de huidige breedte- en lengtecoördinaten. Gebruikt ook aandachtspunten die in het `ADBMobileConfig.json` dossier worden bepaald of de plaats die als parameter werd verstrekt in om het even welk van uw POIs is. Als de huidige coördinaten zich in een bepaalde POI bevinden, wordt een variabele van contextgegevens gevuld en met de `TrackLocation` vraag verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   Tracks wanneer een gebruiker nabijheid van een baken ingaat.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   Wist beacons gegevens nadat een gebruiker de nabijheid van het baken verlaat.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   Hiermee voegt u een bedrag toe aan de levensduurwaarde van de gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   Een getimede actie starten met een naamactie. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   > Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Geef gegevens door om de contextgegevens bij te werken die aan de opgegeven actie zijn gekoppeld. De gegevens die worden doorgegeven, worden toegevoegd aan de bestaande gegevens voor de opgegeven handeling en overschrijft de gegevens als dezelfde toets al voor de handeling is gedefinieerd.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Een getimede actie beëindigen.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   Retourneert of een getimede actie wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Hiermee dwingt u de bibliotheek alle treffers in de offline wachtrij te verzenden, ongeacht het aantal treffers dat momenteel in de wachtrij wordt geplaatst.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SendQueuedHits();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   Wist alle treffers van de off-line rij.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void ClearQueue(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   Hiermee wordt het aantal treffers opgehaald dat zich momenteel in de offline wachtrij bevindt.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static long QueueSize(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Ervaar de methoden van Cloud ID {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Haalt de Experience Cloud ID op van de ID-service.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string MarketingCloudId;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Met de Experience Cloud-id kunt u aanvullende klant-id&#39;s instellen die aan elke bezoeker worden gekoppeld. De bezoeker-API accepteert meerdere klant-id&#39;s voor dezelfde bezoeker, met een id voor het klanttype om het bereik van de verschillende klant-id&#39;s te scheiden. Deze methode komt overeen met `setCustomerIDs` in de JavaScript-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Doelmethoden {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Verzendt een verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een `Action<NSDictionary>` callback wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   Een gebruiksvriendelijke constructor om een `ADBTargetLocationRequest` object met de opgegeven parameters te maken.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   Maakt een `ADBTargetLocationRequest`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   Wist doelcookies uit uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void ClearCookies(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Target.ClearCookies (); 
      ```

## Auditiebeheer {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **Bezoekerprofiel**

   Retourneert het bezoekersprofiel dat het laatst is verkregen. Retourneert nul als er nog geen signaal is verzonden. Het bezoekersprofiel wordt opgeslagen in `NSUserDefaults` zodat u eenvoudig toegang hebt tot meerdere startpagina&#39;s van uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Retourneert de huidige `DPID`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string Dpuuid; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Retourneert de huidige `DPUUID`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Hiermee stelt u de `dpid` en `dpuuid`. Als `dpid` en `dpuuid` worden geplaatst, worden zij verzonden met elk signaal.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Verzendt publieksbeheer een signaal met eigenschappen en krijgt de passende segmenten die in een `Action<NSDictionary>` callback zijn teruggekeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **Herstellen**

   Hiermee wordt het profiel van de publieksmanager opnieuw ingesteld `UUID` en het huidige bezoekersprofiel opgeschoond.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Reset ();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
       AudienceManager.Reset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Zie [Video Analytics](/help/android/analytics-main/video-qs.md)voor meer informatie over Video Analytics.

* **MediaSettings**

   Retourneert een `MediaSettings` object met opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   Retourneert een `MediaSettings` object voor gebruik bij het bijhouden van een advertentievideo.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Open**

   Hiermee opent u een `ADBMediaSettings` object dat u wilt bijhouden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **Sluiten**

   Sluit het media-item genaamd name.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Close(string name);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.Close (settings.Name); 
      ```

* **Afspelen**

   Hiermee wordt het media-item met de naam name afgespeeld bij de opgegeven verschuiving (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Voltooid**

   Markeer het media-item handmatig als voltooid bij de opgegeven verschuiving (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stoppen**

   Hiermee wordt aan de mediamodule gemeld dat de video bij de opgegeven verschuiving is gestopt of gepauzeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Klik op**

   Hiermee wordt aan de mediamodule gemeld dat op het media-item is geklikt.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Track**

   Hiermee wordt een aanroep van een handeling track verzonden (geen paginaweergave) voor de huidige mediastatus.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.Track (settings.Name, null); 
      ```
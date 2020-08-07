---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Methoden van ADBMobile.cs
solution: Marketing Cloud,Developer
title: Methoden van ADBMobile.cs
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 35%

---


# Methoden van ADBMobile.cs {#adbmobile-cs-methods}

## Configuratiemethoden

* **CollectLifecycleData**

   Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/ios/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void CollectLifecycleData();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications (alleen iOS)**

   Schakel lokale meldingen in uw app in.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void EnableLocalNotifications();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.EnableLocalNotifications();
      ```

* **GetDebugLogging**

   Retourneert de huidige voorkeur voor foutopsporing. De standaardwaarde is `false`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static bool GetDebugLogging();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   Retourneert de levensduurwaarde van de huidige gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static double GetLifetimeValue();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   Retourneert de opsomming van de privacystatus voor de huidige gebruiker.
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: De berichten worden onmiddellijk verzonden.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Hits worden weggegooid.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de privacystatus verandert in een aanmeldingsnaam (dan worden treffers verzonden) of een uitschakelfunctie (dan worden treffers genegeerd).

      Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden. De standaardwaarde wordt ingesteld in het bestand [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) .

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Retourneert de aangepaste gebruikers-id als er een aangepaste id is ingesteld. Retourneert null als er geen aangepaste id is ingesteld. De standaardwaarde is `null`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string GetUserIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var userId = ADBMobile.GetUserIdentifier();
      ```

* **GetVersion**

   Hiermee wordt de bibliotheekversie opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string GetVersion();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive (alleen iOS)**

   Wijst aan SDK erop dat uw volgende hervat van achtergrond geen nieuwe zitting, ongeacht de waarde van de tijd van de levenscycluszitting in uw configuratiedossier zou moeten beginnen.

   >[!TIP]
   >
   >Deze methode is bedoeld voor toepassingen die zich registreren voor meldingen terwijl ze zich op de achtergrond bevinden en mag alleen worden aangeroepen vanuit de code die wordt uitgevoerd terwijl de toepassing op de achtergrond wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData (alleen Android)**

   Geeft aan de SDK aan dat de app is gepauzeerd, zodat de levenscycluswaarden correct worden berekend. Bij pauzeren wordt bijvoorbeeld een tijdstempel verzameld om de duur van de vorige sessie te bepalen. Hierdoor wordt ook een vlag ingesteld zodat de levenscyclus correct weet dat de app niet vastloopt. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (alleen Android)**

   Geeft aan de SDK door dat de toepassingscontext moet worden ingesteld vanuit de huidige activiteit van de UnityPlayer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SetContext();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   Hiermee stelt u de voorkeur voor foutopsporing in op ingeschakeld.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   Hiermee stelt u de privacystatus voor de huidige gebruiker in op status. Stel een van de volgende waarden in:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: De berichten worden onmiddellijk verzonden.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Hits worden weggegooid.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de privacystatus verandert in een aanmeldingsnaam (dan worden treffers verzonden) of een uitschakelfunctie (dan worden treffers genegeerd). Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * Hier is het codevoorbeeld voor deze syntaxis:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Hiermee wordt de gebruikersnaam ingesteld op userId.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Analysemethoden

* **GetTrackingIdentifier**

   Haalt de id voor het bijhouden van analyses op.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string GetTrackingIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier();
      ```

* **TrackState**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;titelscherm&#39;, &#39;niveau 1&#39;, &#39;onderbreken&#39; enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `TrackState` roepen paginaweergaven met meer pagina&#39;s aan.

   Als de status leeg is, wordt deze weergegeven zoals *`app name app version (build)`* in rapporten. Als u deze waarde in rapporten ziet, zorg ervoor u staat in elke `TrackState` vraag plaatst.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var contextData = new Dictionary<string, object>);
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   Tracks an action in your app. Acties zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;sterfte&#39;, &#39;aangewonnen niveau&#39;, &#39;abonnementen voor diervoeders&#39; en andere maatstaven.

   >[!TIP]
   >
   >Als u code hebt die kan worden uitgevoerd terwijl de toepassing zich op de achtergrond bevindt (bijvoorbeeld het ophalen van achtergrondgegevens), gebruikt u `trackActionFromBackground` deze.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground (alleen iOS)**

   Tracks an action that occurred in the background. Dit onderdrukt levenscyclusgebeurtenissen van het vuren in bepaalde scenario&#39;s.

   >[!TIP]
   >
   >Deze methode mag alleen worden aangeroepen in code die wordt uitgevoerd terwijl de toepassing op de achtergrond wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Verzendt de huidige breedte- en lengtecoördinaten. Gebruikt ook aandachtspunten die in het `ADBMobileConfig.json` bestand zijn gedefinieerd om te bepalen of de locatie die als parameter wordt opgegeven zich binnen een van uw POI-taken bevindt. Als de huidige coördinaten binnen bepaalde POI zijn, wordt een variabele van contextgegevens bevolkt en verzonden met de vraag TrackLocation.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null);
      ```

* **TrackBeacon**

   Tracks wanneer een gebruiker nabijheid van een baken ingaat.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata);
      ```

* **TrackingClearCurrentBeacon**

   Wist beacons gegevens nadat een gebruiker de nabijheid van het baken verlaat.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Hiermee voegt u de waarde toe aan de levensduur van de gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null);
      ```

* **TrackTimedActionStart**

   Een getimede actie starten met een naamactie. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Geef gegevens door om de contextgegevens bij te werken die aan de opgegeven actie zijn gekoppeld. De gegevens die worden doorgegeven, worden toegevoegd aan de bestaande gegevens voor de opgegeven handeling en overschrijft de gegevens als dezelfde toets al voor de handeling is gedefinieerd.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var contextData = new Dictionary<string, object>;
      contextData.Add("checkpoint", "1:32");
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   Een getimede actie beëindigen.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackTimedActionEnd(string action);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackTimedActionEnd("level2");
      ```

* **TrackingTimedActionExists**

   Retourneert of een getimede actie wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static bool TrackingTimedActionExists(string action);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2");
      ```

* **TrackingSendQueuedHits**

   Hiermee dwingt u de bibliotheek alle treffers in de offline wachtrij te verzenden, ongeacht het aantal dat momenteel in de wachtrij staat.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackingSendQueuedHits();
      ```

* **TrackingClearQueue**

   Wist alle treffers van de off-line rij.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void TrackingClearQueue();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Hiermee wordt het aantal treffers opgehaald dat momenteel in de offline wachtrij staat.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static int TrackingGetQueueSize();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Methoden van Experience Cloud ID

* **GetMarketingCloudID**

   Haalt de Experience Cloud-id op van de id-service.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static string GetMarketingCloudID();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Met de Experience Cloud-id kunt u aanvullende klant-id&#39;s instellen die aan elke bezoeker worden gekoppeld. De bezoeker-API accepteert meerdere Customer ID&#39;s voor dezelfde bezoeker, samen met een id voor het klanttype om het bereik van de verschillende klant-id&#39;s te scheiden. Deze methode komt overeen met setCustomerIDs in de JavaScript-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      var ids = new Dictionary<string, object> ();
      ids.Add ("player1", "jimbob");
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

## Verwervingsmethoden

* **ProcessGooglePlayInstallReferrerUrl** *(alleen Android)*

   Geef de URL van de referentie die door een aanroep van de Google Play-installatieverwijzing naar deze methode is geretourneerd, door.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```

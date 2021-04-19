---
description: Informatie die u helpt bij het gebruik van de Windows 8.1 Universal App Store SDK met Adobe Analytics.
seo-description: Informatie die u helpt bij het gebruik van de Windows 8.1 Universal App Store SDK met Adobe Analytics.
seo-title: Analysemethoden
solution: Experience Cloud,Analytics
title: Analysemethoden
topic-fix: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
exl-id: 007bb801-55ef-4c5b-87fa-d0db42cde163
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 26%

---

# Analysemethoden {#analytics-methods}

Informatie die u helpt bij het gebruik van de Windows 8.1 Universal App Store SDK met Adobe Analytics.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target en Audience Manager. Methoden worden vooraf bepaald volgens de oplossing. Analysemethoden worden voorafgegaan door &quot;Analytics&quot;.

Elk van deze methoden wordt gebruikt om gegevens naar uw Adobe Analytics-rapportenpakket te verzenden.

>[!TIP]
>
>Wanneer u `winmd` methodes van winJS (JavaScript) gebruikt, hebben alle methodes automatisch hun eerste brief verminderd.

* **TrackState (winJS: trackState)**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;thuisdashboard&#39;, &#39;app-instellingen&#39;, &#39;winkelwagentje&#39; enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `TrackState` roept de weergave van de verhogende pagina op. Als `state` leeg is, wordt deze weergegeven als &quot;app name app version (build)&quot; in rapporten. Als u deze waarde in rapporten ziet, zorg ervoor u `state` in elke `TrackState` vraag plaatst.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS: trackAction)**

   Tracks an action in your app. Handelingen zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;logons&#39;, &#39;bannertiketten&#39;, &#39;feed-abonnementen&#39; en andere meetwaarden.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **GetTrackingIdentifierAsync (winJS: getTrackingIdentifierAsync)**

   Retourneert de automatisch gegenereerde bezoeker-id voor Analytics. Dit is een app-specifieke unieke bezoeker-id die bij de eerste keer starten wordt gegenereerd en vervolgens vanaf dat moment wordt opgeslagen en gebruikt. Deze id blijft behouden tussen upgrades van apps en wordt verwijderd bij het verwijderen.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **TrackLocation (winJS: trackLocation)**

   Verzendt de huidige x y-coördinaten. Gebruikt ook punten van belang die in het `ADBMobileConfig.json` dossier worden bepaald om te bepalen als de plaats die als parameter wordt verstrekt binnen om het even welk van uw POI is. Als de huidige coördinaten binnen een bepaalde POI zijn, wordt een variabele van contextgegevens bevolkt en verzonden met `trackLocation` vraag.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **TrackLifetime &#x200B; ValueIncrease (winJS: trackLifetime &#x200B; ValueIncrease)**

   Voegt `amount` aan de levenwaarde van de gebruiker toe.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **TrackTimed &#x200B; ActionStart (winJS: trackTimed &#x200B; ActionStart)**

   Start een getimede actie met de naam `action`. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS: trackTimed &#x200B; ActionUpdate)**

   Geef `contextData` door om de contextgegevens bij te werken die aan gegeven `action` worden geassocieerd. De `data` gegeven wordt toegevoegd aan de bestaande gegevens voor de bepaalde actie, en beschrijft de gegevens als de zelfde sleutel reeds voor `action` wordt bepaald.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **TrackTimedActionExistsAsync (winJS: trackTimedActionExistsAsync)**

   Retourneert true als de opgegeven tijdactie bestaat en false als dit niet het geval is.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd (winJS: trackTimed &#x200B; ActionEnd)**

   Een getimede actie beëindigen.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Hiermee wist u alle opgeslagen resultaten uit de wachtrij Analytics tracking.

   * Hier volgt de syntaxis voor dit bericht:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Hier volgt het codevoorbeeld:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS: getQueueSizeAsync)**

   Retourneert het aantal resultaten dat momenteel is opgeslagen in de wachtrij Analytics.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```

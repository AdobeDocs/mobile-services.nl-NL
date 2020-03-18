---
description: Informatie die u helpt bij het gebruik van de Universal Windows Platform SDK met Adobe Analytics.
seo-description: Informatie die u helpt bij het gebruik van de Universal Windows Platform SDK met Adobe Analytics.
seo-title: Analysemethoden
solution: Marketing Cloud,Analytics
title: Analysemethoden
topic: Developer and implementation
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analysemethoden {#analytics-methods}

Informatie die u helpt bij het gebruik van de Universal Windows Platform SDK met Adobe Analytics.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target en Audience Manager. Methoden worden vooraf bepaald volgens de oplossing. Analysemethoden worden voorafgegaan door &quot;Analytics&quot;.

Elk van deze methoden wordt gebruikt om gegevens naar uw Adobe Analytics-rapportensuite te verzenden.

>[!TIP]
>
>Wanneer u methoden van winJS (JavaScript) gebruikt, wordt de eerste letter van alle methoden automatisch verlaagd. `winmd`

* **TrackState (winJS: trackState)**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;thuisdashboard&#39;, &#39;app-instellingen&#39;, &#39;winkelwagentje&#39; enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `TrackState` roepen paginaweergaven met meer pagina&#39;s aan.
Als de app leeg `state` is, wordt deze weergegeven als &quot;app name app version (build)&quot; in rapporten. Als u deze waarde in rapporten ziet, zorg ervoor u `state` in elke `TrackState` vraag plaatst.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS: trackAction)**

   Tracks an action in your app. Handelingen zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;logons&#39;, &#39;bannertiketten&#39;, &#39;feed-abonnementen&#39; en andere meetwaarden.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync (winJS: getTrackingIdentifierAsync)**

   Retourneert de automatisch gegenereerde bezoeker-id voor Analytics. Dit is een unieke bezoeker-id die specifiek is voor de app en die wordt gegenereerd bij de eerste keer starten en vervolgens wordt opgeslagen en vanaf dat moment wordt gebruikt. Deze id blijft behouden tussen upgrades van apps en wordt verwijderd bij het verwijderen.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation (winJS: trackLocation)**

   Verzendt de huidige x y-coördinaten. Gebruikt ook aandachtspunten die in het `ADBMobileConfig.json` bestand zijn gedefinieerd om te bepalen of de locatie die als parameter wordt opgegeven zich binnen een van uw POI-taken bevindt. Als de huidige coördinaten zich binnen bepaalde POI bevinden, wordt een variabele van contextgegevens bevolkt en verzonden met de `trackLocation` vraag.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime &#x200B; ValueIncrease (winJS: trackLifetime &#x200B; ValueIncrease)**

   Hiermee voegt u `amount` de levensduurwaarde van de gebruiker toe.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed &#x200B; ActionStart (winJS: trackTimed &#x200B; ActionStart)**

   Start een getimede actie met naam `action`. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS: trackTimed &#x200B; ActionUpdate)**

   Geef aan `contextData` om de contextgegevens bij te werken die aan de opgegeven gegevens zijn gekoppeld `action`. De `data` doorgegeven code wordt toegevoegd aan de bestaande gegevens voor de opgegeven actie en overschrijft de gegevens als dezelfde sleutel al is gedefinieerd voor `action`.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync (winJS: trackTimedActionExistsAsync)**

   Retourneert true als de opgegeven getimede actie bestaat en false als deze niet bestaat.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
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
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Hiermee wist u alle opgeslagen resultaten uit de wachtrij Analytics tracking.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

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
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```

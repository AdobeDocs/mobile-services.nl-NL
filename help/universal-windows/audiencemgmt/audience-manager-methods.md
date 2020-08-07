---
description: Lijst met methoden voor Audience Managers die worden geleverd door de Universal Windows Platform-bibliotheek.
seo-description: Lijst met methoden voor Audience Managers die worden geleverd door de Universal Windows Platform-bibliotheek.
seo-title: Methoden van Audience Manager
solution: Marketing Cloud,Analytics
title: Methoden van Audience Manager
topic: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 27%

---


# Methoden van Audience Manager{#audience-manager-methods}

Lijst met methoden voor Audience Managers die worden geleverd door de Universal Windows Platform-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target en Audience Manager. Methoden worden vooraf bepaald volgens de oplossing. Methoden van Audience Managers hebben de voorkeur `AudienceManager`.

>[!TIP]
>
>Wanneer u methoden van winJS (JavaScript) gebruikt, wordt de eerste letter van alle methoden automatisch verlaagd. `winmd`

Als publieksbeheer is geconfigureerd in uw JSON-bestand, wordt een signaal dat levenscyclusmetriek bevat verzonden met uw hit tijdens de levenscyclus.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Retourneert het bezoekersprofiel dat het laatst is verkregen. Retourneert `null` of nog geen signaal is verzonden. Bezoekersprofiel wordt opgeslagen in `SharedPreferences` zodat u eenvoudig toegang hebt tot meerdere startpagina&#39;s van uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS: getDpid)**

   Retourneert de huidige DPID.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      var dpid = ADB.AudienceManager.getDpid(); 
      ```

* **GetDpuuid (winJS: getDpuuid)**

   Retourneert de huidige DPUUID.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid (winJS: setDpidAndDpuuid)**

   Hiermee stelt u de DPID en DPUUID in. Als DPID en DPUUID worden geplaatst, zullen zij met elk signaal worden verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS: signaalWithData)**

   Verzendt publieksbeheer een signaal met eigenschappen en krijgt de passende segmenten die in een blokcallback worden teruggekeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      });
      ```

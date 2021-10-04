---
description: Lijst met methoden voor Audience Managers die worden geleverd door de Universal Windows Platform-bibliotheek.
solution: Experience Cloud,Analytics
title: Methoden van Audience Manager
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 28%

---

# Methoden van Audience Manager{#audience-manager-methods}

Lijst met methoden voor Audience Managers die worden geleverd door de Universal Windows Platform-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target en Audience Manager. Methoden worden vooraf bepaald volgens de oplossing. Methoden van Audience Managers worden voorafgegaan door `AudienceManager`.

>[!TIP]
>
>Wanneer u `winmd` methodes van winJS (JavaScript) gebruikt, hebben alle methodes automatisch hun eerste brief verminderd.

Als publieksbeheer is geconfigureerd in uw JSON-bestand, wordt een signaal dat levenscyclusmetriek bevat verzonden met uw hit tijdens de levenscyclus.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Retourneert het bezoekersprofiel dat het laatst is verkregen. Retourneert `null` als er nog geen signaal is verzonden. Bezoekersprofiel wordt opgeslagen in `SharedPreferences` voor eenvoudige toegang bij meerdere keren starten van uw app.

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

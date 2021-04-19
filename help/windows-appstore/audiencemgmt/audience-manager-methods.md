---
description: Lijst met methoden voor Audience Managers die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.
seo-description: Lijst met methoden voor Audience Managers die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.
seo-title: Methoden van Audience Manager
solution: Experience Cloud,Analytics
title: Methoden van Audience Manager
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 26%

---

# Methoden van Audience Manager {#audience-manager-methods}

Lijst met methoden voor Audience Managers die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target en Audience Manager. Methoden worden vooraf bepaald volgens de oplossing. Methoden van Audience Managers worden vooraf vastgelegd met &quot;AudienceManager&quot;.

>[!NOTE]
>
>Wanneer u winde methodes van winJS (JavaScript) gebruikt, hebben alle methodes automatisch hun eerste brief verminderd.

Als publieksbeheer is geconfigureerd in uw JSON-bestand, wordt een signaal met levenscyclusmetriek verzonden bij een hit tijdens de levenscyclus.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Retourneert het bezoekersprofiel dat het laatst is verkregen. Retourneert `null` als er nog geen signaal is verzonden. Bezoekersprofiel wordt opgeslagen in `SharedPreferences` voor eenvoudige toegang bij meerdere keren starten van uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
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

   Verzendt Audience Manager een signaal met eigenschappen en krijgt de passende segmenten die in een blokcallback zijn teruggekeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

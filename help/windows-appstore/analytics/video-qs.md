---
description: Informatie die u helpt met Video Analytics.
seo-description: Informatie die u helpt met Video Analytics.
seo-title: Video Analytics
solution: Marketing Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 15%

---


# Video Analytics {#video-analytics}

Informatie die u helpt met Video Analytics.

Videometingen worden gedetailleerd beschreven in de handleiding [Metingaudio en -video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html/) . Het algemene proces voor het meten van video lijkt op dat voor alle AppMeasurement-platforms. Deze snelle beginsectie verstrekt een basisoverzicht van de ontwikkelaarstaken samen met codesteekproeven.

In de volgende tabel worden de mediagegevens weergegeven die naar Analytics worden verzonden. Gebruik verwerkingsregels om de contextgegevens toe te wijzen aan een Analytics-variabele.

* **a.media.name**

   (Vereist) Verzamelt de naam van de video, zoals opgegeven in de implementatie, wanneer een bezoeker de video op een of andere manier bekijkt. U kunt classificaties toevoegen voor deze variabele.

   (**Optioneel**) De variabele Custom Insight biedt informatie over het plakken van video&#39;s.

   * Type variabele: eVar
   * Standaardvervaldatum: Bezoek
   * Custom Insight (s.prop, gebruikt voor videoverven)

* **a.media.name**

   (Optioneel) Bevat informatie over het plakken van video. Het plakken moet voor deze variabele door ClientCare worden toegelaten.

   Type gebeurtenis: Custom Insight (s.prop)

   * Type variabele: Custom Insight (s.prop)

* **a.media.segment**

   (Vereist) Verzamelt videosegmentgegevens, met inbegrip van de segmentnaam en de orde waarin het segment in de video voorkomt. Deze variabele wordt gevuld door de `segmentByMilestones` variabele in te schakelen wanneer spelergebeurtenissen automatisch worden bijgehouden, of door een aangepaste segmentnaam in te stellen wanneer spelergebeurtenissen handmatig worden bijgehouden. Wanneer een bezoeker bijvoorbeeld het eerste segment in een video bekijkt, verzamelt SiteCatalyst het volgende in het `1:M:0-25` segment Var.

   De standaardmethode voor het verzamelen van videogegevens verzamelt gegevens op de volgende punten:

   * video starten (afspelen)
   * begin segment
   * videoeinde (stoppen)
   Analytics telt de eerste segmentweergave bij het begin van het segment, wanneer de bezoeker begint te kijken. Volgende segmentweergaven als het segment begint.

   * Type variabele: eVar
   * Standaardvervaldatum: Paginaweergave


* **a.contentType**

   Hiermee worden gegevens verzameld over het type inhoud dat door een bezoeker wordt weergegeven. Aan door videometing verzonden berichten wordt een inhoudstype &quot;video&quot; toegewezen. Deze variabele hoeft niet uitsluitend voor videotracering te worden gereserveerd. Als u andere inhoudsrapportinhoudstypen gebruikt met dezelfde variabele, kunt u de distributie van bezoekers over de verschillende typen inhoud analyseren. U kunt bijvoorbeeld andere inhoudstypen labelen met waarden zoals &quot;artikel&quot; of &quot;productpagina&quot; met deze variabele. Vanuit een videomeetperspectief kunt u met het inhoudstype videobezoekers identificeren en de videoconversiesnelheden berekenen.

   * Type variabele: eVar
   * Standaardvervaldatum: Paginaweergave

* **a.media.timePlayed**

   Telt de tijd, in seconden, besteed aan het bekijken van een video sinds het laatste proces van de gegevensinzameling (beeldverzoek).

   * Type variabele: Gebeurtenis
   * Type: Teller

* **a.media.view**

   Geeft aan dat een bezoeker een gedeelte van een video heeft weergegeven. Het biedt echter geen informatie over hoeveel of welk deel van een video de bezoeker heeft bekeken.

   * Variabele: Gebeurtenis
   * Type: Teller

* **a.media.segmentView**

   Geeft aan dat een bezoeker een gedeelte van een videosegment heeft weergegeven. Het biedt echter geen informatie over hoeveel of welk deel van een video de bezoeker heeft bekeken.

   * Type variabele: Gebeurtenis
   * Type: Teller

* **a.media.complete**

   Geeft aan dat een gebruiker een volledige video heeft weergegeven. Standaard wordt de complete-gebeurtenis 1 seconde voor het einde van de video gemeten. Tijdens de implementatie kunt u opgeven hoeveel seconden vanaf het einde van de video u een volledige weergave wilt overwegen. Voor live video en andere streams zonder gedefinieerd einde kunt u een aangepast punt opgeven om de voltooiing te meten. Bijvoorbeeld na een bepaalde tijd die is weergegeven.

   * Type variabele: Gebeurtenis
   * Type: Teller


## Media-instellingen configureren {#section_929945D4183C428AAF3B983EFD3E2500}

Configureer een `MediaSettings` object met de instellingen die u wilt gebruiken voor het bijhouden van video:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Gebeurtenissen van speler bijhouden {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Om het afspelen van video te meten, moeten de methoden `Play`, `Stop`en `Close` The op de juiste momenten worden aangeroepen. Wanneer de speler bijvoorbeeld wordt gepauzeerd, `Stop`. `Play` wordt aangeroepen wanneer het afspelen begint of wordt hervat.

## Klassen {#section_16838332727348F990305C0C6B0D795C}

### Klasse: MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## Mediummeetklasse en methodeverwijzing {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS: settingsWith)**

   Retourneert een `MediaSetting` object met opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS: adSettingsWith**

   Retourneert een `MediaSettings` object voor gebruik bij het bijhouden van een advertentievideo.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Open (winJS: open)**

   Hiermee worden media bijgehouden die zijn geopend met de instellingen die zijn gedefinieerd in `settings`.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Close (winJS: sluiten)**

   Houdt een media dicht voor het media punt genoemd *naam* bij.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.Media.close("mediaName");
      ```

* **Play (winJS: afspelen)**

   Volgt een media spel voor het media punt genoemd *`name`* bij de bepaalde *compensatie* (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Voltooid (winJS: complete)**

   Markeer het media-item handmatig als voltooid bij de opgegeven *verschuiving* (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **Stop (winJS: stop)**

   Meldt aan de mediamodule dat de video is gestopt of gepauzeerd bij de opgegeven *verschuiving*.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **Klikken (winJS: klikken)**

   Hiermee wordt aan de mediamodule gemeld dat op het media-item is geklikt.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winJS: track)**

   Hiermee wordt een aanroep van een handeling track verzonden (geen paginaweergave) voor de huidige mediastatus.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.Media.track("mediaName", null);
      ```


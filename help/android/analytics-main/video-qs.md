---
description: Hier volgt informatie over het meten van video's op Android met de video-meetoplossing.
keywords: android;library;mobile;sdk
seo-description: Hier volgt informatie over het meten van video's op Android met de video-meetoplossing.
seo-title: Video Analytics
solution: Marketing Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Video Analytics {#video-analytics}

Hier volgt informatie over het meten van video&#39;s op Android met de video-meetoplossing.

>[!TIP]
>
>Tijdens het afspelen van video worden vaak &#39;hartslagaanroepen&#39; naar deze service verzonden om de afspeeltijd te meten. Deze hartslagvraag wordt verzonden om de 10 seconden, wat in korrelige videobetrokkenheidsmetriek en nauwkeurigere video neerslagrapporten resulteert. Zie Audio en video [meten in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)voor meer informatie over de meetoplossing voor video&#39;s van Adobe.

Het algemene proces voor het meten van video is op alle platforms vergelijkbaar. Deze inhoud biedt een overzicht van de ontwikkelaarstaken met codevoorbeelden. In de volgende tabel worden de mediagegevens weergegeven die naar Analytics worden verzonden. De regels van de verwerking worden gebruikt om de contextgegevens aan een variabele van de Analyse in kaart te brengen.

## Gebeurtenissen van speler toewijzen aan variabelen van Analyse {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Type variabele: eVar
      * Standaardvervaldatum: Bezoek
      * Aangepast inzicht (s.prop, wordt gebruikt voor videotekenen)
   * (**Vereist**) Wanneer een bezoeker de video op een of andere manier bekijkt, verzamelt deze contextgegevensvariabele de naam van de video, zoals opgegeven in de implementatie. U kunt classificaties toevoegen voor deze variabele.
   * (**Optioneel**) De variabele Aangepast inzicht biedt informatie over het plakken van video.

* **a.media.name**
   * Type variabele: Aangepast inzicht (s.prop)
   * (**Optioneel**) Bevat informatie over het plakken van video.

      >[!IMPORTANT]
      >
      >Pathing moet voor deze variabele door ExpCare worden toegelaten.
   * Type gebeurtenis: Aangepast inzicht (s.prop)

* **a.media.segment**
   * Type variabele: eVar
   * Standaardvervaldatum: Paginaweergave
   * (**Vereist**) Verzamelt videosegmentgegevens, met inbegrip van de segmentnaam en de orde waarin het segment in de video voorkomt.

      Deze variabele wordt gevuld door de `segmentByMilestones` variabele in te schakelen bij het automatisch bijhouden van spelergebeurtenissen of door een aangepaste segmentnaam in te stellen bij het handmatig bijhouden van spelergebeurtenissen. Wanneer een bezoeker bijvoorbeeld het eerste segment in een video weergeeft, kan SiteCatalyst het volgende verzamelen in de Segmenten Var: `1:M:0-25`.

      De standaardmethode voor het verzamelen van videogegevens verzamelt gegevens op de volgende punten:

      * video starten (afspelen)
      * begin segment
      * videoeinde (stoppen)
      Analytics telt de eerste segmentmening bij het begin van het segment, wanneer de bezoeker begint te letten. Volgende segmentweergaven als het segment begint.


* **a.contentType**
   * Type variabele: eVar
   * Standaardvervaldatum: Paginaweergave
   * Verzamelt gegevens over het type inhoud dat door een bezoeker wordt bekeken.

      Aan de door videometing verzonden opdrachten wordt een inhoudstype `video`toegewezen. Vanuit het oogpunt van videometing kunt u met **Inhoudstype** videobezoekers identificeren en de videoconversiesnelheden berekenen.

* **a.media.timePlayed**
   * Type variabele: Gebeurtenis
   * Type: Teller
   * Telt de tijd, in seconden, die wordt besteed aan het bekijken van een video sinds het laatste proces van de gegevensinzameling (beeldverzoek).

* **a.media.view**
   * Type variabele: Gebeurtenis
   * Type: Teller
   * Geeft aan dat een bezoeker een gedeelte van een video heeft weergegeven.

      Het biedt echter geen informatie over hoeveel of welk deel van een video de bezoeker heeft bekeken.

* **a.media.segmentView**
   * Type variabele: Gebeurtenis
   * Type: Teller
   * Geeft aan dat een bezoeker een gedeelte van een videosegment heeft weergegeven.

      Het biedt echter geen informatie over hoeveel of welk deel van een video de bezoeker heeft bekeken.

* **a.media.complete**
   * Type variabele: Gebeurtenis
   * Type: Teller
   * Geeft aan dat een gebruiker een volledige video heeft weergegeven.

      Standaard wordt de complete-gebeurtenis 1 seconde voor het einde van de video gemeten. Tijdens de implementatie kunt u opgeven hoeveel seconden vanaf het einde van de video u een weergave als voltooid wilt beschouwen. Voor live video en andere streams zonder een bepaald einde kunt u een aangepast punt opgeven om de voltooiing te meten (bijvoorbeeld na een bepaalde weergegeven tijd).


## Media-instellingen configureren {#section_929945D4183C428AAF3B983EFD3E2500}

Configureer een `MediaSettings` object met de instellingen die u wilt gebruiken voor het bijhouden van video:

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Gebeurtenissen van speler bijhouden {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Als u het afspelen van video wilt meten, moeten de methoden `mediaPlay`, `mediaStop`en `mediaClose` methoden op de juiste momenten worden aangeroepen. Roep de speler bijvoorbeeld aan wanneer de speler is gepauzeerd `mediaStop`. `mediaPlay` wordt aangeroepen wanneer het afspelen begint of wordt hervat.

## Klassen {#section_16838332727348F990305C0C6B0D795C}

**Klasse: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**Klasse: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Media Measurement, klasse en methodereferentie {#section_50DF9359A7B14DF092634C8E913C77FE}

Hier volgen de methoden in de Media Measurement-klasse:

* **settingsWith**

   Retourneert een `MediaSettings` object met opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   Retourneert een `MediaSettings` object voor gebruik bij het bijhouden van een advertentievideo.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   Hiermee opent u een `MediaSettings` object dat u wilt bijhouden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      Sluit het media-item genaamd *name*.

      * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void close(String name);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.close("name"); 
      ```


* **play**
   * Hiermee wordt het media-item met de naam *name* in de opgegeven *verschuiving* in seconden afgespeeld.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **complete**

   Markeer het media-item handmatig als voltooid bij de *verschuiving* in seconden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void complete(String name, double offset); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.complete("name", 0); 
      ```

* **stoppen**

   Meldt aan de mediamodule dat de video is gestopt of gepauzeerd bij de opgegeven *verschuiving*.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void stop(String name, double offset); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.stop("name", 0);
      ```

* **klikken**

   Hiermee wordt aan de mediamodule gemeld dat op het media-item is geklikt.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void click(String name double offset); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.click("name", 0);
      ```

* **track**

   Hiermee wordt een aanroep van een handeling track verzonden (geen paginaweergave) voor de huidige mediastatus.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Media.track("name", null); 
      ```

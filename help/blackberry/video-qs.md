---
description: Het algemene proces voor het meten van video lijkt op dat voor alle AppMeasurement-platforms. Deze sectie verstrekt een basisoverzicht van de ontwikkelaarstaken samen met codesteekproeven.
seo-description: Het algemene proces voor het meten van video lijkt op dat voor alle AppMeasurement-platforms. Deze sectie verstrekt een basisoverzicht van de ontwikkelaarstaken samen met codesteekproeven.
seo-title: Video Analytics
title: Video Analytics
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Video Analytics {#video-analytics}

Het algemene proces voor het meten van video lijkt op dat voor alle AppMeasurement-platforms. Deze sectie verstrekt een basisoverzicht van de ontwikkelaarstaken samen met codesteekproeven.

Raadpleeg de handleiding [Metingaudio en video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) voor meer informatie over Videometing.  In de volgende tabel worden de mediagegevens weergegeven die naar Analytics worden verzonden. Gebruik verwerkingsregels om de contextgegevens in de kolom Contextgegevensvariabele toe te wijzen aan een variabele Analytics, zoals wordt beschreven in de kolom Type variabele.

## Gebeurtenissen van speler toewijzen aan variabelen van Analyse

* **a.media.name**

   (Vereist) Verzamelt de naam van de video, zoals opgegeven in de implementatie, wanneer een bezoeker de video op een of andere manier bekijkt. U kunt classificaties toevoegen voor deze variabele.

   **(Optioneel)** De variabele Aangepast inzicht biedt informatie over het plakken van video.

   * Naam variabele: eVar
      * Standaardvervaldatum: Bezoek
      * Aangepast inzicht (s.prop, wordt gebruikt voor videotekenen)

* **a.media.name**

   (**Optioneel**) Bevat informatie over het plakken van video. Het plakken moet voor deze variabele door ClientCare worden toegelaten.

   * Type gebeurtenis: Aangepast inzicht (s.prop)
   * Aangepast inzicht (s.prop)

* **a.media.segment**

   (**Vereist**) Verzamelt videosegmentgegevens, met inbegrip van de segmentnaam en de orde waarin het segment in de video voorkomt. Deze variabele wordt gevuld door de `segmentByMilestones` variabele in te schakelen wanneer spelergebeurtenissen automatisch worden bijgehouden, of door een aangepaste segmentnaam in te stellen wanneer spelergebeurtenissen handmatig worden bijgehouden.

   Wanneer een bezoeker bijvoorbeeld het eerste segment in een video bekijkt, kan SiteCatalyst zich verzamelen `1:M:0-25` in de sectie Segmenten Var. De standaardmethode voor het verzamelen van videogegevens verzamelt gegevens op de videostart- (afspelen), segmentbegin- en videoeindpunten (stoppen).

   Analytics telt de eerste segmentmening bij het begin van het segment, wanneer de bezoeker begint te letten. Volgende segmentweergaven als het segment begint.

   * Type variabele: eVar
   * Standaardvervaldatum: Paginaweergave

* **a.contentType**

   Hiermee worden gegevens verzameld over het type inhoud dat door een bezoeker wordt weergegeven. Aan door videometing verzonden berichten wordt een inhoudstype &quot;video&quot; toegewezen. Deze variabele hoeft niet uitsluitend voor videotracering te worden gereserveerd. Als u andere inhoudsrapportinhoudstypen gebruikt met dezelfde variabele, kunt u de distributie van bezoekers over de verschillende typen inhoud analyseren. U kunt bijvoorbeeld andere inhoudstypen labelen met waarden zoals &quot;artikel&quot; of &quot;productpagina&quot; met deze variabele. Vanuit het perspectief van videometing kunt u met Inhoudstype videobezoekers identificeren en zo de videoconversiesnelheden berekenen.

   * Type variabele: eVar
   * Standaardvervaldatum: Paginaweergave

* **a.media.timePlayed**

   Telt de tijd, in seconden, besteed aan het bekijken van een video sinds het laatste proces van de gegevensinzameling (beeldverzoek).

   * Type variabele: Gebeurtenis
   * Type: Teller

* **a.media.view**

   Geeft aan dat een bezoeker een gedeelte van een video heeft weergegeven. Het biedt echter geen informatie over hoeveel of welk deel van een video de bezoeker heeft bekeken.

   * Type variabele: Gebeurtenis
   * Type: Teller

* **a.media.segmentView**

   Geeft aan dat een bezoeker een gedeelte van een videosegment heeft weergegeven. Het biedt echter geen informatie over hoeveel of welk deel van een video de bezoeker heeft bekeken.

   * Type variabele: Gebeurtenis
   * Type: Teller

* **a.media.complete**

   Geeft aan dat een gebruiker een volledige video heeft weergegeven. Standaard wordt de complete-gebeurtenis 1 seconde voor het einde van de video gemeten. Tijdens de implementatie kunt u opgeven hoeveel seconden vanaf het einde van de video u een volledige weergave wilt overwegen. Voor live video en andere streams zonder gedefinieerd einde kunt u een aangepast punt opgeven om de voltooiing te meten. Bijvoorbeeld na een bepaalde tijd die is weergegeven.

   * Type variabele: Gebeurtenis
   * Type: Teller

## Gebeurtenissen van speler bijhouden {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Om het afspelen van video te meten, moeten de methoden `mediaPlay`, `mediaStop`en `mediaClose` The op de juiste momenten worden aangeroepen. Wanneer de speler bijvoorbeeld wordt gepauzeerd, `mediaStop`. `mediaPlay` wordt aangeroepen wanneer het afspelen begint of wordt hervat.

## Mediummeetklasse en methodeverwijzing {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Hiermee opent u een video die u wilt bijhouden.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   Hiermee opent u een `MediaSettings` object dat u wilt bijhouden.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Sluit het media-item genaamd *`name`*.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      void close(QString name);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Hiermee wordt het media-item met de naam *`name`* op het opgegeven *`offset`* (in seconden) afgespeeld.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      void play(QString name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **complete**

   Markeer het media-item handmatig als voltooid op de *`offset`* opgegeven waarde (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      void complete(QString name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stoppen**

   Meldt aan de mediamodule dat de video is gestopt of gepauzeerd bij de opgegeven *verschuiving*.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      stop(QString name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **klikken**

   Hiermee wordt aan de mediamodule gemeld dat op het media-item is geklikt.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      void click(QString name, double offset);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   Hiermee wordt een aanroep van een handeling track verzonden (geen paginaweergave) voor de huidige mediastatus.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```

---
description: Hier volgt informatie over het meten van video's op iOS met behulp van milestone-videometingen.
seo-description: Hier volgt informatie over het meten van video's op iOS met behulp van milestone-videometingen.
seo-title: Video Analytics
solution: Marketing Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: d75fa415-78f6-4f50-a563-76949f040138
translation-type: tm+mt
source-git-commit: c64e2fa7cee3cd35c4574e5007406b7604c99499
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 14%

---


# Video Analytics {#video-analytics}

Hier volgt informatie over het meten van video&#39;s op iOS met behulp van milestone-videometingen.

>[!TIP]
>
>Tijdens het afspelen van video worden vaak &#39;hartslagaanroepen&#39; naar deze service verzonden om de afspeeltijd te meten. Deze hartslagvraag wordt verzonden om de 10 seconden, wat in korrelige videobetrokkenheidsmetriek en nauwkeurigere video neerslagrapporten resulteert. Zie Audio en video [meten in Adobe Analytics](https://docs.adobe.com/content/help/nl-NL/media-analytics/using/media-overview.html)voor meer informatie.

Het algemene proces voor het meten van video is op alle platforms zeer vergelijkbaar. Deze inhoud biedt een basisoverzicht van de ontwikkelaarstaken met codevoorbeelden.

## Gebeurtenissen van speler toewijzen aan variabelen van Analyse {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

In de volgende tabel worden de mediagegevens weergegeven die naar Analytics worden verzonden. Gebruik verwerkingsregels om de contextgegevens toe te wijzen aan een variabele Analytics.

* **a.media.name**

   (Vereist) Hiermee wordt de naam van de video verzameld, zoals opgegeven in de implementatie, wanneer een bezoeker de video op een of andere manier weergeeft. U kunt classificaties toevoegen voor deze variabele.

   (Optioneel) De variabele Custom Insight biedt informatie over het plakken van video&#39;s.

   * Type variabele: eVar
   * Standaardvervaldatum: Bezoek
   * Custom Insight (s.prop, gebruikt voor videoverven)

* **a.media.name**

   (Optioneel) Bevat informatie over het plakken van video. Voor deze variabele moet het plakken door de klantenservice worden ingeschakeld.

   * Type variabele: Custom Insight (s.prop)
   * Type gebeurtenis: Custom Insight (s.prop)

* **a.media.segment**

   (Vereist) Verzamelt videosegmentgegevens, met inbegrip van de segmentnaam en de orde waarin het segment in de video voorkomt. Deze variabele wordt gevuld door de `segmentByMilestones` variabele in te schakelen wanneer spelergebeurtenissen automatisch worden bijgehouden, of door een aangepaste segmentnaam in te stellen wanneer spelergebeurtenissen handmatig worden bijgehouden. Wanneer een bezoeker bijvoorbeeld het eerste segment in een video bekijkt, verzamelt SiteCatalyst het volgende in het `1:M:0-25` dialoogvenster Segmenten.

   De standaardmethode voor het verzamelen van videogegevens verzamelt gegevens op de volgende punten:

   * video starten (afspelen)
   * begin segment
   * videoeinde (stoppen)

   Analytics telt de eerste segmentmening bij het begin van het segment, wanneer de bezoeker begint te letten. Volgende segmentweergaven als het segment begint.

   * Type variabele: eVar
   * Standaardvervaldatum: Paginaweergave


* **a.contentType**

   Verzamelt gegevens over het type inhoud dat door een bezoeker wordt bekeken. Aan de door videometing verzonden opdrachten wordt een inhoudstype `video`toegewezen. Deze variabele hoeft niet uitsluitend voor videotracering te worden gereserveerd. Als u andere inhoudrapporten van het inhoudstype gebruikt door deze variabele te gebruiken, kunt u de distributie van bezoekers over de verschillende typen inhoud analyseren. U kunt bijvoorbeeld andere inhoudstypen labelen met waarden zoals &quot;artikel&quot; of &quot;productpagina&quot; met deze variabele. Vanuit het oogpunt van videometing kunt u met Inhoudstype videobezoekers identificeren en de videoconversiesnelheden berekenen.

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

   Geeft aan dat een gebruiker een volledige video heeft weergegeven. Standaard wordt de complete-gebeurtenis 1 seconde voor het einde van de video gemeten. Tijdens de implementatie kunt u opgeven hoeveel seconden vanaf het einde van de video u een volledige weergave wilt overwegen. Voor live video en andere streams zonder een bepaald einde kunt u een aangepast punt opgeven dat moet worden gemeten nadat een bepaalde tijd is weergegeven.

   * Type variabele: Gebeurtenis
   * Type: Teller

## Media-instellingen configureren {#section_929945D4183C428AAF3B983EFD3E2500}

Configureer een `ADBMediaSettings` object met de instellingen die u wilt gebruiken voor het bijhouden van video:

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## Gebeurtenissen van speler bijhouden {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Om het afspelen van video te meten, moeten de methoden `mediaPlay`, `mediaStop`en `mediaClose` The op de juiste momenten worden aangeroepen. Wanneer de speler bijvoorbeeld wordt gepauzeerd, `mediaStop`. `mediaPlay` wordt aangeroepen wanneer het afspelen begint of wordt hervat.

In het volgende voorbeeld ziet u hoe u meldingen configureert en de mediamethoden oproept om video te meten:

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## Klassen {#section_16838332727348F990305C0C6B0D795C}

### Klasse: ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### Klasse: ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## Mediummeetklasse en methodeverwijzing {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings &#x200B; WithName: &#x200B; length: &#x200B; playerName: &#x200B; playerID:**

   Retourneert een `ADBMediaSettings` object met opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings &#x200B; WithName: &#x200B; length: &#x200B; playerName: &#x200B; parentName: &#x200B; parentPod: &#x200B; parentPodPosition: &#x200B; CPM:**

   Retourneert een `ADBMediaSettings` object voor gebruik bij het bijhouden van een advertentievideo.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings: &#x200B; callback:**

   Hiermee opent u een `ADBMediaSettings` object dat u wilt bijhouden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   Sluit het media-item genaamd *name*.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay: &#x200B; verschuiving:**

   Hiermee wordt het media-item met de naam *name* afgespeeld bij de opgegeven *verschuiving* (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete: &#x200B; verschuiving:**

   Markeer het media-item handmatig als voltooid bij de opgegeven *verschuiving* (in seconden).

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop: &#x200B; verschuiving:**

   Meldt aan de mediamodule dat de video is gestopt of gepauzeerd bij de opgegeven *verschuiving*.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **MediaClick: &#x200B; verschuiving:**

   Hiermee wordt aan de mediamodule gemeld dat op het media-item is geklikt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack: &#x200B; metData:**

   Hiermee wordt een aanroep van een handeling track verzonden (geen paginaweergave) voor de huidige mediastatus.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```


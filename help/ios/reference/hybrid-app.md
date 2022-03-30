---
description: Als uw app mobiele webinhoud opent, moet u ervoor zorgen dat bezoekers niet afzonderlijk worden geïdentificeerd wanneer ze tussen het systeemeigen en mobiele web bewegen.
solution: Experience Cloud Services,Analytics
title: Bezoeker die tussen een app en het Web van Mobile volgt
topic-fix: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
exl-id: d8459d59-0edd-42c4-81b5-529b250accb4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Bezoekerspatiëring tussen een app en een mobiel web  {#visitor-tracking-between-an-app-and-mobile-web}

Als uw app mobiele webinhoud opent, moet u ervoor zorgen dat bezoekers niet afzonderlijk worden geïdentificeerd wanneer ze tussen het systeemeigen en mobiele web bewegen.

## Bezoeker-id&#39;s in apps

De iOS SDK genereert een unieke bezoeker-id wanneer een app wordt geïnstalleerd. Deze id wordt opgeslagen in permanent geheugen op het mobiele apparaat en wordt bij elke hit verzonden. Deze id wordt alleen verwijderd wanneer de gebruiker de app verwijdert.

>[!TIP]
>
>Id&#39;s van App-bezoekers blijven aanwezig via upgrades.

## Bezoeker-id&#39;s op het mobiele web

Voor mobiele webimplementaties wordt gebruikgemaakt van dezelfde standaard Analytics `s_code.js` of `AppMeasurement.js` die wordt gebruikt in desktopsites. De JavaScript-bibliotheken beschikken over eigen methoden voor het genereren van unieke bezoeker-id&#39;s, waardoor een andere bezoeker-id wordt gegenereerd wanneer u mobiele webinhoud opent vanuit uw app.

U kunt als volgt dezelfde bezoeker-id gebruiken in de app en het mobiele web en de id van de bezoeker van de app doorgeven aan het mobiele web in de URL:

## Controleren van bezoekers tussen een app en mobiele websites implementeren {#section_EDC91D6C67AD43999227707C2769C65D}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md).
1. Om bezoekersinformatie aan URL toe te voegen die wordt gebruikt om de Webmening te openen, vraag `visitorAppendToURL`:

   ```objective-c
   NSURL *url = [NSURL URLWithString:@"https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   U kunt ook vanaf SDK versie 4.16.0 `visitorGetUrlVariablesAsync:` en genereren u uw eigen URL:

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

De de dienstcode van identiteitskaart op het bestemmingsdomein haalt MID uit URL in plaats van het verzenden van een verzoek naar Adobe voor een nieuwe identiteitskaart. De de dienstcode van identiteitskaart op de bestemmingspagina gebruikt overgegaan MID om de bezoeker te volgen.

Controleer bij hits in de mobiele webinhoud of de `mid` parameter aanwezig is op elke hit en dat deze waarde overeenkomt met de waarde `mid` die wordt verzonden door de toepassingscode.

## Problemen met het bijhouden van bezoekers oplossen {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### Ik zie het niet `[ADBMobile visitorAppendToURL:]`.

Controleer of de Adobe-SDK die in de bovenliggende toepassing is gebundeld, versie 4.12.0 of hoger is.

### Ik zie geen Adobe-id&#39;s in mijn URL.

Controleer het volgende:

* De URL-tekenreeks waarmee de webweergave wordt geopend, is gegenereerd door  `[ADBMobile visitorAppendToURL:]`

* De Adobe-id&#39;s worden gecodeerd.

   Als u wilt controleren of id&#39;s worden toegevoegd aan de URL die wordt geopend, zoekt u naar de `adobe_mc` queryparameter.

### Mijn &#39;mid&#39; is in mijn app niet identiek aan mijn webweergave.*

Controleer het volgende:

* De URL-tekenreeks waarmee de webweergave wordt geopend, is gegenereerd door `[ADBMobile visitorAppendToURL:]`

   De URL-tekenreeks bevat Adobe-parameters.

   De tekenreeks moet het volgende bevatten `adobe_mc="SAMPLE_ID_DATA"` waar `"SAMPLE_ID_DATA"` bevat de id&#39;s die worden gegenereerd in de Adobe Mobile SDK.

* De `VisitorAPI.js` is versie 1.7.0 of hoger.

Als deze het oplossen van problemenstappen uw kwesties niet oplossen, contacteer de Zorg van de Adobe Cliënt; bereid zijn om een steekproeftoepassing en de bijbehorende plaats te delen zodat Adobe de implementatie kan bevestigen.

---
description: Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw iOS-apps.
solution: Experience Cloud Services,Analytics
title: Geo-Locatie en belangenpunten
topic-fix: Developer and implementation
uuid: c800ec85-a33f-425d-b28f-bfe8bf229ae8
exl-id: 732c3863-2010-4d04-a17b-a656e857f567
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 1%

---

# Geolocatie en aandachtspunten {#geo-location-and-points-of-interest}

Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw iOS-apps.

Elk `trackLocation` de vraag verzendt het volgende:

* Breedtegraad, lengtegraad en locatie in een interessant punt (POI) dat is gedefinieerd in Adobe Mobile-services.

   Deze informatie wordt doorgegeven aan mobiele oplossingvariabelen voor automatische rapportage.

* Afstand van middelpunt en nauwkeurigheid die als contextgegevens worden doorgegeven.

   Deze variabelen worden niet automatisch vastgelegd. U moet deze variabelen van contextgegevens in kaart brengen door instructies in te gebruiken *Aanvullende gegevens verzenden* hieronder.

## Dynamische POI-updates {#section_3747B310DD5147E2AAE915E762997712}

Vanaf versie 4.2 worden POI&#39;s gedefinieerd in de Adobe Mobile-interface en dynamisch gesynchroniseerd met het configuratiebestand van de app. Voor deze synchronisatie is een `analytics.poi` in het dialoogvenster `ADBMobile.json` bestand:

```js
"analytics.poi": "https://assets.adobedtm.com/…/yourfile.json",
```

Zie voor meer informatie [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

Als dit niet wordt gevormd, een bijgewerkte versie van `ADBMobile.json` bestand moet worden gedownload en aan uw app worden toegevoegd. Zie voor meer informatie en instructies *SDK en testgereedschappen downloaden* in [Voordat u begint](/help/ios/getting-started/requirements.md).

## Go-locaties en POI&#39;s volgen {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md).
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Bellen `trackLocation` om de huidige locatie bij te houden:

   ```objective-c
   CLLocation *currentLocation = location; 
   [ADBMobile trackLocation: currentLocation data: nil]; 
   ```

   >[!TIP]
   >
   >U kunt bellen `trackLocation` op elk moment.

   Om de plaats te bepalen die tot wordt overgegaan `trackLocation` oproepen, gebruik [De locatie van de gebruiker ophalen](https://developer.apple.com/Library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/CoreLocation/CoreLocation.html).

Als bovendien wordt vastgesteld dat de locatie zich in een gedefinieerde POI-straal bevindt, `a.loc.poi` de contextgegevensvariabele wordt verzonden binnen met `trackLocation` hit en wordt gerapporteerd als een POI in Locatierapporten. An `a.loc.dist` de contextvariabele wordt ook verzonden met de afstand in meters van de gedefinieerde coördinaten.

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de locatiegegevens kunt u aanvullende contextgegevens verzenden bij elke aanroep van de tracklocatie:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"GPS" forKey:@"myapp.location.LocationSource"]; 
[ADBMobile trackLocation: currentLocation data:contextData];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-location-context-data.png)

## Locatiecontextgegevens {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

De breedte en lengte worden elk verzonden gebruikend drie verschillende parameters van contextgegevens, met elke parameter die een verschillend niveau van precisie vertegenwoordigt, voor een totaal van zes parameters van contextgegevens.

De coördinaten lat = 40,93231, lon = -111,93152 vertegenwoordigen bijvoorbeeld een locatie met een precisie van 1 m. Deze locatie wordt gesplitst op basis van het precisieniveau in de volgende variabelen:

* `a.loc.lat.a`= 040,9
* `a.loc.lat.b` = 32
* `a.loc.lat.c` = 31
* `a.loc.lon.a` = -111,9
* `a.loc.lon.b` = 31
* `a.loc.lon.c` = 52

Sommige precisieniveaus worden weergegeven als &quot;00&quot;, afhankelijk van de nauwkeurigheid van de huidige locatie. Als de locatie momenteel bijvoorbeeld nauwkeurig is tot 100 m, `a.loc.lat.c` en `a.loc.lon.c` wordt gevuld met &quot;00&quot;.

## Aanvullende informatie {#section_931AC1E0D88147E29FE1B6E3CC1E9550}

De volgende informatie onthouden:

* A `trackLocation` verzoek wordt ingediend, gelijkwaardig aan een `trackAction` vraag.

* POI&#39;s worden niet doorgegeven als onderdeel van normale `trackAction` en `trackState` vraag, zodat moet u een `trackLocation` oproep om POI&#39;s bij te houden.

* `trackLocation` zo vaak als nodig moet worden opgeroepen om de locatie en de lokalen te volgen.

   We raden aan `trackLocation` wanneer de app wordt gestart en zo nodig op basis van de vereisten van de toepassing.

* POI&#39;s worden alleen gevuld nadat ze zijn gedefinieerd in het configuratiebestand van de app.

   Ze worden niet toegepast op historisch `trackLocation` vraag die eerder werd verzonden.
* `trackLocation` vraag steun die extra contextgegevens gelijkend op verzenden `trackAction` oproepen.

* Wanneer twee POIs overlappende diameters hebben, wordt eerste POI die de huidige plaats bevat gebruikt.

   Als uw POIs overlappen, zou u POIs in orde van het meest korrelige aan minst korrelig moeten opsommen om ervoor te zorgen dat de meest korrelige POI wordt gemeld.

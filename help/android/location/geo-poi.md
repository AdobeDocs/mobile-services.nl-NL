---
description: Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw Android-apps.
solution: Experience Cloud Services,Analytics
title: Geo-Locatie en belangenpunten
topic-fix: Developer and implementation
uuid: b8209370-cbc4-40f9-97d8-017e2d74a377
exl-id: e1fed35b-5ce9-48ee-ade0-b1701cf2a3a9
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 1%

---

# Geolocatie en aandachtspunten {#geo-location-and-points-of-interest}

Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw Android-apps.

Elk `trackLocation` de vraag verzendt de volgende informatie:

* Breedtegraad, lengtegraad en locatie in een interessant punt (POI) dat is gedefinieerd in de gebruikersinterface van Adobe Mobile Services.

   Deze informatie wordt doorgegeven aan mobiele oplossingvariabelen voor automatische rapportage.

* Afstand van middelpunt en nauwkeurigheid die als contextgegevens worden doorgegeven.

   Deze variabelen worden niet automatisch vastgelegd. U moet deze variabelen van contextgegevens in kaart brengen door de instructies in te gebruiken *Aanvullende gegevens verzenden* hieronder.

## Dynamische POI-updates {#section_3747B310DD5147E2AAE915E762997712}

Vanaf versie 4.2 worden POI&#39;s gedefinieerd in de gebruikersinterface van Adobe Mobile en dynamisch gesynchroniseerd met het configuratiebestand van de app. Voor deze synchronisatie is een `analytics.poi` in het dialoogvenster [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md):

```js
"analytics.poi": "https://assets.adobedtm.com/…/yourfile.json",
```

Als dit niet wordt gevormd, moet u een bijgewerkte versie van downloaden `ADBMobile.json` en deze aan uw app toevoegen. Zie voor meer informatie [SDK en testgereedschappen downloaden](/help/android/getting-started/requirements.md).

## Geo-locatie en POI&#39;s bijhouden {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Bellen `trackLocation` om de huidige locatie bij te houden:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >U kunt bellen `trackLocation` op elk moment.

   U kunt locatiestrategieën gebruiken om de plaats te bepalen die tot wordt overgegaan `trackLocation` vraag. Zie voor meer informatie [Locatiestrategieën voor Android](https://developer.android.com/guide/topics/location/strategies.html).

Als bovendien wordt vastgesteld dat de locatie zich in een gedefinieerde POI-straal bevindt, `a.loc.poi` de contextgegevensvariabele wordt verzonden binnen met `trackLocation` raakgebied en wordt gerapporteerd als een POI op de **[!UICONTROL Location Breakdown]** rapporten. An `a.loc.dist` de contextvariabele wordt ook verzonden met de afstand in meters van de gedefinieerde coördinaten.

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de locatiegegevens kunt u aanvullende contextgegevens verzenden bij elke aanroep van de tracklocatie:

```java
HashMap<String, Object> locationContextData = new HashMap<String, Object>(); 
locationContextData.put("myapp.location.LocationSource", "GPS"); 
 
Location currentLocation = new Location("my location here"); 
Analytics.trackLocation(currentLocation, locationContextData);
```

De waarden van contextgegevens moeten aan douanevariabelen in de UI van de Diensten van Adobe Mobile in kaart worden gebracht:

![](assets/map-location-context-data.png)

## Locatiecontextgegevens {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

De breedte en lengte worden verzonden door drie verschillende parameters van contextgegevens te gebruiken, waarbij elke parameter een verschillend precisieniveau vertegenwoordigt, voor een totaal van zes parameters van contextgegevens.

De coördinaten lat = 40,93231, long = -111,93152 vertegenwoordigen bijvoorbeeld een locatie met een precisie van 1 m. Deze locatie wordt gesplitst op basis van het precisieniveau in de volgende variabelen:

`a.loc.lat.a`= 040,9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111,9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

Sommige precisieniveaus kunnen er zo uitzien `00` afhankelijk van de nauwkeurigheid van de huidige locatie. Als de locatie momenteel bijvoorbeeld nauwkeurig is tot 100 m, `a.loc.lat.c` en `a.loc.lon.c` wordt gevuld met `00`.

De volgende informatie onthouden:

* A `trackLocation` verzoek wordt ingediend, gelijkwaardig aan een `trackAction` vraag.

* POI&#39;s worden niet doorgegeven als onderdeel van standaard `trackAction` en `trackState` vraag, zodat moet u een `trackLocation` oproep om POI&#39;s bij te houden.

* `trackLocation` zo vaak als nodig moet worden opgeroepen om de locatie en de lokalen te volgen.

   We raden aan `trackLocation` wanneer de app wordt gestart en zo nodig, afhankelijk van de vereisten van de app.

* POI&#39;s worden alleen gevuld nadat ze zijn gedefinieerd in het configuratiebestand van de app.

   De POI&#39;s worden niet toegepast op historische `trackLocation` vraag die eerder werd verzonden.
* `trackLocation` vraag steun die extra contextgegevens gelijkend op verzenden `trackAction` oproepen.

* Wanneer twee POIs overlappende diameters hebben, wordt eerste POI die de huidige plaats bevat gebruikt.

   Als uw POIs overlappen, zou u POIs in orde van meeste aan minste korrelig moeten vermelden om ervoor te zorgen dat de meest korrelige POI wordt gemeld.

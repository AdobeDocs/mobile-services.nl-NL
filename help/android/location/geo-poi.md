---
description: Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw Android-apps.
seo-description: Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw Android-apps.
seo-title: Geo-Locatie en belangenpunten
solution: Experience Cloud,Analytics
title: Geo-Locatie en belangenpunten
topic: Developer and implementation
uuid: b8209370-cbc4-40f9-97d8-017e2d74a377
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# Geolocatie en aandachtspunten {#geo-location-and-points-of-interest}

Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw Android-apps.

Elke `trackLocation` vraag verzendt de volgende informatie:

* Breedtegraad, lengtegraad en locatie in een interessant punt (POI) dat is gedefinieerd in de gebruikersinterface van Mobiele services Adobe.

   Deze informatie wordt doorgegeven aan mobiele oplossingvariabelen voor automatische rapportage.

* Afstand van middelpunt en nauwkeurigheid die als contextgegevens worden doorgegeven.

   Deze variabelen worden niet automatisch vastgelegd. U moet deze variabelen van contextgegevens in kaart brengen door de instructies in de *Verzendende Extra sectie van Gegevens* hieronder te gebruiken.

## Dynamische POI-updates {#section_3747B310DD5147E2AAE915E762997712}

Vanaf versie 4.2 worden POI&#39;s gedefinieerd in de gebruikersinterface van Adobe Mobile en dynamisch gesynchroniseerd met het configuratiebestand van de app. Voor deze synchronisatie is een `analytics.poi` instelling vereist in de [ADBMobile JSON-configuratie](/help/android/configuration/json-config/json-config.md):

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Als dit niet is geconfigureerd, moet u een bijgewerkte versie van het `ADBMobile.json` bestand downloaden en toevoegen aan uw app. Zie de SDK [downloaden en de testgereedschappen](/help/android/getting-started/requirements.md)voor meer informatie.

## Geo-locatie en POI&#39;s bijhouden {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Vraag `trackLocation` om de huidige plaats te volgen:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >U kunt `trackLocation` op elk ogenblik roepen.

   U kunt plaatsstrategieën gebruiken om de plaats te bepalen die tot de `trackLocation` vraag wordt overgegaan. Zie [Android-locatiestrategieën](https://developer.android.com/guide/topics/location/strategies.html)voor meer informatie.

Bovendien, als de plaats wordt bepaald om in een bepaalde POI straal te zijn, wordt een variabele van `a.loc.poi` contextgegevens verzonden in met de `trackLocation` slag en als POI op de **[!UICONTROL Location Breakdown]** rapporten gerapporteerd. Een `a.loc.dist` contextvariabele wordt ook verzonden met de afstand in meters van de gedefinieerde coördinaten.

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de locatiegegevens kunt u aanvullende contextgegevens verzenden bij elke aanroep van de tracklocatie:

```java
HashMap<String, Object> locationContextData = new HashMap<String, Object>(); 
locationContextData.put("myapp.location.LocationSource", "GPS"); 
 
Location currentLocation = new Location("my location here"); 
Analytics.trackLocation(currentLocation, locationContextData);
```

De waarden van contextgegevens moeten aan douanevariabelen in de UI van de Diensten van de Mobiele Adobe worden in kaart gebracht:

![](assets/map-location-context-data.png)

## Locatiecontextgegevens {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

De breedte en lengte worden verzonden door drie verschillende parameters van contextgegevens te gebruiken, waarbij elke parameter een verschillend precisieniveau vertegenwoordigt, voor een totaal van zes parameters van contextgegevens.

De coördinaten lat = 40,93231, long = -111,93152 vertegenwoordigen bijvoorbeeld een locatie met een precisie van 1 m. Deze locatie wordt gesplitst op basis van het precisieniveau in de volgende variabelen:

`a.loc.lat.a`= 040.9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111.9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

Sommige precisieniveaus worden weergegeven, `00` afhankelijk van de nauwkeurigheid van de huidige locatie. Als de locatie bijvoorbeeld momenteel nauwkeurig is tot 100 m, wordt deze gevuld `a.loc.lat.c` en `a.loc.lon.c` gevuld met `00`.

De volgende informatie onthouden:

* Een `trackLocation` verzoek verzendt in het equivalent van een `trackAction` vraag.

* POIs wordt niet overgegaan als deel van typisch `trackAction` en `trackState` vraag, zodat moet u een `trackLocation` vraag gebruiken om POIs te volgen.

* `trackLocation` zo vaak als nodig moet worden opgeroepen om de locatie en de lokalen te volgen.

   We raden u aan aan te roepen `trackLocation` wanneer de app wordt gestart en zo nodig, afhankelijk van de vereisten van de app.

* POI&#39;s worden alleen gevuld nadat ze zijn gedefinieerd in het configuratiebestand van de app.

   De POIs wordt niet toegepast op historische `trackLocation` vraag die eerder werd verzonden.
* `trackLocation` vraag steun verzendend extra contextgegevens gelijkend op `trackAction` vraag.

* Wanneer twee POIs overlappende diameters hebben, wordt eerste POI die de huidige plaats bevat gebruikt.

   Als uw POIs overlappen, zou u POIs in orde van meeste aan minste korrelig moeten vermelden om ervoor te zorgen dat de meest korrelige POI wordt gemeld.


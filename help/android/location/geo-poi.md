---
description: Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw Android-apps.
seo-description: Geo-location helpt u locatiegegevens te meten door breedte- en lengtegegevens en vooraf gedefinieerde interessepunten te gebruiken in uw Android-apps.
seo-title: Geo-Locatie en belangenpunten
solution: Experience Cloud,Analytics
title: Geo-Locatie en belangenpunten
topic-fix: Developer and implementation
uuid: b8209370-cbc4-40f9-97d8-017e2d74a377
exl-id: e1fed35b-5ce9-48ee-ade0-b1701cf2a3a9
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
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

   Deze variabelen worden niet automatisch vastgelegd. U moet deze variabelen van contextgegevens in kaart brengen door de instructies in *Verzendend Extra Gegevens* hieronder te gebruiken.

## Dynamische POI-updates {#section_3747B310DD5147E2AAE915E762997712}

Vanaf versie 4.2 worden POI&#39;s gedefinieerd in de gebruikersinterface van Adobe Mobile en dynamisch gesynchroniseerd met het configuratiebestand van de app. Voor deze synchronisatie is een `analytics.poi`-instelling vereist in [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md):

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Als dit niet wordt gevormd, moet u een bijgewerkte versie van het `ADBMobile.json` dossier downloaden en het toevoegen aan uw app. Zie [SDK downloaden en tools testen](/help/android/getting-started/requirements.md) voor meer informatie.

## Geo-locatie en POI&#39;s bijhouden {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het dossier SDK en Config aan uw Project IntelliJ IDEA of Eclipse* in [de implementatie van de Kern en levenscyclus](/help/android/getting-started/dev-qs.md) toe.

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Roep `trackLocation` aan om de huidige locatie bij te houden:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >U kunt `trackLocation` op elk ogenblik roepen.

   U kunt plaatsstrategieën gebruiken om de plaats te bepalen die tot `trackLocation` vraag wordt overgegaan. Zie [Locatiestrategieën voor Android](https://developer.android.com/guide/topics/location/strategies.html) voor meer informatie.

Als bovendien wordt bepaald dat de locatie zich in een gedefinieerde POI-straal bevindt, wordt een `a.loc.poi`-contextgegevensvariabele verzonden in combinatie met de `trackLocation`-hit en wordt deze als een POI gerapporteerd in de **[!UICONTROL Location Breakdown]**-rapporten. Een contextvariabele `a.loc.dist` wordt ook verzonden met de afstand in meters van de gedefinieerde coördinaten.

## Extra gegevens {#section_3EBE813E54A24F6FB669B2478B5661F9} verzenden

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

`a.loc.lat.a`= 040,9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111,9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

Afhankelijk van de nauwkeurigheid van de huidige locatie kunnen sommige precisieniveaus `00` worden weergegeven. Als de locatie bijvoorbeeld momenteel nauwkeurig is tot 100 m, worden `a.loc.lat.c` en `a.loc.lon.c` gevuld met `00`.

De volgende informatie onthouden:

* Een `trackLocation` verzoek verzendt in het equivalent van een `trackAction` vraag.

* POIs wordt niet overgegaan als deel van typische `trackAction` en `trackState` vraag, zodat moet u een `trackLocation` vraag gebruiken om POIs te volgen.

* `trackLocation` zo vaak als nodig moet worden opgeroepen om de locatie en de lokalen te volgen.

   We raden u aan `trackLocation` aan te roepen wanneer de app start en vervolgens naar wens, afhankelijk van de vereisten van de app.

* POI&#39;s worden alleen gevuld nadat ze zijn gedefinieerd in het configuratiebestand van de app.

   POIs wordt niet toegepast op historische `trackLocation` vraag die eerder werden verzonden.
* `trackLocation` vraag steun verzendend extra contextgegevens gelijkend op  `trackAction` vraag.

* Wanneer twee POIs overlappende diameters hebben, wordt eerste POI die de huidige plaats bevat gebruikt.

   Als uw POIs overlappen, zou u POIs in orde van meeste aan minste korrelig moeten vermelden om ervoor te zorgen dat de meest korrelige POI wordt gemeld.

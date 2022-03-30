---
description: Bij het bijhouden van baken kunt u microlocaties meten en als doel instellen met behulp van iBeacon en Bluetooth Low Energy.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Beacon bijhouden
topic-fix: Developer and implementation
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
exl-id: b8493e9d-ed1c-4404-a218-47a18a9c8faa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Beacon bijhouden {#beacon-tracking}

Bij het bijhouden van baken kunt u microlocaties meten en als doel instellen met behulp van iBeacon en Bluetooth Low Energy.

De volgende bakengegevens worden verzonden naar Analytics en Target wanneer `trackBeacon` wordt aangeroepen:

* `a.beacon.uuid` - ProximityUID van het baken
* `a.beacon.major` - Groot nummer van het baken (zoals archiefnummer)
* `a.beacon.minor` - Klein nummer van het baken (bijvoorbeeld een uniek nummer in een winkel)
* `a.beacon.prox` - De waarden 0-3 geven aan hoe dicht de gebruiker bij het baken is.

Dit zijn wat deze waarden betekenen:

* 0 = onbekend
* 1 = onmiddellijk
* 2 = dichtbij
* 3 = ver

Deze baken-gegevens worden vastgelegd in variabelen voor mobiele oplossingen.

## Ballonen bijhouden {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Bandenlocatie verzamelen.

   Er zijn meerdere bibliotheken van derden beschikbaar om Bluetooth LE-beacons te scannen, afhankelijk van de fabrikant van het baken.
1. Nadat de bakeninformatie is verkregen, gebruik de volgende vraag om de plaats te volgen:

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. Wanneer de gebruiker de nabijheid van het baken verlaat, ontruim het huidige baken:

   ```java
   Analytics.clearBeacon();
   ```

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de baken gegevens, kunt u extra contextgegevens met elk verzenden `trackBeacon` oproep:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

De waarden van contextgegevens moeten aan douanevariabelen in de diensten van Adobe Mobile worden in kaart gebracht:

![](assets/map-variable-context-ltv.png)

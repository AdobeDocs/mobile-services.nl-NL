---
description: Met behulp van iBeacon tracking kunt u microlocaties meten en als doel instellen met iBeacon en Low Energy Bluetooth.
seo-description: Met behulp van iBeacon tracking kunt u microlocaties meten en als doel instellen met iBeacon en Low Energy Bluetooth.
seo-title: Beacon tracking
solution: Marketing Cloud,Analytics
title: Beacon tracking
topic: Developer and implementation
uuid: 390883db-027e-4d12-8a16-86d514579db1
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Beacon tracking {#ibeacon-tracking}

Met behulp van iBeacon tracking kunt u microlocaties meten en als doel instellen met iBeacon en Low Energy Bluetooth.

De volgende bakengegevens worden verzonden naar Analytics en Target wanneer `trackBeacon` wordt geroepen:

* `a.beacon.uuid` - ProximityUID van het baken
* `a.beacon.major` - Groot aantal van het baken, zoals archiefaantal
* `a.beacon.minor` - Klein nummer van het baken, zoals een uniek nummer in een winkel
* `a.beacon.prox` - De volgende waarden geven aan hoe dicht de gebruiker bij het baken is:

   * `0` is onbekend
   * `1` onmiddellijk
   * `2` is bijna
   * `3` is ver

## Beacons bijhouden {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Wanneer een apparaat binnen de nabijheid van een baken is, roep `trackBeacon`:

   ```objective-c
   [ADBMobile trackBeacon:beacon data:nil];
   ```

1. Wanneer de gebruiker de nabijheid van het baken verlaat, ontruim het huidige baken:

   ```objective-c
   [ADBMobile trackingClearCurrentBeacon];
   ```

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de naam van de getimede actie kunt u aanvullende contextgegevens verzenden met elke aanroep van de trackactie:

```objective-c
[ADBMobile trackBeacon:beacon data:@{@"myapp.ImageLiked" : imageName}];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-variable-context-ltv.png)

## Voorbeelden {#section_9749238BCBC148998CB18E97D7670D19}

```objective-c
- (void)locationManager:(CLLocationManager *)manager didRangeBeacons:(NSArray *)beacons inRegion:(CLBeaconRegion *)region { 
    if (beacons.count > 0) { 
        CLBeacon *beacon = beacons[0]; 
        // Adobe - track when in range of a beacon 
        [ADBMobile trackBeacon:beacon data:@{@"sampleContextData" : @"sampleContextDataVal"}]; 
    } 
} 
 
// When the user leaves the proximity of the beacon, clear the current beacon 
[ADBMobile trackingClearCurrentBeacon];
```


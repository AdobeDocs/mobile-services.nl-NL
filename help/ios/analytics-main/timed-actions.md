---
description: Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd die de sessie in beslag neemt om de handeling te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.
seo-description: Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd die de sessie in beslag neemt om de handeling te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.
seo-title: Gedetailleerde acties
solution: Marketing Cloud,Analytics
title: Gedetailleerde acties
topic: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Gedetailleerde acties {#timed-actions}

Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd die de sessie in beslag neemt om de handeling te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.

De volgende metriek wordt gerapporteerd voor acties met tijdslimiet:

* Totaal aantal seconden in app tussen begin- en eindsessies
* Totaal aantal seconden tussen begin en eind (kloktijd)

Een facultatieve callback staat u toe om extra actie te voeren wanneer de getimede actie voltooit:

* Voer code uit en voeg logica toe. Optionele aangepaste logica op basis van de resultaten van de duur.
* Voeg contextgegevens toe voordat u de tijdsduur doorgeeft.
* Druk op Annuleren en duur nog niet verzonden.

## Acties met tijdslimiet bijhouden {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Vraag `trackTimedActionStart` en verstrek een getimede actienaam en facultatieve contextgegevens.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Optioneel) Als u aanvullende contextgegevens wilt toevoegen, kunt u op elk gewenst moment een oproep doen `trackTimedActionUpdate` met de naam van de getimede actie.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. Wanneer de gebeurtenis voltooit, vraag `trackTimedActionEnd` en ga de getimede actienaam en `TimedActionBlock` (callback) over, die alle gegevens omhoog zullen kijken en duur berekenen.

   Metrische gegevens voor getimede gebeurtenissen worden opgeslagen in mobiele oplossingvariabelen voor automatische rapportage.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de naam van de getimede actie kunt u aanvullende contextgegevens verzenden met de aanroepen van het begin en de update van de actie:

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-variable-context-ltv.png)

## Voorbeeld {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```


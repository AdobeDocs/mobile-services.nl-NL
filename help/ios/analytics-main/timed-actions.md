---
description: Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd die de sessie in beslag neemt om de handeling te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.
seo-description: Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd die de sessie in beslag neemt om de handeling te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.
seo-title: Gedetailleerde acties
solution: Experience Cloud,Analytics
title: Gedetailleerde acties
topic-fix: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
exl-id: 3499766b-55f6-4861-8291-2269d56ba983
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Gedetailleerde handelingen {#timed-actions}

Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd die de sessie in beslag neemt om de handeling te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.

De volgende metriek wordt gerapporteerd voor acties met tijdslimiet:

* Totaal aantal seconden in app tussen begin- en eindsessies
* Totaal aantal seconden tussen begin en eind (kloktijd)

Een facultatieve callback staat u toe om extra actie te voeren wanneer de getimede actie voltooit:

* Voer code uit en voeg logica toe. Optionele aangepaste logica op basis van de resultaten van de duur.
* Voeg contextgegevens toe voordat u de tijdsduur doorgeeft.
* Druk op Annuleren en duur nog niet verzonden.

## Handelingen met tijdslimiet {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1} bijhouden

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en LiveCycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Roep `trackTimedActionStart` aan en geef een naam voor een getimede actie en optionele contextgegevens op.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Optioneel) Als u aanvullende contextgegevens wilt toevoegen, kunt u `trackTimedActionUpdate` met de naam van de getimede actie aanroepen.

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

## Extra gegevens {#section_3EBE813E54A24F6FB669B2478B5661F9} verzenden

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

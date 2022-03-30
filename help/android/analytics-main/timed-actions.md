---
description: Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd in alle sessies die nodig zijn om de actie te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.
solution: Experience Cloud Services,Analytics
title: Gedetailleerde handelingen
topic-fix: Developer and implementation
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
exl-id: d9851440-6e65-4d89-a6b3-81c8abd2bf06
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Gedetailleerde acties {#timed-actions}

Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd in alle sessies die nodig zijn om de actie te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.

De volgende metriek wordt gerapporteerd voor acties met tijdslimiet:

* Het totale aantal seconden in de app tussen het begin en het einde (meerdere sessies)
* Totaal aantal seconden tussen begin en eind (kloktijd)

Een facultatieve callback staat u toe om extra actie te voeren wanneer de getimede actie voltooit:

* Voer code uit en voeg logica toe. Optionele aangepaste logica op basis van de resultaten van de duur.
* Voeg contextgegevens toe voordat u de tijdsduur doorgeeft.
* Druk op Annuleren en duur nog niet verzonden.

## Acties met tijdslimiet bijhouden {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).
1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Bellen `trackTimedActionStart` en geef een naam voor een getimede actie en optionele contextgegevens op.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Optioneel) U kunt op elk gewenst moment `trackTimedActionUpdate` met de naam van de getimede actie om extra contextgegevens toe te voegen.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Wanneer de gebeurtenis is voltooid, roept u `trackTimedActionEnd` en geeft de naam van de getimede actie door en `TimedActionBlock` (callback), die alle gegevens opzoekt en de duur berekent.

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   Metrische gegevens voor getimede gebeurtenissen worden opgeslagen in mobiele oplossingvariabelen voor automatische rapportage.

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de naam van de getimede actie kunt u ook aanvullende contextgegevens verzenden met de aanroepen voor het starten van de actie en het bijwerken van de actie:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

De waarden van contextgegevens moeten aan douanevariabelen in de diensten van Adobe Mobile worden in kaart gebracht:

![](assets/map-variable-context-ltv.png)

## Voorbeelden {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```

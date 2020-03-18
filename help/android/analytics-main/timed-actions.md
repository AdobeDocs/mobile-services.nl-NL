---
description: Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd in alle sessies die nodig zijn om de actie te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.
seo-description: Met getimede acties kunt u de tijd in de app en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in elke sessie en de totale tijd in alle sessies die nodig zijn om de actie te voltooien. U kunt acties met tijdslimiet gebruiken om segmenten te definiëren en tijd te vergelijken met aanschaf, niveau doorgeven, doorloop uitchecken, enzovoort.
seo-title: Gedetailleerde handelingen
solution: Marketing Cloud,Analytics
title: Gedetailleerde handelingen
topic: Developer and implementation
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
translation-type: tm+mt
source-git-commit: 97c0dc17bcc624b38e9eb8023eb1d69d02568d11

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

   Voor meer informatie, zie *voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.
1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Vraag `trackTimedActionStart` en verstrek een getimede actienaam en facultatieve contextgegevens.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Optioneel) U kunt op elk gewenst moment een oproep doen `trackTimedActionUpdate` met de naam van de getimede actie om extra contextgegevens toe te voegen.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Wanneer de gebeurtenis voltooit, vraag `trackTimedActionEnd` en ga de getimede actienaam en `TimedActionBlock` (callback) over, die alle gegevens omhoog zullen kijken en duur berekenen.

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

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen in Adobe Mobile-services:

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


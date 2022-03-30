---
description: Met de levenwaarde kunt u een levensduurwaarde voor elke Android-gebruiker meten en als doel instellen. De waarde kan worden gebruikt om tijdens het leven aankopen, weergaven, voltooide video's, sociale aandelen, uploads van foto's, enzovoort op te slaan.
solution: Experience Cloud Services,Analytics
title: Levenswaarde bezoeker
topic-fix: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
exl-id: 93c6d711-c7c0-4fca-93b2-6a6fc19377bd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Levenswaarde bezoeker {#visitor-lifetime-value}

Met de levenwaarde kunt u een levensduurwaarde voor elke Android-gebruiker meten en als doel instellen. De waarde kan worden gebruikt om tijdens het leven aankopen, weergaven, voltooide video&#39;s, sociale aandelen, uploads van foto&#39;s, enzovoort op te slaan.

Elke keer dat u een waarde verzendt met `trackLifetimeValueIncrease`, wordt de waarde toegevoegd aan de bestaande waarde. De waarde van het leven wordt opgeslagen op apparaat en kan op elk ogenblik worden teruggewonnen door te roepen `lifetimeValue`.

## De levenwaarde van de bezoeker bijhouden {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).
1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Bellen `trackLifetimeValueIncrease` met het bedrag waarmee de waarde wordt verhoogd:

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de levenwaarde, kunt u extra contextgegevens met elke vraag van de spooractie ook verzenden:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

De waarden van contextgegevens moeten aan douanevariabelen in de diensten van Adobe Mobile worden in kaart gebracht:

![](assets/map-variable-context-ltv.png)

---
description: Met de waarde Lifetime kunt u een levensduurwaarde voor elke gebruiker meten en als doel instellen.
seo-description: Met de waarde Lifetime kunt u een levensduurwaarde voor elke gebruiker meten en als doel instellen.
seo-title: Levenswaarde bezoeker
solution: Experience Cloud,Analytics
title: Levenswaarde bezoeker
topic-fix: Developer and implementation
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
exl-id: f1b684b1-9919-400d-a88a-6d4a0809d9e1
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Levenswaarde van bezoeker {#visitor-lifetime-value}

Met de waarde Lifetime kunt u een levensduurwaarde voor elke gebruiker meten en als doel instellen.

Telkens wanneer u een waarde met `trackLifetimeValueIncrease` verzendt, wordt de waarde toegevoegd aan de bestaande waarde. De waarde van het leven wordt opgeslagen op apparaat en kan op elk ogenblik worden teruggewonnen door `lifetimeValue` te roepen. Dit kan worden gebruikt om levensduuraankopen, meningen, video voltooit, sociale aandelen, foto uploads, etc. op te slaan.

## De levenwaarde {#section_390943A49AF841F2941E65D6DF2B3F5A} van de bezoeker bijhouden

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en LiveCycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Roep `trackLifetimeValueIncrease` met het bedrag aan om de waarde te verhogen:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Aanvullende gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de levenwaarde, kunt u extra contextgegevens met elke vraag van de spooractie verzenden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-variable-context-ltv.png)

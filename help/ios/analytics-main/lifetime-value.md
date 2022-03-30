---
description: Met de waarde Lifetime kunt u een levensduurwaarde voor elke gebruiker meten en als doel instellen.
solution: Experience Cloud Services,Analytics
title: Levenswaarde bezoeker
topic-fix: Developer and implementation
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
exl-id: f1b684b1-9919-400d-a88a-6d4a0809d9e1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Levenswaarde bezoeker {#visitor-lifetime-value}

Met de waarde Lifetime kunt u een levensduurwaarde voor elke gebruiker meten en als doel instellen.

Elke keer dat u een waarde verzendt met `trackLifetimeValueIncrease`, wordt de waarde toegevoegd aan de bestaande waarde. De waarde van het leven wordt opgeslagen op apparaat en kan op elk ogenblik worden teruggewonnen door te roepen `lifetimeValue`. Dit kan worden gebruikt om levensduuraankopen, meningen, video voltooit, sociale aandelen, foto uploads, etc. op te slaan.

## De levenwaarde van de bezoeker bijhouden {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md).
1. De bibliotheek importeren:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Bellen `trackLifetimeValueIncrease` met het bedrag waarmee de waarde wordt verhoogd:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de levenwaarde, kunt u extra contextgegevens met elke vraag van de spooractie verzenden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-variable-context-ltv.png)

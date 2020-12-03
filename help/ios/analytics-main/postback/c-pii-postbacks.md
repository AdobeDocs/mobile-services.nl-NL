---
description: U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.
seo-description: U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.
seo-title: PII-postbacks
title: PII-postbacks
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# PII-postbacks {#pii-postbacks}

U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.

Wanneer u Adobe SDK wilt gebruiken om PII te verzamelen, zou u een spoorPII vraag moeten verzenden. Hoewel het gebruiken van deze vraag inzameling van PII- gegevens toelaat, verzendt SDK niet automatisch de gegevens naar om het even welk eindpunt van Adobe. Een PII type postback moet met het aangewezen eindpunt worden gevormd.

>[!TIP]
>
>Een eindpunt dat HTTPS steunt wordt vereist om het PII postback type te gebruiken.

## PII-postbacks bijhouden {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Wanneer u klaar bent om PII vast te leggen, roep dan `trackPII` om een hit voor deze actie, gebeurtenis of weergave te verzenden:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```


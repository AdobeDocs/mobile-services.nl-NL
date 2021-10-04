---
description: U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.
title: PII-postbacks
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '157'
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

   Zie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en LiveCycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Wanneer u klaar bent om PII te vangen, vraag `trackPII` om een klap voor deze actie, gebeurtenis, of mening te verzenden:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

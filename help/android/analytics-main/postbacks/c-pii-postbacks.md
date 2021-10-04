---
description: U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.
title: PII-postbacks
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
exl-id: 9f0b9d7b-e51d-477b-ae04-72ab09fbc6fd
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# PII-postbacks {#pii-postbacks}

U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.

Wanneer u Adobe SDK wilt gebruiken om PII te verzamelen, zou u een spoorPII vraag moeten verzenden. Hoewel het gebruiken van deze vraag inzameling van PII- gegevens toelaat, verzendt SDK niet automatisch de gegevens naar een eindpunt van Adobe. Een PII type postback moet met het aangewezen eindpunt worden gevormd.

>[!TIP]
>
>Een eindpunt dat HTTPS steunt wordt vereist om het PII postback type te gebruiken.

## PII-postbacks bijhouden {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het dossier SDK en Config aan uw Project IntelliJ IDEA of Eclipse* in [de implementatie van de Kern en levenscyclus](/help/android/getting-started/dev-qs.md) toe.

1. De bibliotheek importeren:

   ```java
   #import "ADBMobile.h"
   ```

1. Wanneer u klaar bent om PII te vangen, vraag `trackPII` om een klap voor deze actie, gebeurtenis, of mening te verzenden:

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```
